---
title: "GGPLOTS"
bibliography: https://rstudio.github.io/cheatsheets/html/data-visualization.html?_gl=1*lf2yr8*_ga*MTUxNjk2OTczMC4xNjk0MjkyNTE0*_ga_2C0WZ1JHG0*MTY5NzY2NTY5Ny41LjAuMTY5NzY2NTY5Ny4wLjAuMA..
link-citations: TRUE
author : sud0
---
ggplot2 is based on the grammar of graphics, the idea that you can build every graph from the same components: 
a data set, a coordinate system, and geoms—visual marks that represent data points.



# Basic Structure of GGplots
```r
ggplot(data = <Data>) +
  <Geom_Function>(mapping = aes(<Mappings>),
  stat = <Stat>,
  position = <Position>) +
  <Coordinate_Function> +
  <Facet_Function> +
  <Scale_Function> +
  <Theme_Function>
```

## Scatter Plots.

```r
ggplot(data = facts_state,        # which data set?
       aes(x=college, y=income))  # which variables as aesthetics?
       + geom_point()
```

The geompoints create a **scatter Plot**
The same plots can be plotted in within the geompoints such as the following : 

```r
# same plot as above
ggplot(data = facts_state) + 
  geom_point(mapping = aes(x = college, y = income)) 
```


| Function                                | Explanation                      |
|-----------------------------------------|----------------------------------|
| `geom_points`                           | Scatter plot                     |
| `geom_smooth`                           | Loess curve                      |
| `geom_smooth(method = "lm")`            | Linear regression line           |
| `geom_points(aes(x, y, size = Population))` | Size of points according to Population |
| `geom_points(aes(x, y, size = white_pct))`  | Color of points depending on "white_pct" column |

## Barplots & Line Plots


| Function                                | Explanation                      |
|-----------------------------------------|----------------------------------|
| `geom_bar(aes(x = growth))`             | Bar Plot mapped for x            |
| `geom_col(aes(x = canidate, y = votes))`| Directly Feed the Y, so geom_col can plot the fed plot|
| `geom_line(aes(x, y))`                  | geom_line creates a line plot|



*geom_polygon -> plots the maps or any other shapes*


*aes()*
stands for aesthetics and is used define how the variables in your data should be mapped to visual plots.
mappings -> function to specify how these variables are mapped to the visual properties.

Thus if it was used without the aes like the code below : 

```{r}
library(ggplot2)
ggplot(data = your_data_frame) +
geom_point(aes(x = x, y = y), color = "blue")
```

would plot all the points blue no matter the value of the points. On the other hand, if the variables
were `aes(color = variables)`, then the aes() will automatically assign colors based on the unique values.


