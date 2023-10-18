---
title: "GGPLOTS"
bibliography: https://rstudio.github.io/cheatsheets/html/data-visualization.html?_gl=1*lf2yr8*_ga*MTUxNjk2OTczMC4xNjk0MjkyNTE0*_ga_2C0WZ1JHG0*MTY5NzY2NTY5Ny41LjAuMTY5NzY2NTY5Ny4wLjAuMA..
link-citations: TRUE
author : sud0
---
ggplot2 is based on the grammar of graphics, the idea that you can build every graph from the same components: 
a data set, a coordinate system, and geoms—visual marks that represent data points.



### Basic Structure of GGplots
```
ggplot(data = <Data>) +
  <Geom_Function>(mapping = aes(<Mappings>),
  stat = <Stat>,
  position = <Position>) +
  <Coordinate_Function> +
  <Facet_Function> +
  <Scale_Function> +
  <Theme_Function>
```


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


### Plotting
