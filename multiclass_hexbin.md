
# Multi-class hexbins

Hritik Jain and Shahen Mirzoyan



In one of her lectures, Prof. Robbins introduces students to hexagonal heatmaps as one of the most common methods for visualizing the observed frequency of two variables in a dataset. We came across a variation of this visualization tool known as multi-class hexbins. Multi-class hexbins allow you to see two features of a dataset while accounting for a third categorical variable. The third variable is visualized by dividing up each hexbin so that every class is represented proportionally to its observed frequency. In this tutorial, we will demonstrate the R package **hextri**.

As a running example, let's pick up on the same assignment problem where we first got to use hexagonal heatmaps - "weather" data from the R package "nycflights13". Here is the hexagonal heatmap that shows the heatmap of **wind_dir** and **humid**.


```r
library(tidyverse)
data("weather", package="nycflights13")
ggplot(weather, aes(humid, wind_dir)) + geom_hex(bins=20) + scale_fill_gradient(low = "white", high = "black") +
  xlab("Relative Humidity") +
  ylab("Wind direction (degrees)") +
  theme(plot.margin = margin(1.8,.7,1.8,.7, "cm"), panel.border = element_rect(colour = "black", fill=NA), panel.background = element_rect(fill='white', color='white'))
```

<img src="multiclass_hexbin_files/figure-html/unnamed-chunk-3-1.png" width="672" style="display: block; margin: auto;" />

The heatmap above includes all the three source airports (variable **orging** in the dataset) - _LGA_, _JFK_ and _EWR_ while displaying counts in the different hex bins. Now if we want to visualize the same information separately for each of the airports, we could do faceting on **origin**. But what if we could do that without faceting, in one panel?


```r
library(hextri)
with(weather, hextri(humid, wind_dir, class=origin, colour=c("orange","green", "blue"),
    nbins=20,xlab="Relative humidity",ylab="Wind direction (degrees)"))
```

<img src="multiclass_hexbin_files/figure-html/unnamed-chunk-4-1.png" width="672" style="display: block; margin: auto;" />

The above plot represents each of the three airports in our dataset as a separate color, and the representation of each airport within a given hexbin is proportional to the observed frequency for that airport.

The default behavior of hextri is to use alpha to represent the weight of each bin. However, the function also gives us the flexibility to use hexagon size to represent the weight of each bin.


```r
with(weather, hextri(humid, wind_dir, class=origin,style="size",colour=c("orange","green", "blue"),
    nbins=20,xlab="Relative humidity",ylab="Wind direction"))
```

<img src="multiclass_hexbin_files/figure-html/unnamed-chunk-5-1.png" width="672" style="display: block; margin: auto;" />

For classes that have less than 1/12th representation, hextri allows us to use the optional diffuse parameter which takes these underrepresented classes and divides them up evenly among nearby hexbins. 


```r
with(weather, hextri(humid, wind_dir, class=origin,colour=c("orange","green", "blue"),
    nbins=20,xlab="Relative humidity", ylab="Wind direction", diffuse=TRUE))
```

<img src="multiclass_hexbin_files/figure-html/unnamed-chunk-6-1.png" width="672" style="display: block; margin: auto;" />


For more use cases and further customization options, please refer to the [hextri documentation](https://cran.r-project.org/web/packages/hextri/vignettes/hexbin-classes.html){target="_blank"}
