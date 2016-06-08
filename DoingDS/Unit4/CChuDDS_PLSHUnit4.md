# MSDS 6304 Wednesday 6:30PM : Week 4 Homework
Claire Chu  
May 30, 2016  
<br>
<br>
<strong><u>Assignment: Write bootstrap code to illustrate the central limit theorem in R markdown and push the result to GitHub. Use a normal distribution with two different sample sizes and an exponential distribution with two different sample sizes. Please also comment on the code and explain the results. 
</u></strong><br>
<br>
Based on the assignment, I will show the Central Limit Theorem at work through the following steps. 
<br>
step 1: Generate Normal Distribution & Stats
step 2: Bootstrap code with a sampling size of 50 & Stats
step 3: Bootstrap code with a sampling size of 100 & Stats
step 4: Generate Exponential Distribution & Stats
step 5: Bootstrap code with a sampling size of 50 & Stats
step 6: Bootstrap code with a sampling size of 100 & Stats
step 7: Conclusion
<br>

------------
<br>
<strong>Step 1: Generate normal distribution and take note of the Mean (meannorm) and the Standard Deviation (sdnorm) </strong>
<br>
generate normal distribution

```r
normalD <- c(rnorm(5, 2))
normalD
```

```
## [1]  3.0315029  3.1020373 -0.4973295  1.9171840  4.0036243
```
<br>
generate histogram of the normal distribution

```r
hist(normalD)
```

![](CChuDDS_PLSHUnit4_files/figure-html/unnamed-chunk-2-1.png)<!-- -->
<br>
generate mean of normal distribution

```r
meannorm <- c(mean(normalD))
meannorm
```

```
## [1] 2.311404
```
<br>
generate the standard deviation of normal distribution

```r
sdnorm <- c(sd(normalD))
sdnorm
```

```
## [1] 1.735774
```
<br>
<strong>Step 2: Generate boostrap code for the normal distribution with a sample size of 50 and take note of the Mean, Standard Deviation, and Standard Error</strong>
<br>
generate bootstrap code to get 50 sample means of the normal distribution (normalD) generated above

```r
rfifty <- 50
bootmeanfif <- numeric(rfifty)

for (i in 1:rfifty) {
  bootsamplefif <- sample(normalD, size=length(normalD), replace=TRUE)
  bootmeanfif[i] <- mean(bootsamplefif)}
bootmeanfif
```

```
##  [1] 2.7286919 2.1451933 2.5058281 2.8509597 2.9090093 3.1034335 2.7286919
##  [8] 2.3114038 2.5714427 1.6056373 1.6199700 3.0171703 1.3686667 2.3770184
## [15] 1.1883493 1.8426080 1.5915305 2.5058281 2.4917212 3.0597167 3.4485652
## [22] 2.2688574 2.3911253 3.2257014 2.3770184 3.4485652 1.8800089 2.7145850
## [29] 3.0453840 2.8084134 2.5058281 2.1310864 1.1742424 1.3686667 2.5483744
## [36] 3.0171703 2.3114038 2.2972969 2.3114038 2.9887308 2.4917212 0.9513786
## [43] 0.9283103 2.1310864 2.0088185 1.8800089 3.2823547 1.8143942 1.8941157
## [50] 1.8800089
```
<br>
print histogram to show the distribution of bootstrap sample means

```r
hist(bootmeanfif)
```

![](CChuDDS_PLSHUnit4_files/figure-html/unnamed-chunk-6-1.png)<!-- -->
<br>
get the mean value of the 50 bootstrap samples

```r
mean(bootmeanfif)
```

```
## [1] 2.32095
```
<br>
get the standard deviation of the 50 bootstrap samples

```r
sd(bootmeanfif)
```

```
## [1] 0.6426827
```
<br>
get the standard error of the 50 bootstrap samples

```r
sd(bootmeanfif)/sqrt(50)
```

```
## [1] 0.09088906
```
<br>
<strong>Step 3: Generate boostrap code for the normal distribution with a sample size of 100 and take note of the Mean, Standard Deviation, and Standard Error</strong>
<br>
generate bootstrap code to get 100 sample means of the normal distribution (normalD) generated above

```r
rhund <- 100
bootmeanhund <- numeric(rhund)

for (i in 1:rhund) {
  bootsamplehund <- sample(normalD, size=length(normalD), replace=TRUE)
  bootmeanhund[i] <- mean(bootsamplehund)}
bootmeanhund
```

