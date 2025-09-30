# Genetic Algorithm for Customer Purchase Prediction

This repository contains an implementation of a Genetic Algorithm (GA) for predicting customer purchase behavior and optimizing product-mix strategies. The GA results are compared with K-Means clustering to evaluate clustering quality and the potential business value of GA-driven recommendations.



---

## Project overview

The main goals of this project are:

- Use a Genetic Algorithm to search for near-optimal product allocation / recommendation strategies that maximize business profit.
- Compare the GA approach against a baseline K-Means clustering method for customer segmentation and strategy evaluation.
- Preprocess and analyze the `Sales Superstore` dataset to extract relevant features and remove noise.
- Visualize clustering results and compare performance metrics (e.g., average profit per cluster, intra-cluster dispersion).


## Repository structure

```
├── description.pdf     # Project report (Persian)
├── Untitled-1.ipynb        # Jupyter notebook with code and visualizations
├── dataset                  #  dataset files
├── requirements.txt        # Python dependencies
└── README.md               # This file
```


## Dependencies

Recommended Python packages (additions may exist in `requirements.txt`):

- Python 3.8+
- numpy
- pandas
- scikit-learn
- matplotlib
- seaborn (optional, used for nicer plots)

Install with:

```bash
pip install -r requirements.txt
```


## How to run

1. Clone the repository:

```bash
git clone https://github.com/username/repo-name.git
cd repo-name
```

2. Prepare the dataset: place the `Superstore` CSV file into the `dataset/` folder ). The dataset used in the project is available on Kaggle: `Superstore`.

3. Launch the Jupyter Notebook:

```bash
jupyter notebook Untitled-1.ipynb
```

4. Run the notebook cells from top to bottom. The notebook includes: data loading, preprocessing, GA implementation, K-Means baseline, evaluation, and plotting.


## Implementation details

Key parts implemented in the notebook:

1. **Data preprocessing**
   - Remove duplicates and irrelevant columns
   - Handle missing values
   - Convert date columns into `day`, `month`, `year`
   - Numerical encoding (label encoding / one-hot encoding)
   - Outlier detection and removal (boxplots)

2. **Genetic Algorithm**
   - Representation: each chromosome encodes a product combination / allocation strategy (binary or integer vector depending on design)
   - Population initialization: random chromosomes
   - Fitness function: estimated profit (sum of predicted or historical profits per chosen product mix)
   - Selection: rank-based / tournament selection
   - Crossover: single-point crossover
   - Mutation: bit-flip or small random perturbation
   - Iterative evolution until convergence or max generations

3. **K-Means baseline**
   - Standard K-Means clustering on customer features
   - Use elbow method to discover a reasonable number of clusters
   - Compute cluster-level metrics for comparison with GA results

4. **Evaluation & Visualization**
   - Profit per cluster or per strategy
   - Cluster dispersion (inertia), silhouette score
   - Visualizations: cluster scatter plots, GA fitness curve over generations, bar charts of profit by cluster


## Results summary

- The Genetic Algorithm is able to propose product mixes that increase average profit for many clusters compared to a simple baseline.
- K-Means provides interpretable segments but may not directly optimize profit as GA does.
- Results (plots and numeric comparisons) are available inside the notebook and the project report (PDF).


## Notes & tips

- The GA is a stochastic optimizer — rerunning with different random seeds can produce different solutions. Save seeds or the best chromosome to reproduce results.
- Carefully tune GA hyperparameters (population size, crossover/mutation rates, number of generations) for stability and runtime trade-offs.
- Large datasets may require subsampling or vectorized fitness evaluation for performance.


## License

This project is provided for educational purposes. Feel free to reuse and adapt the code — attribution appreciated.
