# Linear regression

Linear regression is a statistical technique used to analyze the linear
relationship between a continuous dependent variable and one or more
numerical or categorical independent variables. It is a commonly used
method in data analysis and modeling to predict the value of the
dependent variable based on the values of the independent variables.

![](Linear-regression_files/figure-markdown_strict/unnamed-chunk-2-1.png)

In this particular example, you can calculate the cholesterol level of a
person if you know his/her age:

**y = a+bx1**

\_\_Cholesterol = a + b\*age + e\_\_

where `y` is the response variable, `age` is the predictor variable, `a`
is the intercept, and `b` is the slope coefficient.

In a **simple linear regression**, there is only one independent
variable and one dependent variable. The relationship between the two
variables is represented by a straight line, which is fitted to the data
using the least squares method. The slope of the line represents the
change in the dependent variable for a unit change in the independent
variable, while the intercept represents the value of the dependent
variable when the independent variable is zero.

### Simple linear regression in R

    # Create a linear regression model
    model <- lm(cholesterol ~ age, data = mydata)
    summary(model) #Review the results

    ## 
    ## Call:
    ## lm(formula = cholesterol ~ age, data = mydata)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -5.3528 -4.2178 -0.5828  1.8443  9.5552 
    ## 
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)  68.5429    10.8683   6.307 0.000231 ***
    ## age           3.1135     0.2276  13.679 7.86e-07 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 5.198 on 8 degrees of freedom
    ## Multiple R-squared:  0.959,  Adjusted R-squared:  0.9539 
    ## F-statistic: 187.1 on 1 and 8 DF,  p-value: 7.858e-07

**Multiple linear regression** is an extension of simple linear
regression and is used when there are two or more independent variables.
In this case, the relationship between the dependent variable and the
independent variables is represented by a plane or hyperplane.

The main objective of linear regression is to find the line or plane
that best fits the data. This is done by minimizing the sum of the
squared differences between the observed values of the dependent
variable and the values predicted by the model.

Linear regression is widely used in various fields such as economics,
finance, social sciences, engineering, and medical research. It can be
used for prediction, forecasting, and trend analysis. It is also used
for hypothesis testing and to assess the strength of the relationship
between variables.
