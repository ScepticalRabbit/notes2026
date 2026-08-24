# Project Specification: High-Accuracy Stereo Camera Calibration

## Background & Motivation

Experiments used to validate the performance of fusion engineering components are often large, time-consuming and expensive. It is therefore desirable to maximise the information obtained from limited experimental campaigns through the use of full-field image-based measurement techniques such as digital image correlation (DIC).

Stereo-DIC uses observations from two or more cameras to reconstruct the three-dimensional shape and deformation of a specimen. Accurate calibration of the camera system is therefore fundamental to the accuracy of the resulting displacement and strain measurements. Errors in the camera calibration propagate directly into the reconstructed geometry and may introduce systematic errors into subsequent DIC measurements.

Most stereo-DIC systems use variants of the conventional pinhole camera model, with lens distortion represented using a relatively small number of parameters. These models are convenient, computationally efficient and well established, but necessarily make assumptions about the geometry of the imaging system. Incomplete modelling of lens distortion, particularly towards the edges of the sensor or across large measurement depths, can leave systematic errors even when the overall calibration reprojection error is small.

Recent work has investigated alternative approaches including dense model-free distortion maps, DIC-based calibration targets, bundle-adjustment methods and ray-based camera models. In a ray-based representation, individual image coordinates are associated directly with lines of sight in three-dimensional space rather than being constrained to pass through a single idealised camera projection centre. This provides a much more general representation of the imaging system and has been demonstrated to reduce systematic reconstruction errors in some stereo measurement configurations. The supplied Bräuer-Burchardt et al. paper, for example, develops a practical ray-based calibration approach and reports substantial reductions in systematic 3D measurement error relative to the corresponding pinhole model.

Digital image correlation provides an additional opportunity for improved camera calibration. Speckled calibration targets can provide a large number of spatially distributed correspondences with sub-pixel localisation accuracy, allowing the imaging system to be characterised much more densely than is possible using conventional sparse calibration features. Recent model-free calibration work has demonstrated dense distortion estimation across almost the complete image sensor using this approach.

The objective of this project is therefore to investigate improved stereo camera calibration methods and develop a high-performance, reusable calibration library for integration into PyVale.

---

## Aims & Objectives

The aim of this project is to develop a software library for accurate stereo camera calibration and three-dimensional reconstruction suitable for stereo-DIC and synthetic imaging applications.

The project should establish a robust conventional calibration capability as a baseline before investigating progressively more flexible camera representations and calibration methods.

The objectives of the project are to:

* Review existing camera calibration approaches used in machine vision, photogrammetry and stereo-DIC.
* Develop a clear representation of calibration observations, camera models and stereo camera systems.
* Implement a high-quality conventional stereo calibration method as a reference implementation.
* Investigate dense calibration approaches using highly distributed image correspondences, including the potential use of DIC on speckled calibration targets.
* Investigate camera representations that relax the assumptions of conventional parametric lens-distortion models.
* Investigate ray-based camera representations in which image coordinates are mapped directly to three-dimensional viewing rays.
* Develop accurate and efficient stereo triangulation algorithms.
* Compare calibration methods based on their resulting three-dimensional measurement accuracy rather than reprojection error alone.
* Develop a C library containing the performance-critical calibration and reconstruction algorithms.
* Provide a clean Python interface suitable for direct use from PyVale.
* Produce a documented and tested software implementation suitable for future extension and research.

The project is intentionally open regarding the final camera representation and optimisation strategy. Candidate approaches should be investigated and evaluated objectively rather than prescribing a single method in advance.

---

## Core Software Requirements

The final software should provide a reusable stereo camera calibration library with a C computational core and a Python interface.

The library should separate three major concepts:

### Calibration Observations

Experimental information used to calibrate the cameras, for example:

* image coordinates;
* corresponding calibration-target coordinates;
* camera identifier;
* calibration-image or target-pose identifier;
* known distances;
* known planar constraints;
* stereo image correspondences.

The software architecture should avoid coupling the calibration algorithms unnecessarily to a particular calibration target.

This should allow future support for:

* checkerboards;
* circular grids;
* coded targets;
* speckled calibration targets;
* active phase targets;
* arbitrary known calibration geometries.