```
##   [1] 2.8084134 1.7859547 2.3680570 1.8800089 1.8941157 2.3255107 2.5342676
##   [8] 3.2541409 3.4060188 2.3114038 2.7427987 2.2972969 2.0885400 2.3114038
##  [15] 0.6913397 2.7145850 1.8426080 1.4112130 3.4344583 2.2032428 3.6288826
##  [22] 1.6056373 2.3680570 2.5342676 1.1883493 1.7859547 2.5483744 2.9746239
##  [29] 0.8857640 2.6280960 2.3539502 3.6147757 2.3255107 2.3114038 2.7286919
##  [36] 2.3114038 2.6139891 2.3770184 3.4344583 2.5342676 3.4203515 3.2257014
##  [43] 2.5483744 0.9513786 1.1742424 2.7801996 2.3539502 2.5058281 1.1227346
##  [50] 0.6913397 2.1310864 2.3398433 1.6481837 2.7943065 2.7943065 2.2972969
##  [57] 2.3629116 2.3114038 1.8426080 2.3114038 0.7054466 1.1883493 2.3680570
##  [64] 2.5483744 1.8941157 1.6056373 2.6861455 0.6913397 2.5342676 1.6622906
##  [71] 1.3030520 2.5483744 2.2688574 3.8092000 2.0744331 2.7286919 1.4253199
##  [78] 3.6429895 1.8426080 2.5483744 1.8800089 1.4253199 2.5998822 2.8084134
##  [85] 1.8143942 2.1310864 1.4253199 2.5058281 1.1742424 2.1028727 1.7859547
##  [92] 2.0088185 2.5857754 2.7943065 2.8368529 3.2115946 1.3686667 2.7943065
##  [99] 1.1086278 2.9887308
```
<br>
print histogram to show the distribution of bootstrap sample means

```r
hist(bootmeanhund)
```

![](CChuDDS_PLSHUnit4_files/figure-html/unnamed-chunk-11-1.png)<!-- -->
<br>
get the mean value of the 100 bootstrap samples

```r
mean(bootmeanhund)
```

```
## [1] 2.240932
```
<br>
get the standard deviation of the 100 bootstrap samples

```r
sd(bootmeanhund)
```

```
## [1] 0.7179686
```
<br>
get the standard error of the 100 bootstrap samples

```r
sd(bootmeanhund)/sqrt(100)
```

```
## [1] 0.07179686
```
<br>
<strong>Step 4: Generate an Exponential function and take note of its mean (meanexp) and standard deviation (sdexp).</strong> 
<br>


```r
expD <- c(rexp(5))
expD
```

```
## [1] 0.6516464 0.2862060 0.1676949 0.5070677 0.6542755
```
<br>
generate a histogram of the exponential distribution

```r
hist(expD)
```

![](CChuDDS_PLSHUnit4_files/figure-html/unnamed-chunk-16-1.png)<!-- -->
<br>
generate the mean of the exponential distribution

```r
meanexp <- c(mean(expD))
meanexp
```

```
## [1] 0.4533781
```
<br>
generate the standard deviation of the exponential distribution

```r
sdexp <- c(sd(expD))
sdexp
```

```
## [1] 0.2191541
```
<br>
<strong>Step 5: Generate boostrap code for the exponential distribution with a sample size of 50 and take note of the Mean, Standard Deviation, and Standard Error</strong>
<br>
generate bootstrap code to get 50 sample means of the exponential distribution (expD) generated above  

```r
rexfifty <- 50
bootmeanfifexp <- numeric(rexfifty)

for (i in 1:rexfifty) {
  bootsamplefifexp <- sample(expD, size=length(expD), replace=TRUE)
  bootmeanfifexp[i] <- mean(bootsamplefifexp)}
bootmeanfifexp
```

```
##  [1] 0.3508485 0.4296759 0.4302017 0.4002343 0.3618013 0.5264662 0.4770803
##  [8] 0.5207268 0.4002343 0.5948666 0.2829739 0.3560620 0.5501684 0.5259404
## [15] 0.3066761 0.4970246 0.4681089 0.4918111 0.4296759 0.4329080 0.3328856
## [22] 0.3508485 0.4302017 0.3797642 0.4097316 0.4244624 0.3560620 0.5269920
## [29] 0.2592717 0.4244624 0.5275178 0.5654250 0.4828196 0.4765545 0.5212527
## [36] 0.5559077 0.2644852 0.3802900 0.3860293 0.4681089 0.4580658 0.3565878
## [43] 0.3855035 0.4533781 0.4833455 0.4296759 0.4776061 0.4334338 0.5496426
## [50] 0.4765545
```
<br>
print histogram to show the distribution of bootstrap sample means

