# House Prices: Advanced Regression Techniques (Top 8%)

![top](images/top-8-percent.png)

## Removing Outliers

There are significant outliers in this data set. Identifying and removing such data points can have a great impact on the residual error your model.

![outliers](images/outliers.png)

## Feature Selection: Multicollinearity

Variance Inflation Factor can detect Multicollinearity.

<img src="https://render.githubusercontent.com/render/math?math=VIF_{i} = \frac{1}{1 - R_{i}^{2}}">

where <img src="https://render.githubusercontent.com/render/math?math=R_{i}^{2}"> is the <img src="https://render.githubusercontent.com/render/math?math=R^{2}">from a regression of an input vector <img src="https://render.githubusercontent.com/render/math?math=X_{i}"> from all of the other features. If <img src="https://render.githubusercontent.com/render/math?math=R^{2}"> is close to 1, then collinearity is present, and so the VIF will be large.

Preforming this calculation found significant collinearity with 1StFlrSF all other features with a VIF > 30. This is consistent with the intuition that the first floor is going to be equal in size the the square footage of the basement and second floor.

![sf-collinearity](images/sf-vs-basement-collinearity.png)

Also GarageAre proved to had

![garage-collinearity](images/garage-collinearity.png)

Removing these features showed a significant increase in score.

## Dealing with Skewness

We used used the followin calculates the coefficient of skewness:

<img src="https://render.githubusercontent.com/render/math?math=\frac{\mu_{3}}{\mu_{2}^{3/2}}">

where <img src="https://render.githubusercontent.com/render/math?math=\mu_{i}"> is tthe cetral moment. Negative skew usually  indicates that the tail is on the left side of the distribution, and positive skew indicates that the tail is on the right. For normally distributed data, the skewness should be about 0. Applying a one parameter box cox transformation to the skewed variable that have a skewness of s such that 2 < s < -2.

![bc](https://www.statisticshowto.datasciencecentral.com/wp-content/uploads/2015/07/boxcox-formula-1.png)

Making this transformation with helped us  achieve symmetry, and normality of our variables. It will also help us stabilize the variance of the distributions and improve the validity of association measures (e.g. correlation).

![box-cox](images/skewness-coefficient.png)

## Natural Log Transformation of Sale Price

![before](images/kde-before-log.png)
![after](images/kde-after-log.png)

## Prediction

![prediction](images/prediction.png)