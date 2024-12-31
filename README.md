# A Tutorial on Performing Principal Component Analysis (PCA) in R
**Authors:** Michelle Zong, Daniia Newman, Jasmin Mendoza



## Codebook
#### Breast Cancer Wisconsin (Diagnostic) Data Set
For this demo, we used a subset of the Breast Cancer [Kaggle data set](https://www.kaggle.com/data sets/uciml/breast-cancer-wisconsin-data).

Features are computed from a digitized image of a fine needle aspirate (FNA) of a breast mass. They describe characteristics of the cell nuclei present in the image.

#### Attribute Information:

  * ID - int - unique identifier for each patient
  * Diagnosis - str - breast cancer diagnosis (B = Benign, M = Malignant)

Real-valued features (10) are computed for each cell nucleus. All feature values are re-coded with four significant digits:

  * Radius_mean - float - mean of distances from center to points on the perimeter
  * Texture_mean - float - standard deviation of gray-scale values
  * Perimeter_mean - float - mean size of the core tumor
  * Area_mean - float - mean area of the core tumor
  * Smoothness_mean - float - mean of local variation in radius lengths
  * Compactness_mean - float - mean of perimeter^2 / area - 1.0
  * Concavity_mean - float - mean of severity of concave portions of the contour
  * Concave points_mean - float - mean for number of concave portions of the contour
  * Symmetry_mean - float - mean of symmetry
  * Fractal_dimension_mean - float - mean for 'coastline approximation' - 1


## Introduction
In this tutorial, we will perform **Principal Component Analysis (PCA)** on the Breast Cancer data set. Principal Component Analysis (PCA) is an unsupervised statistical technique used to reduce the dimensionality of a data set while retaining most of the variance present in the data. PCA does what the name describes, it finds 'principal components' of the data.

  * It is a tool often used for data visualization or in data pre-processing before supervised techniques are applied. PCA can also be used to *impute* missing data values through a process called *matrix completion*, which is where all of our Netflix recommendations come from, but we will not go into that today. 
  * The process if PCA involves transforming the original variables into a new set of uncorrelated variables, known as principal components. Being uncorrelated is equivalent to being orthogonal or perpendicular to each other. 
  * These components are ordered so that the first few retain most of the variation present in the original data set. The first principal component (PC1) is defined as the direction that maximizes the variance of the projected data. We want maximal variation because more variation equals more information (If all of our values were all equal to 1, there would be no variation in the data set and thus, no information). 
  * The second principal component (PC2) is uncorrelated to PC1, and is the direction that maximizes the variance of the projected data with this constraint of orthogonality to PC1. This continues with every subsequent principal component, all needing to be orthogonal to the principal components before them.



## Main Steps
The main steps in PCA that will be conducted in this tutorial are as follows:

**1) Standardize the data:** Centering the data by subtracting every observation in column by the mean of that column, and scaling by dividing every observation in a column by the standard deviation of that column. 

**2) Calculate the correlation matrix:** The goal of this step is to understand if there is any relationship between the variables. The matrix summarizes the correlations between all possible pairs of variables. 

**3) Compute the the principal components:** Use the function prcomp() to compute the principal components. This function uses Singular Value Decomposition. 

**4) Visualize and interpret PCA results:** There are many ways to do this, in our tutorial we will look at the rotation matrix, Scree plot, Biplot, bar graphs, and a scatter plot with concentration ellipses. 



## Results (very light) Summary
#### Please refer to the results section within the knitted PDF file or the .Rmd file for further interpretations and mathematical explanations of the results.

#### Interpretation of first two principal components:

* *PC1* has a standard deviation of 2.3432 and explains 54.91% of the variance in the data.
* *PC2* explains an additional 25.12% of the variance, bringing the cumulative proportion to 80.02%.

The first two components together explain about 80.02% of the total variance, suggesting that they capture the majority of the information in the data set. We can reduce the dimensionality of the data set while retaining most of the information by deciding which principal components to keep based on the cumulative proportion. 

#### Principal Components (Scores) in PCA

In Principal Component Analysis (PCA), the principal components (scores) are the coordinates of the original data points in the new coordinate system defined by the principal components. These scores represent the projection of the original data points onto the principal component axes - meaning they are the distance between each observation and the principal component direction, for each principal component.



## General Information
#### Requirements
- R
- RStudio (recommended)
- Required packages: 
    - `ggplot2` - for ggplot() scatter plot
    - `factoextra` - for fviz_eig() scree plot, fviz_pca_var biplot
    - `dplyr` - for na.omit(), select(), select_if()
    - `ggcorrplot` - for ggcorrplot() correlation matrix

#### How to Run the Analysis
1. Fork the repository.
   ```bash
   git fork https://github.com/mmzong/PCA_BreastCancerDetection.git
   ```
2. Open `PCA_Tutorial_FINAL.Rmd` in RStudio.
4. Run the R Markdown file.

#### Contributions
Contributions and suggestions are welcome. Please open an issue or submit a pull request for any enhancements or corrections.