```r
hist(bootmeanfifexp)
```

![](CChuDDS_PLSHUnit4_files/figure-html/unnamed-chunk-20-1.png)<!-- -->
<br>
get the mean value of the 50 bootstrap samples

```r
mean(bootmeanfifexp)
```

```
## [1] 0.437207
```
<br>
get the standard deviation of the 50 bootstrap samples

```r
sd(bootmeanfifexp)
```

```
## [1] 0.08030541
```
<br>
get the standard error of the 50 bootstrap samples

```r
sd(bootmeanfifexp)/sqrt(50)
```

```
## [1] 0.0113569
```
<br>
<strong>Step 6: Generate boostrap code for the exponential distribution with a sample size of 100 and take note of the Mean, Standard Deviation, and Standard Error</strong>
<br>
generate bootstrap code to get 100 sample means of the exponential distribution (expD) generated above

```r
rexhund <- 100
bootmeanhundexp <- numeric(rexhund)

for (i in 1:rexhund) {
  bootsamplehundexp <- sample(expD, size=length(expD), replace=TRUE)
  bootmeanhundexp[i] <- mean(bootsamplehundexp)}
bootmeanhundexp
```

```
##   [1] 0.3328856 0.3271462 0.4817680 0.5506942 0.4039922 0.3802900 0.4828196
##   [8] 0.5801358 0.5264662 0.5501684 0.5654250 0.5506942 0.3118896 0.5217785
##  [15] 0.5796099 0.4476388 0.4923369 0.5943407 0.4770803 0.5564335 0.5501684
##  [22] 0.3855035 0.4528523 0.4476388 0.4970246 0.3797642 0.3565878 0.4591174
##  [29] 0.4092057 0.3855035 0.4975504 0.3855035 0.3802900 0.5264662 0.4591174
##  [36] 0.6537497 0.4092057 0.6237823 0.4975504 0.4828196 0.3323597 0.4329080
##  [43] 0.4539039 0.4591174 0.4302017 0.5790841 0.4980763 0.5269920 0.3565878
##  [50] 0.4828196 0.4765545 0.2829739 0.4476388 0.5559077 0.4776061 0.5512200
##  [57] 0.4528523 0.4092057 0.3361177 0.5496426 0.3565878 0.4776061 0.5217785
##  [64] 0.5264662 0.5212527 0.5659508 0.4239365 0.5065219 0.3355918 0.1676949
##  [71] 0.5054702 0.5506942 0.3361177 0.4686347 0.5207268 0.4923369 0.5553819
##  [78] 0.2881874 0.5796099 0.4329080 0.5207268 0.3855035 0.4329080 0.4302017
##  [85] 0.4828196 0.5790841 0.4244624 0.4302017 0.5059960 0.5654250 0.4686347
##  [92] 0.4975504 0.5948666 0.4239365 0.3355918 0.5264662 0.2644852 0.4776061
##  [99] 0.3802900 0.5275178
```
<br>
print histogram to show the distribution of bootstrap sample means

```r
hist(bootmeanhundexp)
```

![](CChuDDS_PLSHUnit4_files/figure-html/unnamed-chunk-25-1.png)<!-- -->
<br>
get the mean value of the 100 bootstrap samples

```r
mean(bootmeanhundexp)
```

```
## [1] 0.4643249
```
<br>
get the standard deviation of the 100 bootstrap samples

```r
sd(bootmeanhundexp)
```

```
## [1] 0.08829752
```
<br>
get the standard error of the 100 bootstrap samples

```r
sd(bootmeanhundexp)/sqrt(100)
```

```
## [1] 0.008829752
```
<br>
<strong>Step 7: Conclusion</strong>
Based on our results, we can see that there are three components of the Central Limit Theorem being shown. 
<br>
A: We can see that the distribution of the bootstrap sample means will, as the sample size increases, approach a normal distribution. If we look at the histogram of normalD, the histogram of bootmeanfif, and the histogram of bootmeanhund, the histogram of bootmeanhund shows a trend towards normalization. The same can be said if we look at the histogram of bootmeanfifexp and the histogram of bootmeanfifhund.
<br>
B: We can see that as the sample size increases, the mean of the sample means gets closer to the population mean. This is why we are able to make many assumptions that the population mean is equal to the sample mean. 
<br>
C: We can see that as the sample size increases, the standard error of the mean decreases.

