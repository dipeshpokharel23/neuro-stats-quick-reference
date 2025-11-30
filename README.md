# Neuro Stats Quick Reference 📊  
**Author:** Dipesh Pokharel  

A concise cheat sheet for common statistical tools used in behavioral and systems neuroscience, with a focus on:

- t-tests  
- ANOVA  
- Cohen’s kappa  
- Fleiss’ kappa  
- Effect sizes in behavioral neuroscience  

Useful for quick recall while analyzing rodent behavior, paw preference, chemogenetic experiments, and neuroanatomical data.

---

## 1. t-tests

t-tests compare means between conditions. Common variants in neuroscience:

### 1.1 One-sample t-test
> Compare a sample mean to a known value (e.g., chance level = 0.5 for paw preference).

- **Null (H₀):** μ = μ₀  
- **Test statistic:**  
  \[
  t = \frac{\bar{x} - \mu_0}{s / \sqrt{n}}
  \]

### 1.2 Paired t-test
> Same animals measured twice (e.g., pre- vs post-lesion, vehicle vs CNO in same rats).

- Use when: **repeated measures** on the same subject.  
- Compute differences \( d_i = x_{1i} - x_{2i} \), then one-sample t-test on \( d \).  

### 1.3 Independent (two-sample) t-test
> Compare two independent groups (e.g., left-dominant vs right-dominant rats).

- **Equal variances (Student):**
  \[
  t = \frac{\bar{x}_1 - \bar{x}_2}{s_p \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}}
  \]
  where  
  \[
  s_p^2 = \frac{(n_1 - 1)s_1^2 + (n_2 - 1)s_2^2}{n_1 + n_2 - 2}
  \]

- **Unequal variances (Welch):** default in many software; more robust.

### 1.4 Quick R example

```r
# Independent t-test: LI in left- vs right-dominant rats
t.test(LI ~ group, data = df, var.equal = FALSE)
