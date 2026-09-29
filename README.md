# PCA – Principal Component Analysis

## 📌 Overview

This project demonstrates **Principal Component Analysis (PCA)**, an unsupervised learning technique used for **dimensionality reduction**.

PCA transforms a dataset with multiple correlated features into a smaller set of new features called **Principal Components**, while preserving as much of the important information in the original data as possible.

In this practical, PCA is applied to the **Iris dataset** to reduce its original feature dimensions to two principal components and visualize the transformed data.

---

# 🌱 Introduction to PCA

**PCA stands for Principal Component Analysis.**

PCA is mainly used for **feature extraction and dimensionality reduction**.

When a dataset contains many features, working with all of them can make analysis and visualization difficult. PCA transforms the original features into a smaller number of new variables called **Principal Components**.

### Simple Idea

```text
Original Features
       ↓
   Feature Scaling
       ↓
       PCA
       ↓
Principal Components
       ↓
Reduced Dimensions
```

---

# 🎯 Project Objective

The main objectives of this practical are:

* Understand PCA
* Perform data preprocessing
* Handle feature scaling before PCA
* Reduce feature dimensions
* Understand Principal Components
* Analyze explained variance
* Visualize high-dimensional data in two dimensions

---

# 📊 Dataset

The **Iris dataset** contains measurements of iris flowers.

It contains four original features:

| Feature      | Description         |
| ------------ | ------------------- |
| Sepal Length | Length of the sepal |
| Sepal Width  | Width of the sepal  |
| Petal Length | Length of the petal |
| Petal Width  | Width of the petal  |

The dataset also contains a target variable representing the iris species.

---

# 🔄 Project Workflow

```text
Load Iris Dataset
       ↓
Create DataFrame
       ↓
Check Dataset Information
       ↓
Check Missing Values
       ↓
Check Duplicate Values
       ↓
Separate Features and Target
       ↓
Train-Test Split
       ↓
Feature Scaling
       ↓
Apply PCA
       ↓
Reduce Dimensions
       ↓
Calculate Explained Variance
       ↓
Analyze Principal Components
       ↓
Visualize PCA Data
```

---

# 🔹 Dataset Loading

The Iris dataset is loaded using Scikit-learn.

```python
from sklearn.datasets import load_iris

iris = load_iris()

X = iris.data
y = iris.target
```

---

# 🔹 Train-Test Split

The dataset is divided into training and testing sets.

A test size of `0.2` is used, meaning 20% of the data is kept for testing.

Stratification is used to maintain the class distribution.

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42,
    stratify=y
)
```

---

# 🔹 Feature Scaling

Feature scaling is performed before applying PCA.

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
```

Scaling is important because PCA is affected by the scale of the input features.

---

# 🔹 Applying PCA

PCA is applied with two components.

```python
from sklearn.decomposition import PCA

pca = PCA(n_components=2)

X_train_pca = pca.fit_transform(X_train_scaled)
X_test_pca = pca.transform(X_test_scaled)
```

The original four features are transformed into two principal components:

```text
4 Original Features
        ↓
       PCA
        ↓
  PC1 + PC2
```

---

# 📉 Dimensionality Reduction

The original training data contains four features.

After PCA, the data is represented using only two principal components.

```python
print("Original Shape:", X_train.shape)
print("PCA Shape:", X_train_pca.shape)
```

This demonstrates **dimensionality reduction**.

---

# 📊 Explained Variance

Explained variance tells us how much information from the original features is represented by each principal component.

```python
print("Explained Variance Ratio:")
print(pca.explained_variance_ratio_)

print(
    "Total Explained Variance:",
    pca.explained_variance_ratio_.sum()
)
```

### Explained Variance Ratio

Each principal component explains a certain proportion of the total variance in the dataset.

The total explained variance of the selected components can be calculated by summing their explained variance ratios.

---

# 🔹 Principal Components

PCA creates new feature directions called **Principal Components**.

```python
print("Principal Components:")
print(pca.components_)
```

The principal components are combinations of the original features.

For example:

```text
Original Features
      ↓
Sepal Length
Sepal Width
Petal Length
Petal Width
      ↓
      PCA
      ↓
PC1
PC2
```

---

# 📈 PCA Visualization

The two principal components can be visualized using a scatter plot.

```python
plt.figure(figsize=(8, 6))

plt.scatter(
    X_train_pca[:, 0],
    X_train_pca[:, 1],
    c=y_train
)

plt.xlabel("Principal Component 1")
plt.ylabel("Principal Component 2")
plt.title("PCA - Iris Dataset")

plt.show()
```

This allows the reduced two-dimensional representation of the Iris dataset to be visualized.

---

# 🧠 Important PCA Concepts

### Principal Component

A Principal Component is a new feature created as a linear combination of the original features.

### PC1

**PC1** is the first principal component and captures the maximum possible variance.

### PC2

**PC2** captures the maximum remaining variance while being orthogonal to PC1.

### Explained Variance

Explained variance represents how much information or variation is captured by each principal component.

---

# 🔄 Feature Selection vs Feature Extraction

PCA performs **feature extraction**, not feature selection.

### Feature Selection

Selects some of the original features.

```text
A, B, C, D
 ↓
A, C
```

### Feature Extraction

Creates new features from the original features.

```text
A, B, C, D
 ↓
PCA
 ↓
PC1, PC2
```

Therefore:

> **PCA is a Feature Extraction technique.**

---

# 📚 Concepts Covered

* Unsupervised Learning
* Dimensionality Reduction
* Principal Component Analysis
* Feature Scaling
* Principal Components
* Explained Variance
* Feature Extraction
* Data Visualization

---

# 🛠️ Technologies Used

* Python
* Pandas
* Matplotlib
* Scikit-learn
* Jupyter Notebook / Google Colab

---

# 🎓 Key Learning

Through this practical, I learned how PCA can reduce the dimensionality of a dataset while preserving important information.

I also learned:

* Why feature scaling is important before PCA
* How PCA transforms original features
* How Principal Components are created
* How to calculate explained variance
* How to interpret Principal Components
* The difference between feature selection and feature extraction
* How PCA can make high-dimensional data easier to visualize

---

# 📌 Conclusion

This project demonstrates **Principal Component Analysis (PCA)** using the Iris dataset.

PCA was used to transform the original four-dimensional feature space into two principal components. The reduced data was then visualized to understand the structure of the dataset.

PCA is useful for **dimensionality reduction, visualization, feature extraction, and simplifying high-dimensional datasets**.

---


B.Tech – Computer Science Engineering (AI & ML)