### Camera Models

The library should provide a common interface for mapping between image coordinates and three-dimensional geometry.

At minimum, the project should implement a conventional pinhole camera model with lens distortion as a baseline.

More flexible models should then be investigated. Candidate approaches include:

* higher-order parametric distortion models;
* dense distortion maps;
* interpolated distortion fields;
* spline-based camera models;
* dense ray fields;
* spline or grid-based ray fields.

The final selection should be based on accuracy, numerical robustness, computational cost and implementation complexity.

### Stereo Reconstruction

Given corresponding image coordinates in two calibrated cameras, the library should provide accurate three-dimensional reconstruction.

For a general ray-based representation this reduces to:

```text
left image coordinate  -> left viewing ray
right image coordinate -> right viewing ray

                         ↓

                 ray triangulation

                         ↓

                     3D point
```

The reconstruction implementation should support sub-pixel image coordinates and therefore provide suitable interpolation where camera models are represented discretely.

---

## Work Packages & Deliverables

### WP1 — Literature Review and Software Requirements

Review relevant literature covering:

* conventional camera calibration;
* stereo camera calibration;
* calibration methods used in stereo-DIC;
* lens-distortion modelling;
* dense and model-free distortion calibration;
* ray-based and generic camera models;
* bundle adjustment;
* calibration quality assessment;
* stereo triangulation.

The literature review should identify candidate algorithms for subsequent implementation but should retain flexibility regarding the final method selected.

**Deliverables**

* Short literature review.
* Definition of software requirements.
* Candidate calibration and camera-model approaches.
* Initial software architecture.
* Definition of quantitative validation metrics.

---

### WP2 — Conventional Stereo Calibration Baseline

Develop a conventional stereo camera calibration implementation suitable for use as the baseline against which subsequent methods can be compared.

The implementation should provide:

* intrinsic camera calibration;
* lens-distortion calibration;
* relative stereo camera pose;
* image projection and back-projection;
* stereo triangulation;
* calibration diagnostics.

Existing established implementations such as OpenCV may be used for verification and comparison, but the project should develop sufficient independent functionality to understand and control the complete calibration and reconstruction process.

**Deliverables**

* Working conventional stereo calibration implementation.
* Python prototype interface.
* Comparison against an established calibration library.
* Unit tests using known synthetic camera configurations.
* Initial stereo reconstruction validation.

---

### WP3 — Calibration Validation Framework

Develop a framework for quantitatively assessing camera calibration accuracy.

Validation should extend beyond conventional reprojection error and investigate the errors that calibration introduces into three-dimensional measurements.

Candidate tests include:

* reprojection error;
* reconstruction of known planar surfaces;
* reconstruction of known distances;
* rigid translations;
* known rotations;
* known three-dimensional geometry;
* stereo-DIC displacement measurements.

Synthetic calibration data should be generated where appropriate so that the exact camera geometry and three-dimensional ground truth are known.

**Deliverables**

* Automated calibration validation suite.
* Synthetic calibration datasets with known ground truth.
* Comparison metrics for image-space and three-dimensional errors.
* Baseline assessment of the conventional calibration method.

---

### WP4 — Dense Calibration Methods

Investigate whether calibration accuracy can be improved by increasing the number and spatial distribution of calibration observations.

Particular attention should be given to approaches using speckled calibration targets and DIC to obtain dense, sub-pixel calibration correspondences across the camera sensor.

The project should investigate whether improved observations alone reduce systematic calibration errors before introducing more complicated camera models.

**Deliverables**

* Prototype dense calibration workflow.
* Method for obtaining or importing dense calibration correspondences.
* Comparison between sparse and dense calibration observations.
* Assessment of calibration accuracy across the complete camera field of view.

---

### WP5 — Flexible and Ray-Based Camera Models

Investigate camera representations that reduce the modelling assumptions imposed by conventional parametric lens-distortion models.

Candidate approaches include dense model-free distortion fields and general ray-based camera models.

A ray-based camera model associates an image coordinate directly with a three-dimensional viewing ray. Possible representations include:

* dense per-pixel rays;
* rays represented by intersections with two reference planes;
* regular grids of calibrated rays;
* spline-based ray fields;
* other smooth interpolated representations.

