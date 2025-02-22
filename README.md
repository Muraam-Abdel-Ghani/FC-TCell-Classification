# FC-TCell-Classification
This Repository contains the code and datasets used for training two machine learning models, a Neural Network, and XGBoost model on flowcytometry data for the classification of cell samples into the three main T-Cell types.

# Dataset

The datasets were downloaded from: http://flowrepository.compbio.cs.cmu.edu/experiments/6660/download_ziped_files

The data extraction and annotation details are presented in our paper. All the datasets were saved in .csv file format. Due to file size limitations on Github, the data was uploaded to Google Drive and is accessible through the following link:

https://drive.google.com/drive/folders/1-2cFJA0_V2zlYPBrw7WY7TcQSpLq9v-h?usp=drive_link

For training, dataset1Normal.csv and dataset1Patient.csv were used. The rest of the files were used for the external dataset validation.

# Repo Directories
There are two main directories in this repo:

The "code" dir contains the main Jupyter notebook with the training, testing, and external dataset validation. Google Colab was used for creating and running this notebook. All paths are thus assuming that the files are uploaded to the Colab session. Simply edit the paths to your local filepath if you desire to run the notebook elsewhere.

The "models" dir contains the trained models that can be easily loaded for testing the code without the need to retrain the models. The model files include: 

1- best_model_nn.keras: This is the neural network model used. The model can be loaded using: 
```
nn_model = tf.keras.models.load_model("best_model_nn.keras")
```

2- xgboost_best.pkl: This is the XGBoost model. It was saved in pickle (.pkl) format. To load it, use: 

```
with open("xgboost_best.pkl", "rb") as f:
    xgboost_model = load(f)
```

3- yeo_johnson_transformer.pkl: This is the Yeo Johnson Transformer object. It is necessary to apply this transformer on the loaded data before passing the data into the model as it applies the Yeo Johnson transformation which normalises the data for model use. To load the transformer use:

```
  with open("yeo_johnson_transformer.pkl", "rb") as f:
    yeo_johnson_transformer = load(f)
```
  To apply it on the loaded data, use: 

```
X_transformed = yeo_johnson_transformer.transform(X)  # where X is the loaded data
```

# Running this code:

To start using this code:

1- Download or clone the repository. 

2- The code assumes all data is uploaded to the root directory of the Google Colab session. If you wish to run the notebook locally, ensure that the file paths are updated in the code to match the file paths in your local directory.

3- For reference, the code was run with the following libraries and corresponding versions:

```
  pandas: v(2.2.2)
  tensorflow: v(2.18.0)
  numpy: v(1.26.4)
  matplotlib: v(3.10.0)
  sklearn: v(1.6.1)
  imblearn: v(0.13.0)
```

# Citing this work

If you would like to build or do research based on the findings and published code in this work, please cite it in all publications or research:

```
"Citation of the work once it is published."
```
