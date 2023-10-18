# Political Communications & Data Analysis

For a political communication & data analysis class, there is going to be an assesment for the R part, this repo is going to contain the basics of R.



### R TidyVerse

Data Transformation, otherwise known as data preprocessing can be done with the [R Tidyverse](./tidy.rmd).

```r
read_csv(url) |> 
  filter(Question == 'age-21') |>
  mutate(party_diff = abs(`Republican Support` - `Democratic Support`)) |>
  select(Question, Pollster, party_diff) |>
  arrange(-party_diff)
```


### GGplots

For most of the visualization we can use the [ggplots](./ggplots.rmd) library


### Basic R Chunk
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
