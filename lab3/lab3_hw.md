---
title: "Lab 3 Homework"
author: "Zhuoya Wang"
date: "2024-01-18"
output:
  html_document: 
    theme: spacelab
    keep_md: true
---

## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove the `#` for the included code chunks to run. Be sure to add your name to the author header above.  

Make sure to use the formatting conventions of RMarkdown to make your report neat and clean!  

## Load the tidyverse

```r
library(tidyverse)
```

### Mammals Sleep  
1. For this assignment, we are going to use built-in data on mammal sleep patterns. From which publication are these data taken from? Since the data are built-in you can use the help function in R. The name of the data is `msleep`.  

```r
msleep <- msleep
```

2. Store these data into a new data frame `sleep`.  

```r
sleep = data.frame(msleep)
```

3. What are the dimensions of this data frame (variables and observations)? How do you know? Please show the *code* that you used to determine this below.  

```r
dim(sleep)
```

```
## [1] 83 11
```

```r
nrow(sleep)
```

```
## [1] 83
```

```r
ncol(sleep)
```

```
## [1] 11
```
The dimension of this data frame is 83 x 11. We can get the dimensions by using the dim() function, or get the number of observation by nrow(),and the number of variables by ncol()


4. Are there any NAs in the data? How did you determine this? Please show your code.  

```r
sum(is.na(sleep))
```

```
## [1] 136
```
Yes, there is 136 NAs in total.


5. Show a list of the column names is this data frame.

```r
colnames(sleep)
```

```
##  [1] "name"         "genus"        "vore"         "order"        "conservation"
##  [6] "sleep_total"  "sleep_rem"    "sleep_cycle"  "awake"        "brainwt"     
## [11] "bodywt"
```

6. How many herbivores are represented in the data?  

```r
table(sleep$vore)
```

```
## 
##   carni   herbi insecti    omni 
##      19      32       5      20
```
There are 32 herbi in the data.



7. We are interested in two groups; small and large mammals. Let's define small as less than or equal to 19kg body weight and large as greater than or equal to 200kg body weight. Make two new dataframes (large and small) based on these parameters.

```r
large <- filter(sleep, bodywt >= 200)

small <- filter(sleep, bodywt <= 19 )
```


8. What is the mean weight for both the small and large mammals?

```r
small_means <- mean(small$bodywt);small_means
```

```
## [1] 1.797847
```

```r
large_means <- mean(large$bodywt);large_means
```

```
## [1] 1747.071
```
The mean weight for small mammals is 1.797847kg, and the mean weight for large mammals is 1747.071kg



9. Using a similar approach as above, do large or small animals sleep longer on average?  


```r
small_time <- mean(small$sleep_total);small_time
```

```
## [1] 11.78644
```

```r
large_time <- mean(large$sleep_total);large_time
```

```
## [1] 3.3
```
Small animals sleep longer on average. 



10. Which animal is the sleepiest among the entire dataframe?

```r
summary(sleep)## max = 19.9
```

```
##      name              genus               vore              order          
##  Length:83          Length:83          Length:83          Length:83         
##  Class :character   Class :character   Class :character   Class :character  
##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
##                                                                             
##                                                                             
##                                                                             
##                                                                             
##  conservation        sleep_total      sleep_rem      sleep_cycle    
##  Length:83          Min.   : 1.90   Min.   :0.100   Min.   :0.1167  
##  Class :character   1st Qu.: 7.85   1st Qu.:0.900   1st Qu.:0.1833  
##  Mode  :character   Median :10.10   Median :1.500   Median :0.3333  
##                     Mean   :10.43   Mean   :1.875   Mean   :0.4396  
##                     3rd Qu.:13.75   3rd Qu.:2.400   3rd Qu.:0.5792  
##                     Max.   :19.90   Max.   :6.600   Max.   :1.5000  
##                                     NA's   :22      NA's   :51      
##      awake          brainwt            bodywt        
##  Min.   : 4.10   Min.   :0.00014   Min.   :   0.005  
##  1st Qu.:10.25   1st Qu.:0.00290   1st Qu.:   0.174  
##  Median :13.90   Median :0.01240   Median :   1.670  
##  Mean   :13.57   Mean   :0.28158   Mean   : 166.136  
##  3rd Qu.:16.15   3rd Qu.:0.12550   3rd Qu.:  41.750  
##  Max.   :22.10   Max.   :5.71200   Max.   :6654.000  
##                  NA's   :27
```

```r
filter(sleep, sleep_total == 19.9)
```

```
##               name  genus    vore      order conservation sleep_total sleep_rem
## 1 Little brown bat Myotis insecti Chiroptera         <NA>        19.9         2
##   sleep_cycle awake brainwt bodywt
## 1         0.2   4.1 0.00025   0.01
```
Little brown bat is the sleepiest among the entire dataframe.


## Push your final code to GitHub!
Please be sure that you check the `keep md` file in the knit preferences.   
