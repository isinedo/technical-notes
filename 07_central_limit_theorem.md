# Central Limit Theorem
A few things to note about the central limit theorem:

1. For large samples, the normal distribution gives a good approximation to the distribution of many interesting sample statistics, such as means or variances, which are proportional to the sum of independent and equally distributed terms.

2. Suppose that $X_1$, $X_2$,..., $X_n$,... is a sequence of independent equally disributed variables, with a finite mean and variance, $\mu$ and $\sigma^2$, and denoted by $\tilde{X}_n$. The mean is:

$$
\tilde{X}_n = {{X_1 + ... + X_n} \over n}
$$

   According to the central limit theorem, the cummulative density function (CDF) of $\tilde{X}_n$ converges to the standard normal $\Phi$ as $n$ $\to$ $\infty$. This means that in practice, we can use the normal distribution as an approximation to calculate probabilities related to $\tilde{X}_n$.

## Putting the Central Limit Theorem to Work
### Hypothesis testing: Example 1
Suppose people drive an average of 12,000 miles per year with a standard deviation of 2,580 miles per year.

What is the probability that **a randomly selected sample of 36 drivers** will drive, on average, **more than** 12,500 miles?

$$
P(\tilde{x} > 12,500) = ?
$$

**Note**:
1. We want to test the probability that the $z$-score associated with the sample mean and sample standard deviation, falls within the lower tail of the distribution. 
2. Since in statistics, we do not test an alternate hypothesis, we'll instead test the null hypothesis in this scenario. 
3. We can express the null hypothesis as: On average, a randomly selected sample of 36 drivers will drive **less than or equal** to 12,500 miles.
4. Visually, we want to test the probability that the average driving distance for a sample of 36 drivers will fall within the lower tail of the distribution shown below. 

    ![Distribution for a sample of 36 drivers](./images/Screenshot%202023-07-06%20at%2023-25-37%20Chapter%207%20-%20dbs3e_ppt_ch07.pdf.png)


5. Recall that we can compute the **sample** standard error:

$$
\sigma_{\tilde{x}} ={ \sigma \over \sqrt{n}} ={ 2,580 \over \sqrt{36}} = 430.
$$

6. Next, we'll compute the desired probability in the following steps:

   - Compute the $z$-score:

$$
z_{\tilde{x}} = {{\tilde{x} - \mu_{\tilde{x}}} \over \sigma_{\tilde{x}}} = {{12,500 - 12,000} \over 430} = 1.16
$$

- To determine the desired probability, compute the $p$-value associated with $z = 1.16$. As computed below, this $p$-value is approximately 0.8770. As shown in the diagram above, this is the sum of all probability values up to the $z = 1.16$. 
- We are interested in the probability that the sample of drivers will drive on average, **more than** 12,500 miles. 
- The sum of all probabilities in the distribution must equal 1.
- To find the probability of interest, we'll therefore subtract $p = 0.8770 from 1$. The result is $1- 0.8770 = 0.1230$:

$$
P(\tilde{x} > 12,500) = P(z_{\tilde{x}} > 1.16) = 1 - P(z_{\tilde{x}} \leq 1.16) = 1 - 0.8770 = 0.1230
$$

   - Alternatively, to compute the probability, you can enter the $z$-score into the R function `pnorm()`. The argument `lower.tail = T`, indicates that the function call `pnorm()` computes the lower tail of the distribution. As explained above, this value is subtracted from 1 to arrive at the probability of interest.

      **In R**:
      ```r
      1 - pnorm(1.16, lower.tail=T)
      # [1] 0.1230244
      ```

      **In Python**:
      ```python
      import scipy.stats
      scipy.stats.norm.sf(abs(1.16))
      # 0.12302440305134343
      ```

**Conclusion**: The probability that a randomly selected sample of 36 drivers will drive more than 12,500 miles on average is 0.123 or 12.3%.

### Hypothesis testing: Example 2
This example illustrates when to use the **finite population correction factor** (FPC). Typically, we use the general standard error calculation when we are trying to make statistical inference for a sample that is less than 5% of the population. In such scenarios, the population is referred to as an **approximately infinite population**.

