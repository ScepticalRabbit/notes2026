# Project Specification: Electromagnetic Effects on DIC Measurement Uncertainty

## Background & Motivation

Digital image correlation (DIC) is increasingly used for full-field deformation measurement in demanding engineering experiments. In fusion engineering, there is growing interest in applying DIC to components subjected to strong electromagnetic loading, including experiments involving electromagnetic body forces in facilities such as CHIMERA.

For these experiments, cameras, lenses, mounts, cables and associated electronics may be exposed to strong static or time-varying electromagnetic fields. These fields may affect the measurement system through several possible mechanisms, including electromagnetic interference in the camera electronics, induced currents in cables or conductive structures, changes in camera timing or image response, and mechanical forces or heating caused by eddy currents in camera mounts and surrounding hardware.

Even where the camera continues to operate normally, small changes in image intensity, spatial noise, camera position or orientation may introduce additional bias or variance into DIC displacement and strain measurements.

A review of the available literature suggests that strong electromagnetic interference is recognised as a potential limitation for camera-based deformation measurements, but there is little or no systematic experimental work quantifying how electromagnetic-field strength and temporal characteristics affect DIC measurement uncertainty.

This project will experimentally determine whether strong electromagnetic fields measurably affect DIC cameras and quantify how any observed effects propagate into displacement and strain uncertainty. Where significant degradation is observed, shielding or mitigation approaches will be developed and evaluated.

The project should remain exploratory. The investigator is expected to refine the experimental methodology as the dominant physical effects become clear.

---

## Aims & Objectives

The aim of this project is to experimentally characterise the effect of strong electromagnetic fields on the uncertainty of digital image correlation measurements and to develop practical mitigation strategies where required.

The objectives are to:

* Characterise changes in raw camera response as a function of electromagnetic loading.
* Quantify the effect of electromagnetic exposure on DIC displacement and strain uncertainty.
* Distinguish between random noise, systematic image errors and apparent motion of the camera system.
* Investigate the influence of both field magnitude and time-varying electromagnetic effects.
* Determine whether camera orientation, acquisition settings, cabling or mounting configuration affect susceptibility.
* Investigate mechanical effects on camera mounting systems, including forces, vibration, heating and deformation caused by induced or eddy currents.
* Identify the dominant mechanisms responsible for any observed degradation.
* Develop and experimentally assess shielding, mounting or other mitigation approaches where necessary.
* Establish practical operating recommendations for DIC measurements in strong electromagnetic environments.
* Publish the results as a journal article submitted to *Experimental Mechanics*.

---

## Experimental Variables

The precise experimental design should be developed during the project, but the following variables should be considered.

### Electromagnetic Loading

Relevant controlled or measured quantities may include:

* magnetic-field magnitude;
* magnetic-field direction;
* spatial field gradient;
* field frequency;
* field ramp rate;
* pulse duration;
* current waveform;
* time derivative of the magnetic field;
* relative position of the camera and field source.

The project should consider both static and time-varying fields where experimentally possible.

### Camera Configuration

Candidate variables include:

* camera model and sensor type;
* camera orientation relative to the applied field;
* exposure time;
* frame rate;
* analogue or digital gain;
* trigger mode;
* image bit depth;
* region-of-interest and readout mode.

A complete factorial investigation is not required. Parameters should be varied where there is a plausible physical reason that they may influence the result.

### Electrical Configuration

The project should consider whether electromagnetic effects originate from the camera itself or from associated electrical connections.

Relevant variables may include:

* power-supply arrangement;
* data-cable type and routing;
* trigger cables;
* cable length;
* shielding;
* grounding;
* location of support electronics.

Where practical, experiments should distinguish exposure of the camera head from exposure of cabling and other electronics.

### Mechanical Configuration

The camera mounting system must be treated as part of the measurement chain.

Strong or rapidly changing magnetic fields may induce currents and forces in conductive camera mounts, optical rails, fasteners or surrounding structures. These may cause:

* camera translation;
* camera rotation;
* vibration;
* transient deformation;
* thermal expansion;
* changes in stereo camera geometry.

These effects could create apparent DIC errors even if the camera electronics themselves are unaffected.

The project should therefore consider:

* mount material;
* conductive versus non-conductive mounting components;
* mount stiffness;
* camera-to-target distance;
* mechanical natural frequencies;
* temperature;
* independent measurement of camera or mount motion where feasible.

