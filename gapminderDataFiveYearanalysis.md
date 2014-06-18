

```r
setwd("/users/Nicole/Skydrive/Courses/sc")
data<- read.delim("gapminderDataFiveYear.txt")
IIIdata<- subset(data, country=="Mali" | country=="Oman" | country=="Italy")
```

Mali has a consistently lower GDP than OMan and Italy. The GDP for Oman spiked precipitously in the 1970s.


```r
library(reshape2)
```

```
## Warning: package 'reshape2' was built under R version 3.0.3
```

```r
library(ggplot2)
```

```
## Warning: package 'ggplot2' was built under R version 3.0.3
```

```r
ggplot(data=IIIdata, aes(x=year, y=gdpPercap), color = country) + geom_point(aes(shape=country))
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 
Calculate the mean, min, and max life expectancies for each continent (hint: you use aggregate() if you like). Describe what you see in the results using a markdown text.


```r
maxagg<- aggregate(lifeExp ~ country, IIIdata, FUN=max)
aggdata<- aggregate(lifeExp ~ country, IIIdata, FUN=min)
minagg<- aggdata
avgagg<- aggregate(lifeExp ~ country, IIIdata, FUN=mean)

maxagg
```

```
##   country lifeExp
## 1   Italy   80.55
## 2    Mali   54.47
## 3    Oman   75.64
```

```r
minagg
```

```
##   country lifeExp
## 1   Italy   65.94
## 2    Mali   33.69
## 3    Oman   37.58
```

```r
avgagg
```

```
##   country lifeExp
## 1   Italy   74.01
## 2    Mali   43.41
## 3    Oman   58.44
```
Overall, life expectancies show more of a bimodal distribution when the bin size is reduced. 


```r
ggplot(data, aes(x=lifeExp)) + geom_histogram(binwidth = 30, colour = "black")
```

![plot of chunk unnamed-chunk-4](figure/unnamed-chunk-41.png) 

```r
ggplot(data, aes(x=lifeExp)) + geom_histogram(binwidth = 10, colour = "black")
```

![plot of chunk unnamed-chunk-4](figure/unnamed-chunk-42.png) 

```r
ggplot(data, aes(x=lifeExp)) + geom_histogram(binwidth = 5, colour = "black")
```

![plot of chunk unnamed-chunk-4](figure/unnamed-chunk-43.png) 
