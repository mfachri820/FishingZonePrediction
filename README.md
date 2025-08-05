# Predicting Yellowfin Tuna Fishing Zones with RandomForest

This project uses a Jupyter Notebook (`cluster_model.ipynb`) to identify potential fishing zones for **Yellowfin Tuna** in the waters of the Philippines.

The analysis is based on correlating gridded oceanographic satellite data with **apparent fishing activity** from Global Fishing Watch to build a predictive model on a cell-by-cell basis.

The notebook performs the following key tasks:
1.  **Loads Gridded Datasets**: Reads oceanographic data (NetCDF files) and apparent fishing activity data, which are already aligned on a geographic grid.
2.  **Data Aggregation**: Processes and aligns all data into a quarterly time series for each individual grid cell.
3.  **Predictive Modeling**: Trains and evaluates several machine learning models to predict habitat suitability, with **RandomForest** being identified as the best-performing model.
4.  **Clustering & Visualization**: Applies clustering to the high-potential grid cells identified by the model and generates maps to visualize the results as coherent zones.

## Modeling Approach

The core of this project is a supervised machine learning model that operates on a grid, with each cell representing an independent data point.
- **Features:** Quarterly aggregated oceanographic data (SST, Chlorophyll-a, SLA, etc.) for each grid cell.
- **Target Variable:** Apparent fishing activity (e.g., total fishing hours per quarter) within each grid cell.
- **Best Model:** After experimentation, a **RandomForest** model was selected for its high accuracy and ability to handle complex interactions between the environmental variables.

## Setup and Installation

To run this notebook, you will need to set up a Python environment and install the required packages.

1.  **Create a Virtual Environment:**
    ```bash
    python -m venv .venv
    ```

2.  **Activate the Environment:**
    * **Windows PowerShell:**
        ```powershell
        .\.venv\Scripts\Activate.ps1
        ```
    * **macOS / Linux:**
        ```bash
        source .venv/bin/activate
        ```

3.  **Install Dependencies:**
    This project requires several data science and geospatial libraries. Install them from the `requirements.txt` file.
    ```bash
    pip install -r requirements.txt
    ```
    *(Note: If a `requirements.txt` file is not available, you will need to install `jupyterlab`, `pandas`, `geopandas`, `xarray`, `rioxarray`, `matplotlib`, and `scikit-learn` manually).*

## How to Use

1.  **Place Data:** Ensure your NetCDF (`.nc`) and fishing activity (`.csv`) data are placed in the correct directories as referenced within the notebook.

2.  **Launch Jupyter Lab:**
    With your environment activated, run the following command in your terminal:
    ```bash
    jupyter lab
    ```

3.  **Run the Notebook:**
    Open `cluster_model.ipynb` in Jupyter Lab and run the cells sequentially to replicate the analysis and generate the final prediction maps.