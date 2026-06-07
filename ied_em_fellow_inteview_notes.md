# NOTES: interview

General notes:
- electrical contact BCs

# NAME /5

## Presentation + Questions /5
- VVUQ, limitations, feasibility, independence

## Motivation & Drive /5

## Behavioural Competencies /5

## EDI Question /5

## Their Questions /5

------------------------------------------------------------------------
# Nagu Sathappan 2/5
- Depth on simulations not great, awareness of experiments was awful

- Research Fellow at Brunel doing FE using COMSOL, thermal-electro-mech
- Started at Indian Space Research org
- Worked on ROS - interested in robotics

## Presentation + Questions 4/5 for motivation and fusion knowledge, 3/5 for actual research depth
- VVUQ, limitations, feasibility, independence
- Motivation clear, inputs to simulation clear, 
- Didn't really give a plan for how to address the problem
- VVUQ?
- Coupling? Computational tradeoff?
- RQ 3: what do you mean by improve? what is not working right now?
- Slide 7: validation strategy - how did you account for uncertainties in the experimental sensors? What were the key sources of systematic errors in the sensors? Random errors?
    - What were the most important factors when designing your validation experiments?
- Good knowledge of UKAEA but the research gap was not clearly articulated and backed up by literature. Need to be much more specific when defining the problem.

- QUESTIONS: steve on clarifying what PhD was - response ok still generic
    - Response very long...
    - My question: drill into RQ3 - working with plasma, how do we couple plasma then material properties first and boundary conditions. Material properties is definitely important but did not mention coupling... Still not specific enough...     

## Motivation & Drive 3/5 - went off tangent a lot :(
- 1 Very long response to this question and went on to motivation...
- 2 Good response about what UKAEA does, does not know much about actual fusion industry, went off tangent again...
- 4 Did PhD during COVID, really liked making the sensor and reducing lift off, least enjoyed experiments with the furnace 
- 5 Key highlights - build global pipeline, restated the ad. Wants skill developement and collaboration. Want to update existing skills, learn new skills
- 6 - reduce off normal events and deal with extreme temperature conditions?? - not a great response but not a great question  

## Behavioural Competencies 3/5 - generic responses
- 8 Mentioned PhD during COVID - ok
- 9 Always part of a multi-dis team. Works remotely. Gives regular updates through meetings and progress tracker. Not extremely specific
-10 During COVID needed a PCB printed in the uni, contacted someone in the uni to do it. Not a great example...

## Technical Questions 1/5 - very concerned about this maybe they were being put on the spot a bit. Might have been better as a take home assignment?
- 11 Not great... Had to be walked through the question
    - Did mention lorentz force and did get to changing field and inducation, changing magnetic field creates a current.
    - Did not get that ferromagnets only have a force when the B field has a gradient. If ferromagnet in a uniform field then no force.
- 15 - current to apply to get the output, material properties??? Plasma current ??? 
    - measure the current, how can we measure the magnetic field... Not great
- 16 - start with literature review, compare to literature, mentioned simulation calibration but did not focus on validation.
    - Follow up on uncertainties - not great.
    - Talked about parameter sweeps for simulations - again focused on simulation calibration not UQ
    - Ignored experiment UQ, just talked about re-trying experiments 

## EDI Question
- Related to work place culture, maintain a great working culture???

## Their Questions
- What are the research goals in the first year?: would have a lot of academic freedom to go the way you want to. 
- 

------------------------------------------------------------------------
# Tasnia Shahid 4/5
- PhD at strathcylde UQ of PDEs with a maths background
- Main concern is EM/physics knowledge but more than capable of learning this and background knowledge is excellent

- Excellent, knows limitations of own knowledge

## Presentation + Questions 5/5 - WOW! very aware of VVUQ, uncertainty etc
- VVUQ, limitations, feasibility, independence

- Likes open source software
- Actually has references to real literature
- PERFECT: great identification of specific gaps with literature references
- Very aware of VV.
- Great dual specific research questions - 
    - dominant sources of error are normally 
- Research strategy is great 

- Why NNs or PINNs and not another surrogate modelling method that is less data hungry?
    - Integration of real sensor data and simulated data into PINNs - what are the challenges
    - Choose NNs because familiar with the technique - very honest didn't try to justify 
    - Analysed a bunch of regression techniques - 
    - Chose model based on numerical error

