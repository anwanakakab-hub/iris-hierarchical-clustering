# Hierarchical Clustering of the Iris Dataset

## About the Project

This project applies **Agglomerative Hierarchical Clustering** to the classic Iris dataset to identify natural groups of flowers based only on their physical measurements.

The clustering model uses:

- **Complete linkage**
- **Euclidean distance**
- Z-score standardized features
- Candidate cluster counts from **k = 2 to 7**

The project evaluates cluster quality with three complementary measures:

- **Silhouette Score**
- **Davies–Bouldin Index**
- **Within-Cluster Sum of Squares (WCSS)**

A dendrogram and PCA visualization are then used to verify whether the statistical results make sense visually.

The final analysis selects **three clusters**.

---

## Key Finding

The strongest cluster solution is **k = 3**.

| Metric | Result at k = 3 | Interpretation |
|---|---:|---|
| Silhouette Score | **0.4496** | Highest among k = 2–7 |
| Davies–Bouldin Index | **0.7584** | Lowest among k = 2–7 |
| PCA variance explained by PC1 + PC2 | **95.81%** | 2D visualization retains most information |

The two evaluation metrics independently select the same cluster count.

This is important because the final decision does not depend on only one measure.

---

## Why This Analysis Is Insightful

A common mistake in clustering is to choose a cluster count only because the data is known to contain a certain number of classes.

This analysis avoids that shortcut.

Although the Iris dataset is known to contain three species, the species labels are **not used to create the clusters**.

Instead, the final number of clusters is selected from the actual unsupervised-learning evidence:

1. Silhouette Score
2. Davies–Bouldin Index
3. WCSS pattern
4. Dendrogram structure
5. PCA visual evidence

That makes the final three-cluster solution data-driven rather than assumed.

---

## Dataset

The Iris dataset contains:

- **150 observations**
- **4 numeric features**
- No missing values
- One exact duplicate measurement row

### Features

- Sepal length
- Sepal width
- Petal length
- Petal width

The duplicate measurement is retained because two separate flowers can legitimately have identical measurements.

The known species labels are excluded from model formation because hierarchical clustering is an **unsupervised** method.

---

## Project Objectives

The project is designed to:

- Load and inspect the Iris dataset
- Review missing values and duplicate measurements
- Standardize the four numeric features
- Explain why scaling is necessary for distance-based clustering
- Apply agglomerative hierarchical clustering
- Use complete linkage and Euclidean distance
- Test integer values of k from 2 to 7
- Compare Silhouette Score, Davies–Bouldin Index, and WCSS
- Select the final cluster count using statistical and visual evidence
- Build a dendrogram showing the three-cluster cut
- Use PCA to visualize the final cluster structure
- Profile clusters using the original centimeter measurements

---

## My Role

For this project, I completed the full unsupervised-learning workflow, including:

- Data inspection
- Data-quality assessment
- Feature scaling
- PCA analysis
- Hierarchical clustering
- Linkage and distance selection
- Cluster-count evaluation
- Silhouette analysis
- Davies–Bouldin analysis
- Manual WCSS calculation
- Dendrogram construction
- Cluster profiling
- Visual interpretation
- Final model recommendation

---

## Key Skills & Tools

### Programming and Analytics

- Python
- Pandas
- NumPy
- Jupyter Notebook

### Machine Learning

- Unsupervised Learning
- Agglomerative Hierarchical Clustering
- Complete Linkage
- Euclidean Distance
- StandardScaler
- Principal Component Analysis

### Model Evaluation

- Silhouette Score
- Davies–Bouldin Index
- WCSS
- Dendrogram Analysis
- Visual Cluster Validation

### Visualization

- Matplotlib
- PCA Scatter Plots
- Scree Plot
- Cumulative Variance Plot
- Dendrogram

---

## Methodology

### 1. Data Inspection

The Iris measurements are loaded from `sklearn.datasets`.

The dataset contains 150 flowers and four numeric measurements.

A data-quality check confirms that there are no missing values.

### 2. Duplicate Review

One exact duplicate measurement row is present.

It is retained because identical measurements do not necessarily mean the same flower was recorded twice.

### 3. Standardization

All four features are standardized using `StandardScaler`.

This is necessary because hierarchical clustering uses distances between observations.

Without scaling, features with larger numeric ranges could contribute more heavily to Euclidean distance.

### 4. PCA

PCA is fitted to the standardized data for visualization.

The first two components explain approximately **95.81%** of total variance.

This means a 2D PCA chart represents most of the information in the original four-dimensional dataset.

### 5. Hierarchical Clustering

The model uses:

- Agglomerative clustering
- Complete linkage
- Euclidean distance

Complete linkage defines the distance between two clusters using their farthest points.

This tends to produce compact groups and reduces the chaining behaviour that can occur with single linkage.

### 6. Cluster-Count Evaluation

The analysis tests:

- k = 2
- k = 3
- k = 4
- k = 5
- k = 6
- k = 7

The results are:

| k | Silhouette Score | Davies–Bouldin Index | WCSS |
|---:|---:|---:|---:|
| 2 | 0.4408 | 0.8927 | 296.36 |
| 3 | **0.4496** | **0.7584** | 153.88 |
| 4 | 0.4106 | 0.8768 | 125.52 |
| 5 | 0.3521 | 0.8584 | 107.19 |
| 6 | 0.3107 | 0.8824 | 99.87 |
| 7 | 0.3076 | 0.7948 | 91.77 |

Both major cluster-quality measures select **k = 3**.

---

## Final Cluster Sizes

The three-cluster solution contains:

| Cluster | Flowers |
|---:|---:|
| 1 | 77 |
| 2 | 49 |
| 3 | 24 |

The clusters are not forced to be the same size.

