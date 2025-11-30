# Neuro Stats Quick Reference 📊  
Dipesh Pokharel  

A concise cheat sheet for statistical tools commonly used in behavioral and systems neuroscience, with a focus on:

- t-tests  
- ANOVA  
- Cohen’s kappa  
- Fleiss’ kappa  
- Effect sizes in behavioral neuroscience  

Useful for quick recall while analyzing data. 

---

# 📚 Table of Contents
1. [t-tests](#1-t-tests)  
2. [ANOVA](#2-anova)  
3. [Cohen’s Kappa](#3-cohens-kappa)  
4. [Fleiss’ Kappa](#4-fleiss-kappa)  
5. [Effect Sizes](#5-effect-sizes-in-behavioral-neuroscience)  
6. [Practical Tips](#6-practical-tips-for-neuroscience-data)  

---

## 1. t-tests

t-tests compare group means. Common variants relevant to neuroscience:

---

### **1.1 One-sample t-test**  
> Compare a sample mean to a known value (e.g., chance level 0.5 in tests).

- **Null hypothesis (H₀):**  
  \( \mu = \mu_0 \)

### **Test statistic (GitHub-safe LaTeX):**

$$
t = \frac{\bar{x} - \mu_0}{s / \sqrt{n}}
$$

---

### **1.2 Paired t-test**  
> Same animals measured twice. 

Compute differences:

$$
d_i = x_{1i} - x_{2i}
$$

Then perform a one-sample t-test on the vector \( d \).

---

### **1.3 Independent (two-sample) t-test**  
> Compare two independent groups. 

#### **Equal variances (Student’s t-test):**

$$
t = \frac{\bar{x}_1 - \bar{x}_2}{s_p \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}}
$$

Pooled variance:

$$
s_p^2 = 
\frac{
(n_1 - 1)s_1^2 + (n_2 - 1)s_2^2
}{
n_1 + n_2 - 2
}
$$

#### **Unequal variances (Welch’s t-test):**  
Default in R and Python; more robust unless sample variances are identical.

---

### **1.4 Quick R example**

```r
# Independent t-test: 
t.test(LI ~ group, data = df, var.equal = FALSE)
