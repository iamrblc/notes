## 🧰 **Core Causal Concepts Worth Including**

### ✅ 1. **Causation ≠ Association**

- **Why it matters:** Students often interpret correlations or regression outputs as causal.
    
- **What to teach:** Show clear counterexamples (e.g., storks and birth rates, ice cream and sunburn).
    
- **Key idea:** _"If X goes up when Y goes up, it doesn’t mean X causes Y."_
    

---

### ✅ 2. **Confounding, Mediation, and Colliders (The Big Three)**

- **Why it matters:** These three roles explain _why_ simple comparisons can be misleading.
    
- **What to teach:**
    
    - Confounder = common cause (must control)
        
    - Mediator = in-between (don’t control if you care about total effect)
        
    - Collider = common effect (never control!)
        

> Use **simple DAGs** and **concrete examples** — e.g.,
> 
> - **Confounder:** Exercise ← age → blood pressure
>     
> - **Mediator:** Exercise → fitness → blood pressure
>     
> - **Collider:** Exercise → injury ← clumsiness
>     

---

### ✅ 3. **Simpson’s Paradox as a warning sign**

- **Why it matters:** Shows how _aggregated data can lie_.
    
- **What to teach:** Always ask: _"What are the groups here?"_  
    If effects reverse when you stratify, something important is being hidden.
    

---

### ✅ 4. **The idea of a causal graph — even informally**

- **Why it matters:** It helps students _think through_ causal questions, even if they don’t use formal DAG tools.
    
- **What to teach:** A graph is a _story_ of what causes what.  
    Ask:
    

> _“If I changed X, what would change downstream?”_  
> Use arrows to represent that story.

		## 🧭 **Causal Graphs to Show in the Handbook**
		
		### ✅ 1. **DAGs (Directed Acyclic Graphs)**
		
		- **Teach first.**
		    
		- Emphasize:
		    
		    - Direction of causality
		        
		    - No feedback loops
		        
		    - Confounders, mediators, colliders
		        
		- Use _hand-drawn examples_ to walk through reasoning:
		    
		    - What paths exist between X and Y?
		        
		    - What would you control for?
		        
		- Even if students forget the term “DAG,” they’ll remember:
		    
		
> 		_“Draw arrows to figure out what causes what — and what messes that up.”_
		
		---
		
		### ✅ 2. **Cyclic Graphs / SEM-style Feedback Loops**
		
		- **Teach second,** **only after DAG intuition is clear.**
		    
		- Motivate with **real-life feedback systems**:
		    
		    - Hormones regulating themselves
		        
		    - Predator-prey dynamics
		        
		    - Stress ↔ sleep in behavior studies
		        
		- Present as:
		    
    > 		_“Sometimes variables affect each other in a loop — DAGs can’t show this, but you still need to think causally.”_
		    
		- Use **simple loop diagrams** (not formal SEM math unless needed).
		    
		- For example:
		    
		    pgsql
		    
		    CopyEdit
		    
		    `Cortisol → Behavior → Social Conflict → Cortisol`
		    
		
		---
		
		## 🧠 Teaching Philosophy
		
		- **DAGs = thinking tool for study design**
		    
		- **Cyclic Graphs = reminder that life is messier than the model**
		    
		
		Don't go deep into SEMs unless:
		
		- You want to show how **math handles these loops**
		    
		- Or you have **psych/neuro/econ students** who _might_ see SEMs later
		    
		
		Otherwise, keep it intuitive.

---

### ✅ 5. **Think about _design_, not just _analysis_**

- **Why it matters:** Many students learn to plug numbers into software, but never ask if their study _can answer the question_.
    
- **What to teach:**
    

> - “Where would you intervene, if you could?”
>     
> - “What else might affect both your cause and effect?”
>     
> - “What does your study control for — and should it?”
>     

This builds intuition even in messy observational setups.