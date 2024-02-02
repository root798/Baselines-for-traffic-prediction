## For Lstm Models, 

run each ipynb files inside "LSTMCODEseparate" folder with name listed, change the file path to the .csv file that you want to run

## For Stgcn Models,

### step 1 preprocess

run "datapreprocess.ipynb" (change the file path in it to .csv files that you want to run), to create "combined_data.npz" file ,then store the "combined_data.npz" to new subfolder inside "data" folder, 

### step 2 prepare data 

run by :

```python
python prepareData.py --config configurations/astgcn.conf
```

The input and output parameters should be set in "configurations/astgcn.conf"

### step 3 train and test models

run by:

```
python train_ASTGCN_r.py --config configurations/astgcn.conf
```



### For Unet Models

Unet is similar to Graph Convolutional  Method, in combining and to be update.

### Bug log

1. Last update of adjacency matrix with real adjacency matrix from data( instead of setting a threshold by oneself), because it should not be optimized as hyperparameters and could give false results that has overstate performance. 
2. For the ASTGCN model and the MSTGCN model, the time slice should be treated without weight, rather than giving weights to month, day and hour respectively. The latter will improve the performance of the model, but it is different from the input information of the LLM model and cannot produce a comparison effect.
3. The calculation methods of MAPE and RMSE are modified to reduce the influence of the minimum value and the excessive value