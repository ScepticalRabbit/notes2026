# Swansea PhD interview
3 projects:
1 - digital twin validation and UQ
2 - material failure and stochastics
3 - neutronics

1. Introduction of panel members and the applicant - Myself 
2. 10-minute presentation from the applicant - Applicant 
3. Multiple follow-up questions - thoroughly testing the applicant’s knowledge of the presentation 
4. Why do they want to do a PhD, why fusion and why Swansea? - Myself 
5. Questions on computational mechanics aspects - FE, other numerical methods, algorithms - 2nd Member of the panel 
6. Questions on ML and AI related questions to evaluate the applicant’s knowledge - 3rd panel member 
7. Questions on programming experience, languages used, ML libraries used, open source codes etc - Myself 
8. Any other question from panel members including any fusion linked experience 
9. Applicant asks questions to the panel 
10. End

# General Questions
- How do you identify the most promising directions or research?
- Walk me through how you solved problem X?
- If you could do X again, what would you do differently and why?
- How did you validate your results for X?
- How did you quantify the uncertainty in your prediction of X?
- What were the main limitations in X? How would you deal with these in future work?

# AI/ML questions
- How do you approach an AI/ML problem? What is the first thing you do and why and how do you proceed from there?
- What are some common pitfalls in machine learning and how do you avoid them?
- How do you validate you ML models? What would give you the confidence to use an ML model for real world engineering decisions?
- How do you quantify uncertainty when using ML?
- How do you select ML algorithms for specific applications?
- What are some common types of ML algorithms and for what applications would you use these?

# Programming languages
- What is your favourite programming language and why?
- What is the best software library you have used and why?

# Notes: interview 1
- Masters in computational mechanics
- Good reference to CHIMERA, knew about pegasus
- Good note on sensor problems
- Liked the gap
- Perfectly on time, focused on succinct
- Was happy to say when he did not know - really like this

# Questions:
- Talk to me about sensors - what can we do about sparse data with sensors? How do we account for uncertainty in sensors?
- You talked about sensor noise but sensors have other error sources like systematic errors and sometimes sensors fail - how should we deal with this?
- Talked a lot about sensor modelling which I really liked 

- When you generate training data for digital twin ML models how do you make sure your trainign dataset encompasses all real conditions?

- How would you validate a digital twin? How would you test the predicitive capability of a digital twin and quantify its uncertainty?

- You talked about which models are "trustable" - how would go about designing a project 

- You mention recommendations on when to use which model - do you think this is truly a one or the other problem or should we be using an ensemble of models and why?

- Focused on sparse, noisy data - how can we test this? 

- You talk and verification and validation - can you tell me what the difference is in these two terms and how you approach these different types of analysis

- Python! 

# Answers
- Question about equations being solved for solid mechanics - damage and plasticity then to hyper elastic modelling of fibres with neo-hookean. 
- Commercial software vs inhouse codes - mostly using commercial software, matlab, ANSYS
- Solving coupling problems with multi-physics: not properly coupled thermo-mech stresses used Abaqus. One way coupling vs two way coupling - 
- Plane stress vs plane strain - good answer
- Great on verification, ok on validation, ok on sensors and experiments 
- AI/ML models 
    - EPJD and PJD - encapsulated 
    - POD vs PJD - PJD does not guarantee orthogonal modes   
- Very good computationally and thinks about problems well


- You are completely stuck on a deep research problem and your supervisors are not available to help - what do you do to make progress?
    - Discuss with other PhD students, explain the problem to them
    - Check online for similar issues, 
    - Make a report of the problem and everything that was done to show us 

- Give me an example of when you were completely stuck on a research or engineering problem and your supervios or anyone else wasn't available to help - what did you do?

- Loves learning, knows limits of knowledge, great answer on what to do when we are not available

## Candidate 2
### General Questions
- How do you identify the most promising directions or research?
- Walk me through how you solved problem X?
- If you could do X again, what would you do differently and why?
- How did you validate your results for X?
- How did you quantify the uncertainty in your prediction of X?
- What were the main limitations in X? How would you deal with these in future work?

*GOOD QU*
- You are completely stuck on a deep research problem and your supervisors are not available to help - what do you do to make progress?
    - Proceed on work currently or start work on something else
    - Do something else or parallel

### Questions:
- GREAT knowledge of VVUQ, mixed verification and validation but had a good intuitive sense of validation/calibration as well as good knowledge of measurement uncertainty - even knew there could be offsets/calibration errors in IR measurements. 

- Verification & validation - what do these two terms mean to you?
    - Mixed these up

- What do you think the key sources of uncertainty in digital twins?

- Calibration vs validation - what is the difference between these two and how do we make sure that these are independent?
     - Calibration is tuning - 

- Model form uncertainty - what does this term mean to you? Can you give me an example of a model form uncertainty and how you would deal with this in building a digital twin?

- What are the key difference in simulation and experimental uncertainty?

- Mentioned open tools - do you have any experience developing and distributing open research outputs - like datasets or software 

- Gap1: 
    - Mentioned sparse uncertain experimental data - what are main sources of uncertainty in experiments/sensors and how should we deal with them?
- Gap2:
    - Sparse measurement and UQ, if we have sparse measurements what can we do to improve the information gained from those meausrements

- Previous IR experience! - what are the key sources of uncertainty in IR measurements and how did these change you model predictions?
    - Excellent, talked about offsets 

- Build everything in python - most efficient in python

### Machine Learning
- Common pitfalls?

- Why fusion?
    - Belong to something important for the world
    - Want to enjoy the work and contribute to something important for the world
    - Apply knowledg to a critical sector

