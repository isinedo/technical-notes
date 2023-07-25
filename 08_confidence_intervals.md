# Confidence Intervals
The BLS reported that the unemployment rate
dropped over a six-month period, from 4.20% in
September 2017 to 4.10% in March 2018. This
provided encouragement that the economy was
improving.

However, As it turns out, based on their sample of the workforce, the government was 90% confident that the actual U.S. unemployment rate in March 2018 was between $3.95\%$ and $4.25$\%.

$$
Confidence \hspace{1mm} interval \hspace{1mm} (CI) = \bar{x} \pm z_{\frac{\alpha}{2}} \sigma_{\bar{x}}
$$

In R, you can compute the $z$-score for any given confidence level. To do so, first you need to divide the $z$-score by 2, to account for the right and left tails of the normal distribution.

Say, we were interested in calculating the $z$-score for the 90% confidence level. This confidence level implies that each tail encloses $5\%$ of the area in the normal distribution. Since we are dealing with probabilities, we use the probability value for $10\% = 0.10$.

Hence: $0.10  \div 2 = 0.05$. Next, we'll enter this value into the `qnorm()` function in R.

```r
qnorm(0.05, lower.tail=F)
# [1] 1.644854
```
**Result**: The $z$-score for the $90\%$ CI $\approx$ $1.645$. See the image below for a visual representation.

![Confidence intervals for the mean](./images/Screenshot%202023-07-10%20at%2011-22-07%20Chapter%208%20-%20dbs3e_ppt_ch08.pdf.png)

The `qnorm()` function will return the $z$-score for any confidence level or for a list of confidence levels.

```r
> conf_levels <- c(0.10, 0.05, 0.025, 0.01, 0.005)
> qnorm(conf_levels, lower.tail=F)
# [1] 1.281552 1.644854 1.959964 2.326348 2.575829
```
**Note**: $z$-scores for confidence levels are constant values that rely on the $z$ table. Therefore, they do not change or vary.

## Student's $t$ distribution
One version of the history of the Student's *t* distribution goes like this. William Sealy Gosset was an employee of Guineess Brewery in Dublin, Ireland. While he dealing with samples as small as three observations, he developed the Student's *t* distribution as an approximation of the standard normal distribution.

For the Student's $t$, the amount of mass in the tail ends of the distribtion is controlled by a parameter $v$. "For $ν = 1$, the Student's $t$ distribution $t_ν$ becomes the standard Cauchy distribution, whereas for $ν → ∞$, it becomes the standard normal distribution $N (0, 1)$". For reference, see [Wikipedia: Student's t-distribution](https://en.wikipedia.org/wiki/Student's_t-distribution). 

In other words, as the sample size approaches infinity, the Student's $t$ becomes the standard normal distribution with a mean of $0$ and a standard deviation of $1$.

Note, one mistake some analysts make with the Student's *t* distribution is to think that the assumptions of the normal distribution can be applied to small samples.


## Calculating the sample size to estimate a population mean
The sample size needed to achieve a specific margin of error can be calculated, given the following information:
- The confidence level
- The population standard deviation

Hence, where these parameters are known, the sample size formula below works.

$$
n = {(z_{\alpha \over 2})^2 \bar{p}(1 - \bar{p}) \over (ME_{p})^2}
$$

However, in practice, population parameters are unknown. To solve this problem, statisticians have argued that sample sizes can be determined using a combination of estimates from past studies and statistical simulations. Statistical simulations is left out of this technical note for now. 
