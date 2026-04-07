

Mudis only

Here’s a simple Bayesian paired analysis on the **differences** (stranger − no_stranger), excluding dog 10, using a conjugate model:

- Model: di∼N(μ,σ)d_i \sim \mathcal{N}(\mu,\sigma)di​∼N(μ,σ), with Jeffreys prior p(μ,σ)∝1/σp(\mu,\sigma)\propto 1/\sigmap(μ,σ)∝1/σ.  
    This yields a **Student-t posterior** for μ\muμ.
    

**Results (n = 29):**

- Posterior for μ\muμ: Student-t(df = 28, loc = **-0.138**, scale = **0.255**)
    
- Posterior mean of μ\muμ: **−0.138**
    
- 95% credible interval: **[−0.659, 0.383]**
    
- P(μ>0)P(\mu > 0)P(μ>0): **0.295**
    

Interpretation: Given this model and prior, the posterior puts ~30% probability on a _positive_ mean effect (more barking with a stranger), and ~70% on a _negative or null_ effect. The 95% credible interval straddles zero and is fairly tight around small effects, suggesting any systematic shift (if it exists) is likely modest.

For a normal likelihood with unknown mean μ\muμ and variance σ2\sigma^2σ2, the **Jeffreys prior** is

p(μ,σ)  ∝  1σ.p(\mu,\sigma) \;\propto\; \frac{1}{\sigma}.p(μ,σ)∝σ1​.

I used it because:

1. **Non-informative / invariant** → it doesn’t favor particular values of μ\muμ or σ\sigmaσ, and it’s invariant under reparameterization (unlike flat priors on variance).
    
2. **Conjugacy** → combined with the normal likelihood, it yields a closed-form Student-t posterior for μ\muμ. That makes the Bayesian analysis transparent and analytically tractable without needing MCMC.
    
3. **Common default** → for simple Gaussian models, this prior is a standard baseline when we don’t want to inject strong prior beliefs.
    

👉 In short: Jeffreys prior is a principled “objective” choice for location-scale models when you want the posterior to be driven mostly by the data.

Here’s the Bayesian paired analysis **including** dog 10 (same Jeffreys prior model):

- Posterior for μ (mean difference = stranger − no_stranger): Student-t(df = 29, loc = **0.600**, scale = **0.894**)
    
- 95% credible interval: **[−1.228, 2.428]**
    
- P(μ>0)P(\mu > 0)P(μ>0): **0.746**
    

The plot shows the posterior density, the shaded region for P(μ>0)P(\mu>0)P(μ>0), and the 95% credible bounds.  
Compared to the outlier-excluded run, including dog 10 shifts the posterior rightward and increases P(μ>0)P(\mu>0)P(μ>0), but substantial mass still spans both sides of zero.


- **Without dog 10 (the extreme barker):** the posterior for the mean difference centers slightly _below_ zero, with about a **30% chance** that dogs bark more when strangers are present. So the model suggests no clear effect, leaning toward little or even reduced barking with strangers.
    
- **With dog 10 included:** the posterior shifts upward, mean difference ≈ **+0.6**, with about a **75% chance** that dogs bark more with strangers. But the credible interval (−1.2 to +2.4) still spans zero, meaning the data don’t strongly rule out no effect or even a small negative effect.
    

👉 In words: the “stranger effect” on barking looks modest overall, highly uncertain, and very sensitive to the inclusion of a single extreme dog.