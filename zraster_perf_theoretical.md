# Theoretical Performance Bounds: Higher-Order Element Software Rasteriser

**Target Architecture & Assumptions:**
* **Instruction Set:** AVX-512 (8-wide `f64` / Double Precision)
* **Execution:** Single-threaded
* **Clock Speed:** ~4.0 GHz sustained ($4 \times 10^9$ cycles/second)
* **Sampling:** 2x2 SSAA (4 sub-pixel evaluations = 1 Final Pixel)
* **Geometry:** Full-screen 1-2 element tests (Tri6, Quad8, Quad9) -> Zero geometry overhead.

---

### 1. Cycle Budget Estimates (Per Sub-Pixel)

*Note: In an 8-wide AVX-512 vector, 8 sub-pixels are processed concurrently. The cycle costs below are amortized effective costs per individual sub-pixel evaluation assuming high ALU utilization.*

* **Coarse Hull Check:** ~5 - 10 cycles
    * Barycentric edge functions; negligible amortized cost when vectorized.
* **Newton-Raphson Solver:** ~30 - 60 cycles
    * Assumes 2-3 iterations with spatial gradient extrapolation for the initial guess.
    * AVX-512 `vfmadd231pd` (f64 FMA) handles the shape function evaluations and $2\times2$ Jacobian inversion efficiently, provided lane divergence is minimized.
* **Texture Fetch & Interpolation:**
    * **Cubic (16 texels):** ~50 - 100 cycles (assuming excellent L1 cache hits via Morton ordering).
    * **Quintic (36 texels):** ~150 - 300 cycles. (f64 doubles the memory footprint versus f32, placing immense pressure on L1 bandwidth and AVX-512 ZMM register allocation).

---

### 2. Theoretical Throughput Scenarios

**Scenario A: Cubic Interpolation (Highly Optimized)**
* **Conditions:** Morton ordered textures, ~100% L1 cache hit rate, minimal NR divergence, 32 ZMM registers preventing stack spilling.
* **Estimated Cost:** ~100 cycles per sub-pixel.
* **Cost per Final Pixel (2x2 SSAA):** 400 cycles.
* **Theoretical Limit:** $4 \times 10^9 / 400 \approx$ **10 MPx/s**

**Scenario B: Cubic Interpolation (Typical / Memory Bound)**
* **Conditions:** Linear texture memory, occasional L2 fetches, moderate NR divergence.
* **Estimated Cost:** ~250 cycles per sub-pixel.
* **Cost per Final Pixel (2x2 SSAA):** 1000 cycles.
* **Theoretical Limit:** $4 \times 10^9 / 1000 \approx$ **4 MPx/s**

**Scenario C: Quintic Interpolation (Memory/Register Bound)**
* **Conditions:** 36 `f64` texel fetches heavily tax the L1 cache. Math overhead is significant, requiring aggressive instruction pipelining and Horner's method to avoid ALU stalls.
* **Estimated Cost:** ~400 cycles per sub-pixel.
* **Cost per Final Pixel (2x2 SSAA):** 1600 cycles.
* **Theoretical Limit:** $4 \times 10^9 / 1600 \approx$ **2.5 MPx/s**

---

### 3. Current Engine Validation

* **Observed Cubic:** ~6 MPx/s (Sits comfortably in the upper half of the theoretical bound).
* **Observed Quintic:** ~4 MPx/s (Significantly exceeds the typical memory-bound theoretical limit of 2.5 MPx/s).

**Conclusion:** Hitting 4 MPx/s for f64 quintic interpolation on a single thread indicates exceptional cache locality and memory layout. The engine is bypassing the expected L1 memory latency wall and is currently bottlenecked almost entirely by raw L1 bandwidth and ALU throughput (FMA instruction latency).

# Theoretical Performance Bounds: Linear Triangle Software Rasteriser

**Target Architecture & Assumptions:**
* **Instruction Set:** AVX-512 (8-wide `f64` / Double Precision)
* **Execution:** Single-threaded
* **Clock Speed:** ~4.0 GHz sustained ($4 \times 10^9$ cycles/second)
* **Sampling:** 2x2 SSAA (4 sub-pixel evaluations = 1 Final Pixel)
* **Geometry:** Full-screen 1-2 element tests (Linear Triangles) -> Direct barycentric interpolation, NO Newton-Raphson solver.

---

### 1. Cycle Budget Estimates (Per Sub-Pixel)

*Note: In an 8-wide AVX-512 vector, 8 sub-pixels are processed concurrently. The cycle costs below are amortized effective costs per individual sub-pixel evaluation.*

* **Edge Setup & Barycentric Weights:** ~5 - 10 cycles
    * Direct evaluation via half-space edge functions. Amortized cost is negligible.
* **Coordinate Interpolation:** ~5 cycles
    * 1 or 2 FMA instructions per attribute ($u, v$) using the calculated barycentric weights.
* **Texture Fetch & Interpolation:**
    * **Cubic (16 texels):** ~50 - 90 cycles (Your memory layout is proven highly optimal based on previous 6 MPx/s results).
    * **Quintic (36 texels):** ~150 - 200 cycles. (Freed from the NR solver's register pressure, the compiler can dedicate nearly all 32 ZMM registers to the quintic spline math and memory loads).

---

### 2. Theoretical Throughput Scenarios

**Scenario A: Cubic Interpolation (Linear Triangles)**
* **Conditions:** Pure L1 cache bandwidth and spline-FMA bound. ALUs are dedicated entirely to evaluating the 16-texel cubic splines.
* **Estimated Cost:** ~60 to 100 cycles per sub-pixel.
* **Cost per Final Pixel (2x2 SSAA):** 240 to 400 cycles.
* **Theoretical Expectation:** $4 \times 10^9 / 300 \approx$ **12 to 16 MPx/s**

**Scenario B: Quintic Interpolation (Linear Triangles)**
* **Conditions:** Still heavily taxes L1 cache bandwidth with 36 `f64` fetches, but instruction pipelining improves massively without the NR solver branching and state management.
* **Estimated Cost:** ~160 to 220 cycles per sub-pixel.
* **Cost per Final Pixel (2x2 SSAA):** 640 to 880 cycles.
* **Theoretical Expectation:** $4 \times 10^9 / 750 \approx$ **5 to 6.5 MPx/s**

---

### 3. Summary vs. Higher-Order Elements

By removing the Newton-Raphson solver overhead:
* **Cubic** performance should practically double (jumping from your current 6 MPx/s up to the **12-16 MPx/s** range).
* **Quintic** performance will see a smaller relative boost (jumping from your current 4 MPx/s up to the **5-6.5 MPx/s** range) because the 36-texel memory fetch latency remains the dominant limiting factor, even with completely free ALUs.
