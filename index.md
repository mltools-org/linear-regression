# Simple Linear Regression 

## Store the response variable as $y$ and the predictor variable as $x$

*Code 1:*
```R
x = DATASET$input
y = DATASET$output
```

## Compute the 3 Sum of squares definitions:

*Code 2:*
```R
Sxy = sum((x - mean(x)) * (y - mean(y)))
Sxx = sum((x - mean(x)) ^ 2)
Syy = sum((y - mean(y)) ^ 2)
c(Sxy, Sxx, Syy)
```

*Code 2 result:*
```R
[1]  5387.40  1370.00 32538.98
```

## Find the intercept and slope coefficients using Sum of squares definitions

*Code 3:*
```R
beta_1_hat = Sxy / Sxx
beta_0_hat = mean(y) - beta_1_hat * mean(x)
c(beta_0_hat, beta_1_hat)
```
*Code 3 result:*
```R
[1] -17.579095   3.932409
```

## Estimation using the lm() function

*Code 4:*
```R
model = lm(ouput ~ input, data = DATASET)
```

## Summary the result of the *model*

*Code 5:*
```R
summary(model)
```
*Code 5 result:*
```R
Call:
lm(formula = output ~ input, data = DATASET)

Residuals:
    Min      1Q  Median      3Q     Max 
-29.069  -9.525  -2.272   9.215  43.201 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) -17.5791     6.7584  -2.601   0.0123 *  
input         3.9324     0.4155   9.464 1.49e-12 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 15.38 on 48 degrees of freedom
Multiple R-squared:  0.6511,	Adjusted R-squared:  0.6438 
F-statistic: 89.57 on 1 and 48 DF,  p-value: 1.49e-12
```

## Plot each observation (x,y) with the fitted regression line


```R
plot(output ~ input, data = DATASET,
     xlab = " name of the Input variable",
     ylab = "name of the Output variable",
     main = "Title of your plot,
     pch  = 20,
     cex  = 2,
     col  = "grey")
abline(model, lwd = 3, col = "darkorange")
```



