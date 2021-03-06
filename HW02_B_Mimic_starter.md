HW02\_B\_Graph-Mimic
================
Julia Shangguan

``` r
library("ggplot2")
library("magrittr") 
data("diamonds")
data("mpg")
data("iris")
theme_set(theme_bw()) 
library("ggrepel")
```

## HW02 Part B

### Graph 1

``` r
ggplot(diamonds, aes(x = cut, fill = clarity)) +
  geom_bar(position = "dodge") + 
  annotate("rect", xmin = 4.5, xmax = 5.5, ymin = 0, ymax = 5000,fill = "black", alpha = 0.2) +
  annotate("text", x = 4, y = 4500, label = "My Best Diamonds,\nof course") +
  theme_bw() +
  xlab("Diamond Cut") +
  ylab("Number of Diamonds") +
  labs(title = "My Diamond Collection", subtitle = "Boxplot representing the number of diamonds in my diamond collection by\ntype of cut quality and clarity of diamond") +
  theme(plot.title = element_text(hjust = 0.5)) 
```

![](HW02_B_Mimic_starter_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

### Graph 2

``` r
ggplot(iris, aes(x = Sepal.Length, y = Petal.Length, color = Species, shape = Species)) +
  geom_point() +
  facet_wrap(~Species, ncol = 3, scales = "free_y") +
  xlim(4,8) +
  geom_smooth(method = "lm", formula = y~x, se = FALSE, color = "black")
```

![](HW02_B_Mimic_starter_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

### Graph 3

``` r
data("mpg")
corvette <- mpg[mpg$model == "corvette",]
#install
require("ggrepel") #useful for making text annotations better, hint hint
set.seed(42)
```

``` r
ggplot(mpg, aes(displ, hwy, label = paste("Corvette,",year))) +
  geom_point() +
  labs(title = "Corvettes are a bit of an outlier") +
  geom_text_repel(data = subset(corvette)) +
  geom_point(data = subset(corvette), color ="blue")
```

![](HW02_B_Mimic_starter_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

### Graph 4

I assume that Robert added jitter to get the extra data points, so I
added jitter.

``` r
ggplot(mpg, aes(cty, class, color = class))+
  geom_point() +
  geom_jitter() +
  geom_boxplot(alpha = 0, color = "black") +
  scale_color_brewer(palette="Set2") +
  xlab("Car Class") +
  ylab("City mpg") +
  labs(title = "Horizontal BoxPlot of City MPG and Car Class")
```

![](HW02_B_Mimic_starter_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->
