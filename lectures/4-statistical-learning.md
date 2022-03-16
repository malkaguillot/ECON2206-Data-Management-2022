# Data Management
## Statistical Learning
### [Malka Guillot](https://malkaguillot.github.io/)
### HEC Liège | <a href="https://gitlab.uliege.be/mguillot/econ2306-data-management-2021-22/">ECON2306</a>


<!-- exportation :
decktape --chrome-arg=--disable-web-security 4-statistical-learning.html 4-statistical-learning.pdf -s 1024x768
--->



---

<!-- .slide: id="prologue"  -->
# Prologue
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

--

<!-- .slide:  id="toc" class: left, inverse -->
## Table of contents

1. [Machine Learning: an overview](#ml)

1. [What is statistical learning?](#what)

3. [Why estimate $f(X)$?](#why)

3. [How do we estimate $f(X)$?](#how)

2. [Model accuracy](#accuracy)

3. [The Bias-Variance Trade Off](#bias_variance)

3. [How to choose training and test set?](#train_test)

3. [Conclusion](#conclusion)

Notes: my notes

--

## Context
### Today
- What is statistical learning?
- Statistics in social science – causality.
- Statistics in machine learning – prediction.
- Accuracy v. interpretability.
- Model accuracy.
- The bias-variance tradeoff.

### Next
- Supervised learning
  - Classification
  - Regression
- Unsupervised learning

--

## References

- <i class="fa fa-book fa-fw" aria-hidden="true"></i> [introduction to Statistical Learning](https://hastie.su.domains/ISLR2/ISLRv2_website.pdf) chap 1. & 2 & 5.1
-  Kleinberg, Ludwig, Mullainathan, and Obermeyer (2015), ["Prediction Policy Problems."](https://www.aeaweb.org/articles?id=10.1257/aer.p20151023) American Economic Review, 105 (5), pp. 491-95.
- Mullainathan and Spiess (2017), ["Machine Learning: An Applied Econometric Approach"]((https://pubs.aeaweb.org/doi/pdfplus/10.1257/jep.31.2.87)), Journal of Economic Perspectives, 31 (2), pp. 87-106,


---

<!-- .slide: id="ml"  -->
# Machine Learning: overview and examples
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

## Supervised vs. unsupervised learning

--

## Supervised  learning
Estimating functions with <bcolor>known observations</bcolor> and <bcolor>outcome</bcolor> data.
- We observe data on $Y$ and $X$
- We want to learn the mapping $\hat Y=\hat f(X)$

- **Classification** when $\hat Y$ discrete
- **Regression** when $\hat Y$ continuous

--

## Unsupervised learning

Estimating functions without the aid of outcome data.
  - We only observe $X$ and want to learn something about its structure

  - <bcolor>Clustering</bcolor>: Partition data into homogeneous groups based on X

  - <bcolor>Dimensionality reduction</bcolor> (e.g. PCA)

--

## The Machine learning landscape
<img data-src="images/machine_learning_landscape.jpeg"  style="height: 550px; position:relative;     margin-left: auto;margin-right: auto;display: block" >

--

## Examples: Studies using ML for p rediction
<div style="font-size:80%;">
<ul>
  <li><a href "https://onlinelibrary.wiley.com/doi/full/10.1111/ecin.12364">Glaeser, Kominers, Luca, and Naik (2016)</a> use images from Google Street View to measure block-level income in New York City and Boston</li>
  <li><a href "http://science.sciencemag.org/content/353/6301/790"> Jean et al. (2016)</a> train a neural net to predict local economic outcomes from satellite data in African countries</li>
  <li><a href "https://www.aeaweb.org/articles?id=10.1257/aer.101.3.288"> Chandler, Levitt, and List (2011)</a> predict shootings among high-risk youth so that mentoring interventions can be appropriately targeted</li>
  <li><a href "https://academic.oup.com/qje/article-abstract/133/1/237/4095198?redirectedFrom=fulltext"> Kleinberg, Lakkaraju, Leskovec, Ludwig, and Mullainathan (2018)</a> predict the crime probability of defendants released from investigative custody to improve judge decisions</li>
  <li><a href "https://aclanthology.info/pdf/D/D13/D13-1150.pdf"> Kang, Kuznetsova, Luca, and Choi (2013)</a> use restaurant reviews on Yelp.com to predict the outcome of hygiene inspections</li>
  <li><a href "http://doc.rero.ch/record/308901/files/WP_SES_494.pdf">Huber and Imhof (2018) </a> use machine learning to detect bid-rigging cartels in Switzerland</li>
  <li><a href "https://homes.cs.washington.edu/~nasmith/papers/kogan+levin+routledge+sagi+smith.naacl09.pdf)">Kogan, Levin, Routledge, Sagi, and Smith (2009) </a> predict volatility of firms from market-risk disclosure texts (annual 10-K forms)</li>
  </ul>
</div>


---

<!-- .slide: id="what"  -->
# What is statistical learning?
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

note:
https://raw.githubusercontent.com/ljanastas/Princeton_WWS586A-Machine-Learning-Policy-Analysis/master/Lectures/Stat_Learning/WWS586a-02-21-18.pdf
https://teaching.parisschoolofeconomics.eu/docs/SHAREDmachinelearning/Part1.pdf


--

## Setting

- Input variables `$\mathcal{X}$`
  - AKA features, independent variables, predictors
- Output variables `$\mathcal{Y}$`
  - AKA dependent variables, outcomes, etc.

--

## Statistical learning theory

  `$$ f: \mathcal{X} \rightarrow \mathcal{Y}$$`

  `$$ \mathcal{X}\in \mathbb{R}^{n \times p} ,  \mathcal{Y}\in \mathbb{R}^{p}  $$`

  > SL= approaches for finding a function that accurately maps the inputs `$\mathcal{X}$` to outputs `$\mathcal{Y}$`


--

## Statistical model

Concretely, finding $f(.)$ s.t. `$$ Y=f(X)+\epsilon$$`

  - $f(X)$ is an unknown function of a matrix of predictors $X= (X_1,···,X_p)$,
  - $Y$: a scalar outcome variable
  - an error term $\epsilon$ with mean zero.
  - While $X$ and $Y$ are known, $f(·)$ is unknown.

<bcolor>Goal of statistical learning</bcolor>: to utilize a set of approaches to estimate the “best” $f(·)$ for the problem at hand.

--

### Example: income as a function of education

<div class="r-stack"><img data-src="images/jwht-fig2-2.png" style="height: 400px;" > </div>

Notes:
- The **red dots** are the *observed values* of income and years of education for 30 individuals.
- The **blue curve** represents the *true underlying relationship* between in come and years of education, which is generally unknown (but is known in this case because the data were simulated).
- The **black lines** represent the *error* associated with each observation. Overall, these errors have approximately mean zero.


---

<!-- .slide: id="why"  -->
# Why estimate $f(X)$?

<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

--

## Prediction

- Predict $Y$ by $\hat Y =\hat f (X)$
- When do we care about "pure prediction"?
  - $X$ readily available but $Y$ is not
- $\hat f$ can be a **black box**:
  - the only concern is accuracy of the prediction

Notes:
- $\hat f = $ our estimate for $f$
- $\hat Y$ =resulting prediction for $Y$


--

## Inference

- Understanding the way that $Y$ is affected as $X_1,...,X_p$ change
  - Which predictors are associated with the response?
  - What is the relationship between the response and each predictor?

$\Rightarrow \hat f$ is cannot be a **black box** anymore


--

## Example: prediction or inference paradigm?

Two policy makers :
- one **facing a drought**:
  - must decide whether to invest in a rain dance to increase the chance of rain.

- one **seeing clouds**:
  - must deciding whether to take an umbrella to work to avoid getting wet on the way home

$\rightarrow$ Both decisions could benefit from an empirical analysis on rain

*Which one relates to a causality / prediction problem?*

Notes:
- Causality: do rain dances cause rain?
- Prediction: is the chance of rain high enough to merit an umbrella?

--

## Approach in social science

- *Objective*: Understanding the way that $Y$ is affected as $X_1,...,X_p$ change
- The goal not necessarily to make predictions for $Y$
- Often linear function to estimate $Y$: $ f(X)=\sum_{i=1}^p \beta_i x_i$
- Assume  $ \epsilon \sim  N(0, \sigma^2)$
- Parameters $\beta$ are estimated by minimizing the sum of squared errors

$$ Y= \sum_{i=1}^p \beta_i x_i + \epsilon $$

Notes:
Assume that the error term is normally distributed with a zero mean :

--

## Approach in social science: causality
$$ Y= \beta_0 + \beta_1 T + \sum_{i=1}^{p-1} \beta_i x_i + \epsilon $$

- Interested in the values of one or two parameters and whether they are **causal** or not.
- Framework to interpret statistical causality: <bcolor>Rubin (1974)</bcolor>
- $\beta_1$ measures the extent to which $\Delta X_t$ will affect $\Delta Y_{t+1}$

--

## Approach in social science: causality

- Causal inference requires that $T \perp \epsilon $ or $T|X \perp \epsilon $

$\rightarrow$ can be achieved through randomization of $T$

- This implies that we are not really all that interested in choosing an optimal $f(.)$
- (We want to estimate unbiased coefficients)

--

## Approach in machine learning: prediction
$$ \hat Y = \hat f(X) $$
- *Objectives*:
  - find the “best” $f(·)$ and the “best” set of $X$’s which give the best predictions,$\hat Y$
  - **Accuracy**: find the function that <bcolor>minimize the difference between *predicted* and *observed* values</bcolor>
  - (We want to minimize prediction error)

Note:  Machine learning is primarily concerned with prediction


--

## Reducible and irreducible error
$\hat f(X)=\hat Y$ estimated function

$f(X)+\epsilon =\hat Y$ true function

- <bcolor>Reducible error</bcolor>: $\hat f$ is used to estimate f, but not perfect
  - Accuracy can be improved by adding more features

- <bcolor>Irreducible error</bcolor>: $\epsilon$ = all other features that can be used to predict $f$
  - Unobserved $\rightarrow$ irreducible

--

## Reducible and irreducible error
$$\begin{align}
E(Y-\hat Y)^2 &= E[f(X)+\epsilon - \hat f (X)]^2 \\\\
      &= \underbrace{[f(X) - \hat f(X)]^2}_{Reducible} +  \overbrace{Var(\epsilon)}^{Irreducible} \\
\end{align}$$

$\Rightarrow$ **Objective**: estimating $f$ with the aim of minimizing the reducible error

Notes:
where $E(Y−\hat Y)^2$ represents the average, or expected value, of the squared expected value difference between the predicted and actual value of $Y$,and $Var(\epsilon)$ represents the variance associated with the error term.

We focus on estimating $f$ with the aim of minimizing the reducible error.
The irreducible error will always provide an upper bound on the accuracy of our prediction for $Y$. This bound is almost always unknown in practice.

---

<!-- .slide: id="how"  -->
# How do we estimate $f$?
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

--

## Context
We use observations to "teach" our ML algorithm to predict outcomes

- <bcolor>Training data</bcolor>: $ \\{ (x_1,y_1), (x_2,y_2), \dots, (x_n,y_n)\\} $
where $x_i=(x_{i1}, x_{i2}, \dots, x_{ip})^T$

- *Goal*: use the training data to estimate the unknown function $f$

- 2 types of SL methods: <bcolor>parameteric vs. nonparametric</bcolor>

--

### Parametric methods
**Model-based approaches**, 2 steps:

1. Specify a <bcolor>*parametric* (functional) form</bcolor> for $f(X)$, e.g. linear:
   $$ f(X) = \beta_0+\beta_1X_1+\cdots+\beta_pX_p$$
   (Parametric means that the function depends on a finitenumber of parameters, here $p+1$).

2. <bcolor>Training</bcolor>: Estimate the parameters by OLS and predict $Y$ by
   $$ \hat Y = \hat f(X)=\hat \beta_0+\hat \beta_1X_1+\cdots+\hat \beta_pX_p$$

Notes:
 - Parametric methods involve a two-step model-based approach.
 1. make an assumption about the functional form
 2. use the training data to fit or train the model
 $\Rightarrow$ reduces the problem of estimating $f$ down to one of estimating a set of parameters

--

### True function

<div class="r-stack"><img data-src="images/jwht-fig2-3.png" style="height: 400px;" > </div>

Notes:
The plot displays income as a function of years of education and seniority.
- The **blue surface** represents the true underlying relationship between income and years of education and seniority, which is known since the data are simulated.
- The **red dots** indicate the observed values of these quantities for30individuals

--

### Linear estimate

<div class="r-stack"><img data-src="images/jwht-fig2-4.png" style="height: 400px;" > </div>

Notes:
the true $f$ has some curvature that is not captured in the linear fit

--

### Parametric methods -- issues
Misspecification of $f(X)$

1. Rigid models (e.g. strictly linear) may not fit the data well
2. More flexible models require more parameter estimation $\rightarrow$ **overfitting**

Note:

--

### Non-parametric methods
- **No assumptions** about the functional form of $f$

- Estimates a function only **based on the data itself**.

- **Disadvantage**: very large number of observations is required to obtain an accurate estimate of $f$

--

### “Smooth” nonlinear estimate

<div class="r-stack"><img data-src="images/jwht-fig2-5.png" style="height: 400px;" > </div>

Notes:
The approach attempts to produce an estimate for $f$ that is as close as possible to the observed data, subject to the fit being smooth

--

### Rough nonlinear estimate with perfect fit $\Rightarrow$ overfit

<div class="r-stack"><img data-src="images/jwht-fig2-6.png" style="height: 400px;" > </div>

Notes:
But if we allow for a rougher fit, =>  zero errors on the training data.
= Example of OVERFITTING

--

## Accuracy and interpretability tradeoffs

- <bcolor>More accurate</bcolor> models often require estimating <bcolor>more parameters</bcolor> and/or having more flexible models

- Models that are better at prediction generally are <bcolor>less interpretable</bcolor>.

$\Rightarrow$ What we care about:
  - For inference: interpretability.
  - For prediction: accuracy.

<!--$\rightarrow$ More on this next week!-->


---

<!-- .slide: id="accuracy"-->
# Model Accuracy
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

Notes:
In order to evaluate the performance of a statistical learning method on a given data set, we need some way to measure how well its predictions actually match the observed data

--

## Mean Squared Error (MSE)

`$$MSE= \frac{1}{n} \sum_{i=1}^n (y_i - \hat f(x_i))^2$$`

- **Regression setting**: the <bcolor>mean squared error</bcolor> is a metric of how well a model fits the data.

- But it’s <bcolor>in-sample</bcolor>.  

- What we are really interested in is the <bcolor>out-of-sample</bcolor> fit!

Notes:

MSE will be small if the predicted responses are very close to the true responses,and will be large if for some of the observations, the predicted and true responses differ substantially

--

## Measuring fit (1)

- We would like $(y_0 - \hat f(x_0))^2$ to be small for some $(y_0, x_0)$, not in our training sample $\{(x_i, y_i)\}_{i=1}^n$.

- Assume we had a large set of observations $(y_0, x_0)$ (a test sample),

- then we would like a low
  $$ Ave(y_0 - \hat f(x_0))^2$$

- i.e a low average squared prediction error (test MSE)

--

## Measuring fit (2)

To estimate model fit we need to partition the data:

1. <bcolor>Training set</bcolor>: data used to **fit** the model
  - <bcolor>Training MSE</bcolor>: how well our model fits the training data.
2. <bcolor>Test set</bcolor>: data used to **test the fit**
  - <bcolor>Test MSE</bcolor>: how well our model fits new data

We are most concerned in <bcolor>minimizing test MSE</bcolor>

--

## Training MSE, test MSE and model flexibility

<img data-src="images/jwht-fig2-9.png"  style="height: 350px; position:relative;     margin-left: auto;margin-right: auto;display: block" >
Red (grey) curve is test (train) MSE

Increasing model flexibility tends to <bcolor>decrease</bcolor> training MSE but will eventually <bcolor>increase</bcolor> test MSE

Notes:

- Left:Data simulated from $f$, shown in black.
- Three estimates of $f$ are shown:
    - the linear regression line (orange curve),
    - and two smoothing splinefits (blue and green curves).
- Right:Training MSE (grey curve), test MSE (red curve), and minimum possible test MSE over all methods (dashed line).
- Squares represent the training and test MSEs for the three fits shown in the left-hand panel.

- we observe a monotone decrease in the training MSE and a U-shape in the test MSE

--

## Overfitting

- As model flexibility increases, training MSE will decrease, but the test MSE may not.

- When a given method yields a small training MSE but a large test MSE, we are said to be **overfitting** the data.

- (We almost always expect the training MSE to be smaller than the test MSE)

- Estimating test MSE is important, but requires training data...


---

<!-- .slide: id="bias_variance"  -->
# The Bias-Variance Trade-Off
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>


Notes:
The U-shape observed in the test MSE curves (Figures2.9  –2.11  ) turns out to be the result of two competing properties of statistical learning methods.

--

## Decomposing the expected (test) MSE

$$ E(y_0 - \hat f(x_0))^2 = Var(\hat f(x_0)) + [Bias(\hat f(x_0))]^2 + Var(\epsilon)$$

3 components:
1. $ Var(\hat f(x_0))=$ Variance of the predictions
   - how much would $\hat f$ change if we applied it to a different data set
2. $[Bias(\hat f(x_0))]^2=$ Bias of the predictions
   - how well does the model fit the data?
3. $Var(\epsilon)=$ variance of the error term

Notes:

-  notation $E(y_0 - \hat f(x_0))^2 $ defines the expected test MSE, and refers expected test MSE to the average test MSE that we would obtain if we repeatedly estimated $f$ using a large number of training sets, and tested each at $x_0$
- to minimize E, need to minimize both variance and bias
- the expected test MSE can never lie below $Var(\hat f(x_0))$, the irreducible error

- more flexible methods, the variance will increase and the bias will decrease

--

## The bias-variance tradeoff

<img data-src="images/jwht-fig2-9-11.png"  style="height: 350px; position:relative;     margin-left: auto;margin-right: auto;display: block" >

- less flexibility $\rightarrow$ high bias and low variance

- more flexibility $\rightarrow$ low bias and high variance

Models that are too flexible or expressive or complex overfit!!

Notes:
- Simple models give consistent results across test sets (low variance) but don’t predict well. (high bias).
- Very flexible (complex) models give inconsistent results across test sets (high variance), but do well at prediction(low bias).

--

## Accuracy in Classifications

$$ \textrm{(training) error rate}=\frac{1}{n}\sum_{i=1}^n 1(y_i\neq \hat y_i)$$

$$ \textrm{(test) error rate}=Ave(1(y_0\neq \hat y_0))$$

- MSE in the context of regression (continuous predictor).

- Modifications in the setting in which we’re interested in prediction classes

- We are essentially interested in what % of classifications are correct.

- For cross-validation we could also use the estimated test error rate


---

<!-- .slide: id="train_test"-->
# How to choose training and test set?
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>

Notes:
In real life situation, it is generally not possible to explicitly compute the test MSE, bias, or variance for a statistical learning method

They involve repeatedly drawing samples from a training set and refitting a model of interest on each sample in order to obtain additional information about the fitted model

--

## Resamling methods

Estimate the test error rate by

<bcolor>holding out</bcolor> a subset of the training observations from the fitting process,

$+$ then <bcolor>applying</bcolor> the statistical learning method to those held out observations

--

## Validation set approach
- Labeled data <bcolor>randomly</bcolor> into two parts: training and test (validation) sets.

<div class="r-stack"><img src="https://docs.splunk.com/images/thumb/3/3b/TrainTest.png/550px-TrainTest.png
" style="height: 400px;" > </div>

--

## Two concerns
- Arbitrariness of split
- Only use parts of the data for estimation

  $\rightarrow$ we tend to overestimate test MSE because our estimate of $f(x)$ is less precise

--

## Leave-One-Out Cross-Validation (LOOC)

- Fit on $n−1$ training observations, and a prediction the Last
- Iterate $n$ times
- Assess the average model fit across each test set.

Estimate for the test MSE:
`$$ CV_n=\sum_{i=1}^n MSE_i$$`

--

## Leave-One-Out Cross-Validation (LOOC)
<div class="r-stack"><img data-src="images/jwht-fig5.3.png" style="height: 400px;" > </div>

- less bias than the validation set approach
- always yield the same results
- potentially too expensive to implement

Notes:
- less bias because tends not to overestimate the test error rate as much as the validation set approach does


--

## $k$-fold Cross-validation
- Leave-One-Out Cross-Validation with $k=1$
- Randomly dividing the data into the set of observations into $k$ groups
- 1st fold is treated as a validation set, and the method is fit on the remaining $k−1$ folds
- Iterate $k$ times


Estimate for the test MSE:
`$$ CV_k=\sum_{i=1}^k MSE_i$$`

--

## $k$-fold Cross-validation
<div class="r-stack"><img data-src="images/jwht-fig5.5.png" style="height: 400px;" > </div>

$\Rightarrow$ Arguably the contribution to econom(etr)ics: Cross-validation (to estimate test MSE)!

--

##  Bias-Variance Trade-Off $f$-Fold Cross-Validation
Bias
- **validation set approach** can lead to overestimates of the test error rate
- **1-fold validation**: almost unbiased estimates of the test error
- **k-fold validation** is in between

Variance
- **1-fold validation**: higher variance
- **k-fold validation**: lower variance

$k=5$ or $k=10$ is a good benchmark


---

<!-- .slide: id="conclusion"  -->
# Conclusion:
## Econometrics vs. Machine Learning
<html><div style='float:left'></div><hr color='#EB811B' size=1px width=796px></html>


--

## Econometrics vs. Machine Learning (1)

- **Common objective**: to build a predictive model, for a variable of interest, using explanatory variables (or features)
- **Different cultures**:
  - *E*: probabilistic models designed to describe economic phenomena
  - *ML*: algorithms capable of learning from their mistakes

<cite><i class="fa fa-book fa-fw" aria-hidden="true"> </i> Charpentier A., Flachaire, E. & Ly, A. (2018). [Econometrics and Machine Learning](https://www.insee.fr/en/statistiques/fichier/3706234/505-506_Charpentier-Flachaire-Ly-EN.pdf). *Economics and Statistics*, 505-506, 147–169.</cite>

--

##  Econometrics vs.  Machine Learning (2)

<img data-src="images/ml_vs_traditional_paradigm2.png"  style="height: 300px; position:relative;     margin-left: auto;margin-right: auto;display: block" >

- **Classical computer programming**: <span style="color:#66cdaa">humans</span> input the <span style="color:#66cdaa">rules</span> and the <span style="color:#66cdaa">data</span>, and the <span style="color:#f5ae47">computer</span> provides <span style="color:#f5ae47">answers</span>.

- **Machine learning**: <span style="color:#66cdaa">humans</span> input the <span style="color:#66cdaa">data</span> and the <span style="color:#66cdaa">answer</span>, and the <span style="color:#f5ae47">computer</span>  learns the <span style="color:#f5ae47">rules</span>.

--

## The Machine learning workflow

1. Look at the big picture.
2. Get the data.
3. Discover and visualize the data to gain insights.
4. Prepare the data for Machine Learning algorithms.
5. Select a model and train it.
6. Fine-tune your model.
7. Present your solution.
8. Launch, monitor, and maintain your system

<i class="fa fa-book fa-fw" aria-hidden="true"></i>
Aurelien Geron, *Hands-on machine learning with Scikit-Learn & TensorFlow*, Chapter 2
