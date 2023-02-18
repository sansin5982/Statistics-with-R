# Correlation

Correlation analysis is a statistical method used to examine the
strength and direction of the relationship between two continuous
variables. The most commonly used correlation coefficient is **Pearson’s
correlation coefficient**, which measures the linear relationship
between two variables. Pearson’s correlation coefficient, denoted by
“r,” takes on values between -1 and 1, where a value of -1 indicates a
perfect negative correlation, a value of 0 indicates no correlation, and
a value of 1 indicates a perfect positive correlation.

To perform a correlation analysis, we first need to collect data on the
two variables of interest. Once we have the data, we can calculate the
correlation coefficient using R.

For example, suppose we want to examine the relationship between a
person’s age and their cholesterol level. We collect data on 100
individuals and obtain the following data:

<table>
<thead>
<tr class="header">
<th>Age (in years)</th>
<th>Cholesterol Level (in mg/dL)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>45</td>
<td>210</td>
</tr>
<tr class="even">
<td>38</td>
<td>185</td>
</tr>
<tr class="odd">
<td>52</td>
<td>240</td>
</tr>
<tr class="even">
<td>60</td>
<td>250</td>
</tr>
<tr class="odd">
<td>35</td>
<td>175</td>
</tr>
<tr class="even">
<td>42</td>
<td>200</td>
</tr>
<tr class="odd">
<td>48</td>
<td>220</td>
</tr>
<tr class="even">
<td>55</td>
<td>235</td>
</tr>
<tr class="odd">
<td>50</td>
<td>230</td>
</tr>
<tr class="even">
<td>47</td>
<td>210</td>
</tr>
</tbody>
</table>

![](Correlation_files/figure-markdown_strict/unnamed-chunk-2-1.png)

## Pearson Correlation Coefficient

Pearson correlation is a statistical technique used to measure the
strength and direction of the linear relationship between two continuous
variables. It assumes that both variables are normally distributed and
have a linear relationship. The Pearson correlation coefficient (r)
ranges from -1 to +1, where a value of -1 indicates a perfect negative
correlation, 0 indicates no correlation, and +1 indicates a perfect
positive correlation.

There are a few assumptions that must be met in order to use Pearson
correlation:

**1. Normality:** Both variables should be normally distributed. You can
check for normality using a histogram, a Q-Q plot, or a normal
probability plot.

**2. Linearity:** The relationship between the two variables should be
linear. You can check for linearity by creating a scatter plot of the
two variables and visually inspecting the plot to see if there is a
linear relationship.

**3. Level of measurement:** Both variables should be continuous.

**4. Realted pairs:** Each observation in the dataset should have a pair
of values.

**5. No outliers:** here should be no extreme outliers in the dataset.

**6. Independence:** The observations should be independent of each
other. This means that there should be no relationship between the
observations that could influence the correlation coefficient.

If these assumptions are not met, the results of the Pearson correlation
may be biased or misleading. If the normality assumption is not met, you
may need to transform the data or use a nonparametric correlation
technique such as **Spearman’s rank correlation**. If the independence
assumption is not met, you may need to use a different statistical
technique or account for the non-independence using a mixed-effects
model or other appropriate method.

    # Check for normality
    ggplot(mydata, aes(x = age)) +
      geom_histogram(binwidth = 10, fill = "lightblue", color = "black") +
      labs(title = "Histogram of Age", x = "Age", y = "Frequency")+
      theme_classic()

![](Correlation_files/figure-markdown_strict/unnamed-chunk-3-1.png)

    ggplot(mydata, aes(x = cholesterol)) +
      geom_histogram(binwidth = 25,fill = "lightblue", color = "black") +
      labs(title = "Histogram of Cholesterol", x = "Cholesterol", y = "Frequency")+
      theme_classic()

![](Correlation_files/figure-markdown_strict/unnamed-chunk-4-1.png)

    # Shapiro-Wilk normality test for mpg
    #H0: data are normally distributed
    shapiro.test(mydata$age) 

    ## 
    ##  Shapiro-Wilk normality test
    ## 
    ## data:  mydata$age
    ## W = 0.99077, p-value = 0.9977

    # Shapiro-Wilk normality test for wt
    shapiro.test(mydata$cholesterol)

    ## 
    ##  Shapiro-Wilk normality test
    ## 
    ## data:  mydata$cholesterol
    ## W = 0.96909, p-value = 0.8823

    # Check for linearity
    ggplot(mydata, aes(x = age, y = cholesterol)) + 
      geom_point() + 
      labs(title = "Relationship between Age and Cholesterol", x = "Age", y = "Cholesterol")+
      theme_classic()

![](Correlation_files/figure-markdown_strict/unnamed-chunk-7-1.png)

    # Calculate Pearson correlation coefficient
    cor(mydata$age, mydata$cholesterol) #default Perason's

    ## [1] 0.9792846

    cor(mydata$age, mydata$cholesterol, method="pearson") #specify the method

    ## [1] 0.9792846

    cor(mydata$age, mydata$cholesterol, method="pearson",use = "complete.obs")

    ## [1] 0.9792846

    #in case of NAs being present, specify complete.obs

    #is my correlation statistically significant?
    #Ho=there is no association between the two variables
    cor.test(mydata$age, mydata$cholesterol)

    ## 
    ##  Pearson's product-moment correlation
    ## 
    ## data:  mydata$age and mydata$cholesterol
    ## t = 13.679, df = 8, p-value = 7.858e-07
    ## alternative hypothesis: true correlation is not equal to 0
    ## 95 percent confidence interval:
    ##  0.9119540 0.9952539
    ## sample estimates:
    ##       cor 
    ## 0.9792846

    library(corrplot)

    ## corrplot 0.92 loaded

    corr1<-cor(mydata) #compute multiple correlations
    corr1

    ##                   age cholesterol
    ## age         1.0000000   0.9792846
    ## cholesterol 0.9792846   1.0000000

    corrplot(corr1)

![](Correlation_files/figure-markdown_strict/unnamed-chunk-13-1.png)

    corrplot(corr1, method="color")

![](Correlation_files/figure-markdown_strict/unnamed-chunk-13-2.png)
