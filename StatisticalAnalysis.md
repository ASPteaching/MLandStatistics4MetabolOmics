**Targeted Metabolomics Data Analysis: Unlocking Insights with Machine
Learning, AI and Statistics**

**Agenda (Day 3)**

Canadian Bioinformatics Workshops

**www.bioinformatics.ca**

**Yesterday**

**Today**

Learning Objectives

- **Learn about basic concepts in ‘omics data analysis **

- **Learn about p values calculation and interpretation**

- **Learn about multivariate statistics (PCA and PLS-DA)**

- **Learning about machine learning concepts (clustering, classification
and performance evaluation,)**

Omics Data Analysis (in a nutshell)

General Steps in Statistical Analysis

Input & Output

- Input: metabolomics data

- X: a table containing numerical values

- Concentrations, peak intensities

- Y: meta-data: data about data

- Class labels, experimental factors

- Output: useful information

- Significant features

- Clustering patterns

- Rules (for prediction)

- Models …...

X: Quantitative Data

- Continuous

- Microarray intensities

- Metabolite concentrations

- Discrete

- Read counts (RNAseq)

- Need to be treated with different statistical models

- Normal distribution

- Poisson distribution

Y: Meta Data (data about X)

- Binary data

- 0/1, Y/N, Case/Control

- Nominal Data (\> two groups)

- Single = 1, Married = 2, Divorced = 3, Widowed = 4

- Order is not important

- Ordinal data

- Time series

- Disease severities

- Dose responses

Put Together (X+Y)

- Requested by most modules in MetaboAnalyst

Common Terms

- Dimension

- The number of variables (metabolites, peaks)

- Univariate:

- Measuring one variable per subject

- Multivariate

- Measuring many variables per subject

- Omics data are usually high-dimensional data

How Do We Describe the Data?

- Central Tendency – center of the data location

- Mean, Median, Mode

- Variability – the spread of the data

- Variance

- Standard deviation

- Relative standing – distribution of data within the spread

- Quantiles

- Range

- IQR (inter-quantile range)

Box-and-whisker plot

- The 1<sup>st</sup> quantile Q<sub>1</sub> is the value for which 25%
of the observations are smaller and 75% are larger

- Q<sub>2</sub> is the same as median (50% are smaller and 50% larger)

- Q<sub>3</sub> is the value that only 25% of the observations are
larger

- Range is minimum to maximum

Mean vs. Variance

- Most univariate tests compare the difference in the means, assuming
equal variance

Normal Distribution

- Almost any set of biological or physical measurements will display
some some variation and these will almost always follow a Normal
distribution

- The larger the set of measurements, the more “normal” the curve

- Minimum set of measurements to get a normal distribution is 30-40

**A Bell Curve**

**Other Distributions are Common**

Data Normalization

- Most statistics models have been developed based on the assumption
that the underlying data are ”normally” distributed

- They work suboptimal when this assumption is not met (i.e. high false
positives)

- Solution - to transform data to close to model

data normalization

**Log Transformation**

**Log Transformation (Real Data)**

**Data Normalization in MetaboAnalyst**

Workflow of Omics Analysis

**Understanding**  
**P values**

Uncertainties in Parameter Estimation

From Samples to Population

- So how do we know whether the effect observed in our sample was
genuine?

- We don’t

- Instead we use *p values *to indicate our level of uncertainty that
our results represent a genuine effect present in the whole population

P values

- P values = the probability that the observed result was obtained by
chance

- i.e. when the null hypothesis (H<sub>0</sub>: *i.e. *no effect) is
true

- If that probability (p-value) is small, it suggests the observed
result cannot be easily explained by chance

How do we calculate a p value?

**Distribution is known**

Empirical P-values

- Previously mentioned p-values are based on well defined models

- *Gaussian* distributions, *Poisson* distribution

- What if we don’t know the distribution?

- The only thing we know is that the data does not follow a normal
distribution

- Poor performance using a model based on normal distribution

- We can find out the <u>null distribution </u>from the data itself,
then calculate the p-value

- Also known as empirical p-values

Basic Principle

- Under the null hypothesis (H<sub>0</sub>), all data comes from the
same distribution

- We calculate our statistic, such as the mean difference, from the
original data

- We then <u>shuffle the data with respect to group labels </u>and
recalculate the statistic (mean difference)

- group labels do not matter under H<sub>0 </sub>

- Repeat step 3 multiple times

- Find out where our statistic lies in comparison to the null
distribution

**A Simple Example**

- **To find out whether there is a mean difference between case vs.
control**

**Permutation One**

**Permutations**

**Compute Empirical P-value**

General Advantages

- Does not rely on distributional assumptions

- Corrects for hidden correlation

- Disadvantage?

- Need relatively large number of samples

- Computationally intensive

**Multiple Testing Issues**

Multiple Testing Issues

- Omics yields high-dimensional data

- 100s to 10,000s of variables

- Lots of hypothesis tests, with each one we accept a small chance

