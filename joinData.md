---
title: "Join Data"
author : sud0
---

# Joining Data & Reshaping

| Function | Description               |
|----------|---------------------------|
| `Inner_join`| Join the datsets       |
|`Inner_join(c = "")`| Join the datasets on a specific column|
| `left_join` | keeps the rows from the left dataset and make it NA.values|
|`pivot_longer`| Transform Data from Columns to Rows|
|`pivot_wider`| Transform Dat from Rows to Columns |


## Inner_join

Joining data, inner would add the two datasets together.

```r
inner_join(results_state, schedule)
```

If we want to add a specific column to join on :

```r
inner_join(results_state, schedule, by= c("state" = "area_name"))
```


## Left/Right_join
When *inner_joining* some of the rows are silently removed from the dataset, because their names don't occur in
the other datasets. 

To preven this we can use the **left_join()**:

```r
left_join(results_state, age)
```

This will keep all rows in the first dataset(the left one), filling them with *NA values*


## pivot_longer (columns -> Row)
```r
income = income_raw %>% pivot_longer(U.S.:Europe, names_to = 'country', values_to = 'income_topdecile')
```


## pivot_wider (row -> columns)
```r
wealth = pivot_wider(wealth, names_from=measurement, values_from=value)
wealth
```
