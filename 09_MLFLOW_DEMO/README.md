# MLFLOW Experimentation

1 . Setup the environment :

```
conda create --prefix ./env python=3.7 -y
source activate env/
pip install -r requirements.txt
```

2 . run train.py with the default hyperparameters as follows :

```
train.py
```

3 . Pass other values for alpha and l1_ratio by passing them as arguments to train.py :

```
python train.py <alpha> <l1_ratio>
```
ex :
```
python train.py 0.7 0.9
```

mlruns folder will be created and folders for each experimental run will be created .
These folders will contain all the experimental results .

4 . Run : 
```
mlflow ui
```
* This will run a user interface for you and read all data from 'mlruns' folder .
* With this visualization it's very easy to read the experiments .
* Click the link below and see how the UI experiments generate .
    ```
    http://127.0.0.1:5000
    ```

5 . Add your own tracking uri :
```
    ## Add
    mlflow.set_tracking_uri("http://0.0.0.0:1234")
    mlflow.set_experiment("mlflow_demo")

    # with mlflow.start_run():
    with mlflow.start_run(run_name="LRmodel") as mlops_run:
```        

Run the below command :

```
mlflow server \
--backend-store-uri sqlite:///mlflow.db \
--default-artifact-root ./artifacts \
--host 127.0.0.1 -p 1234
```

Below will be the action happens after this :
* artifacts folder will be created and experiments will not be created under ```mlruns```
* ```mlflow.db``` database will be created .

Run train.py from another gitbash command "
```
python train.py
python train.py 0.9 0.9
```