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
* After the project structure is setup, I will be deploying `model server` by,
    ```
    mlflow models serve -m mlruns/0/abbedf6fc4ef46319b76baa6c72fe100/artifacts/model/ -h localhost -p 1234
    ```
* For testing use CURL command,
    ```
    curl -X POST -H "Content-Type:application/json; format=pandas-split" --data '{"columns":["alcohol", "chlorides", "citric acid", "density", "fixed acidity", "free sulfur dioxide", "pH", "residual sugar", "sulphates", "total sulfur dioxide", "volatile acidity"],"data":[[12.8, 0.029, 0.48, 0.98, 6.2, 29, 3.33, 1.2, 0.39, 75, 0.66]]}' http://localhost:1234/invocations
    ```
    Curl result: [3.986343895324345] Works!!

    