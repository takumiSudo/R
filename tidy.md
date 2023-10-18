---
title: "TidyVerse"
bibliography: https://github.com/ccs-amsterdam/r-course-material/blob/master/tutorials/R-tidy-5-transformation.md
link-citations: TRUE
author : sud0
output:
  html_document:
    pandoc_args: "--toc --mathjax"
    pandoc: "/usr/local/bin/pandoc" # macOS example
---


# TidyVerse

## Installing tidyverse

As before, install.packages() is used to download and install the package (you only need to do this once on your computer) and library() is used to make the functions from this package available for use (required each session that you use the package).
```
install.packages('tidyverse') # only needed once
library(tidyverse)
```

# Basics

## Reading CSVs

```r
url <- "PATH/TO/url.com"
d <- read_csv(url)
d
```
 
This will import the csv from the selected path.


## Filter() -> Rows with Specific values
The filter Function is for specific rows

```r
age21 <- filter(d, Question == 'age-21')
age21
```

This follows a simple function 
$$filter(data, column =="specificValue")$$
We can also combine the two statements such like 

```r
filter(d, Question == 'age-21' & Support >= 80)
```

Note the use of == for comparison: In R, = means assingment and == means equals. Other comparisons are e.g. > (greather than), <= (less than or equal) and != (not equal). You can also combine multiple conditions with logical (boolean) operators: & (and), | or, and ! (not), and you can use parentheses like in mathematics.


## Select() -> Columns with target.
`select` allows you to select specific columsn. We can simply name the columns that we want to retrieve them in that order

```r
select(data, column1, column2, column3)
```

**Renaming the Columns**
  ```r
  select(age21, Pollster, rep = `Republican Support`, dem = `Democratic Support`)
  ```

It is poossible to rename the columns, during the selection process. And Select will drop all of the columns.
While `rename()` will keep the columns but still keep the columns that are not the target.

**Dropping a Column**
The following will keep the columns not mentioned and will drop the others.
```r
select(age21, -Question, -URL)
```


## Arrange() -> Sort Column

Sorting the data set with the  `arrange` function(specify the data then the target columns *to sort in desceding order*) 
```r
age21 <- arrange(age21, Population, -Support) # Population will be sorted ascending order, while Suppor will be Descending 
age21
```

## Mutate() -> Adding or Transform Variable
Makes it easy to create a new variable or to modify existing.

```r
age21 <- mutate(age21, party_diff = abs(`Republican Support` - `Democratic Support`))
```
now this makes a new column called `party_diff`, with the values being calculated with the `abs()` or the absolute values

### Other functions:

  - sqrt(), log(), exp(), sin(), cos(), tan()
  - sum(), mean(), max(), min(), and n()


  -> n() : n() is a special function used to count the number of rows in a group when working with grouped data. 



## Pipes
It makes more sense to make the dataset from each time resulting in overwriting the dataframe, but more pipeline 
```r
d <- read_csv(url)
age21 <- filter(d, Question == 'age-21')
age21 <- mutate(age21, party_diff = abs(`Republican Support` - `Democratic Support`))
age21 <- select(age21, Question, Pollster, party_diff)
arrange(age21, -party_diff)
```

```r
read_csv(url) |> 
  filter(Question == 'age-21') |>
  mutate(party_diff = abs(`Republican Support` - `Democratic Support`)) |>
  select(Question, Pollster, party_diff) |>
  arrange(-party_diff)
```