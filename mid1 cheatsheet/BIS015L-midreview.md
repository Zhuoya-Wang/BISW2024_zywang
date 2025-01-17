---
title: "BIS015L-midreview"
author: "Zhuoya Wang"
date: "2024-02-05"
output: 
  html_document: 
    keep_md: true
---





# Lab 2.1 Objects, Classes & NAs

```r
##### Lab 2

# sum(A, B, C)
# Mean(c(A, B, C)) # ABC are the object names
# class() # check the type of object
# is.xx() # check if the type of object is xx ### output: True or False
# as.xx() # create an object specified as xx

##### Missing Values

# is.na() # check every element in an object (number of TF = # of elements)

# anyNA() # check if the object has NA inside (only T/F)

# mean(objectname, na.rm = T/F) # caculate the mean of object, na.rm = remove NA

##### Vectors

# my_vector <- c(10, 20, 30) #numeric vector

# days_of_the_week <- c("Monday", "Tuesday", "Wednesday", "Thrusday", "Friday", "Saturday", "Sunday") # Characters always have quotes


# days_of_the_week[3] # the third element of that vector, use `[]` to pull out elements in a vector

# eg: my_vector_sequence[my_vector_sequence <= 10] # get the values in m_v_s that <= 10
```


#Lab 2.2 Vectors and Data Matrices

```r
##### Matrices
# provide vectors
Philosophers_Stone <- c(317.5, 657.1)
Chamber_of_Secrets <- c(261.9, 616.9)
Prisoner_of_Azkaban <- c(249.5, 547.1)
Goblet_of_Fire <- c(290.0, 606.8)
Order_of_the_Phoenix <- c(292.0, 647.8)
Half_Blood_Prince <- c(301.9, 632.4)
Deathly_Hallows_1 <- c(295.9, 664.3)
Deathly_Hallows_2 <- c(381.0, 960.5)


## list values by names
box_office <- c(Philosophers_Stone, Chamber_of_Secrets, Prisoner_of_Azkaban, Goblet_of_Fire, Order_of_the_Phoenix, Half_Blood_Prince, Deathly_Hallows_1, Deathly_Hallows_2)
box_office
```

```
##  [1] 317.5 657.1 261.9 616.9 249.5 547.1 290.0 606.8 292.0 647.8 301.9 632.4
## [13] 295.9 664.3 381.0 960.5
```

```r
## make matric by row
harry_potter_matrix <- matrix(box_office, nrow = 8, byrow = T)## organize it by rows



# Provide column names
region <- c("US", "non-US")
region
```

```
## [1] "US"     "non-US"
```

```r
# Provide row names
titles <- c("Philosophers_Stone", "Chamber_of_Secrets", "Prisoner_of_Azkaban", "Goblet_of_Fire", "Order_of_the_Phoenix", "Half_Blood_Prince", "Deathly_Hallows_1", "Deathly_Hallows_2")
titles
```

```
## [1] "Philosophers_Stone"   "Chamber_of_Secrets"   "Prisoner_of_Azkaban" 
## [4] "Goblet_of_Fire"       "Order_of_the_Phoenix" "Half_Blood_Prince"   
## [7] "Deathly_Hallows_1"    "Deathly_Hallows_2"
```

```r
# Add col names to the matrices
colnames(harry_potter_matrix) <- region

# Add row names to the matrices
rownames(harry_potter_matrix) <- titles



##### Row sums
global <- rowSums(harry_potter_matrix)
global
```

```
##   Philosophers_Stone   Chamber_of_Secrets  Prisoner_of_Azkaban 
##                974.6                878.8                796.6 
##       Goblet_of_Fire Order_of_the_Phoenix    Half_Blood_Prince 
##                896.8                939.8                934.3 
##    Deathly_Hallows_1    Deathly_Hallows_2 
##                960.2               1341.5
```

```r
### Add new col to the matrices by "cbind()" 
all_harry_potter_matrix <- cbind(harry_potter_matrix, global) ## show new title directly
all_harry_potter_matrix
```

