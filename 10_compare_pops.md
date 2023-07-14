# Hypothesis Tests: Comparing Two Populations
Comparing populations can be achieved using the same statistics discussed in earlier chapters (e.g., $z$, $t$). However, when dealing with two populations, each population will have its own set of descriptive statistics (e.g., $\bar{x}$, $\sigma^2$,  $\sigma$) including the standard error ($\sigma_{\bar{x}}$). To compare means, we simply compute the difference between the standard error of each population.

$$
\sigma_{\bar{x_1} - \bar{x_2}} = \sqrt{{\sigma_{1}^2 \over n_1} + {\sigma_{2}^2 \over n_2}}
$$

where: <br>
$\sigma_{1}$ and $\sigma_{2}$ = The standard deviations for 
populations 1 and 2 respectively. <br>
$n_{1}$ and $n_{2}$ = The sample sizes from populations 1 and 2 respectively.

## Difference between independent and dependent samples
Many sources describe independent samples as situations where the subjects or participants in one sample cannot be paired meaningfully with the subjects or participants in another sample. More intuitively, we can think of independent samples using scientific experimental contexts.

### An independent sample
Imagine that a phamarceutical company wanted to test the effect of a sleep inducing drug on on a set of 100 lab mice. The lab mice are *randomly* divided into two groups: A and B. The mice in group A are given the drug while the mice in group B are given a placebo. In this context, the mice in group A and group B are independent samples. If on average, the lab mice in group A slept longer than the lab mice in group B, researchers at the phamarceutical company can conclude that the drug had an effect.

### A dependent sample
Using the same scenario as before, now imagine that the pharmaceutical company did not divide the 100 lab mice into two groups. Instead, it first measured how long all 100 lab mice slept. Then, it administered the sleep inducing drug to all 100 lab mice. This is a dependent sample. If on average, the lab mice slept longer after receiving the drug than before receiving the drug, the researchers can conclude that drug had an effect.

## Hypothesis test to compare difference between two means ($\mu$)
### Case study: Amount spent by baseball fans in Chicago and New York
Is there a difference between the amount a fan spends on food at a baseball game in Chicago compared to a fan in New York?

**Quiz**: Is the scenario above a good or bad example of independent samples? Give reason(s) for your answer.

- A random sample of $40$ Chicago fans had mean spending of $\mu_1$ = $\$13.60$. A sample of $36$ New York fans had mean $\mu_2$ = $\$14.75$.
- Assume that the population standard deviations are known,
$\sigma_1$ = $\$1.80$ in Chicago and $\sigma_2$ = $\$2.50$ in New York.
- Assume we are testing with the $95\%$ confidence level

**Quiz**: 
1. This scenario requires a two-tailed test. Explain why.
2. Donnelly's (2020) approach is to use the $z$ statistic to test the null hypothesis in this case study. Do you think the $t$ statistic would be more appropriate? Give reason(s) for your answer. Below is the formula for the $t$ statistic when comparing two independent means.

$$
{t_x} = {(\bar{x_1} - \bar{x_2}) - (\mu_1 - \mu_2)_{H_0} \over {\sqrt{s_{p}^2 \left ({1 \over n_1} + {1 \over n_2} \right)}}}
$$

**Steps**:
1. State the null hypothesis

$$
H_0 = \mu_1 - \mu_2 = 0
$$

$$
H_1 = \mu_1 - \mu_2 \ne 0
$$

2. Determine the test statistic ($z_{\bar{x}}$).

$$
z_{\bar{x}} = {(\bar{x_1} - \bar{x_2}) - (\mu{x_1} - \mu{x_2})_{H_0} \over \sigma_{\bar{x_1} - \bar{x_2}}}
$$

where: <br>
- $(\mu{x_1} - \mu{x_2})_{H_0}$ = The hypothesised difference in population means.
- $\sigma_{\bar{x_1} - \bar{x_2}}$ = The standard error of the difference between two means
- $\bar{x_1} - \bar{x_2}$ = The difference in sample means between populations 1 and 2 respectively

3. Determine the critical value for a two-tailed test ($z_{a/2}$). 

As stated earlier, the confidence level is $95\%$, which corresponds with an alpha level $\alpha = 0.05$. As shown in previous sections, the $z$ score for this alpha level and for a two-tailed test is 1.96.

4. Compute the standard error.

$$
\sigma_{\bar{x_1} - \bar{x_2}} = 
$$

$$
\sigma_{\bar{x_1} - \bar{x_2}} = \sqrt{{\sigma_{1}^2 \over n_1} + {\sigma_{2}^2 \over n_2}} = \sqrt{{\$1.80^2 \over 40} + {\$2.50^2 \over 36}} = \$0.505
$$

5. Compute the test statistic: $z$ statistic.

$$
z_{\bar{x}} = {(\bar{x_1} - \bar{x_2}) - (\mu{x_1} - \mu{x_2})_{H_0} \over \sigma_{\bar{x_1} - \bar{x_2}}} = {(\$13.60 - \$14.75) - (0)_{H_0} \over \$0.505} = 2.28
$$

6. Compare the $z$ statistic with the critical value for a two-tailed test ($z_{a/2}$).

Since $2.28$ is $>$ $1.96$, we can reject the null hypothesis $H_0$.

7. **Conclusion**: Based on these samples, there is evidence to indicate that on average, fans in New York spend more on food than fans in Chicago.