The precise representation and calibration method should be selected through research and numerical testing.

**Deliverables**

* Prototype flexible camera representation.
* Calibration method for the selected representation.
* Sub-pixel ray or distortion evaluation.
* Stereo triangulation using the new model.
* Quantitative comparison against conventional calibration.

---

### WP6 — Optimisation and C Implementation

Once the preferred algorithms have been established through research prototypes, migrate the performance-critical functionality into a standalone C library.

The implementation should prioritise:

* numerical robustness;
* deterministic behaviour;
* clear memory ownership;
* minimal dependencies;
* efficient evaluation of camera models;
* efficient stereo triangulation;
* compatibility with Python through a simple C API.

Optimisation should be driven by profiling rather than performed prematurely.

**Deliverables**

* C calibration and reconstruction library.
* Stable C API.
* Performance benchmarks.
* Numerical regression tests.
* Comparison against the research implementation.

---

### WP7 — Python Interface and PyVale Integration

Develop a clean Python interface around the C library and integrate the resulting functionality into PyVale.

The Python layer should provide:

* user-friendly configuration;
* loading and processing of calibration observations;
* calibration execution;
* camera-model inspection;
* calibration diagnostics;
* serialisation of calibrated camera systems;
* stereo triangulation;
* integration with PyVale camera and DIC workflows.

The interface should hide unnecessary implementation details while retaining access to diagnostics required for research use.

**Deliverables**

* Python bindings.
* PyVale integration.
* Public Python API.
* Calibration file format or serialisation mechanism.
* User documentation.
* Example calibration workflow.
* Complete automated test suite.

---

## Software Workflow

### Inputs

The calibration system should accept:

* calibration images and/or extracted calibration observations;
* known calibration-target geometry;
* camera image dimensions;
* stereo camera identifiers.

Depending on the selected calibration method, additional inputs may include:

* known physical distances;
* multiple target poses;
* planar constraints;
* dense DIC correspondences;
* initial camera parameters;
* initial camera poses.

---

### Calibration Processing

A typical workflow may consist of:

1. Load calibration observations.
2. Perform an initial conventional camera calibration.
3. Determine individual camera intrinsic parameters.
4. Determine relative stereo camera pose.
5. Evaluate calibration residuals.
6. Where required, construct a denser or more flexible camera representation.
7. Optimise the camera representation using the available calibration observations and geometric constraints.
8. Validate the resulting model using independent calibration data.
9. Generate diagnostic information.
10. Serialise the calibrated stereo camera system for subsequent use.

The exact optimisation and camera-model formulation should remain open to investigation during the project.

---

### Outputs

The primary output should be a calibrated stereo camera model that can be stored and subsequently loaded by PyVale.

The library should provide functionality to:

* map image coordinates to viewing rays;
* project three-dimensional points into camera images where supported by the model;
* triangulate corresponding stereo image points;
* calculate calibration residuals;
* report calibration quality metrics;
* save and load calibrated camera systems.

Diagnostic outputs should allow users to inspect spatially varying calibration error rather than relying solely on a single global RMS reprojection value.

---

## Validation Philosophy

The project should distinguish between **calibration fit quality** and **measurement accuracy**.

A camera model may achieve a low image-space reprojection error while retaining systematic errors that affect three-dimensional reconstruction. Calibration methods should therefore be assessed using progressively more physically meaningful metrics:

1. Image-space reprojection error.
2. Spatial distribution of calibration residuals.
3. Three-dimensional reconstruction accuracy.
4. Reconstruction of known geometric constraints.
5. Stereo displacement accuracy.
6. Stereo-DIC strain accuracy.

The principal success criterion should be improvement in three-dimensional measurement accuracy rather than reduction of reprojection error alone.

Synthetic imaging should be used where possible because it allows the true camera mapping, target geometry and reconstructed three-dimensional coordinates to be known exactly.

---

## Research Freedom

This project intentionally does not prescribe a single final calibration algorithm.

The investigator should be encouraged to compare alternative approaches and simplify the final solution wherever possible.

For example, it may be found that:

* improved calibration observations provide most of the required accuracy improvement;
* a dense distortion field is sufficient without requiring a fully non-central camera model;
* a compact spline representation provides equivalent accuracy to a dense ray lookup table;
* full ray-based calibration provides significant advantages only for particular imaging configurations.

Any of these outcomes would represent a useful result provided that the conclusions are supported by quantitative validation.

The aim is therefore not to implement a ray-based model at all costs, but to determine an accurate, general and practical calibration methodology suitable for PyVale.

---

## Key Reference Literature

The following papers provide a starting point for the project rather than an exhaustive reading list. Further literature review and selection of appropriate methods form part of WP1.

### 1. Bräuer-Burchardt et al. — Ray-Based Camera Modelling

C. Bräuer-Burchardt, R. Ramm, P. Kühmstedt and G. Notni, *The Duality of Ray-Based and Pinhole-Camera Modeling and 3D Measurement Improvements Using the Ray-Based Model*, Sensors, 22, 7540, 2022. DOI: 10.3390/s22197540.

This paper provides the primary introduction to the proposed ray-based direction. It describes the relationship between pinhole and ray-based camera models, practical representations of per-pixel viewing rays, calibration refinement and stereo reconstruction.

### 2. Genovese — Dense Model-Free Calibration

K. Genovese, *Single-image camera calibration with model-free distortion correction*, Optics and Lasers in Engineering, 181, 108348, 2024. DOI: 10.1016/j.optlaseng.2024.108348.

This work uses DIC registration of a planar speckle target to obtain a dense distribution of calibration correspondences over the complete image and constructs a model-free distortion map. It is particularly relevant to combining DIC with flexible camera representations.

### 3. Chen, Genovese & Pan — Stereo-DIC Calibration

B. Chen, K. Genovese and B. Pan, *Calibrating large-FOV stereo digital image correlation system using phase targets and epipolar geometry*, Optics and Lasers in Engineering, 2021. DOI: 10.1016/j.optlaseng.2021.106854.

This paper provides a DIC-specific stereo calibration methodology in which camera intrinsics, stereo correspondences and geometric constraints are treated separately. It demonstrates the use of DIC-derived homologous points for stereo calibration and validates the resulting calibration using physical deformation measurements.

### 4. Su et al. — Bundle Adjustment and Auto-Calibration

Z. Su, L. Lu, S. Dong, F. Yang and X. He, *Auto-calibration and real-time external parameter correction for stereo digital image correlation*, Optics and Lasers in Engineering, 121, 46–53, 2019. DOI: 10.1016/j.optlaseng.2019.03.018.

This work investigates stereo-DIC calibration using bundle adjustment and demonstrates that camera calibration and correction can be formulated more generally than conventional target-based calibration. It is particularly relevant to optimisation strategy and future extension towards camera self-calibration.

### 5. Shao & He — Calibration Stability and Camera Motion

X. Shao and X. He, *Camera motion-induced systematic errors in stereo-DIC and speckle-based compensation method*, Optics and Lasers in Engineering, 149, 106809, 2022. DOI: 10.1016/j.optlaseng.2021.106809.

This paper demonstrates how small changes in stereo camera geometry after calibration can produce systematic errors in DIC measurements and investigates the use of the specimen speckle pattern itself to correct relative camera motion. It provides useful context for validation and possible future extension of the library beyond static calibration.

These references should be treated as starting points. The investigator is expected to identify additional relevant literature and is free to pursue alternative methods where they offer advantages.

---

## Expected Outcome

The primary outcome of the project should be a validated stereo camera calibration library integrated into PyVale.

The final software should provide:

```text
Calibration observations
          ↓
Stereo calibration
          ↓
Calibrated camera models
          ↓
Pixel-to-ray mapping
          ↓
Stereo triangulation
          ↓
3D coordinates
```

with a high-performance C implementation beneath a simple Python interface.

The project should establish progressively more capable calibration methods, beginning with a conventional stereo calibration baseline and advancing towards dense, model-free or ray-based approaches where these provide measurable improvements.

The ultimate success criterion is the ability to **reduce calibration-induced systematic error in stereo-DIC shape, displacement and strain measurements while providing a robust and maintainable software capability for PyVale**.