- Performing T-tests on typical metabolomic data might result in
performing 10000 separate hypothesis tests. If we use a standard p value
cut-off of 0.05, we would see 500 (10000\*0.05) genes to be deemed
“significant” by chance alone

Multiple Testing Correction (I)

- Family Wise Error Rate (FWER) - e.g. *Bonferroni corrections*

- Corrected P-value= p-value \* n (number of genes in test) \<0.05. If
testing 1000 genes at a time, the corrected p-value is 0.00005
(0.05/1000).

- False Discovery Rate (FDR) - e.g. Benjamini-Hochberg

- A FDR of 0.05 means that 5% among the significant metabolites are
expected to be false positives

High-dimensional Data

- So far, our analyses are dealing with a single variable (i.e.
univariate analysis)

- T-tests: one variable, two groups

- ANOVA: one variable, \> 2 groups

- First analyze a single variable, and then apply the procedure to all
variables, finally do multiple test adjustment

- Visualization are limited to three dimensions

- How can we analyze & visualize these high-dimensional data?

**Machine Learning & Multivariate Statistics**

The Challenges

- Most statistical methods have been developed before the coming of the
omics era

- Most statistical methods are designed for single or very few variables

- T-tests, ANOVA

- Linear/logistic regression

- These methods assume there are more samples (n) than the number of
variables (p) (i.e. n \> p) for parameter estimation

- In omics data, n \<\< p

The Practice

- Classical multivariate statistics requires more complex,
multidimensional analyses or dimensional reduction methods

- Hard to use, hard to understand

- Omics data analyses borrow a lot from several other fields

- Pattern recognition / machine learning

- Dimension reduction

- Chemometrics

Key Areas in Data Science

Pattern Recognition / Machine Learning

- Focus on “patterns/groups” instead of individual features

- Unsupervised learning: explore the data to find some intrinsic
structures in them <u>Disregard whether they are related to the class
labels or not</u>)

- These patterns can be used to understand the key information within
the data itself

- Supervised learning: discover patterns in the data that relate data
attributes <u>with related to a target (class) attribute</u>.

- These patterns can be utilized to predict the values of the target
attribute in future data instances

Unsupervised Learning Methods for High-dimensional Data

- Clustering

- Organize the 1000s of variables into blocks

- Variables in each block are more homogenous, and treat these blocks as
a unit

- Dimension reduction

- Reduce the high-dimensional data into low-dimension i.e. from 1000s of
variables to 2 ~ 3 variables

- Principal component analysis (PCA)

Clustering

- Definition - a process by which objects that are logically similar in
characteristics are grouped together

- A method to measure similarity (a similarity matrix) or dissimilarity
(a dissimilarity coefficient) between objects

- A threshold value with which to decide whether an object belongs with
a cluster

- A way of measuring the “distance” between two clusters

Two Common Clustering Algorithms

- K-means or Partitioning Methods - divides a set of N objects into M
clusters -- with or without overlap

- Hierarchical Methods - produces a set of nested clusters in which each
pair of objects is progressively nested into a larger cluster until only
one cluster remains

Hierarchical Clustering

- Find the two closest objects and merge them into a cluster

- Find and merge the next two closest objects (or an object and a
cluster, or two clusters) using some similarity measure and a predefined
threshold

- If more than one cluster remains return to step 2 until finished

Key Parameters

- Similarity between samples

- Similarity between clusters

K-means clustering

- Randomly chooses *k* observations from the dataset and uses these as
the initial means

- For the next object calculate the similarity to each existing centroid

- If the similarity is greater than a threshold add the object to the
existing cluster and re-compute the centroid, else use the object to
start new cluster

- Return to step 2 and repeat until done

K-means Clustering

**Similarity Measurements**

- **Euclidean Distance: Absolute difference**

**Similarity Measurements**

- **Pearson Correlation: Trend similarity**

**Hierarchical Clustering & Heatmaps**

Principal Component Analysis (PCA)

- Project high-dimensional data into lower dimensions that capture the
most variance of the data

- Assumption:

Main directions of variance

≈ major data characteristics

**Visualizing PCA**

- **PCA of a “bagel”**

- **One projection produces a weiner (hotdog)**

- **Another projection produces an “O”**

- **The “O” projection captures most of the variation and has the
largest eigenvector (PC1)**

- **The weiner projection is PC2 and gives depth info**

**PCA - The Details**

- **PCA involves the calculation of the eigenvalue (singular value)
decomposition of a data covariance matrix**

- **PCA is an orthogonal linear transformation**

- **PCA transforms data to a new coordinate system so that the greatest
variance of the data comes to lie on the first coordinate (1st PC), the
second greatest variance on the 2nd PC etc.**

Principal Components Analysis On:

- *Covariance Matrix:*

- Variables must be in same units

- Emphasizes variables with most variance

- *Correlation Matrix:*

- Variables are standardized (mean 0.0, SD 1.0)

- Variables can be in different units

- All variables have same impact on analysis

**Widely Used in Metabolomics**

