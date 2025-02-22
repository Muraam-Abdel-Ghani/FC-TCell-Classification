Trained model files and Yeo Johnson Transformer.
The model files include: 

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
