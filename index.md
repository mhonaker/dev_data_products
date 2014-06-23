---
title       : Comparing Iris Data to the Normal Distribution
subtitle    : 
author      : mhonaker
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## The iris dataset
<ul>
<li>This dataset contains some measurements of flower properties of three different species of iris.</li>
<li>Often, but not always, real measurements like these conform to a classic normal distribution.</li>
</ul>

```r
hist(iris$Sepal.Width, breaks = 20, col = "skyblue", xlab = "Sepal Width", main = "")
```

<img src="assets/fig/unnamed-chunk-1.png" title="plot of chunk unnamed-chunk-1" alt="plot of chunk unnamed-chunk-1" style="display: block; margin: auto;" />


---

## The normal distribution     

The normal, or Gaussian, probability density function:   
$$F(x;\mu,\sigma)=\int_{-\infty}^x \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}$$   
is often used to approximate real data, such as flower size.   
A way to compare some real data to a normal distribution would be quite convenient.

---
   
## Comparing the ideal to real data  
The histogram below shows real data, and the line the normal distribution with the same standard deviation.


```r
hist(I(iris$Sepal.Width - mean(iris$Sepal.Width)), freq = F, breaks = 20, xlab = "", 
    main = "", col = "lightblue")
x <- seq(-1.5, 2, length = 1000)
y <- dnorm(x, mean = 0, sd = sd(iris$Sepal.Width))
lines(x, y, type = "l", lwd = 3, col = "blue")
```

<img src="assets/fig/unnamed-chunk-2.png" title="plot of chunk unnamed-chunk-2" alt="plot of chunk unnamed-chunk-2" style="display: block; margin: auto;" />

---

## A shiny app to do the same thing...   
<ul>
<li>The shiny app deployed at <a href = "http://mhonaker.shinyapps.io/proj2/">http://mhonaker.shinyapps.io/proj2/</a> does just that.</li>
<li>A user can plot one of several data sets, and compare the normal distributions.</li>
<li>Additionally, a user can plot a normal distribution of their own mean and standard deviation.</li>
<li>Further projected improvements include the ability to upload a user generated dataset.</li>
</ul>

