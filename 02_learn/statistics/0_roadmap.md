
# PHASE I — Foundations of Bayesian Thinking

_(Uncertainty, probability, structure, causal reasoning)_

###  [[01_what_is_probability|01. What is probability?]]

- Uncertainty vs randomness
- Probability as rational degree of belief
- Coherence and internal consistence
- Events vs parameters
- Probability distributions as states of knowledge

### 2. Random Variables & Distributions

- What a random variable is
- Discrete vs continuous variables
- PMF vs PDF
- Expectation and variance (conceptual meaning)
- Histograms vs theoretical distributions
- Simulation as a thinking tool

### 3. Joint, Conditional & Marginal Probability

- Joint distributions
    
- Conditional probability as restricted belief
    
- Marginalization (summing/integrating out uncertainty)
    
- Independence vs conditional independence
    
- Graphical intuition
    

### 4. Bayes’ Theorem

- Derivation from conditional probability
    
- Prior, likelihood, posterior
    
- Evidence (normalizing constant)
    
- Updating as belief revision
    
- Visual intuition
    

### 5. Causal Thinking & DAGs

- Generative stories and structure
    
- Directed Acyclic Graphs (DAGs)
    
- Conditional independence via graphs
    
- Confounding and adjustment intuition
    
- Difference between association and intervention
    
- Linking DAGs to model structure
    

### 6. Likelihood

- What likelihood is (and is not)
    
- Likelihood vs probability
    
- Data as fixed, parameters as uncertain
    
- Likelihood functions in simple models
    
- How likelihood encodes model structure
    

### 7. Parameters, Estimands & Estimates

- What is a parameter?
    
- What is an estimand?
    
- Posterior distribution vs point estimate
    
- MAP, posterior mean, posterior median
    
- Credible intervals
    

---

# PHASE II — Generative Modeling & Core Bayesian Workflow

_(From story to posterior)_

### 8. Generative Models

- Data generating process
    
- Forward simulation
    
- Model as structured hypothesis
    
- Sampling vs inference
    
- Why simulation is central
    

### 9. Conjugate Models (Intuition Builders)

- Beta–Binomial
    
- Gamma–Poisson
    
- Normal–Normal
    
- Prior strength & pseudo-observations
    
- Shrinkage intuition
    

### 10. Prior Design

- Informative vs weakly informative priors
    
- Regularization
    
- Prior predictive checks
    
- Sensitivity analysis
    
- Incorporating domain knowledge
    

### 11. Posterior Interpretation

- Full posterior vs summaries
    
- Probability statements about parameters
    
- Probability statements about predictions
    
- Decision-relevant quantities
    

### 12. Posterior Predictive Checks

- Model criticism
    
- Overfitting vs underfitting
    
- Graphical checks
    
- Diagnosing model misfit
    

---

# PHASE III — Regression & Research-Grade Models

### 13. Bayesian Linear Regression

- Regression as conditional expectation
    
- Priors on intercepts and slopes
    
- Centering and scaling
    
- Interpreting slope posteriors
    
- Predictive intervals
    

### 14. Logistic Regression

- Modeling probabilities
    
- Log-odds and the logit link
    
- Odds and odds ratios
    
- Interpretation of coefficients
    
- Predictive probability curves
    

### 15. Hierarchical (Multilevel) Models

- Partial pooling
    
- Shrinkage
    
- Group-level variation
    
- Varying intercepts
    
- Varying slopes
    
- Why multilevel models are essential in real research
    

### 16. Model Comparison & Selection

- Predictive accuracy
    
- WAIC
    
- LOO-CV
    
- Overfitting
    
- Model averaging
    

### 17. Robust Models

- Heavy-tailed likelihoods
    
- Student-t models
    
- Handling outliers
    
- When Gaussian assumptions fail
    

---

# PHASE IV — Advanced Modeling & Research Structure

### 18. Causal Inference with Bayesian Models

- Associational vs interventional quantities
    
- The “do” operator intuition
    
- Modeling causal effects
    
- Assumptions behind causal claims
    
- Linking DAGs to causal estimation
    

### 19. Missing Data

- Missingness mechanisms
    
- Modeling missing data directly
    
- Bayesian imputation within the model
    

### 20. Measurement Error & Latent Variables

- Imperfect measurement
    
- Latent variable models
    
- Reliability modeling
    

### 21. Decision Theory

- Loss functions
    
- Expected utility
    
- Bayesian decision rules
    
- Practical research decision-making
    

---

# PHASE V — Scientific Communication & Workflow

### 22. Reporting Bayesian Results

- Writing methods sections
    
- Reporting priors transparently
    
- Reporting uncertainty correctly
    
- Avoiding common misinterpretations
    

### 23. Visualization of Uncertainty (Plotly-Focused)

- Posterior distributions
    
- Predictive intervals
    
- Regression surfaces
    
- Communicating uncertainty clearly
    

### 24. Reproducible Bayesian Workflow in Python

- PyMC model structure
    
- ArviZ diagnostics
    
- Convergence (R-hat, ESS)
    
- Trace plots
    
- Publication-ready workflow
    

---

# Structural Principles of the Course

Each session will follow:

1. Conceptual intuition
    
2. Minimal mathematical structure
    
3. Simulation example
    
4. Real PyMC implementation
    
5. Interpretation
    
6. Short knowledge check
    
7. Handbook-ready summary