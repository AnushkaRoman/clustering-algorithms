# Clustering Algorithms on Mall Customers Dataset

## Project Description

This project implements and compares four **unsupervised machine learning clustering algorithms** using the **Mall Customers dataset**.

The main objective of this project is to identify meaningful groups of customers based on their **Annual Income** and **Spending Score**. The clustering results are evaluated using quantitative metrics and visual inspection.

The four clustering algorithms implemented in this project are:

1. K-Means Clustering
2. Agglomerative Hierarchical Clustering
3. DBSCAN
4. Divisive Hierarchical Clustering

---

## Objectives

The main objectives of this project are:

- To understand unsupervised machine learning and clustering.
- To implement different clustering algorithms.
- To identify meaningful customer groups.
- To compare the performance of different clustering techniques.
- To evaluate clustering quality using Silhouette Score and Davies-Bouldin Index.
- To visualize the clusters.
- To interpret the resulting customer segments.

---

## Dataset

The project uses the **Mall Customers dataset**.

The dataset contains information about customers of a shopping mall, including demographic and spending-related information.

### Dataset Features

| Feature | Description |
|---|---|
| CustomerID | Unique identification number of the customer |
| Gender | Gender of the customer |
| Age | Age of the customer |
| Annual Income (k$) | Annual income of the customer in thousands of dollars |
| Spending Score (1-100) | Spending score assigned to the customer based on purchasing behavior |

### Features Used for Clustering

The following two features were selected for clustering:

- **Annual Income (k$)**
- **Spending Score (1-100)**

These features were selected because they provide useful information for identifying customer segments and allow the resulting clusters to be visualized in two dimensions.

---

# Algorithms Implemented

## 1. K-Means Clustering

K-Means is a centroid-based clustering algorithm that divides the dataset into a predefined number of clusters.

### Working

The algorithm:

1. Selects the number of clusters `K`.
2. Initializes K cluster centroids.
3. Assigns each data point to the nearest centroid.
4. Calculates new centroids.
5. Reassigns the data points.
6. Repeats the process until the clusters stabilize.

### K-Means in this project

The **Elbow Method** was used to help determine a suitable number of clusters.

The final K-Means clusters were then evaluated using:

- Silhouette Score
- Davies-Bouldin Index

### Advantages

- Simple and easy to understand.
- Computationally efficient.
- Works well for relatively well-separated clusters.
- Suitable for numerical datasets.

### Limitations

- The number of clusters must be specified.
- Sensitive to outliers.
- Results can depend on the initial centroid positions.
- Works best when clusters are relatively spherical.

---

# 2. Agglomerative Hierarchical Clustering

Agglomerative Hierarchical Clustering is a bottom-up hierarchical clustering technique.

Initially, every data point is treated as an individual cluster. The closest clusters are then repeatedly merged until the required number of clusters is obtained.

### Working

1. Treat every data point as an individual cluster.
2. Calculate distances between clusters.
3. Merge the closest clusters.
4. Repeat until the desired number of clusters is obtained.

A **dendrogram** was used to visualize the hierarchical structure of the data and help understand the possible number of clusters.

### Advantages

- Does not require random initialization.
- Produces a hierarchy of clusters.
- Dendrogram provides a useful visual representation.
- Can reveal relationships between groups.

### Limitations

- Computationally more expensive for large datasets.
- Once clusters are merged, the decision cannot easily be reversed.
- Results can depend on the linkage method used.

---

# 3. DBSCAN

DBSCAN stands for **Density-Based Spatial Clustering of Applications with Noise**.

Unlike K-Means, DBSCAN does not require the number of clusters to be specified in advance.

It identifies clusters based on the density of data points.

### Main Parameters

- `eps` — maximum distance between neighboring points.
- `min_samples` — minimum number of points required to form a dense region.

### Working

DBSCAN classifies points into:

- Core points
- Border points
- Noise points

