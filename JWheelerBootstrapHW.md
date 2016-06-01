# JWheelerBootStrap_Unit4HW
Jessica Wheeler  
May 26, 2016  



#Week 4 Homework:
##Using Bootstrap Code to Illustrate the Central Limit Theorem
<br>

* Write bootstrap code to illustrate the Central Limit Theorem in RMarkdown.  Use a normal distribution with 2 different sample sizes and an exponential distribution with 2 difference sample sizes.
<br>
<br>

> Central Limit Theorem:

* The distribution of sample means will, as sample size increases, approach a normal distribution.
* The mean of the sample means is the population mean, mu.
* The standard deviation of the distribution of the sample mean is often called the standard error of the mean.  
Sigma(x-bar) = Sigma(x)/ (sqrt(n))

<br>
<br>

* Normal distribution- Let's use n = 20 and n = 100:
<br>
+ Normal distribution with n=20:


```r
x <- rnorm(20) #Random sample of n=20 random normal values.
R <- 1000 #We want 1000 random samples from a sample size of n=20, as specified above.
bootmean <- numeric(R)
for (i in 1:R){
  bootsample <- sample(x, size=length(x), replace=TRUE)
  bootmean[i] <- mean(bootsample)}

mean(bootmean)
```

```
## [1] 0.08197311
```

![](JWheelerBootstrapHW_files/figure-html/unnamed-chunk-1-1.png)<!-- -->![](JWheelerBootstrapHW_files/figure-html/unnamed-chunk-1-2.png)<!-- -->

+ Normal Distribution with n = 100:


```r
x <- rnorm(100)
R <- 1000
bootmean <- numeric(R)
for (i in 1:R){
  bootsample <- sample(x, size=length(x), replace=TRUE)
  bootmean[i] <- mean(bootsample)}

mean(bootmean)
```

```
## [1] 0.01440529
```

![](JWheelerBootstrapHW_files/figure-html/unnamed-chunk-2-1.png)<!-- -->![](JWheelerBootstrapHW_files/figure-html/unnamed-chunk-2-2.png)<!-- -->


> For sample sizes of n greater than or equal 30, the distribution of sample means can be approximated reasonably well by a normal distribution.  And, as n gets larger, the approximation gets better. (1)

* In comparing n=20 and n=100 from a normal random sample, we can see that the distribution is more normal for the larger sample size.  For n=20, there is a bit of a left-tailed skew whereas n=100 is clearly normally distributed.  


* Looking at the qq plot for each, with n=100, more points are closer to the line than in that of n=20.  
* The range of n=20 is greater and from about -0.7 to 0.7 with a sample mean of 0.06.  The range of n=100 is smaller, going from -0.3 to 0.4 with a smaller mean that is closer to 0.
This example demonstrates the CLT for as the sample size gets larger for a random normal population, the distribution is normal.



<br>
<br>
*  Exponential distribution- Let's use n = 20 and n = 100
+  Exponential distribution with n=20:

```r
x <- rexp(20)
R <- 1000
bootmean <- numeric(R)
for (i in 1:R){
  bootsample <- sample(x, size=length(x), replace=TRUE)
  bootmean[i] <- mean(bootsample)}

mean(bootmean)
```

```
## [1] 0.8453613
```

![](JWheelerBootstrapHW_files/figure-html/unnamed-chunk-3-1.png)<!-- -->![](JWheelerBootstrapHW_files/figure-html/unnamed-chunk-3-2.png)<!-- -->

+ Exponential distribution with n=100:

```r
x <- rexp(100)
R <- 1000
bootmean <- numeric(R)
for (i in 1:R){
  bootsample <- sample(x, size=length(x), replace=TRUE)
  bootmean[i] <- mean(bootsample)}

mean(bootmean)
```

```
## [1] 0.9108794
```

![](JWheelerBootstrapHW_files/figure-html/unnamed-chunk-4-1.png)<!-- -->![](JWheelerBootstrapHW_files/figure-html/unnamed-chunk-4-2.png)<!-- -->

> For the exponential distributions, a larger sample size also results in a smaller spread as well as reduced skewness.  The mean of n=100 is smaller and closer to 0 than that of n=20.

* Citations:
+ (1) Notes from Bridge to Statistics MSDS6371, SMU
