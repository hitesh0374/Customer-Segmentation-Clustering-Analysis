# Customer Segmentation - Comparing 4 Clustering Algorithms

I wanted to see how different clustering algorithms handle the same problem, so I picked the Mall Customers dataset and ran it through K-Means, Hierarchical Clustering, DBSCAN, and GMM to compare results.

## Algorithms used

1. **K-Means** – centroid-based
2. **Agglomerative Hierarchical Clustering** – builds a tree of clusters
3. **DBSCAN** – density-based, also flags outliers
4. **Gaussian Mixture Models (GMM)** – probabilistic/soft clustering

Each one is tuned, scored with silhouette score, and plotted so you can compare them visually.

## Dataset

We use the well-known **Mall Customers Dataset**, loaded directly from a public GitHub CSV:

| Column | Description |
|---|---|
| `CustomerID` | Unique identifier for each shopper |
| `Gender` | Customer's gender |
| `Age` | Customer's age |
| `Annual Income (k$)` | Yearly income |
| `Spending Score (1-100)` | Score assigned by the mall based on purchase behavior |

## What the notebook does

- Loads and cleans the data, checks for missing values
- Scales `Annual_Income` and `Spending_Score`
- Runs K-Means, using Elbow + Silhouette to pick K (came out to 5)
- Runs Hierarchical Clustering, using a dendrogram to check the cluster count
- Runs DBSCAN, using a K-Distance graph to pick `eps`
- Runs GMM, using BIC/AIC to pick the number of components
- Plots all four results side by side
- Ranks them by silhouette score and writes up what the clusters actually mean for the business

## Results

K-Means and Hierarchical Clustering scored the highest (~0.55 silhouette score) since the clusters in this data are pretty round and well separated. DBSCAN caught the outliers well but left some points unclassified as noise. GMM was close to K-Means but handles overlapping clusters a bit better.

## Tech stack

- Python
- NumPy & Pandas
- Matplotlib & Seaborn
- SciPy (for hierarchical clustering)
- Scikit-Learn

## Why I built this

I wanted a clear side-by-side of how these algorithms differ in practice, not just in theory. Things like whether you need to set K upfront, whether it handles noisy points, and whether the boundaries are hard or soft all matter depending on the use case.


