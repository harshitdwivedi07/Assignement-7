# Customer Segmentation using K-Means Clustering and PCA

**Harshit Dwivedi**

## Objective
Segment mall customers into groups based on annual income and spending
behavior using K-Means Clustering, and apply Principal Component Analysis
(PCA) to visualize the resulting clusters in two dimensions.

## Dataset Link
Mall Customer Segmentation Dataset (Kaggle):
https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python

## Libraries Used
- pandas
- numpy
- scikit-learn
- matplotlib

## Methodology
1. Loaded the dataset (200 customers), identified numerical features (Age,
   Annual Income, Spending Score) and the categorical feature (Genre), and
   reviewed dataset info and summary statistics.
2. Checked for missing values (none found), dropped the non-predictive
   `CustomerID` column, encoded `Genre` (Male = 0, Female = 1), and
   standardized Annual Income and Spending Score with StandardScaler -
   the two features used for clustering, consistent with the assignment's
   focus on income and spending behavior.
3. Used the Elbow Method (K = 1 to 10) to identify the optimal number of
   clusters, trained a K-Means model with the selected K, assigned cluster
   labels to each customer, and applied PCA to reduce the scaled data to 2
   principal components.
4. Generated the Elbow Curve, a scatter plot of customers colored by
   cluster in the original feature space, and a PCA-based visualization of
   the same clusters.

## Results
**Optimal K (Elbow Method): 5**

| Cluster | Size | Avg. Age | Avg. Income (k$) | Avg. Spending Score |
|---------|------|----------|-------------------|------------------------|
| 0 | 81 | 42.7 | 55.3 | 49.5 |
| 1 | 39 | 32.7 | 86.5 | 82.1 |
| 2 | 22 | 25.3 | 25.7 | 79.4 |
| 3 | 35 | 41.1 | 88.2 | 17.1 |
| 4 | 23 | 45.2 | 26.3 | 20.9 |

PCA explained variance: PC1 = 50.5%, PC2 = 49.5% (together capturing all of
the variance, since only 2 features were used for clustering).

**Observations:**
1. The elbow curve shows inertia dropping sharply up to K=5, after which
   the improvement flattens noticeably, making K=5 the optimal number of
   clusters for this dataset.
2. Since Income and Spending Score were already only two dimensions, PCA
   here mainly confirms the same cluster separation visible in the original
   scatter plot; PCA becomes more valuable when clustering is done on many
   features (e.g. including Age and Genre) and the result needs to be
   viewed in 2D. In general, PCA compresses correlated, high-dimensional
   data into a small number of components that capture most of the
   variance, making otherwise unplottable data visually interpretable.
3. The five identified segments have distinct profiles: a mid-income,
   mid-spending "average" group (Cluster 0); a high-income, high-spending
   group (Cluster 1); a low-income, high-spending group (Cluster 2); a
   high-income, low-spending group (Cluster 3); and a low-income,
   low-spending group (Cluster 4) - Cluster 1 being the most valuable
   target for premium marketing campaigns.
4. The high-income, low-spending segment (Cluster 3) is a particularly
   interesting target for engagement campaigns, since these customers have
   spending capacity that is not currently being converted into purchases.

## Conclusion
This project applied K-Means Clustering to segment mall customers based on
their annual income and spending score, using the Elbow Method to select
K=5 as the optimal number of clusters, and Principal Component Analysis to
visualize the resulting groups in two dimensions. The five clusters
revealed clearly distinct customer profiles, ranging from low-income
low-spenders to high-income high-spenders, with a notable high-income
low-spending segment that represents a strong opportunity for targeted
engagement campaigns. These segments have direct business applications:
the mall's marketing team can design different promotions, loyalty
programs, or store layouts tailored to each group instead of treating all
customers uniformly, improving marketing efficiency and customer
satisfaction. One limitation of K-Means clustering is that it requires the
number of clusters (K) to be chosen in advance and assumes clusters are
roughly spherical and similarly sized, which may not hold for more complex,
irregularly shaped customer segments in real-world data. One advantage of
PCA is that it reduces high-dimensional data into a small number of
components that capture most of the variance, making it possible to
visualize and interpret patterns that would otherwise be difficult to see
across many original features at once.
