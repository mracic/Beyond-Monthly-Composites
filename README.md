# Beyond Monthly Composites: Maximizing Information Retention in Satellite Image Time Series for Forest Stand Classification

This repository contains the Jupyter notebooks and code used for the analyses presented in the publication: [Beyond Monthly Composites: Maximizing Information Retention in Satellite Image Time Series for Forest Stand Classification]() **[LINK TO BE ADDED]**.

The project explores the classification of forest stands using Sentinel-2 satellite time series data. It compares different machine learning approaches (Random Forest and LightGBM) and data strategies, including:
*   Using raw time series data.
*   Generating and using monthly composites.
*   Training and evaluating models on synthetic time series data.
*   Training models on synthetic time series data and testing on raw data.

## Data

The datasets used in these notebooks are derived from Sentinel-2 imagery and ground reference data. The processed time series data (`.csv` files for each year, both raw and synthetic versions) are publicly available on Zenodo:

**https://doi.org/10.5281/zenodo.15249574**

To run the notebooks, you must first:
1.  Download the data from the Zenodo link above.
2.  Create a directory named `data/` in the root of this repository.
3.  Place all the downloaded `.csv` files (e.g., `2018_raw.csv`, `2018_syn_raw.csv`, `2019_raw.csv`, etc.) inside the `data/` directory.

## Setup

We recommend using Conda to manage the environment and install dependencies.

1.  **Clone the repository (if you haven't already):**
    ```bash
    git clone <repository-url>
    cd <repository-directory>
    ```

2.  **Create a Conda environment:**
    ```bash
    conda create --name forest-class python=3.10 scikit-learn jupyterlab lightgbm pandas numpy tqdm ipywidgets -c conda-forge
    ```

3.  **Activate the environment:**
    ```bash
    conda activate forest-class
    ```

## Usage
After installing the dependencies and placing the data in the `data/` directory, you can run the Jupyter notebooks. Launch JupyterLab from your activated conda environment:

```bash
jupyter lab
```

Navigate to the cloned repository directory within the JupyterLab interface and open the notebooks.

### Notebook Descriptions:

*   **`01_monthly.ipynb`**: Explores forest stand classification using monthly NDVI composites derived from the raw time series. It applies K-Fold cross-validation using both Random Forest and LightGBM classifiers.
*   **`02_syn.ipynb`**: Trains and validates Random Forest and LightGBM models *exclusively* on synthetic time series data, using all available spectral bands. K-Fold cross-validation is used to evaluate performance within the synthetic dataset.
*   **`03_RF_syn_raw.ipynb`**: Trains a Random Forest model on synthetic time series data and tests its performance on the corresponding *raw* time series data for each observation date. It uses a K-Fold structure to split reference points for training/testing.
*   **`04_LightGBM_syn_raw.ipynb`**: Similar to `03_RF_syn_raw.ipynb`, but uses a LightGBM model instead of Random Forest. It trains on synthetic data and tests on raw data.
*   **`05_LightGBM_raw.ipynb`**: Trains and validates a LightGBM model using *only* the raw time series data. It uses K-Fold cross-validation to evaluate performance directly on the raw dataset.

## Results

The notebooks are designed to save classification performance metrics (Weighted F1-Score and Overall Accuracy) into CSV files.

Each notebook will save its output CSV files in `results/` directory (e.g., `results/RF_monthly_metrics.csv`, `results/syn_metrics.csv`, `results/syn_test_raw_rf_results.csv`, etc.).

## Citation

If you use this code or the associated data in your research, please cite our publication:

**[LINK TO BE ADDED]**

## License

This project, including the code within the Jupyter notebooks, is licensed under the **Creative Commons Attribution-NonCommercial 4.0 International License (CC BY-NC 4.0)**.

For the full license text, please see: [https://creativecommons.org/licenses/by-nc/4.0/](https://creativecommons.org/licenses/by-nc/4.0/)