```
##                         US non-US global
## Philosophers_Stone   317.5  657.1  974.6
## Chamber_of_Secrets   261.9  616.9  878.8
## Prisoner_of_Azkaban  249.5  547.1  796.6
## Goblet_of_Fire       290.0  606.8  896.8
## Order_of_the_Phoenix 292.0  647.8  939.8
## Half_Blood_Prince    301.9  632.4  934.3
## Deathly_Hallows_1    295.9  664.3  960.2
## Deathly_Hallows_2    381.0  960.5 1341.5
```

```r
# rbind() to add new row to a matrices

# colSums() calculates the col total

# matrice[a,b] # a is row, b is col

all_harry_potter_matrix[1,3] ## 1st row, 3rd col value
```

```
## [1] 974.6
```

```r
all_harry_potter_matrix[1:3] ## 1st row, 3 values in that row
```

```
## [1] 317.5 261.9 249.5
```

```r
colMeans(all_harry_potter_matrix) # all column mean
```

```
##       US   non-US   global 
## 298.7125 666.6125 965.3250
```

```r
mean(all_harry_potter_matrix[,3]) # single column mean
```

```
## [1] 965.325
```

```r
# rowMeans()
```



# Lab 3.1 Data Frames

```r
 library("tidyverse")
```

```
## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
## ✔ dplyr     1.1.2     ✔ readr     2.1.4
## ✔ forcats   1.0.0     ✔ stringr   1.5.0
## ✔ ggplot2   3.4.2     ✔ tibble    3.2.1
## ✔ lubridate 1.9.2     ✔ tidyr     1.3.0
## ✔ purrr     1.0.1     
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
```

```r
## data.frame(A, B,C) # make a data frame for three vectors

Sex <- c("male", "female", "male")
Length <- c(3.2, 3.7, 3.4)
Weight <- c(2.9, 4.0, 3.1)

hbirds <- data.frame(Sex, Length, Weight)
hbirds
```

```
##      Sex Length Weight
## 1   male    3.2    2.9
## 2 female    3.7    4.0
## 3   male    3.4    3.1
```

```r
names(hbirds) # show variables names
```

```
## [1] "Sex"    "Length" "Weight"
```

```r
dim(hbirds) # show dimension of hbirds data
```

```
## [1] 3 3
```

```r
str(hbirds) # show data strucutre
```

```
## 'data.frame':	3 obs. of  3 variables:
##  $ Sex   : chr  "male" "female" "male"
##  $ Length: num  3.2 3.7 3.4
##  $ Weight: num  2.9 4 3.1
```

```r
# Let's use lowercase names when we create the data frame. 
# We just changed to lowercase here, but we could use any names we wish.  

hbirds <- data.frame(sex = Sex, length = Length, weight_g = Weight)
##  rename-- new.name = old.name

# rename (new = old)
# rename(mammals, genus = "Genus", afr = "AFR", maxlife = "max. life", littersyears = "litters/year")

# Adding a new row
new_bird <- c("female", 3.6, 3.9)
new_bird
```

```
## [1] "female" "3.6"    "3.9"
```

```r
hbirds<- rbind(hbirds, new_bird)
hbirds
```

```
##      sex length weight_g
## 1   male    3.2      2.9
## 2 female    3.7        4
## 3   male    3.4      3.1
## 4 female    3.6      3.9
```

```r
# Adding a new col by $
hbirds$neighborhood <- c("lakewood", "brentwood", "lakewood", "scenic Heights")
hbirds
```

```
##      sex length weight_g   neighborhood
## 1   male    3.2      2.9       lakewood
## 2 female    3.7        4      brentwood
## 3   male    3.4      3.1       lakewood
## 4 female    3.6      3.9 scenic Heights
```

```r
## Writing data to file-- save hbirds with name hbirds_data.csv

write.csv(hbirds, "hbirds_data.csv", row.names = FALSE) ##csv = common separate value

# We use `row.names = FALSE` to avoid row numbers from printing out. 
```


# Lab 3.2 Data Frames


```r
getwd()# check the working directory
```

```
## [1] "/Users/zhuoyawang/Desktop/GitHub/BIS15W2024_zywang/mid1 cheatsheet"
```

