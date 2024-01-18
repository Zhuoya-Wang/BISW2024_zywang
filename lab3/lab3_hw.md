---
title: "Lab 3 Homework"
author: "Zhuoya Wang"
date: "2024-01-18"
output:
  html_document: 
    theme: spacelab
    keep_md: yes
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
We can get the dimensions by using the dim() function, or get the number of observation by nrow(),and the number of variables by ncol()


4. Are there any NAs in the data? How did you determine this? Please show your code.  

```r
sum(is.na(sleep))
```

```
## [1] 136
```

5. Show a list of the column names is this data frame.


6. How many herbivores are represented in the data?  


7. We are interested in two groups; small and large mammals. Let's define small as less than or equal to 19kg body weight and large as greater than or equal to 200kg body weight. Make two new dataframes (large and small) based on these parameters.


8. What is the mean weight for both the small and large mammals?




9. Using a similar approach as above, do large or small animals sleep longer on average?  



10. Which animal is the sleepiest among the entire dataframe?


## Push your final code to GitHub!
Please be sure that you check the `keep md` file in the knit preferences.   