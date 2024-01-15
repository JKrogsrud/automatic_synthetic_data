# Differentially Private Data Pipeline to generate Synthetic Data

## Description
This project is intended to attempt to create an entire synthetic dataset from any given data set.
Synthetic data is often useful when one wants to allow a user to make their own queries on a data set.
This allows one to bypass the need to release aggregated and differentially private data that can often
come at quite an expense to the privacy budget. My attempt at doing this should work for datasets made
of categorical data, it will have trouble creating synthetic data when one or more of the columns have
numerical data that has a large variety of possibilities. I used my method, described below, to create a
synthetic data set for the adult dataset of equal length. The primary strategy behind my approach is to
create a Bayesian network to analyze the most likely causal relationships between the columns. For this, I
used the bnlearn python library. Using this graph, I pruned it until I had something resembling a tree or a
forest in the case of multiple root nodes. From the edges of the graph, I created multiple two-way marginals 
corresponding to the nodes of each edge. These marginals are made differentially private using the laplace
mechanism and synthetic data is created using these marginals.
