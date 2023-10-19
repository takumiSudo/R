---
title: "TidyVerse"
author : sud0
---


# DATA summarization

## GroupBy() -> 束ねる
```r
d |>
  group_by(Question)
```

from the dataset, we can use the dataset and groupby the specific rows of a column
(ie if the column has 3 types of unique rows, then it would group by it)


## Summarize() -> new_column = calculations

Given a groupby function, we can feed somekind fo basic calculation functions that creates a new row.
```r
d %>% 
  group_by(Question) %>%                    # group by "Questions"
  summarize(Support = mean(Support)) %>%    # average "Support" per group
  arrange(-Support)                         # sort based on "Support"
```
For this, if the question has 6 unique values, the suppport column would be assigned to find the mean value of 
each of the unique values in groupby

*n()* -> counts how many there are of that particular values.


## Mutate -> Given a groupby
When using mutate after a group_by, allows you to add summary values to the rows themselves.
Meaning that.


```r
d2 <- d %>% 
  group_by(Question) %>%
  mutate(avg_support = mean(Support), 
         diff = Support - avg_support)
d2

d3 <- d |> mutate(avg_support = mean(Support), diff = Support - avg_support) 
d3
```
While d2 calculates the *avg_support* given the unique values of the questions,
d3 calculates the avg_support according to the *whole Dataset*





