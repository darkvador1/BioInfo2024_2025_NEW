# Gene Clusterness and Trajectoriness Quantification

## Overview

This bioinformatics project aims to quantify the spatial and/or temporal organization of genes by characterizing their degree of **clusterness** and **trajectoriness**.

The goal is to develop quantitative measures that capture whether genes exhibit clustering patterns or follow structured trajectories, enabling systematic comparisons of gene organization and behavior.

Based on the methodology proposed by Lim and Qiu (2024), this project focuses on reproducing and evaluating a geometric framework originally designed for single-cell RNA sequencing (scRNA-seq) data.

## Objectives

* Reproduce the original pipeline for quantifying clusterness and trajectoriness.
* Evaluate five geometric scoring metrics.
* Investigate the influence of preprocessing and dimensionality reduction parameters.
* Compare different embedding and classification approaches.
* Assess the applicability of the framework to real scRNA-seq datasets.

## Methodology

The framework uses five complementary metrics to characterize the geometry of datasets:

1. **Pairwise Distance Entropy:** Measures the distribution of distances between cells.
2. **Persistent Homology:** Characterizes how connected components merge across distance thresholds.
3. **Vector Magnitude:** Measures the overall directionality of the data.
4. **Ripley’s K Function:** Evaluates clustering patterns relative to a random distribution.
5. **Degree of Connectivity:** Measures how easily cells become connected through their neighbors.

The resulting five-dimensional score vector summarizes the geometric properties of each dataset.

## Data and Preprocessing

The analysis uses both simulated and real scRNA-seq datasets.

Simulated datasets include:

* Clear clusters
* Clear trajectories
* Noisy clusters
* Noisy trajectories

Real datasets include examples such as planaria, mouse bone marrow, and monkey epiblast.

Preprocessing includes density-based downsampling, Min-Max normalization, and PCA dimensionality reduction. The five scores are calculated for each dataset and used for subsequent analysis.

## Geometric Embedding and Classification

The simulated datasets are used to construct a reference geometric landscape using **UMAP**.

Real datasets are then projected into this reference space to compare their geometric properties with those of the simulated data.

Two classification approaches are explored:

* **K-Nearest Neighbors (KNN):** Estimates geometric classes based on local neighborhoods.
* **Random Forest (RF):** Uses the five geometric scores to predict whether a dataset is more cluster-like or trajectory-like.

PCA is also investigated as an alternative embedding method.

## Results and Evaluation

The experiments investigate:

* The separation of cluster-like and trajectory-like simulated datasets.
* The differences between UMAP and PCA projections.
* The influence of dimensionality reduction and preprocessing choices.
* The behavior of KNN and Random Forest classification.
* The mapping of real scRNA-seq datasets onto the simulated geometric landscape.

The results suggest that UMAP provides a more organized visualization of the simulated geometric landscape than PCA, while Random Forest produces more defined classification boundaries.

The framework also highlights that real datasets may exhibit intermediate or ambiguous geometric structures rather than belonging to strictly separated categories.

## Limitations and Future Work

The geometric scores provide information about the structure of the data, but they do not directly establish biological mechanisms or prove that a dataset represents a specific biological process.

Further investigation could explore:

* The impact of batch effects and different types of technical noise.
* The robustness of the scores under alternative preprocessing strategies.
* Additional classification models, including neural networks.
* The reliability of predictions in ambiguous geometric regions.
* Applications to more diverse biological datasets, including immune response and cellular activation.

## Reference

Lim, H. S., & Qiu, P. (2024). *Quantifying the clusterness and trajectoriness of single-cell RNA-seq data.*

PLOS Computational Biology, 20(2), e1011866.

https://doi.org/10.1371/journal.pcbi.1011866

Original implementation:

https://github.com/pqiu/Quantifying_clusterness_trajectoriness
