### Task 2
Consider the population SLR model:

$$
Y_i=\beta_0+\beta_1 X_i+\varepsilon_i
$$

and an observed, random sample of data $\left(y_1, x_1\right), \ldots,\left(y_n, x_n\right)$ from that model. Suppose you ran an OLS regression on this data but made a mistake and did not include the intercept in the regression.

Questions:
1. Is the mean of the estimated residuals from your OLS regression still equal 0 , i.e. $\bar{e}=0$ ? How does your answer relate to LSA 2? (2 marks)
2. Is the correlation between the estimated residuals and the observed $x$ 's still equal 0. (5 points)
<!-- 
Hint: look at the second equation found when differentiating the residual sum of squares with respect to $\beta_1$. -->
3. What form does the OLS estimator of the slope coefficient in your regression have? (2 marks)
Hint: derive the solution from the 2nd equation found when differentiating the residual

4. Show whether or not the OLS estimator of your regression is still an unbiased
estimator of the true β1. (3 marks)



Sure! Let’s walk through a more **concise and mathematically rigorous proof** for each of the questions. We’ll focus on linear algebra and minimal verbal explanation.

---

The population model:

\[
Y_i = \beta_0 + \beta_1 X_i + \varepsilon_i
\]

The OLS regression without an intercept:

\[
Y = \hat \beta_1 X
\]


---

**1. Is the mean of the estimated residuals \( \bar{e} = 0 \)? Relate to LSA 2?**

The residuals from OLS regression without an intercept are given by:

\[
e_i = Y_i - \hat{Y}_i = Y_i - \hat{\beta}_1 X_i
\]

\[
\sum_{i=1}^{n} e_i = \sum_{i=1}^{n} (Y_i - \hat{\beta}_1 X_i)
\]

Substituting \( Y_i = \beta_0 + \beta_1 X_i + \varepsilon_i \):

\[\begin{aligned}
\sum_{i=1}^{n} e_i &= \sum_{i=1}^{n} \left( \beta_0 + \beta_1 X_i - \hat{\beta}_1 X_i \right) \\
&= \beta_0 \sum_{i=1}^{n} 1 + \sum_{i=1}^{n} (\beta_1 - \hat{\beta}_1) X_i + \sum_{i=1}^{n} \varepsilon_i \\
&= \beta_0 n + (\beta_1 - \hat{\beta}_1) \sum_{i=1}^{n} X_i + \sum_{i=1}^{n} \varepsilon_i
\end{aligned}\]

Subtitute equation (3) here to confirm the residuals do not sum to zero i.e \( \bar{e} \neq 0 \). (continue in the end after 4.)


- LSA 2 requires \( E[\varepsilon_i | X_i] = 0 \) for \( \sum_{i=1}^{n} e_i \) to be zero to satisfy the first condition for optimal RSS of simple linear regression model. However, with intercept set to zero, this assumption is not adequate.

---

**2. Is the correlation between \( e_i \) and \( X_i \) still 0?**

From OLS, the residual sum of squares is:

\[
RSS = \sum_{i=1}^{n} e_i^2 = \sum_{i=1}^{n} (Y_i - \hat{\beta}_1 X_i)^2
\]

Minimizing \( RSS \), the first-order condition with respect to \( \hat{\beta}_1 \) is:

\[\begin{equation}
\frac{\partial RSS}{\partial \hat{\beta}_1} = -2 \sum_{i=1}^{n} X_i (Y_i - \hat{\beta}_1 X_i) = 0
\end{equation}\]

Thus:

\[
\sum_{i=1}^{n} X_i e_i = 0
\]

and we are assuming LSA2.

But \[
\text{Cov}(X, e) = \frac{1}{n} \sum_{i=1}^{n} (X_i - \bar{X})(e_i - \bar{e}) = \frac{1}{n}\sum_{i=1}^{n} (X_i e_i - \bar{X}\bar{e}) = -\bar{X}\bar{e}
\]
This implies that the covariance between \( X_i \) and \( e_i \) is non zero. Thus the correlation is non zero.

---

**3. Form of the OLS estimator \( \hat{\beta}_1 \) without an intercept**


Solving for \( \hat{\beta}_1 \) from (1):

\[\begin{equation}
\hat{\beta}_1 = \frac{\sum_{i=1}^{n} X_i Y_i}{\sum_{i=1}^{n} X_i^2} \end{equation}
\]

This is the OLS estimator for the slope \( \beta_1 \) without an intercept.

---

**4. Is the OLS estimator \( \hat{\beta}_1 \) unbiased?**

We want to check if \( E[\hat{\beta}_1] = \beta_1 \). 

Substitute \( Y_i = \beta_0 + \beta_1 X_i + \varepsilon_i \) into (2):

\[
\hat{\beta}_1 = \frac{\sum_{i=1}^{n} X_i (\beta_0 + \beta_1 X_i + \varepsilon_i)}{\sum_{i=1}^{n} X_i^2}
\]
\[\begin{equation}
\hat{\beta}_1 = \beta_1 + \frac{\beta_0 \sum_{i=1}^{n} X_i + \sum_{i=1}^{n} X_i \varepsilon_i}{\sum_{i=1}^{n} X_i^2}
\end{equation}\]


Take the expectation of \( \hat{\beta}_1 \), since \( E[\varepsilon_i] = 0 \), the third term disappears:

\[
E[\hat{\beta}_1] = \beta_1 + \frac{\beta_0 \sum_{i=1}^{n} X_i}{\sum_{i=1}^{n} X_i^2}
\]

Thus, \( \hat{\beta}_1 \) is **biased** unless \( \beta_0 = 0 \) or  \( \sum_{i=1}^{n} X_i = 0 \).

---

**1. (continue)**

\[
\hat{\beta}_1 = \beta_1 + \frac{\beta_0 \sum_{i=1}^{n} X_i + \sum_{i=1}^{n} X_i \varepsilon_i}{\sum_{i=1}^{n} X_i^2}
\]

Substitute this equation (3) into the sum of residuals:
\[
\sum_{i=1}^{n} e_i = n \beta_0 + \left(\beta_1 - \left( \beta_1 + \frac{\beta_0 \sum_{i=1}^{n} X_i + \sum_{i=1}^{n} X_i \varepsilon_i}{\sum_{i=1}^{n} X_i^2} \right)\right) \sum_{i=1}^{n} X_i + \sum_{i=1}^{n} \varepsilon_i
\]

\[
\sum_{i=1}^{n} e_i = n \beta_0 - \frac{\beta_0 (\sum_{i=1}^{n} X_i)^2 + \sum_{i=1}^{n} X_i \sum_{i=1}^{n} X_i \varepsilon_i}{\sum_{i=1}^{n} X_i^2} + \sum_{i=1}^{n} \varepsilon_i
\]
<!-- ( \(E[\sum_{i=1}^{n} X_i \varepsilon_i] = \sum_{i=1}^{n} X_i E[\varepsilon_i] = 0\) ) -->
\[
\sum_{i=1}^{n} e_i = n \beta_0 - \frac{\beta_0 (\sum_{i=1}^{n} X_i)^2 }{\sum_{i=1}^{n} X_i^2} = \beta_0 \left( n - \frac{(\sum_{i=1}^{n} X_i)^2}{\sum_{i=1}^{n} X_i^2} \right) 
\]

Not zero unless ...