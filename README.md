## Carbon-efficient reaction optimization of nonoxidative direct methane conversion based on the hydrocarbon cofeeding effect 

# 1. Requirements

Our code has been tested within a virtual environment, utilizing the following libraries:

pandas (version 1.4.2)
joblib (version 1.1.0)
xgboost (version 1.3.1)
numpy (version 1.22.3)
sklearn (version 1.0.2)
We recommend using our code with libraries that match our specified versions or higher.

# 2. Usage Descriptions for Our Codes:
Below are detailed descriptions of the procedures involved in using our codes:

A. Optimization of Reaction Parameters and Prediction of Reaction Performance at the Integrated Reactor System (sample_ABC_XGB.ipynb)

(1) Data Sorting
- To ensure the reliability of the ML model, the input data for ML model construction was reorganized by varying the random seed number.
- Target parameters for optimization were selected by assigning specific values to the variable "nTarget". For example, nTarget = 10 was used for optimizing hydrocarbon yield, while values ranging from 11 to 16 were assigned to nTarget for optimizing parameters H1 to H6, respectively.

(2) XGBoost Regression
- The ML regression model was constructed using XGBoost based on the experimental data reorganized in the "Data Sorting" step.
- The constructed ML regression model is saved as a "predictor.*.sav" file.

(3) ABC Optimization
- Multidimensional reaction parameters were optimized using metaheuristic optimization with an artificial bee colony (ABC) algorithm to achieve the optimal target value.
- To run the ABC optimization, both "artificial_bee_colony.py" and "predictor.*.sav" files are required.
- The optimized reaction conditions are listed in the created "ABC.sol.*.csv" file.

(4) From Optimized Results to XGBoost Prediction
- Based on the reaction parameters listed in the "ABC.sol.*.csv" file, reaction performances are predicted using the constructed ML model "predictor.ABC*.sav," and the predicted values using XGBoost models are provided in the "ABC.results*.csv" files.

B. Prediction of Reaction Performance for the 1st Reactor at the Given Reaction Parameter (sample_ABC_XGB_Zone1.ipynb)

(1) ML Model Construction
- An ML model was constructed using only experimental data from the 1st reactor using the "sample_ABC_XGB.ipynb" file.

(2) From Optimized Results to XGBoost Prediction
- The suggested reaction parameters at the integrated reactor system were rescaled using data from the 1st reactor only.
- The previously constructed ML model was used to predict the reaction performance at the rescaled reaction parameters.
