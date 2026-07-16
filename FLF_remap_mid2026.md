# FLF Strategy Reset Cheatsheet

## Simulation-Driven Experimental Design

**Purpose:** Decide the grand challenge, year-4 flagship outcome, MVP demonstrators, paper pathway, and impact plan.

---

# 0. Meeting frame

**Time:** 1 hour
**Audience:** Direct team
**Mode:** Decisive first, motivational second
**Main output:** A shared direction that connects software + OVal-DB into one engineering methodology.

---

# 1. Opening statement

We are 1 year 9 months into a 4-year Future Leaders Fellowship.

The original roadmap has evolved, which is a good thing. Today is not a normal status meeting. The purpose is to remap the fellowship around a single coherent goal:

> **Creating a simulation-driven experimental design platform, validated against real experimental data, that becomes a new engineering methodology for high-value component validation inside and outside fusion.**

We have two main arms:

1. **Software for experimental design and analysis**
   pyvale, Riley, synthetic diagnostics, DIC analysis, validation metrics, sensor placement, test design.

2. **OVal-DB: the Open Validation Database**
   The real experimental datasets that prove the software works in practice.

By the end of this meeting, I want us to agree:

* The **grand challenge**
* The **year-4 flagship outcome**
* The **first MVP demonstrator**
* The **key technical milestones**
* The **paper and impact pathway**
* Who owns what next

---

# 2. The north-star question

Ask the team:

> **By the end of year 4, what should be demonstrably true that is not true now?**

Capture answers under three headings:

| Software capability    | Validation evidence      | Adoption / impact      |
| ---------------------- | ------------------------ | ---------------------- |
| What can the tools do? | What does OVal-DB prove? | Who uses this and why? |

Useful prompts:

* What should an external engineer be able to do with our methodology?
* What should OVal-DB prove?
* What should our software predict, optimise, or explain?
* What would make this clearly more than another DIC/simulation/data project?
* What would make people in fusion, aerospace, nuclear, or advanced manufacturing care?

---

# 3. Candidate grand challenge statements

Discuss and refine these.

## Option A — methodology framing

> Create a simulation-driven experimental design methodology that tells engineers what to measure, where to measure it, and how much trust to place in the resulting validation evidence.

## Option B — software/data platform framing

> Build and validate an open software-and-data platform for designing high-value validation experiments using predictive simulation, synthetic diagnostics, and real-world benchmark datasets.

## Option C — impact framing

> Move high-value component validation from expert-led experimental judgement to simulation-guided, uncertainty-aware, evidence-based engineering decision making.

## Suggested combined version

> **Create a simulation-driven experimental design methodology that tells engineers what to measure, where to measure it, and how much trust to place in the resulting validation evidence, moving high-value component validation from expert judgement toward uncertainty-aware, evidence-based engineering decision making.**

Decision to make:

> What is our preferred grand challenge statement?

---

# 4. Year-4 flagship outcome

Proposed strawman:

> **By the end of the first 4 years, we will have demonstrated a simulation-driven experimental design platform that can take a candidate validation problem, simulate plausible diagnostic outputs, optimise what should be measured, compare predictions against open benchmark experimental data, and produce uncertainty-aware validation evidence suitable for engineering decision making.**

Short version:

> **A validated software-and-data workflow for deciding what to measure, where to measure it, and how to interpret the result for high-value component validation.**

Decision to make:

> Is this the right year-4 flagship outcome?
> What would we add, remove, or sharpen?

---

# 5. Candidate MVP demonstrators

We cannot validate the whole methodology at once. We need MVP demonstrators that are small enough to publish, but strong enough to prove the platform.

---

## MVP 1 — Synthetic-to-real image-based validation

**Core question:**

> Can we use Riley + pyvale + real OVal-DB DIC data to separate synthetic-image error, DIC systematic error, and physical-model validation error?

**Software side:**

* Riley
* pyvale
* synthetic DIC image generation
* renderer convergence
* DIC uncertainty
* diagnostic simulation

**OVal-DB side:**

* Controlled DIC benchmark datasets
* Known geometry/loading/boundary conditions
* Real image data with uncertainty information

**Why it matters:**

This proves that our synthetic diagnostic workflow can support real image-based validation.

**Possible paper:**

> Renderer-converged synthetic image generation for uncertainty-aware DIC validation.

---

## MVP 2 — Sensor or image placement optimisation

**Core question:**

> Can we use simulation to decide where sensors, cameras, or image regions should be placed to maximise validation value?

**Software side:**

* Sensor simulation
* Information gain
* Entropy / KL divergence
* Optimisation
* Mechanical and thermal sensor models
* DIC/image-region design

**OVal-DB side:**

* Real experiment with multiple possible sensor layouts
* Retrospective or prospective comparison of sensor choices
* Benchmark task: predict which measurement configuration is most informative

**Why it matters:**

This is easy for industry to understand:

> Put the sensors where they generate the most useful validation evidence.

**Possible paper:**

> Simulation-driven sensor placement for high-value component validation using open benchmark datasets.

---

## MVP 3 — Validation metrics / model adequacy

**Core question:**

> Given simulation predictions and experimental observations, can we quantify whether the model is good enough for the decision being made?

**Software side:**

* Validation metrics
* Uncertainty propagation
* Model discrepancy
* Decision thresholds
* Evidence scoring

**OVal-DB side:**

* Datasets with known loads, diagnostics, and uncertainty
* Comparison between model predictions and measurements
* Clear acceptance/rejection/adequacy criteria

**Why it matters:**

This turns experimental data into engineering evidence.

**Possible paper:**

> Decision-oriented validation metrics for simulation-driven experimental design.

