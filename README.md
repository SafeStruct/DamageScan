# DamageScan
------------
Machine Learning models for damage assessment from very high-resolution SAR imagery.

You can access the reference paper for **ML models** from **[here](https://doi.org/10.1007/s10518-024-01877-1).**

## Install the dependencies
```bash
# in shell
# clone the repo and navigate into
git clone https://github.com/SafeStruct/damagescan.git
cd damagescan

# create a new virtual environment with conda
conda create --name damagescan --yes python=3.8

# activate the environment
conda activate damagescan

# and finally install the dependecies to load the models
pip install -e .
```

## Loading the models

```python
# in python
import joblib
import json

# load the catalog information
models = json.load(open('models.json','r'))

# select the desired model. Check related paper 
ml_model = joblib.load(models.get("A")) # models are tagged from A to E


prediction = ml_model.predict(
    # the dataset to predict on
    # the given data set should be a DataFrame with the same structure as the training data
    # the headers of the prediction data should be same with the following field names:

    # Ten textural features needed
    # contrast, dissimilarity, homogeneity, angular second moment (ASM), 
    # energy, maximum probability (MAX), entropy, mean, variance, and correlation
    
    # 'mean_0', 'stdev_0', 'min_0', 'max_0', 'mean_1', 'stdev_1', 'min_1', 'max_1',
    # 'mean_2', 'stdev_2', 'min_2', 'max_2', 'mean_3', 'stdev_3', 'min_3', 'max_3',
    # 'mean_4', 'stdev_4', 'min_4', 'max_4', 'mean_5', 'stdev_5', 'min_5', 'max_5', 
    # 'mean_6', 'stdev_6', 'min_6', 'max_6', 'mean_7', 'stdev_7', 'min_7', 'max_7',
    # 'mean_8', 'stdev_8', 'min_8', 'max_8', 'mean_9', 'stdev_9', 'min_9', 'max_9', 
    # 'mean_10', 'stdev_10', 'min_10', 'max_10'
)
```