Noise points are assigned the label `-1`.

### Advantages

- Does not require the number of clusters beforehand.
- Can identify clusters of irregular shapes.
- Can detect noise and outliers.
- Useful for density-based datasets.

### Limitations

- Sensitive to the choice of `eps` and `min_samples`.
- Can have difficulty when clusters have significantly different densities.
- Results may vary considerably with parameter selection.

---

# 4. Divisive Hierarchical Clustering

Divisive Hierarchical Clustering is a **top-down hierarchical clustering approach**.

Instead of starting with individual points and merging them, divisive clustering starts with all data points in one large cluster and repeatedly splits the clusters.

### Working

1. Start with all observations in a single cluster.
2. Select a cluster to split.
3. Divide the selected cluster into smaller clusters.
4. Continue splitting until the desired number of clusters is obtained.

### Implementation

For this project, a divisive clustering approach was implemented using **K-Means to recursively split clusters**.

This provides a practical implementation of the top-down hierarchical clustering concept.

### Advantages

- Provides a top-down view of the data.
- Can reveal the structure of groups through repeated splitting.
- Useful for hierarchical analysis.

### Limitations

- Computationally more expensive than simple K-Means.
- The splitting strategy affects the final clusters.
- The implementation depends on the method used to split each cluster.

---

# Data Preprocessing

Before applying the clustering algorithms, the dataset was inspected and prepared.

The following preprocessing steps were performed:

1. Loaded the dataset using Pandas.
2. Checked the shape of the dataset.
3. Examined the data types.
4. Checked for missing values.
5. Checked for duplicate records.
6. Selected relevant numerical features.
7. Standardized the selected features.

The features used were:

```text
Annual Income (k$)
Spending Score (1-100)
```

Feature scaling was performed using `StandardScaler` because clustering algorithms based on distance can be affected by differences in feature scales.

---

# Exploratory Data Analysis

A scatter plot was created using:

- Annual Income
- Spending Score

This visualization helps identify possible natural groupings in the dataset before applying clustering algorithms.

---

# Evaluation Metrics

The clustering algorithms were evaluated using the following metrics.

## Silhouette Score

The Silhouette Score measures how similar each data point is to its own cluster compared with other clusters.

The score ranges from:

```text
-1 to +1
```

Interpretation:

- Close to **+1** → well-separated clusters
- Around **0** → overlapping clusters
- Less than **0** → possible incorrect cluster assignments

**Higher Silhouette Score indicates better-defined clusters.**

---

## Davies-Bouldin Index

The Davies-Bouldin Index measures the similarity between clusters based on their internal distances and separation.

**Lower Davies-Bouldin Index indicates better clustering.**

Therefore, a good clustering solution generally has:

```text
High Silhouette Score
+
Low Davies-Bouldin Index
```

---

# Visual Inspection

In addition to numerical evaluation, scatter plots were created for each algorithm.

The visualizations allow the clusters produced by:

- K-Means
- Agglomerative Hierarchical Clustering
- DBSCAN
- Divisive Hierarchical Clustering

to be compared visually.

This is particularly useful for understanding cluster separation, overlap, and noise points.

---

# Results

The four clustering algorithms were compared using:

- Silhouette Score
- Davies-Bouldin Index
- Visual inspection

The results generated by the notebook are summarized in a comparison table.

| Algorithm | Silhouette Score | Davies-Bouldin Index |
|---|---:|---:|
| K-Means | Generated in notebook | Generated in notebook |
| Agglomerative Hierarchical | Generated in notebook | Generated in notebook |
| DBSCAN | Generated in notebook | Generated in notebook |
| Divisive Hierarchical | Generated in notebook | Generated in notebook |

> **Note:** The values in this table should be updated with the actual results generated when the notebook is executed.

The algorithm with the **highest Silhouette Score** and **lowest Davies-Bouldin Index** can generally be considered to provide the best clustering performance for this dataset, while visual inspection is also considered when interpreting the results.