Potential comparisons could include conventional metallic mounting systems and alternative low-conductivity or non-metallic configurations.

---

## Measured Quantities

The experimental campaign should distinguish between effects on the camera image and effects on the resulting DIC measurement.

### Camera-Level Measurements

Candidate quantities include:

* mean grey level;
* grey-level variance;
* temporal noise;
* spatial noise;
* fixed-pattern noise;
* row or column artefacts;
* intensity drift;
* image sharpness;
* apparent image translation;
* dropped or corrupted frames;
* frame timing;
* frequency content of image fluctuations.

Where the applied field varies with time, camera data should be synchronised with field or coil-current measurements wherever possible.

### DIC-Level Measurements

The primary measurement outputs should include:

* displacement bias;
* displacement standard deviation;
* apparent displacement under zero-motion conditions;
* apparent strain under zero-strain conditions;
* spatial structure in displacement and strain errors;
* stereo reconstruction error;
* temporal variation of the measured displacement field.

The project should seek to separate:

* random uncertainty;
* systematic image-processing bias;
* rigid motion of the camera;
* deformation of the camera mounting system;
* true electromagnetic effects on camera electronics.

---

## Work Packages & Deliverables

### WP1 — Literature Review and Experimental Design

Review relevant literature covering:

* DIC measurement uncertainty;
* camera noise and its effect on DIC;
* camera motion and stereo-DIC error;
* camera self-heating and environmental drift;
* DIC in harsh electromagnetic environments;
* electromagnetic compatibility of digital cameras and imaging electronics;
* eddy-current forces and heating in structures exposed to changing magnetic fields;
* electromagnetic shielding techniques.

The review should be used to refine the experimental programme rather than prescribe it completely.

**Deliverables**

* Short literature review.
* Experimental requirements.
* Initial test matrix.
* Definition of uncertainty metrics.
* Identification of relevant field measurements and environmental measurements.

---

### WP2 — Baseline Camera and DIC Characterisation

Establish the zero-field behaviour of the selected camera system.

Acquire stationary image sequences and quantify the baseline camera noise and DIC measurement uncertainty.

Where practical, investigate the influence of basic acquisition settings such as exposure and gain.

**Deliverables**

* Baseline camera noise characterisation.
* Baseline displacement and strain uncertainty.
* Repeatable reference experimental configuration.
* Automated or documented analysis procedure.

---

### WP3 — Electromagnetic Camera Characterisation

Expose the camera system to controlled electromagnetic loading while imaging a stationary target.

Increase the electromagnetic loading over a suitable range and quantify any changes in raw camera response.

Where possible, investigate whether any effects correlate with:

* field magnitude;
* field direction;
* field ramp rate;
* excitation frequency;
* camera orientation.

The investigator should adapt the experiment if unexpected image artefacts or failure mechanisms are identified.

**Deliverables**

* Camera response versus electromagnetic loading.
* Identification of significant image artefacts or noise mechanisms.
* Assessment of field conditions under which camera behaviour changes.
* Recommended variables for subsequent DIC testing.

---

### WP4 — DIC Uncertainty Under Electromagnetic Loading

Quantify the effect of electromagnetic exposure on DIC measurement uncertainty.

A Reu-style sub-pixel displacement experiment should be considered as one possible method for obtaining precisely known displacement increments. Other suitable approaches may include precision translation stages, rigid stationary targets or independently measured physical motion.

Experiments should investigate both:

* zero-displacement or zero-strain measurements; and
* known imposed displacements.

For stereo-DIC, a rigid target should also be considered so that apparent three-dimensional motion and strain can be measured while the true deformation remains zero.

**Deliverables**

* DIC displacement uncertainty versus electromagnetic loading.
* DIC strain uncertainty versus electromagnetic loading.
* Separation of systematic and random measurement errors.
* Assessment of whether electromagnetic exposure produces practically significant DIC degradation.

---

### WP5 — Camera Mounting and Mechanical Effects

Investigate whether apparent measurement errors originate from physical movement or deformation of the camera mounting system.

Particular attention should be given to time-varying fields capable of generating eddy currents in conductive structures.

Potential investigations may include:

* changing mount material;
* reducing conductive loops;
* comparing metallic and electrically insulating mounting arrangements;
* measuring mount temperature;
* independently monitoring camera motion;
* investigating vibration during field ramps or pulses.