```r
#hot_springs <- read_csv("lab3/hsprings_data.csv") # Load the file
#class(hot_springs$scientist)
#hot_springs$scientist <- as.factor(hot_springs$scientist) # change the class of 'scientist' variable to factor

#levels(hot_springs$scientist) # show level of that


# glimpse() another way to show strucutre
# summary() summary our data frame
# head() first rows of data
# tail() last rows of data
# table(hot_springs$scientist)# produces counts of the number of observations in a variable
```



# Lab 4.1 select()  extract variables (col)

```r
# select(fish, "lakeid", "scalelength") # select(dataname, "var1", "var2") to pull out the iterest variables 

# select(fish, fish_id:length) ## select from the start_col to end_col

# select(fish, -"fish_id", -"annnumber", -"length", -"radii_length_mm") # minus operator is going to select everything expect the select variables.   

# select(fish, contains("length")) extract the variables whose name contains 'length'

# select(fish, starts_with("radii")) Select columns that start with a character string  
# select(fish, matches("a.+er"))  a column contains a letter (in this case "a") followed by a subsequent string (in this case "er") -- > "annnunumber 


# select_if(fish, is.numeric) extract numeric variables in fish dataset

# select_if(fish, ~!is.numeric(.)) # select if in the fish data look across all the data, do not select all numeric variables. ! is Not

# select_all(mammals, tolower) #use lowercase to keep
```

Options to select columns based on a specific criteria include:  
1. ends_with() = Select columns that end with a character string  
2. contains() = Select columns that contain a character string  
3. matches() = Select columns that match a regular expression  
4. one_of() = Select columns names that are from a group of names  



# Lab 4.2 filter() -- extract row from dataset

```r
# filter(fish, lakeid == "AL")# select the rows which contain AL## 2equal sign and ""

# !=  is not equal 

# filter(fish, length %in% c(167, 175)) # choose the observation with length = 167 and length = 175

# filter(fish, between(scalelength, 2.5, 2.55)) #filter the observation with scalelength in between (2.5 2.55)   between a range --> between(variable_name, range)

# filter(fish, near(radii_length_mm, 2, tol = 0.2))# tol = tolerance; extract observations "near" a certain value with tolerance range

# filter(fish, lakeid == "AL" & length > 350) From Al or length > 350 (more rows than use "and")


# filter(fish, length > 400, (scalelength > 11 | radii_length_mm > 8)). we filter out the fish with a length over 400 and a scale length over 11 or a radii length over 8.
```

+`filter()` allows all of the expected operators; i.e. >, >=, <, <=, != (not equal), and == (equal)

'|' is or; '&' is and

Rules:  
+ `filter(condition1, condition2)` will return rows where both conditions are met.  
+ `filter(condition1, !condition2)` will return all rows where condition one is true but condition 2 is not.  
+ `filter(condition1 | condition2)` will return rows where condition 1 or condition 2 is met.  
+ `filter(xor(condition1, condition2)` will return all rows where only one of the conditions is met, and not when both conditions are met.  


# Lab 5.1 --> filter 2.0

```r
library(janitor)
```

```
## 
## Attaching package: 'janitor'
```

```
## The following objects are masked from 'package:stats':
## 
##     chisq.test, fisher.test
```

```r
# clean_names() change variables' names to lower cases

# primate <- filter(new_mammals, genus %in% c("Lophocebus" , "Erythrocebus"  ,"Macaca")) ## within is %in% 选择有L，E，M的rows
```

# Lab 5.2 --> Pipes, arrange(), mutate(), and if_else()
1. Use pipes to connect functions in dplyr.  
2. Use `arrange()` to order dplyr outputs.  
3. Use `mutate()` to add columns in a dataframe.  
4. Use `mutate()` and `if_else()` to replace values in a dataframe.  

pipes

```r
# select(fish, lakeid, scalelength)
# filter(fish, lakeid == "AL")

###### Pipe can call the data at one time

# fish%>%
# select(lakeid, scalelength)%>%
# filter(lakeid == "AL")


### example

#fish %>% #work with the fish data
#  select( lakeid, radii_length_mm) %>% # pull out variables of interest
#  filter(lakeid == "AL"|lakeid ==  "AR")%>% #only these lakes
#  filter(between(radii_length_mm, 2,4)) #sort to make easier to read
```