---

# Customer Segmentation

The clusters can be interpreted in terms of customer characteristics.

For example, the clustering may identify groups such as:

- Low Income / Low Spending
- Low Income / High Spending
- Average Income / Average Spending
- High Income / Low Spending
- High Income / High Spending

The exact interpretation depends on the cluster assignments generated by the algorithms.

These customer segments can potentially be useful for:

- Targeted marketing
- Personalized offers
- Customer relationship management
- Identifying high-value customers
- Designing promotional campaigns

---

# Technologies Used

The project was implemented using the following technologies and libraries:

- **Python**
- **Google Colab**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Scikit-learn**
- **SciPy**

---

# Project Structure

```text
Clustering-Algorithms/
│
├── Clustering_Algorithms_Mall_Customers.ipynb
│
├── Mall_Customers.csv
│
└── README.md
```

### Files

**Clustering_Algorithms_Mall_Customers.ipynb**

Contains the complete implementation of all four clustering algorithms, preprocessing, visualization, evaluation, and comparison.

**Mall_Customers.csv**

Contains the Mall Customers dataset used for the analysis.

**README.md**

Contains the project description, methodology, algorithms, evaluation metrics, and instructions for running the project.

---

# How to Run the Project

## Option 1: Google Colab

1. Open Google Colab.
2. Open the notebook:

```text
Clustering_Algorithms_Mall_Customers.ipynb
```

3. Upload the `Mall_Customers.csv` dataset.
4. Execute the notebook cells from top to bottom.
5. Observe the clustering visualizations and evaluation results.

---

## Option 2: Run Locally

Install the required Python libraries:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn scipy
```

Then open the notebook using Jupyter Notebook or JupyterLab.

```bash
jupyter notebook
```

Open:

```text
Clustering_Algorithms_Mall_Customers.ipynb
```

and execute the cells sequentially.

---

# GitHub

This project is maintained using GitHub for version control and project sharing.

The repository contains:

- Python/Colab notebook
- Dataset
- Project documentation

The notebook can be opened directly in Google Colab for execution.

---

# Conclusion

This project demonstrates the application of four different unsupervised clustering algorithms to a real-world customer dataset.

K-Means provides a simple centroid-based approach, while Agglomerative Hierarchical Clustering provides a hierarchical view of customer relationships. DBSCAN uses density-based clustering and can identify noise points, while Divisive Hierarchical Clustering provides a top-down approach to dividing the dataset.

The clustering methods were compared using **Silhouette Score**, **Davies-Bouldin Index**, and **visual inspection**.

The comparison helps determine which clustering approach is most suitable for identifying meaningful customer segments in the Mall Customers dataset.

---

# Learning Outcomes

After completing this project, the following concepts were demonstrated:

- Understanding unsupervised machine learning.
- Understanding clustering algorithms.
- Implementing K-Means clustering.
- Implementing Agglomerative Hierarchical Clustering.
- Implementing DBSCAN.
- Implementing Divisive Hierarchical Clustering.
- Feature selection and preprocessing.
- Feature scaling.
- Cluster visualization.
- Silhouette Score evaluation.
- Davies-Bouldin Index evaluation.
- Comparing different clustering techniques.
- Interpreting customer segments.
- Using Google Colab for machine learning.
- Publishing a machine learning project on GitHub.
```

### One thing I strongly recommend

Before submitting, replace the **"Generated in notebook"** entries in the Results table with the **actual numbers from your Colab output**. That makes the README look like a completed experiment rather than a template.

For example, after your comparison cell runs, you can copy the four rows into the README.

Also, your **DBSCAN row may contain `NaN`** if DBSCAN didn't produce enough clusters. If that happens, don't hide it—it's a legitimate result and you can explain that the DBSCAN parameters were tuned or that the dataset did not form sufficient density-based clusters under the selected parameters.