The exact experimental method should be selected based on observations from the earlier work packages.

**Deliverables**

* Assessment of camera-mount susceptibility to electromagnetic loading.
* Identification of rigid-body camera motion or mount deformation where present.
* Separation of mount-induced errors from electronic camera effects.
* Recommendations for camera mounting in high-field experiments.

---

### WP6 — Shielding and Mitigation

Where measurable degradation is identified, develop and assess suitable mitigation methods.

Candidate approaches may include:

* conductive electromagnetic shielding;
* alternative grounding arrangements;
* cable shielding or rerouting;
* optical-fibre communication;
* relocation of sensitive electronics;
* non-conductive camera mounts;
* reduction of conductive loops;
* vibration isolation;
* thermal management.

The shielding strategy should be driven by the observed failure mechanism rather than selected in advance.

The most promising mitigation should be tested using the same uncertainty measurements used for the unshielded system.

**Deliverables**

* Candidate mitigation concepts.
* Experimental comparison of unshielded and mitigated configurations.
* Quantification of uncertainty reduction.
* Practical recommendations for DIC deployment in strong electromagnetic environments.

---

### WP7 — Integrated Demonstration and Publication

Demonstrate the final measurement configuration under the most representative electromagnetic conditions available.

The final experimental campaign should combine:

* representative field conditions;
* selected camera settings;
* selected mounting configuration;
* selected shielding or mitigation;
* DIC measurement uncertainty assessment.

The results should then be prepared for publication.

**Deliverables**

* Final validated experimental dataset.
* Recommended operating and mitigation guidance.
* Complete uncertainty analysis.
* Journal manuscript submitted to *Experimental Mechanics*.

---

## Suggested Experimental Progression

A suitable progression may be:

1. Stationary target with no electromagnetic field.
2. Stationary target with increasing electromagnetic loading.
3. Known sub-pixel or physical displacement with increasing electromagnetic loading.
4. Stereo rigid-target measurements under electromagnetic loading.
5. Investigation of mounting and camera motion.
6. Identification of dominant degradation mechanisms.
7. Implementation of shielding or mitigation.
8. Repeat of the most sensitive tests with the mitigated configuration.

This sequence is intentionally flexible and should be modified as evidence is collected.

---

## Validation Philosophy

The project should avoid treating camera operation as a binary condition in which the system either works or fails.

The important question is whether electromagnetic exposure changes the uncertainty of the resulting engineering measurement while the acquired images may still appear visually acceptable.

The study should therefore distinguish three levels of response:

### Imaging Response

Does the electromagnetic environment measurably alter the raw camera images?

### DIC Response

Do those changes increase displacement or strain bias and variance?

### Measurement-System Response

Are apparent DIC errors actually caused by the camera electronics, or by changes elsewhere in the measurement system such as cable coupling, camera motion, mount deformation or thermal effects?

This separation is important for determining appropriate mitigation.

---

## Research Freedom

The project deliberately leaves significant freedom in the detailed experimental methodology.

The investigator should be encouraged to:

* refine the test matrix based on early observations;
* introduce alternative displacement standards where useful;
* investigate unexpected failure mechanisms;
* modify the field variables examined;
* develop alternative shielding or mounting concepts;
* introduce additional diagnostics where they help distinguish between competing explanations.

A null result is also valuable. If no measurable increase in DIC uncertainty is observed within a well-characterised electromagnetic operating envelope, this provides an experimentally supported limit for future DIC experiments.

The objective is therefore not to demonstrate that electromagnetic fields necessarily degrade DIC measurements, but to determine experimentally **whether, when and by what mechanism they do so**.

---

## Expected Outcome

The primary outcome of the project should be an experimentally validated understanding of the effect of strong electromagnetic environments on DIC measurement uncertainty.

The project should establish:

* whether camera image quality changes with electromagnetic loading;
* whether DIC displacement or strain uncertainty increases;
* which electromagnetic characteristics are most important;
* whether camera mounting systems introduce additional errors through induced currents, forces, vibration or heating;
* the dominant physical mechanisms responsible for any observed effects;
* practical methods for mitigating these effects.

The final outcome should be a set of experimentally justified recommendations for deploying DIC cameras in electromagnetic fusion-engineering experiments and a journal article submitted to *Experimental Mechanics*.