$$
\sigma_{\tilde{x}} = {\sigma \over \sqrt{n}}
$$

However, in cases where the sample size exceeds this 5% requirement, we apply a correction factor to the general standard error formula. This is what referred to as a finite population correction factor.

$$
FPC = {\sigma \over \sqrt{n}} \sqrt{{N - n \over N - 1}}
$$

A company has 100 customers. Each customer rated the company on customer service on a scale of 1-10. The average rating was 7.2 with a standard deviation of 0.7. A recent sample of 40 customers showed that the average customer service rating was 7.5. What is the probability that the average customer service rating for the entire customer base is **different from 7.2**?

**Note**:
1. This problem requires a two-tailed test. Why? To compute the probability that rating is different from 7.2, we must assume that the mean rating could be either greater than or less than 7.2. Based on this assumption, the true mean rating could fall on either tail of the normal distribution.
   
2. We want to test the null hypothesis that the probability average rating is $7.2$.

3. We can determine the probability using the following steps:
   
   - Compute the standard error of the mean:

$$
\sigma_{\tilde{x}} =  { \sigma \over \sqrt{n}} \sqrt{{N - n \over N - 1}} = {0.7 \over \sqrt{40}} \sqrt{{100 - 40 \over 100 - 1}} = (0.111)(0.778) = 0.086.
$$   
   
   - Compute the $z$-score associated with the mean ($\tilde{x}$) and the standard error of the mean ($se$).

$$
z_{\tilde{x}} = {{\tilde{x} - \mu_{\tilde{x}}} \over {\sigma_{\tilde{x}}}} = {{7.5 - 7.2} \over {0.086}} = 3.49
$$

   - Compute the probability:
  
$$
P(\tilde{x} > 7.5) = P(z_{\tilde{x}} > 3.49) = 0.0002
$$
   
   - As stated above, since we assume the probability could fall on either tail of the distribution, we multiply the value we obtained above by 2: $0.0002 \times 2 = 0.0004$ or $0.4\%$. Since the probability value is far less than $0.05$, we reject the null hypothesis. Therefore, we can conclude that the average customer service rating is most likely different from 7.2 is $0.004$.

   - Alternatively, to compute the probability, you can enter the $z$-score into the R function `pnorm()`.

   **In R**:

     ```r
     pnorm(3.49, lower.tail=F)
     # [1] 0.0002415103
     ```

   **In Python**:

    ```python
    import scipy.stats
    scipy.stats.norm.sf(abs(3.49))
    # 0.00024151027356783604
    ```

### Hypothesis testing: Example 3
A College claims that 70% of its 770 graduates have landed full-time jobs in fields related to their majors. To test this claim, 120 students are randomly surveyed, and 97 had found jobs in fields related to their majors. Is the college's claim accurate?

**Null hypothesis**: Seventy percent of the college's graduates landed full-time jobs in fields related to their majors.

This example requires knowledge on how to deal with binary dependent variables. In practice the application is very similar to Example 2 above.

**Steps**:
1. Find the standard error of the proportion. 

$$
\sigma_p = {\sqrt{p(1 - p) \over n}} {\sqrt{N - n \over N - 1}} = \sqrt{0.70(1-0.70) \over 120} \sqrt{770-120 \over 770-1} = 0.0384.
$$

2. Calculate the $z$-score for $\tilde{p}$ = $\frac{97}{120} = 0.808$

$$
z_p = {\tilde{p} - p \over \sigma_p} = {0.808 - 0.70 \over 0.0384} = 2.81
$$

3. Determine the probability that a sample proportion of $\tilde{p} = 0.808$ or more could be obtained if the true proportion is $p = 0.70$.

$$
P(\tilde{p} \ge 0.808) = P(z_p \ge 2.81) = 0.0025 \hspace{1mm} or \hspace{1mm} 0.25\%
$$

**In R**:
```r
> 1 - pnorm(2.81, lower.tail=T)
# [1] 0.002477075
```

**In Python**:
 ```python
 import scipy.stats
 scipy.stats.norm.sf(abs(2.81))
 # 0.002477074998785861
 ```