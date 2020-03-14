# House Prices: Advanced Regression Techniques (Top 8%)

## Removing Outliers

There are significant outliers in this data set. Identifying and removing such data points can have a great impact on the residual error your model.

![outliers](images/outliers.png)

## Feature Selection: Multicollinearity

Variance Inflation Factor can detect Multicollinearity.

$VIF_{i} = \frac{1}{1 - R_{i}^{2}$

where $R_{i}^{2}$ is the $R^{2}$ from a regression of an input vector $X_{i}$ from all of the other features. If $R^{2}$ is close to 1, then collinearity is present, and so the VIF will be large.

Preforming this calculation found significant collinearity with 1StFlrSF all other features with a $VIF > 30$. This is consistent with the intuition that the first floor is going to be equal in size the the square footage of the basement and second floor.

![sf-collinearity](images/sf-vs-basement-collinearity.png)

Also GarageAre proved to had

![garage-collinearity](images/garage-collinearity.png)

Removing these features showed a significant increase in score.