---

## MVP 4 — MT2.0 / test design

**Core question:**

> Can we design a test that produces the most useful validation evidence for a target model, component, or failure mode?

**Software side:**

* Test design
* Synthetic diagnostics
* Forward models
* Uncertainty-aware optimisation
* Comparison of candidate experiments

**OVal-DB side:**

* Physical experiments designed or reinterpreted through the platform
* Benchmark datasets for testing alternative experimental designs

**Why it matters:**

This is the broadest and most ambitious version of the methodology.

**Possible paper:**

> Simulation-driven test design for model validation of high-value engineering components.

---

# 6. MVP selection discussion

Ask the team:

> Which MVP gives us the best combination of publishability, strategic value, and impact?

Score each candidate quickly from 1–5.

| MVP                                 | Publishable soon? | Strategic value? | OVal-DB fit? | Industry/internal impact? | Total |
| ----------------------------------- | ----------------: | ---------------: | -----------: | ------------------------: | ----: |
| Synthetic-to-real DIC validation    |                   |                  |              |                           |       |
| Sensor/image placement optimisation |                   |                  |              |                           |       |
| Validation metrics / model adequacy |                   |                  |              |                           |       |
| MT2.0 / test design                 |                   |                  |              |                           |       |

Decision to make:

> What is our first MVP demonstrator?

---

# 7. Paper ladder

The paper pathway should tell one coherent story.

## Paper 1 — Foundation capability

**Theme:** Synthetic diagnostics / renderer convergence / DIC uncertainty

**Purpose:**

> Prove that the synthetic data pipeline is trustworthy.

Possible title:

> Renderer-Converged Synthetic Image Generation for Uncertainty-Aware DIC Validation

---

## Paper 2 — Experimental design method

**Theme:** Sensor placement, image placement, or validation metrics

**Purpose:**

> Prove that the software can make useful experimental design decisions.

Possible title:

> Simulation-Driven Sensor Placement for High-Value Component Validation

---

## Paper 3 — End-to-end OVal-DB validation case study

**Theme:** Full software + real dataset demonstrator

**Purpose:**

> Prove that the methodology works on real validation data.

Possible title:

> An Open Benchmark Demonstration of Simulation-Driven Experimental Design for Engineering Validation

---

## Paper 4 — Broader methodology / impact paper

**Theme:** The complete engineering methodology

**Purpose:**

> Position the fellowship as a new approach to validation, not just a set of tools.

Possible title:

> Simulation-Driven Experimental Design as an Engineering Methodology for High-Value Component Validation

---

# 8. Impact pathway

Use this pipeline:

| Stage             | Output                             | Purpose                     |
| ----------------- | ---------------------------------- | --------------------------- |
| MVP demo          | Small working workflow             | Show the concept works      |
| Paper             | Peer-reviewed method/proof         | Establish credibility       |
| OVal-DB release   | Dataset + benchmark task           | Let others test against it  |
| Internal adoption | Apply to UKAEA/fusion programme    | Prove operational value     |
| External adoption | Transfer to non-fusion engineering | Show the method generalises |

Ask:

* What is the first demonstrator we can show internally?
* What dataset supports it?
* What software needs to exist?
* Who is the first internal customer?
* Who outside fusion would care first?
* What would a convincing “demo day” version look like?
* What needs to be open, documented, packaged, or simplified for adoption?

---

# 9. Six-month milestones

Ask:

> What are the three things that, if we deliver them in the next six months, make the year-4 outcome feel inevitable?

Possible milestone categories:

## Software milestones

* Riley/pyvale synthetic-to-real DIC workflow
* Sensor simulation for mechanical and/or thermal diagnostics
* Initial sensor placement optimisation method
* Validation metric prototype
* Reproducible benchmark scripts
* Documentation and tutorial examples

## OVal-DB milestones

* First curated benchmark dataset
* Dataset metadata standard
* Uncertainty description for measurements
* Baseline simulation model
* Baseline validation task
* Public or internal release candidate

## Impact milestones

* First MVP paper drafted
* Internal demonstration to target programme
* External conference abstract
* OVal-DB landing page or technical note
* Industry-facing explainer
* Adoption target identified

Decision to make:

> What are our top three six-month milestones?

---

# 10. Ownership

Before closing, assign owners.

| Workstream              | Owner | Next concrete output | Target date |
| ----------------------- | ----- | -------------------- | ----------- |
| Grand challenge wording |       |                      |             |
| MVP demonstrator        |       |                      |             |
| Paper 1                 |       |                      |             |
| Paper 2                 |       |                      |             |
| OVal-DB first dataset   |       |                      |             |
| Software workflow       |       |                      |             |
| Impact / adoption plan  |       |                      |             |

---

# 11. Closing question

End with this:

> **What would make us proud to say, at the end of year 4, that this fellowship changed how engineering validation is done?**

Then close with:

> Our goal is not just to write software or collect datasets. Our goal is to create a new engineering methodology: simulation-driven experimental design for high-value component validation. The software and OVal-DB are the two halves of the same proof.

---

# 12. Final decisions to capture

By the end of the meeting, capture:

* [ ] Grand challenge statement
* [ ] Year-4 flagship outcome
* [ ] First MVP demonstrator
* [ ] Key OVal-DB dataset for MVP
* [ ] First software workflow to demonstrate
* [ ] Top 3 six-month milestones
* [ ] Paper ladder
* [ ] First internal impact target
* [ ] First external impact target
* [ ] Owners and next outputs

---

# One-sentence summary

> We are turning software and OVal-DB into one coherent engineering methodology for deciding what to measure, where to measure it, and how to interpret the resulting evidence for high-value component validation.