arrange() function

```r
###### arrange() like a sord command, and it always show in a ascending order(small to large)

#fish %>% 
#  select(lakeid, scalelength) %>% 
#  arrange(scalelength)

###### arrange(dec()) make it to be descending order (large to small)
```


mutate() function helps creating a new col from the exsiting variables

```r
#fish %>%  in the fish dataset 
#  mutate(length_mm = length*10) %>% create a new col with name length_mm that leng*10
#  select(fish_id, length, length_mm) select three cols from the dataset



### mutate_all() is helpful in cleaning data 
#mammals %>%
#  mutate_all(tolower) make the obs to be all lowercase (not the variables names)


### use across() to specify the cols we want to clean
#mammals %>% 
#  mutate(across(c("order", "family"), tolower))



### ifelse() --> replace -999.00 with NA, and others remain the same value as newborn
#mammals %>% 
#  select(genus, species, newborn) %>%
#  mutate(newborn_new = ifelse(newborn == -999.00, NA, newborn))%>% 
#  arrange(newborn)
```



 Lab 6.1 same as 5.2

# Lab 6.2 tabyl() a version of table and produces counts but also percentages

```r
library("janitor")
# tabyl(dataset, variable_name)
```


# Lab 7.1 summarize(), group_by() and n_distinct()
`summarize()` will produce summary statistics for a given variable in a data frame.

```r
#install.packages("skimr")
library("skimr")

# msleep%>%
#  filter(bodywt > 200)%>% # extract the rows with bodywt > 200
#  summarize(mean_sleep_lg = mean(sleep_total)) # calculate the mean of total sleep of animals whose body weights are over 200


##### example
# msleep%>%
#  filter(bodywt > 200)%>%
#  summarize(mean_sleep_lg = mean(sleep_total),
#            min_sleep_lg = min(sleep_total),
#            max_sleep_lg = max(sleep_total),
#            sd_sleep_lg = sd(sleep_total),
#            total = n()) # total number of observations
```


`n_distinct()` is a very handy way of cleanly presenting the number of distinct observations.

```r
#msleep%>%
#  summarize(n_genera = n_distinct(genus))# this is going to count the number of genera in msleep


# n_distinct() makes a integer and summarize makes it to be data frame.

# n_distinct() is similar as unique() 
```


'group_by()' providing what we want by the diffeent of 'vore'

```r
#msleep %>%
#  group_by(vore) %>% #we are grouping by feeding ecology, a categorical variable
#  summarize(min_bodywt = min(bodywt),
#           max_bodywt = max(bodywt),
#            mean_bodywt = mean(bodywt),
#           total=n())
```


# Lab 7.2 summarize practice, count(), across()

```r
## pull out all obs with a number = remvoe NAs

#penguins%>%
#  filter(!is.na(body_mass_g))%>%#pull out all of the observations with a number
#  group_by(island)%>%
#  summarize(n=n(), mean_body_mass = mean(body_mass_g))

#### remove warning maessage by .group = 'keep'

#penguins %>% 
#  group_by(species, island) %>% 
#  summarize(n=n(),.groups= 'keep')#the .groups argument here just prevents a warning message
```


`count()` is an easy way of determining how many observations you have within a column. It acts like a combination of `group_by()` and `n()`.


```r
#penguins%>%
#  group_by(island)%>%
#  summarize(n=n()) summary the the numeber of obs by groups

### same result computed by count()

#penguins %>% 
#  count(island, sort = T) #sort=T sorts the column in descending order




###### for multi variables with counts
#penguins %>% 
#  count(island, species, sort = T) # sort=T will arrange in descending order

##### same output with the following

#penguins %>%
#  tabyl(island, species)


##### compute the distinct obs for three variables

#penguins %>%
#  summarize(across(c(species, island, sex), n_distinct))# n_dis counts the number of unique



#### For continues variables
#penguins %>%
#  summarize(across(contains("mm"), mean, na.rm=T)) # compute mean values of all varibales with 'mm' without NA

#### remove warning 

#penguins %>%
#  summarize(across(contains("mm"), \(x) mean(x, na.rm = TRUE)))#use this to correct the error
```

