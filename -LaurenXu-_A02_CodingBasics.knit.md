---
title: "Assignment 2: Coding Basics"
author: "Lauren Xu"
output: pdf_document
geometry: margin=2.54cm
editor_options: 
  chunk_output_type: console
---

## OVERVIEW

This exercise accompanies the lessons/labs in Environmental Data Analytics on coding basics.

## Directions

1.  Rename this file `<FirstLast>_A02_CodingBasics.Rmd` (replacing `<FirstLast>` with your first and last name).
2.  Change "Student Name" on line 3 (above) with your name.
3.  Work through the steps, **creating code and output** that fulfill each instruction.
4.  Be sure to **answer the questions** in this assignment document.
5.  When you have completed the assignment, **Knit** the text and code into a single PDF file.
6.  After Knitting, submit the completed exercise (PDF file) to Canvas.

## Basics, Part 1

1.  Generate a sequence of numbers from one to 55, increasing by fives. Assign this sequence a name.

2.  Compute the mean and median of this sequence.

3.  Ask R to determine whether the mean is greater than the median.

4.  Insert comments in your code to describe what you are doing.


``` r
#1.Creating the data vector
vector1 <- seq(from = 1, to = 55, by = 5)
vector1
```

```
##  [1]  1  6 11 16 21 26 31 36 41 46 51
```

``` r
#2.Calculating the mean and median
mean(vector1)
```

```
## [1] 26
```

``` r
median(vector1)
```

```
## [1] 26
```

``` r
#3.Comparing the mean and median
mean(vector1)-median(vector1)
```

```
## [1] 0
```
## Basics, Part 2
5.  Create three vectors, each with four components, consisting of (a) student names, (b) test scores, and (c) whether they are on scholarship or not (TRUE or FALSE).

6.  Label each vector with a comment on what type of vector it is.

7.  Combine each of the vectors into a data frame. Assign the data frame an informative name.

8.  Label the columns of your data frame with informative titles.



``` r
#5.
# Vector_a: Student names
vector_a <- c("Ann", "Bob", "Eric", "David") 
# Vector_b: Test scores
vector_b <- c(77, 88, 78, 66)
# Vector_c: whether they are on scholarship or not (TRUE or FALSE)
vector_c <- c(TRUE, TRUE, TRUE, FALSE)

#7.
df_vector_a <- as.data.frame(vector_a)
df_vector_b <- as.data.frame(vector_b)
df_vector_c <- as.data.frame(vector_c)
df_ScholarshipList <- cbind(df_vector_a,df_vector_b,df_vector_c)
df_ScholarshipList
```

```
##   vector_a vector_b vector_c
## 1      Ann       77     TRUE
## 2      Bob       88     TRUE
## 3     Eric       78     TRUE
## 4    David       66    FALSE
```

``` r
#8.
names(df_ScholarshipList) <- c('StudentName', 'TestScore', 'IfScholarship')
df_ScholarshipList
```

```
##   StudentName TestScore IfScholarship
## 1         Ann        77          TRUE
## 2         Bob        88          TRUE
## 3        Eric        78          TRUE
## 4       David        66         FALSE
```

9.  QUESTION: How is this data frame different from a matrix?

> Answer: A data frame can have different data types in columns. But matrix can only contain a single data type.

10. Create a function with one input. In this function, use `if`...`else` to evaluate the value of the input: if it is greater than 50, print the word "Pass"; otherwise print the word "Fail". 

11. Create a second function that does the exact same thing as the previous one but uses `ifelse()` instead if `if`...`else `. 

12. Run both functions using the value 52.5 as the input

13. Run both functions using the **vector** of student test scores you created as the input. (Only one will work properly...)


``` r
#10. Create a function using if...else
check_score1 <- function(score) {
  if (score > 70) {
    "Pass"
  } else {
    "Fail"
  }
}

#11. Create a function using ifelse()
check_score2 <- function(score) {
  ifelse(score > 70, "Pass", "Fail")
}

#12a. Run the first function with the value 52.5
check_score1(52.5)
```

```
## [1] "Fail"
```

``` r
#12b. Run the second function with the value 52.5
check_score2(52.5)
```

```
## [1] "Fail"
```

``` r
#13a. Run the first function with the vector of test scores
#vector_b <- c(77, 88, 78, 66)
#check_score1(vector_b)

#13b. Run the second function with the vector of test scores
check_score2(vector_b)
```

```
## [1] "Pass" "Pass" "Pass" "Fail"
```

14. QUESTION: Which option of `if`...`else` vs. `ifelse` worked? Why? (Hint: search the web for "R vectorization")

> Answer: Only 'ifelse' worked, whereas 'if'...'else' dose not worked. Because 'if'...'else' only apply to a single value rather than a vector.


**NOTE** Before knitting, you'll need to comment out the call to the function in Q13 that does not work. (A document can't knit if the code it contains causes an error!)
