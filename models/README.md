# Models

This folder contains all the models used in the notebooks.

- gam.pkl : Generalized Additive Model
- log_reg.pkl : Logistic Regression
- mlp.pth : Multi-Layer Perceptron
- mlp_architecture.json : hidden layers and dropout of the MLP, read by `load_mlp`
- unet.pth : U-Net
- xgb.pkl : XGBoost 

They correspond to the final models, trained on the full training dataset.

A lightning hour is an hour with at least 2 flashes in the grid cell, for every model.

## Changes in v0.2.0

The U-Net is unchanged. The other models were retrained after the review of the paper:

- LR, GAM and XGB are trained with the lightning-hour definition above (they were trained on 3 or more flashes in v0.1.0).
- LR is an unpenalised logistic regression fitted with L-BFGS.
- XGB uses depth 3 and 1000 trees, tuned with the same nested cross-validation as the U-Net.
- The MLP hyperparameters (hidden layers, dropout, ...) are tuned in the same way. Load it with `load_mlp(MODELS_PATH, "mlp")`.