- Virtual diagnostics - do you think these will ever give you measurement quality that is the same as a real sensor?

- Step 5: VV Loop - you mention rigorous VV - what do you think makes for rigourous VV?   
    - ensure verification and validation are traceable as well as the metrological chain to SI

- What are the most significant mesh based dependencies 
- Talked about epistemic UQ! what are the most dominant epistemic UQ sources 
    - Why are EM load during off normal events structural limiting?
    - What do you mean by digital twin? And how would we implement a digital twin with limited diagnostics?

- Stephen - question on epistemic UQ:
    - Talked about limited physics background to clarify
    - Linked epistemic UQ to assumptions in the modelling

## Motivation & Drive 4/5
- 1 Good answer
- 2 Reasonable answer about UKAEA, honest about knowledge of fusion industry
- 3 Least - write up, likes experiments and software. Great
- 5 Very interested in the intersection of fusion and UQ, interestin scientific problem. Hoping to gain more experience tackling different physical problems with UQ. 
- 6 Don't like this question on UKAEA impacts, scientists don't care about this. Thinks about things in terms of maths and modelling challenges of complexities. Mentioned funding and political landscape.

## Behavioural Competencies & EDI 4/5
- Excellent, very specific example 
- Good specific example
- Good

## Technical Questions: Ok, but not a physicist 3/5

- Ok, but not EM physicist
- Going to measure the magnetic field and electric charge - 
    - What do we already know? use ground truth values or known states to start calibration
    - Inputs:  and Output: . 
- Mentioned ranges of variables
- Talked about boundary conditions - explanation of atmospheric physics was ok. 
- Used diffusion modeling and turbulent modelling - 

## EDI Question 4/5
- Mentioned women in science, need more people in science from diverse backgrounds. And initiatives for helping EDI. 

## Their Questions 4/5
- Great question on learning EM modelling - excellent, realised weaknesses and looked to plug them
- Good questions on follow up funding

----------------------------------------------------------
# David Brearly /5

- Very experimentally focused
- Not going to be anywhere near as independent as other candidates
- PhD "Failure of composites at cryogenic temperatures" - looking at MRI magnets under loads during operation.  

## Presentation + Questions 4/5
- VVUQ, limitations, feasibility, independence

- Very reliant on PhD research, so scope is limited to previous experience.

- Ok, pacing a bit slow, good overview of off normal events and EM loads
- Nice specific research aim focusing interfaces between dissimilar materials
- Very solid mechanics focused not necessarily multi-physics simulations
- Takes it given that simulations are available

- You mention model validation - how would you approach model validation given a probabilistic simulation and an experiment?
    - Thinks model represents realistic component behaviour... boundary conditions in experimental validation and that these are mirrored in the model. Use full-field data to see if we get the same strain field. Talked about some sources of uncertainty in simulation and experiment but kind of blurred together.
- Probed a bit deeper on body forces and EM loads - different ways of producing body forces and how these are applied.
- What do you think are the key unknowns for multi-physics simulations for fusion component? focusing on thermo-electro-mechanical coupling.
- How will you account for simulation uncertainties when validating against experimental data?
- How will you characterise experimental uncertainties and account for these in your validation analysis?