**PCA Loadings Plot**

- **Loadings plot shows how much each of the variables contributed to
the different principal components**

- **Variables at the extreme corners contribute most to the scores plot
separation**

**Scores & Loadings**

PCA Summary

- Rotates multivariate dataset into a new configuration which is easier
to interpret

- Purposes

- Data overview

- Outlier detection

- Look at relationships between variables

PLS-DA

- When the experimental effects are subtle or moderate, PCA will not
show good separation patterns

- PLS-DA is a supervised method, it is calculated by maximizing the
co-variance between the data matrix (X) and the class labels (Y)

- PLS-DA always produces certain separation patterns with regard the
conditions

**PCA vs. PLS-DA **

Use PLS-DA with Caution

- PLS-DA is susceptible to over-fitting by producing patterns of
separation even for data randomly drawn from the same population

- Need cross validation

- Need permutation tests

Overfitting

- If we put too many variables in the model, including some unrelated to
the response, we are *overfitting*.

- Consequences are:

- Fitted model is not good for prediction of new data – prediction error
is underestimated

- Model is too elaborate, models “noise” that will not be the same for
new data

Cross Validations

- Goal: test whether your model can predict class labels for new samples

Common Splitting Strategies

- Leave-one-out (n-fold cross validation)

Components and Features

- Cross validation is used to determine the optimal number of components
needed to build the PLS-DA model. Three common performance measures:

- Sum of squares captured by the model (R<sup>2</sup>)

- Cross-validated R<sup>2</sup> (also known as Q<sup>2</sup>)

- Prediction accuracy

Permutation Tests

- Goal: to test whether your model is significantly different from the
null models

- Randomly shuffle the class labels (y) and build the (null) model
between new y and x;

- Test whether there is still the similar distances of separation;

- We can compute empirical p values

- If the result is similar to the permuted results (i.e. null model),
then we can NOT say y and x are significantly correlated

**Compute Empirical P-values**

**PLS-DA (Variance & Covariance)**

**PLS-DA (R2 & Q2)**

PLS-DA VIP Score

- **Variable Importance in Projection (VIP) scores estimate the
importance of each variable in a PLS-DA model**

- Weighted sum of the squared correlations between the PLS-DA components
and the original variable

- Weights correspond to the percentage variation explained by the PLS-DA
component in the model

- **VIP \>1 can be considered important **

- **VIP \<1 is less important and might be a good candidate for
exclusion from the model**

**VIP Plots**

- For balanced data

- Accuracy: 9/13 correct =\> 69% accuracy

- Error rate: 1 – accuracy =\> 31%

- Not suitable for imbalanced data

- In a population, cancer incidence is low: ~5 cases in 1000 people. If
a classifier predict all people to be healthy, then it is 99.5% accurate
(majority vote)

Evaluating Performance

- Basic concepts

- True positives (TP)

- True negatives (TN)

- False positives (FP)

- False negatives (FN).

- Sensitivity (Sn)

- Specificity (Sp)

- Sn (sensitivity) = True positive rate

- Sp (specificity) = True negative rate

An Example

ROC Curves

- ROC = Receiver Operating Characteristic

- A historic name from radar studies

- Very popular in biomedical applications

- To assess performance of classifiers.

- To compare different biomarker models

- A graphical plot of the true positive rate (TPR) vs. false positive
rate (FPR), for a binary classifier (i.e. positive/negative) as its
cutoff point is varied

ROC Curve

Area Under ROC Curve (AUC)

- *Overall measure* of test performance

- *Comparisons* between two tests based on differences between
(estimated) AUC

Area Under ROC Curve (AUC)

Other Supervised Classification Methods

- **SIMCA – Soft Independent Modeling of Class Analogy**

- **\*OPLS – Orthogonal Projection of Latent Structures**

- **\*Support Vector Machines**

- **\*Random Forest **

**\* Implemented in MetaboAnalyst**

Data Analysis Progression

- **Unsupervised Methods**

- **PCA or cluster to see if natural clusters form or if data separates
well**

- **Data is “unlabeled” (no prior knowledge)**

- **Supervised Methods/Machine Learning**

- **Data is labeled (prior knowledge)**

- **Used to see if data can be classified**

- **Helps separate less obvious clusters or features**

- **Statistical Significance**

- **Supervised methods <u>always</u> generate clusters -- this can be
very misleading**

- **Check if clusters are real by label permutation**

Note of Caution

- **Supervised classification methods are powerful**

- **Learn from experience**

- **Generalize from previous examples**

- **Perform pattern recognition**

- **Too many people skip the PCA or clustering steps and jump straight
to supervised methods**

- **Some get great separation and think the job is done - *this is where
the errors begin**…***

- **Too many don’t assess significance using permutation testing or
cross validation**

- **If separation isn’t partially obvious by eye-balling your data, you
may be treading on thin ice **

Don’t forget - Biology & Context
:::: {.columns}

::: {.column width='40%'}
Left column
:::

::: {.column width='60%'}
Right column
:::

::::
