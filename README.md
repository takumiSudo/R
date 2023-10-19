# Political Communications & Data Analysis

For a political communication & data analysis class, there is going to be an assesment for the R part, this repo is going to contain the basics of R.

| Function                                | Explanation                      | 
|-----------------------------------------|----------------------------------|
|`read_csv(url)`|Import the csv and read the data|
|`Filter(data, column == "specific_y")`|Filter the data with specific rows| 
|`Select(data, column1, column2, column3)`| Select the target Columns|
|`Select(data, new_name = old_column)`| While selecting, the columns is renamed|
|`select(data, -column)`|Putting a minus is means to delete the data| 
|`Arrange(data, column, -column)`| Sort Columns(- makes it descending)| 
|`Mutate(newColumn = abs(col1 - col2))`| Adding or Transform Variable | 
|`n()` | Count the number of rows in a group when working grouped data|
|-----------------------------------------|----------------------------------|
|`groupby(Question)`| groupby a specifc column (does nothing itself) |
|`grouby(quetions) |> Summarize(support = mean(support))`| Makes a new column, but groupby a certain row|
|-----------------------------------------|----------------------------------|
| `geom_points`                           | Scatter plot                     |
| `geom_smooth`                           | Loess curve                      |
| `geom_smooth(method = "lm")`            | Linear regression line           |
| `geom_points(aes(x, y, size = Population))` | Size of points according to Population |
| `geom_points(aes(x, y, size = white_pct))`  | Color of points depending on "white_pct" column |
|-----------------------------------------|----------------------------------|
| `geom_bar(aes(x = growth))`             | Bar Plot mapped for x            |
| `geom_col(aes(x = canidate, y = votes))`| Directly Feed the Y, so geom_col can plot the fed plot|
| `geom_line(aes(x, y))`                  | geom_line creates a line plot|
| `geom_polygon`| Maps and shapes |
|----------|---------------------------|
| `Inner_join`| Join the datsets       |
|`Inner_join(c = "")`| Join the datasets on a specific column|
| `left_join` | keeps the rows from the left dataset and make it NA.values|
|`pivot_longer`| Transform Data from Columns to Rows|
|`pivot_wider`| Transform Dat from Rows to Columns |








## R Basics _ Tidyverse

Data Transformation, otherwise known as data preprocessing can be done with the [R Tidyverse](./tidy.rmd).

```r
read_csv(url) |> 
  filter(Question == 'age-21') |>
  mutate(party_diff = abs(`Republican Support` - `Democratic Support`)) |>
  select(Question, Pollster, party_diff) |>
  arrange(-party_diff)
```

## Summarization 
Dataset Summarization -> GroupBy, Summarization, this is found -> [Summarization](./summarize.md)

```r
d %>% 
  group_by(Question) %>%                    # group by "Questions"
  summarize(Support = mean(Support)) %>%    # average "Support" per group
  arrange(-Support)  
```

## GGplots

For most of the visualization we can use the [ggplots](./ggplots.md) library


## Joining _data 




































## Basic R Chunk
Embed Code With knitr
Code Chunks
Surround code chunks with ```{r} and ``` or use the Insert Code Chunk button. Add a chunk label and/or chunk options inside the curly braces after r.

```{r chunk-label, include = FALSE}
```

Set Global Options
Set options for the entire document in the first chunk.

```{r include = FALSE}
knitr::opts_chunk$set(message = FALSE)
```

Inline Code
Insert `r <code>` into text sections. Code is evaluated at render and results appear as text.

The markdown text

Built with `r getRversion()` 
will render as “Built with 4.3.0” in the output file.

Chunk Options
Table of chunk options. The first column is the option name, the second column is the option’s default value, the third column describes what the option does.


Build Your Bibliography
Add BibTex or CSL bibliographies to the YAML header.
```
---
title: "My Document"
bibliography: references.bib
link-citations: TRUE
---
```

If Zotero is installed locally, your main library will automatically be available.

Add citations by DOI by searching “from DOI” in the Insert Citation dialog.

Insert Citations
Access the Insert Citations dialog in the Visual Editor by clicking the @ symbol in the toolbar or by clicking Insert > Citation.
Add citations with markdown syntax by typing [@cite] or @cite.


# R