Hierarchical clustering groups observations based on similarity, so unequal group sizes are expected.

---

## Cluster Profiles

Average measurements on the original scale show clear behavioural differences between the three groups.

| Cluster | Sepal Length | Sepal Width | Petal Length | Petal Width |
|---:|---:|---:|---:|---:|
| 1 | 6.47 | 2.99 | 5.16 | 1.82 |
| 2 | 5.02 | 3.45 | 1.47 | 0.24 |
| 3 | 5.51 | 2.60 | 3.91 | 1.17 |

### Interpretation

**Cluster 2** contains the smallest flowers in terms of petal measurements and has the highest average sepal width.

**Cluster 1** contains flowers with the largest average sepals and petals.

**Cluster 3** is an intermediate group, especially in petal length and width.

These profiles help explain why one group appears clearly separated in PCA while the other two overlap more.

---

## PCA Insight

The first two PCA components explain:

- PC1: approximately **72.96%**
- PC2: approximately **22.85%**
- Combined: approximately **95.81%**

This is unusually high for a two-dimensional representation.

The final PCA plot therefore provides a strong visual summary of the four-dimensional measurement space.

However, the PCA plot does **not** show perfectly isolated clusters.

One cluster is clearly separated, while the other two overlap.

This agrees with the moderate Silhouette Score of 0.4496.

---

## Dendrogram Insight

The dendrogram shows the order in which individual flowers and groups merge as the distance threshold increases.

A red dashed horizontal cut is placed at a height that produces exactly **three branches**.

The dendrogram therefore provides a second visual explanation for the final three-cluster solution.

Unlike K-Means, hierarchical clustering also reveals the full nested structure of the data rather than only the final group assignment.

---

## Why Complete Linkage?

Complete linkage compares clusters using the **maximum distance** between their members.

This approach tends to produce relatively compact groups.

### Comparison with Other Linkage Methods

- **Single linkage:** Uses the minimum pairwise distance and can produce long chains.
- **Complete linkage:** Uses the maximum pairwise distance and favours compact clusters.
- **Average linkage:** Uses average pairwise distance.
- **Ward linkage:** Minimizes increases in within-cluster variance and requires Euclidean distance.

Complete linkage is therefore a reasonable choice when compact, well-separated groups are preferred.

---

## Why Euclidean Distance?

Euclidean distance measures straight-line distance between observations.

Because all four Iris features are continuous measurements and are standardized before clustering, Euclidean distance provides a natural similarity measure.

Other possible distance measures include:

- Manhattan distance
- Cosine distance
- Chebyshev distance

The final choice should always match the data type and clustering objective.

---

## Repository Structure

```text
iris-hierarchical-clustering/
│
├── Iris_Hierarchical_Clustering_GitHub.ipynb
│   └── Complete step-by-step hierarchical clustering analysis
│
├── hierarchical_clustering_outputs/
│   ├── 01_pca_standardized_data.png
│   ├── 02_pca_scree_plot.png
│   ├── 03_pca_cumulative_variance.png
│   ├── 04_hierarchical_wcss.png
│   ├── 05_hierarchical_silhouette.png
│   ├── 06_hierarchical_davies_bouldin.png
│   ├── 07_dendrogram_k3.png
│   └── 08_hierarchical_pca_k3.png
│
└── README.md
```

---

## How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/iris-hierarchical-clustering.git
cd iris-hierarchical-clustering
```

### 2. Install the Required Packages

```bash
pip install pandas numpy matplotlib scikit-learn scipy jupyter
```

### 3. Start Jupyter Notebook

```bash
jupyter notebook
```

### 4. Open the Notebook

Open:

```text
Iris_Hierarchical_Clustering_GitHub.ipynb
```

The Iris dataset is built into scikit-learn, so no external CSV file is required.

Run the cells from top to bottom.

---

## Key Learning Outcomes

This project demonstrates several important clustering principles:

1. **Scale features before distance-based clustering.**
2. **Do not use known class labels to form unsupervised clusters.**
3. **Use more than one metric to select the number of clusters.**
4. **Higher Silhouette Scores are better.**
5. **Lower Davies–Bouldin values are better.**
6. **Use a dendrogram to understand hierarchical merge structure.**
7. **Use PCA for visualization rather than replacing the clustering feature space.**
8. **Interpret clusters using original-scale measurements, not only numeric labels.**

---

## Limitations

- The final Silhouette Score of 0.4496 indicates moderate rather than perfect separation.
- Hierarchical clustering results depend on the linkage method and distance metric.
- Dendrograms become difficult to read for very large datasets.
- PCA compresses information and should not be treated as the clustering model itself.
- The Iris dataset is small and relatively clean compared with most real-world datasets.

---

## Future Improvements

Potential extensions include:

- Compare complete linkage with single, average, and Ward linkage.
- Compare hierarchical clustering with K-Means.
- Use known species labels only after clustering to measure external agreement.
- Test cluster stability under resampling or small data perturbations.
- Compare clustering quality across different distance metrics.

---

## Privacy / Data Note

The Iris dataset is a public benchmark dataset distributed with scikit-learn.

It does not contain personally identifiable customer or individual-level sensitive information.

---

## Conclusion

The hierarchical clustering analysis identifies **three meaningful groups** in the Iris measurements.

The strongest evidence comes from agreement across multiple evaluation methods:

- Highest Silhouette Score at k = 3
- Lowest Davies–Bouldin Index at k = 3
- Clear three-branch dendrogram cut
- PCA visualization showing three visible groups
- Original-scale cluster profiles showing distinct petal and sepal measurement patterns

The project demonstrates that reliable clustering requires more than creating labels. The strongest analysis combines **data preparation, statistical evaluation, visualization, and interpretable cluster profiles** before making a final decision.