## Motivation & Drive 3/5, worried about quesitons on phd
1 - fusion, mentioned hyrdogen isotopes creating a plasma and confinement in EM field. Knows we get a He + N + energy. 
2 - UKAEA leading UK contribution to the fusion industry, actually new about STEP/UKIFS, knew about ITER / eurofusion / DEMO. Mentioned other countries working on this.
4 - Really enjoys experiments and learning innovative methods for combined loads at cryo temps. Enjoys conferences and collaboration. Did not enjoy going through the research process would get stuck on details and not have a clear strategy and purpose. Did not like open ended question - :(
5 - Mentioned UKAEAs mission and how this links to net zero and innovation. Actually knew the mission statement. Would like to give back to the community and introducing more people to fusion.
6 - Qualifying materials is a large challenge - this is true and links to materials strategy. Also, talked about robotics. Mentioned cost effective and commercial aspects

## Behavioural Competencies 3/5
- During phd went into a lot of detail and did not keep on top of time sensitive tasks, created a weekly plan and the objectives for these. Reviewed this and was realistic
- During masters project with electrical and materials engineer - designing energy harvestors of remote water ways. Looked at water velocity and getting correct power. 
- Talked about designing a cryostat ok...

## Technical Question 4/5
- Probably not going to get it because Maxwell eqs not really taught in Mech Eng
- Good initial questions and initial conditions
- Asked excellent question about the current in both coils
- Surprisingly good considering no background in EM

- Need to know inputs: EM field and density, directions for the vector, will need to know the geometry and location of the coil pairs. Boundary conditions around coil pairs. 
- Outputs: look at what we are trying to measure with the model. Could use accelerometers to measure acceleration could use these to measure the torque. Could also use non-contact methods like DIC to measure to measure the displacements and speed.

- How would you validate: identify the probability that certain outcomes happen. Not a great answer. Did identify measurement techniques have error. Assumptions of model. 
- Talked about digital twinning? With real time data - seems a bit like overkill
- 

## EDI Question 4/5
- Thinks diversity is important as it brings different mindset and ideas to problems and generate better quality research. Good overall.

## Their Questions /5
- Ok, questions about site and training

----------------------------------------------------------
# Bharat Rawat /5

- Working at university of Liverpool recently finished contract working on digital twins for CERN

## Presentation + Questions /5
- VVUQ, limitations, feasibility, independence
- Good literature review on simulation trust
- Good overview of ROMs
- Knew about SOFE and SOFT as well as fusion specific conferences
- Talked about open source workflows
- Actually had an overview of risks
- Seemed to focus on simulations completely even though gap identified as limits of main code
- Overran a bit - 

- Stephen question on validating with tokamak: sparsity of data?? missed it??
    - Went to approximations of simulation
    
- Didn't really understand the question on validation.

- You mention a large simulation on a cluster without assumptions - do you think this is actually possible?

- Not great in terms of UQ separating systematic and random errors not clear - aleatory and epistemic. Mentioned random errors for experiments. 

- You have correctly identified that a key gap is validation of these simulation codes - 
- What do you think are the domninant sources of uncertainty for simulation of EM-structural coupling?
- You mentioned validation - how would you identify and account for dominant sources of uncertainty in an experiment?

## Motivation & Drive 5/5
- Mentioned light elements combined with a mass effect and get E=Mc^2 and creates fast neutrons that heat steam. Good answer.
- Heard about ukaea during phd at plasma inst research, supervisors friend went to jet. Seen a lot of news articles on next program. Not great answer on fusion industry
- Most enjoyable was overcoming sensor issues had to use stainless steel - enjoyed simulations to design grid to be thermally heated to allow thermal expansion. Did not enjoy purchase delays - based on import delays.  
- Motivating part, during application - liked the broad nature of fellowship and broad possibilities. Wants to gain independence!
- Wants to get complete researcher profile, wants to be in academia and wants to be complete researcher and build skills
- Annoying UKAEA challenges question - good knowledge of funding cuts in research. 

## Behavioural Competencies 4/5
- Doing experiment night shift to do regular cryo filling of SC magnets. Error bars on magnet quench. Needed to stop the magnets to prevent quench. Great example. good follow up on peer review.
- CERN collaboration / hybrdid - focused on simulation but did beam time at CERN. Wanted digital twin model of the penning trap. Started everything from scratch with Monday collaboration meeting.
- During time at Liverpool building particle tracking simulation. Digital twin had two parts. First part was main particle, then cooling ring. No unique workflow for the simulation but no software could solve everything. Mained a connected network of codes to create the model. Ok example. 

## Technical Questions 4/5
- Good, thinking process. But got kind of stuck on eddy current.
- Finally got to induced current from changing magnetic field
- Good knowledge of direction and JxB forces and how this links to current 
- Good on cross product parallel/perpendicular.
- Came to the shear conclusion - best so far
- Dug deep on the experiment - answer ok

## EDI Question /5
- Good answer on everyone having equal opportunity, everybody has their own way of thinking. Can learn a lot 

## Their Questions /5
- Partnership with QST, good questions - 
- Bad question on neutral beams - 
