# mlflow_training

In this repo there are two folders present,

    * MLflow-walkthrough
    * mlflow-packaging

# MLflow-walkthrough

* It contains jupyter file from where **MLflow Tracking Server** was initiated.
    ```
    mlflow server --backend-store-uri mlruns/ --default-artifact-root mlruns/ --host localhost --port 5000
    ```
* Screenshots of code has been provided
* Experiment name: `Elasticnet_wine`
* Training file is created here and few runs are compared on the UI
* Screenshot of MLflow UI is also provided
* There was issue with command `mlflow ui`, so directly posted the uri in the page

# mlflow-packaging

* Copied one **conda.yaml** file from **mlruns** from the above folder and pasted in the directory
* Added **data** folder along with **MLproject** which provides it with *entry_points*, along with information on *command' and *parameters*.
* Ran line,
    
    ```
    mlflow run . -P alpha=0.42
    ```
    Which creates the entire artifacts, along with other files, and calculates other metrics.

