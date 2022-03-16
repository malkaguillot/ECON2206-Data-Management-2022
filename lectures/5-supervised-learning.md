
# Data Management
## Supervised learning
### [Malka Guillot](https://malkaguillot.github.io/)
### HEC Liège | <a href="https://gitlab.uliege.be/mguillot/econ2306-data-management-2021-22/">ECON2306</a>

<!-- exportation : decktape --chrome-arg=--disable-web-security 5-supervised-learning.html 5-supervised-learning.pdf -s 1024x768
--->


---


<!-- .slide:  id="toc" class: left, inverse -->
## Table of Contents

1. [Prologue](#prologue)
2. [Regressions](#linear)
  1. [Linear Regression](#linear)
  2. [Regularized Regression](#linear)
1. [Classifcations](#introduction)
  1. [Performance Measures](#performance)
  2. [Binary Classifier](#binary)
2. [Wrap up](#wrap)


---

<!-- .slide: id="prologue"  -->
# Prologue
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>
<!--  
Things to clarify:
  - what is on the moodle & what is on the GitHub
    - github: things that go public
    - moodle: private documents
    - Also: notebooks depend on images => need for the github folder
    - you can print the html slides yourselves to pdf: by using print on your browser
  - Post class discussion on the course projects
  - You cannot view the notebooks as slides unless you install more options, but why would you?

-->

--

## Reference:
- [JWHT](https://static1.squarespace.com/static/5ff2adbe3fe4fe33db902812/t/601cc86d7f828c4792e0bcae/1612499080032/ISLR+Seventh+Printing.pdf), chap 3, 6.2
- Geron, chapter 2


---

# Linear Regression as a Predictive Model
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

--

## Linear Regression

$$Y=\beta_0 + \beta_1 X_1 + \cdots + \beta_p X_p + \epsilon $$

$=$ one of the simplest algorithms for doing supervised learning

A good starting point before studying more complex learning methods

Notes:
Interpretation of $\beta_j$ = the average effect on $Y$ of a unit increase in $X_j$ holding all other predictors fixed

--

## Estimation by Ordinary Least Squares

$RSS=\textrm{Residual sum of squares}=\sum_{i=1}^n (y_i - \hat y_i)^2$

Minimizing RSS gives a <bcolor>closed form solution</bcolor> for the  $\hat \beta_1,\cdots \hat \beta_p$

Most ML models <bcolor>do not</bcolor> have a a colsed form solution

--

<img data-src="./images/jwht-fig3-4.png"  style="height: 400px; position:relative;     margin-left: auto;margin-right: auto;display: block" >


--

## Extensions of the Linear Model

Going further model's assumptions:

- the <bcolor>additive</bcolor>: the effect of changes in a predictor $X_j$ on the response $Y$ is independent of the values of the other predictors

-  <bcolor>linearity</bcolor>: the change in the response $Y$ due to a one-unit change in $X_j$ is constant

--

### Interactions
- Adding interacted variable can help
- Should respect the <bcolor>hierarchy principle</bcolor>:
  - if an interaction is included, the model should always include the main effects as well

Notes:
- Even if the p-value associated with their coef is not significant
- Interactions are hard to interpret without main effects in the model

--

### Non Linearity
- Include transformed versions of the predictors in the model


$\Rightarrow$ Including polynomials in $X$ may provide a better fit

--

## Linear Models: pros and cons
- [Pros]():
  - Interpretability
  - Good predictive performance
  - Accuracy measures for
      - coefficient estimates (standard errors and confidence intervals)
      - the model

- [Cons]():
  - When $p>n$
  - Tend to over-fit training data.
  - Cannot handle multicollinearity.

--

## Generalization of the Linear Models
- <bcolor>Classification problems</bcolor>: logistic regression, support vector machines

- <bcolor>Non-linearity</bcolor>: nearest neighbor methods

- <bcolor>Interactions</bcolor>: Tree-based methods, random forests and boosting

- <bcolor>Regularized fitting</bcolor>: ridge regression and lasso

Notes:
In much of the rest of the class, we discuss methods that expand the scope of linear models and how they are fit:

---

<!-- .slide: id="regularized"  -->
# Regularized Regressions
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

--

## Why Regularization?

- Solution against <bcolor>over-fitting</bcolor>

-  Allow High-Dimensional Predictors
  - $p>>n$: OLS no longer has a unique solution
  - $x_i$ "high-dimensional" i.e. very many regressors
    - pixels on a picture

Notes:
Corollary of regularization:
- Prediction Accuracy:especially when $p > n$, to control the variance

--

## Adding a Regularization Term to the Loss Function $L(.)$

`$$ \hat \beta =arg min_\beta \frac{1}{n} \sum_{i=1}^n L(h(x_i, \beta), y_i) +\lambda R(\beta) $$`

- $R(\beta)$ = <bcolor> regularization  function </bcolor>
  - $R(\beta)=\sum_{i=1}^n p(\beta_i)$ for $p(.)$ the penalty function

- $\lambda$ is a <bcolor>hyperparameter</bcolor> where higher values increase regularization


--

## Different Penalty Functions $p()$
- <bcolor>Ridge (L2)</bcolor>: $p(\beta_j)=\beta_j^2$

- <bcolor>LASSO (L1)</bcolor>: $p(\beta_j)=|\beta_j|$

- <bcolor>Elastic Net</bcolor>: $p(\beta_j)=\alpha |\beta_j| + (1-\alpha) \beta_j^2$

- <bcolor>Subset selection</bcolor>: $p(\beta_j)=1\\{\beta_j\neq 0\\}$

Notes:
- **Ridge**: shrinks coefficients toward zero and helps select between collinear predictors.
- **Lasso** automatically performs feature selection and outputs a sparse model.


--

## How to Solve Without a Closed-form Solution? Gradient Descent
<img data-src="./images/gradient-descent.jpeg"  style="height: 400px; position:relative;     margin-left: auto;margin-right: auto;display: block" >

Gradient descent measures the local gradient of the error function, and then steps in that direction.

$\rightarrow$ Minimum in 0

Notes:
- Gradient Descent is a first-order iterative optimization algorithm for finding the local minimum of a differentiable function
  - because it uses the first-order derivative of the loss function to find minima
- Initialize the parameters(weights and bias) randomly.
- In each iteration we move a step in direction of steepest descent
- The size of each step is determined by a parameter which is called Learning Rate

--

## Stochastic Gradient Descent

1. Picks a <bcolor>random instance</bcolor> in the training set

2. Computes the gradient only for that single instance

- [**Pro**](): SGD is much faster to train,

- [**Cons**](): bounces around even after it is close to the minimum.

$\rightarrow$ Compromise: <bcolor>mini-batch gradient descent</bcolor>, selects a sample of rows (a “mini-batch”) for gradient compute

Notes:
- Instead of just randomly sampling one point at each step (SGD), the **“mini-batch”** gradient descent samples a small number of points.
- Mini-batch tries to strike a balance between the goodness of gradient descent and speed of SGD.


--

## Varients of Gradient Descent
<img data-src="./images/gradient-descent-details.png"  style="height: 400px; position:relative;     margin-left: auto;margin-right: auto;display: block" >




--

## Ridge Regression

$min_{\beta} \sum_{i=1}^n (y_i - \hat y_i)^2 + \lambda \sum_{j=1}^p \beta_j^2 $

Where
- $\lambda > 0$ = penalty parameter
- covariates can be high-dimensionnal $p>>N$

Trade-off, from the minimization of the sum of
1. RSS
2. shrinkage penalty: decreases with $\beta_j$

$\rightarrow$ relative importance given by $\lambda$

Notes:
- The tuning parameter $\lambda$ serves to control the relative impact of these two terms on the regression coefficient estimates.
- When $\lambda=0$, the penalty term has no effect, and ridge regression will produce the least squares estimates
- when $\lambda \rightarrow \infty$ : penalty grows and coefficient estimates approach zero

--

## Ridge Regression: shrinkage to $0$
<img data-src="./images/jwht-`fig6`-4.png"  style="height: 400px; position:relative;     margin-left: auto;margin-right: auto;display: block" >

Notes:
Next: Why Does Ridge Regression Improve Over Least Squares?

--

## Ridge: Variance-Bias Trade-Off
<img data-src="./images/jwht-fig6-5.png"  style="height: 400px; position:relative;     margin-left: auto;margin-right: auto;display: block" >

Squared bias (black), variance (green), [test] MSE (red)

Notes:
- As $\lambda$ increases, the flexibility of the ridge regression fit decreases, leading to decreased variance but increased bias
- Up to 10, the variance decreases rapidly, with very little increase in bias
- Beyond this point, the decrease in variance due to increasing $\lambda$ slows, and the shrinkage on the coefficients causes them to be significantly underestimated
- Recall that the test MSE (purple), is a function of the variance plus the squared bias.

--

## Ridge vs. Linear Models

- when outcome and predictors are close to having a linear relationship, the OLS will have low bias but potentially high variance
  - small change in the training data $\rightarrow$ large change in the estimates
  - worse with $p$ close tp $n$
  - if $p>n$, OLS do not have a unique solution

$\rightarrow$ ridge regression works best in situations where the least squares estimates have high variance

--

## LASSO
Overcome an important drawback of Ridge (all $p$ predictors are included in the final model)

LASSO proposes a method to build a model which just <bcolor>includes the most important predictors</bcolor>.

Better for interpretability than Ridge!

Notes:
Ridge: the penalty shinks coefficients toward $0$ but not exactly to $0$

This may not be a problem for prediction accuracy, but it can create a challenge in model interpretation when $p$ is quite large

--

## Lasso Coefficients
<img data-src="./images/jwht-fig6-6.png"  style="height: 400px; position:relative;     margin-left: auto;margin-right: auto;display: block" >

Notes:
- When $\lambda=0$: the lasso simply gives the least squares fit
- when $\lambda$ becomes sufficiently large, the lasso gives the null model in which all coefficient estimates equal 0.
- in between these two extremes, the ridge regression and lasso models are quite different from each other

--

## Lasso: Variance-Bias Trade-Off
<img data-src="./images/jwht-fig6-8.png"  style="height: 400px; position:relative;     margin-left: auto;margin-right: auto;display: block" >

Squared bias (black), variance (green), [test] MSE (red)

--

## Constrained Regression
The minimization problem can be written as follow:

`$$ \sum_{i=1}^n(y_i-x_i'\beta)^2 \textrm{ s.t. } \sum_{j=1}^p p(\beta_j) \leq s,$$`

Where
- Ridge: $\sum_{j=1}^p \beta_j^2 <s $
$\rightarrow$ equation of a <bcolor>circle</bcolor>
- Lasso: $\sum_{j=1}^p |\beta_j| <s $
$\rightarrow$ equation of a <bcolor>diamond</bcolor>

Notes:
- Lasso:  we try to find the set of coefficient estimates that lead to the smallest RSS, subject to the constraint that there is a budgets for how large $\sum_{j=1}^p |\beta_j|$ can be.
- if $s$ is extremely large, it is not very restrictive and the least square solution falls within the budget

--

## Constraint Regions
| Lasso | Ridge|
|:------:|:---:|
|<img data-src="./images/jwht-fig6-7lasso.png"  style="height: 350px;" > | <img data-src="./images/jwht-fig6-7ridge.png" style="height: 350px" class="center"> |


Notes:
- Why is it that the lasso, unlike ridge regression, results in coefficient estimates that are exactly equal to zero?
- diamonds & circle represent the ridge & lasso constraint regions
- the red ellipses are the contours of the RSS (for different levels of RSS): regions centered around $\beta$ of constant value of RSS
- $\hat \beta$ is the least square estimate
- the lasso constraint has corners at each of the axes, and so the ellipse will often intersect the constraint region at an axis $\rightarrow$ When this occurs, one of the coefficients will equal zero.

--

## Elastic Net = Lasso + Ridge
$$ MSE(\beta)+\lambda_1 \sum_{j=1}^p |\beta_j| +\lambda_2 \sum_{j=1}^p \beta_j^2$$

$\lambda_1$, $\lambda_2$ $=$ strength of L1 (Lasso) penalty and L2 (Ridge) penalty

--

## Selecting Elastic Net Hyperparameters

- Elastic net <bcolor>hyperparameters</bcolor> should be selected to optimize out-of-sample fit (measured by mean squared error or MSE).

- <bcolor>“Grid search”</bcolor>
  - scans over the hyperparameter space ($\lambda_1 \geq 0, \lambda_2\geq 0$),
  - computes out-of-sample MSE for all pairs $(\lambda_1, \lambda_2)$ ,
  - selects the MSE-minimizing model.

--

## Evaluating Regression Models: $R^2$
MSE is good for comparing regression models, but the units depend on the outcome variable and therefore are not interpretable

Better to use $R^2$ in the test set, which has same ranking as MSE but it <bcolor>more interpretable</bcolor>.

Notes:
$R^2$ proportion of the variance in the dependent variable that is predictable from the independent variable(s)


---

<!-- .slide: id="prologue"  -->
# Classifications
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

Reference:
- [JWHT](https://static1.squarespace.com/static/5ff2adbe3fe4fe33db902812/t/6009dd9fa7bc363aa822d2c7/1611259312432/ISLR+Seventh+Printing.pdf): chap 2.2.3, 4


--

## Classification Framework

-   Response/target variable $y$ is **qualitative** (or
    **categorical**):

    -   2 categories $\rightarrow$ binary classification

    -   More than 2 categories $\rightarrow$ multi-class classification

-   Features $X$:

    -   can be high-dimensional

-   We want to assign a class to a **quantitative response**

    $\rightarrow$ probability to belong to the class

-   **Classifier**: An algorithm that maps the input data to a specific
    category.

-   Performance measures specific to classification

--

## Application examples

-   In business:

    -   Loan default prediction

    -   Type of costumer

-   In public economics:

    -   Tax evasion prediction

-   In political sciences:

    -   political affiliation of author of texts

-   In medical sciences:

    -   Diagnostic diseases, drug choice

-   Other:

    -   email filtering, speech recognition...

--

## Why not fitting a linear regression?

-   **Technically possible** to fit a linear model using a categorical
    response variable but it implies

    -   an **ordering** on the outcome

    -   a **scale** in the class difference

$\rightarrow$  If the response variable was coded differently, the results could be
    completely different

-   Less problematic if the response variable is **binary**

    -   The result of the model would be stable

    -   But prediction may lie outside of $[0, 1]$: hard to interpret
        them in terms of probabilities

Notes:

--

## Example

-   We predict $y$, the **occupation of individuals**:
  $$y = \\{
    \\begin{array}{cc}
      0 & \textrm{ if blue-collar} \\\\
      1 & \textrm{ if white-collar}
    \\end{array}
    $$
-   based on their characteristics $X$ (gender, wage, contract duration,
    experience, age...)

<img data-src="./images/logistic-vs-linear.png"  style="height: 350px; position:relative;background-color:white;     margin-left: auto;margin-right: auto;display: block" >


--

## Linear Regression vs Binary Classifier

-   We model the probability of belonging to a category
    $$P(y=1 \mid X)$$

-   We can rely on this probability to assign a class to the
    observation.

    -   For example, we can assign the class yes for all observations
        where $P(y = 1 | x) > 0.5 $

    -   But we can also select a different **threshold**.


---

<!-- .slide: id="performance"  -->
# Performance measures
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>


--

## Confusion Matrix

- For comparing the predictions of the fitted model to the actual classes.

- After applying a classifier to a data set with known labels *Yes* and *No*:

<table>
<thead>
  <tr>
    <th></th>
    <th></th>
    <th colspan="2">Predicted class</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td></td>
    <td></td>
    <td>no</td>
    <td>yes</td>
  </tr>
  <tr>
    <td rowspan="2">True class</td>
    <td>no</td>
    <td style="color:#90EE90;">TN</td>
    <td style="color:orange;">FP</td>
  </tr>
  <tr>
    <td>yes</td>
    <td style="color:yellow;">FN</td>
    <td style="color:green;">TP</td>
  </tr>
</tbody>
</table>


--

## Precision and Recall

-   <bcolor>Precision</bcolor>

    -   accuracy of positive predictions.

    -   $  \frac{ \color{green}{\text{True Positives}}} {\color{green}{\text{True Positives}} +  \color{orange}{\text{False Positives}}}$

    -   decreases with false positives.

-   <bcolor>Recall</bcolor>

    -   true positive rate.

    -   $  \frac{\color{green}{\text{True Positives}}}{\color{green}{\text{True Positives}} +  \color{yellow}{\text{False Negatives}}}$

    -   decreases with false negatives.


--

## F1 Score

-   The $F_{1}$ score provides a single combined metric it is the **harmonic mean** of precision and recall

    $$\begin{aligned}
    F_{1} &= \frac{2}{\frac{1}{\text{precision}}+\frac{1}{\text{recall}}}
    = 2\times\frac{\text{precision}\times\text{recall}}{\text{precision}+\text{recall}} \\\\
    &=  \frac{\text{Total Positives}}{\text{Total Positives}+\frac{1}{2}(\text{False Negatives}+\text{False Positives})}
    \end{aligned}$$

-   The harmonic mean gives **more weight to low values**.

-   The F1 score values precision and recall **symmetrically**.

--

## The Precision/Recall Trade-off

- $F_1$ favors classifiers with similar precision and recall,
- but sometimes you want **asymmetry**:

1.   <bcolor>low recall + high precision is better</bcolor>

    -   e.g. **deciding “guilty” in court**, you might prefer a model that
    -   lets many actual-guilty go free (high false negatives
        $\leftrightarrow$ low recall)...
    -   ... but has very few actual-innocent put in jail (low false
        positives $\leftrightarrow$ high precision

2.   <bcolor>high recall + low precision is better</bcolor>

--

## The Precision/Recall Trade-off
- $F_1$ favors classifiers with similar precision and recall,
- but sometimes you want **asymmetry**:

1.   <bcolor>low recall + high precision is better</bcolor>
2.   <bcolor>high recall + low precision is better</bcolor>

    -   e.g classifier to **detect bombs during flight screening**, you
        might prefer a model that:
    -   has many false alarms (low precision)...
    -   ... to minimize the number of misses (high recall).


--

## ROC Curve and AUC

-   Plots *true positive rate* (recall) against the *false positive rate* ($\frac{FP}{FP + TN}$):

<img data-src="./images/roc-curve.png"  style="height: 350px; position:relative;background-color:white;     margin-left: auto;margin-right: auto;display: block" >

Notes:
- ROC= "receiver operating characteristics"
- The ROC curve is a popular graphic for simultaneously displaying the ROC curve 2 types of errors for classification problems at various threshold settings
- It tells how much the model is capable of distinguishing between classes.
- An ideal ROC curve will hug the top left corner, so the larger area under the (ROC) curve the AUC the better the classifier

--

## ROC Curve and AUC

-   The area under the ROC curve (AUC) is a popular metric ranging between:

    -   0.5

        -   **random classification**
        -   ROC curve $=$ first diagonal

    -   and 1

        -   **perfect classification**
        -   $=$ area of the square

    -   better classifier $\rightarrow$ ROC curve toward the top-left
        corner

-   Good measure for model comparison


---

<!-- .slide: id="binary"  -->
# Binary Classifier
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

- Logistic Regressions
- K-Nearest Neighbors
- Support Vector Machine


--

## Logistic Regression


-   Like OLS, logistic “regression” computes a weighted sum of the input features to predict the output.

    -   But it transforms the sum using the **logistic function**.
        $$\hat{p}=\Pr(Y_{i}=1)=\sigma(\theta'x)$$ where
        $\sigma(\cdot)$ is the sigmoid function
        $$\sigma(a)=\frac{1}{1+\exp(-a)}$$

--

## Logistic Regression

  <img data-src="./images/ml-book/sigmoid.png"  style="height: 350px; position:relative;background-color:white;     margin-left: auto;margin-right: auto;display: block" >

-   Prediction:
  $$\hat{y} = \\{
     \\begin{array}{cc}
       0 & \textrm{ if } \hat{p}<.5 \\\\
       1 & \textrm{ if } \hat{p}\geq.5
   \\end{array}
  $$

--

## Logistic Regression Cost Function

-   The cost function to minimize is
<img data-src="./images/log-reg-cost-function.png"  style="height: 130px; position:relative;background-color:white;     margin-left: auto;margin-right: auto;display: block" >

  -   this does not have a closed form solution

  -   but it is convex, so gradient descent will find the global
      minimum.

-   Just like linear models, logistic can be regulared with L1 or L2
    penalties, e.g.:
    $$J_{2}(\theta)=J(\theta)+\alpha_{2}\frac{1}{2}\sum_{i=1}^{n}\theta_{i}^{2}$$


--

## Naive Bayes Classifier

-   Relies on the observed conditional probabilities (and the Bayes theorem)

-   For a 2-class problem for a given observation $X=x_0$:

    -   Predict class 1 if $P(Y=1| X=x_0) \geq  0.5 $

    -   Predict class 0 if $P(Y=1| X=x_0) < 0.5$

-   Relies on the independence assumption

Notes:
- It is possible to show that the test error rate is minimized, on average, by a very simple classifier
  - assigns each observation to the most likely class, given its predictor values.
  - we should simply assign a test observation with predictor vectorx0to the class $j$ for which the proba is the largest
- Based on the conditional probabilities


--

## Naive Bayes Classifier
<img data-src="./images/jwht-fig2-13.png"  style="height: 350px; position:relative;background-color:white;     margin-left: auto;margin-right: auto;display: block" >

Notes:
- simulated data set consisting of 100observations in each of two groups, indicated in blue and in orange.
- The purple dashed line represents the Bayes decision boundary.
- The orange background grid indicates the region in which a test observation will be assigned to the orange class, and
- the blue background grid indicates the region in which a test observation will be assigned to the blue class.

--

## K-Nearest Neighbors

-   With real data, we do not know the conditional distribution of Y  given X.

-   computing the Bayes classifier is not possible.

-   The K-nearest neighbors (KNN) classifier estimates the conditional distribution of Y given X.

-   Approximate Bayes decision rule in a subset of data around the testing point

-   **Non-parametric method** often successful in classification situations where the **decision boundary is very irregular**

Notes:
- the Bayes classifier serves as an unattainable gold standard against which to compare other methods


--

## K-Nearest Neighbors

For $K$ and a test observation $x_0$
1. KNN classifier first identifies the $K$ points in the training data that are closest to $x_0$ (i.e $N_0$)
2. estimates the conditional probability for class $j$ as the fraction of points in $N_0$ whose response values equal $j$:

$$ P(Y=j|X=x_O) = \frac{1}{K}\sum_{i \in N_O} I (y_i=j)$$

3. applies Bayes rule and classifies the test observationx0tothe class with the largest probability


--

## KNN: illustration

<img data-src="./images/jwht-fig2-14.png"  style="height: 350px; position:relative;background-color:white;     margin-left: auto;margin-right: auto;display: block" >

- Assume $K=3$
- Left: small training data set consisting of 6 blue and 6 orange observations
- Right: KNN approach at of the possible values for $X_1$ and $X_2$, and  corresponding KNN decision boundary

Notes:
- goal is to make a prediction for the point labeled by the black cross
1. KNN finds the 3 observations that are closest to the cross
2. neighborhood is 1/3 orange & 2/3 blue $\rightarrow$ the cross belongs to the blue class


--

## KNN: illustration

<img data-src="./images/jwht-fig2-15.png"  style="height: 350px; position:relative;background-color:white;     margin-left: auto;margin-right: auto;display: block" >

- black curve: KNN decision boundary
- dashed line: Bayes decision boundary

Notes:
- KNN can often produce classifiers that are surprisingly close to the optimal Bayes classifier

--

## KNN: choice of $K$

<img data-src="./images/jwht-fig2-17.png"  style="height: 350px; position:relative;background-color:white;     margin-left: auto;margin-right: auto;display: block" >

- $K=1$,the KNN training error rate is $0$, but the test error rate may be quite high

Notes:
- with more flexible classification methods, the training error rate will decline but the test error rate may not

--

## Support Vector Machine

-   Context: developed in the mid-1990s

-   A generalization of the early logistic regression (1930s)

-   One of the best “out of the box” classifiers

-   Core idea: hyperplane that separates the data as well as possible,   while allowing some violations to this separation

Notes:
- an approach for classification that was developed in the computer science community in the 1990s
-

--

### Support Vector Machine: context and concepts

-   [Pieces of the puzzle]():

    1.  A <bcolor>maximal margin classifier</bcolor>: requires that classes be
        separable by a linear boundary.

    2.  A <bcolor>support vector classifier</bcolor>: extension of the maximal margin classifier.

    3.  <bcolor>Support vector machine</bcolor>: further extension to accommodate  non-linear class boundaries.

-   For binary classification, can be extended to multiple classes

Notes:
- People often loosely refer to the **maximal margin classifier**, the **support vector classifier**, and the support vector machine as **“support vector machines”**.

--

## Classification and Hyperplane

A perfectly separating linear hyperplan for a binary outcome<img data-src="./images/svm1.png"  style="height: 350px; position:relative;background-color:white;     margin-left: auto;margin-right: auto;display: block" >

There are an infinity of such separating hyperplan\
$\rightarrow$ we need to choose one

Notes:
- If a separating hyperplane exists, we can use it to construct a very natural classifier:
    - a test observation is assigned a class depending on which side of the hyperplane it is located
- but then if there exists 1 separating hyperplan, there exist an infinity

--

## Maximum Margin

Maximum margin classifier for a perfectly separable binary
outcome variable  <img data-src="./images/svm2.png"  style="height: 350px; position:relative;background-color:white;     margin-left: auto;margin-right: auto;display: block" >

<bcolor>Criterium for optimal choice</bcolor>: the separating hyperplane for which the margin is the farthest from the observations\
i.e., to select the <bcolor>maximal margin hyperplane</bcolor>

Notes:
- **Methodo**:  
  - compute the (perpendicular) distance from each training observation to a given separating hyperplane;
  - the smallest such distance is the minimal distance from the observations to the hyperplane $=$ the *margin*
- We can then classify a test observation based on which side of the maximal margin hyperplane it lies.
- This is known as the maximal margin classifier.
- On the figure:
  - 3 training observations are equidistant from the max maring hyperplane = **support vector**


--

## Support Vector

<bcolor>Support vector</bcolor> = the 3 observations from the training set that are
equidistant from the maximal margin hyperplane

$\rightarrow$ they “support” the maximal margin hyperplane (if they
move, the the maximal margin hyperplane also moves)

--

## Overcoming the perfectly separable hyperplan assumption

 We allow some number of observations to violate the rules so that they can lie on the wrong side of the margin boundaries.

$\rightarrow$ find a hyperplane that almost separates the classes

The <bcolor>support vector classifier</bcolor> generalizes the maximum margin classifier to the non-separable case.

--

## Support Vector Classifiers

Maximal margin classifier (left) and support vector classifier
(right) <img data-src="./images/svm3.png"  style="height: 350px; position:relative;background-color:white;     margin-left: auto;margin-right: auto;display: block" >

Notes:
- **pb** of Maximal margin hyperplan: only perfect classification, by essence overfits the training dataset
- **Advantages** of SVC (vs MMH):
  - Greater robustness to individual observations
  - Better classification of most of the training observations

--

## Support Vector Classifiers: Details

- A <bcolor>tuning parameter</bcolor> $C$ determines the severity of the violation ot the margin that the model tolerates
  - chosen by cross Validation
  - controls the bias-variance trade-off

- $C$ small $\rightarrow$ narrow margins, rarely violated
- $C$ large $\rightarrow$ wide margins, allow more violation
  - More bias classifier, but lower variance

--

## Shortcomings of the linearity assumption:
<img data-src="./images/jwht-fig9-8.png"  style="height: 350px; position:relative;background-color:white;     margin-left: auto;margin-right: auto;display: block" >

Notes:
- **Left**:The observations fall into two classes, with a non-linear boundary between them.
- **Right**:The support vector classifier seeks a linear boundary, and consequently performs very poorly


--

## Overcoming the linearity assumption:
### Support vector machines

-  *Idea 1*: (polynomial) transformation of the features + `StandardScaler` + `LinearSVC`.

- *Idea 2*:  convert a linear classifier into a classifier that produced <bcolor>non-linear decision boundaries</bcolor>.
$\rightarrow$  using a <bcolor>Kernel</bcolor> such as:

    - Gaussian RBF kernel
    - Polynomial kernel

-   **We do not open the kernel box**.

    -   Just think as them as a way to construct non-linear hyperplans
    -   Try out different kernel and distance specification

Notes:
- The kernel approach is computationally efficient
- A kernel is a function that quantifies the similarity of 2 observations.

--

## Support vector machines
<img data-src="./images/jwht-fig9-9.png"  style="height: 350px; position:relative;background-color:white;     margin-left: auto;margin-right: auto;display: block" >

- *Left*: polynomial kernel of degree 3;
- *Right*: radial kernel

---

<!-- .slide: id="wrap"  -->
# Wrap-up
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

--

## Selecting the Tuning Parameter By Cross-Validation
1. Choose a <bcolor>grid</bcolor> of $\lambda$ values
2. Compute the <bcolor>CV error</bcolor> for each lambda
3. Select the tuning parameter value for which the CV error is smallest
4. <bcolor>Re-fit</bcolor> the model using all available observation and the best $\lambda$


--

## Data Prep for Machine Learning
- See Geron Chapter 2 for [pandas]() and [sklearn]() syntax:
  - imputing missing values.
  - feature <bcolor>scaling</bcolor> (coefficient size depends on the scaling)
  - <bcolor>encoding</bcolor> categorical variables.

- Best practice
  - <bcolor>reproducible</bcolor> data pipeline
  - <bcolor>standardize</bcolor> coefficients

--

## Other Supervised Machine Learning Methods
- Forward Selection,
- Backward Selection
- Trees and Forests
- Neural Networks
- Boosting
- Ensemble Methods

--

## Types of Classification Algorithms

-   Linear Classifiers

    -   Logistic regression

    -   Naive Bayes classifier

-   Support vector machines

-   Kernel estimation

    -   k-nearest neighbor

-   Decision trees

    -   Random forests

--

> “Essentially, all models are wrong, but some are useful”
-- George Box
