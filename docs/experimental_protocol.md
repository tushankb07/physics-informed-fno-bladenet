# Experimental Protocol

To maintain a fair and reliable comparison, and to prevent overfitting the physics regularization term to the test data, the dataset was strictly divided into separate subsets.

## Dataset Partitioning

* **Training Set:** 100 geometries were used to train the network and optimize its weights using the Adam optimizer.
* **Validation Set:** 25 geometries were reserved exclusively for evaluating different candidate values of the physics loss weighting parameter ($\lambda$).
* **Test Set:** 50 geometries were kept completely unseen during training and model selection and were used only for the final evaluation.

## Model Selection

A baseline FNO ($\lambda = 0$) and multiple PI-FNO variants were trained with different physics loss weights. The validation set was used to determine the optimal value of $\lambda$, with the objective of maximizing continuity improvement while avoiding an unacceptable reduction in overall $L_2$ accuracy.

Based on this evaluation, **$\lambda = 1.0$** was selected as the optimal physics weight for the dataset.

## Held-Out Evaluation

After the model configurations were finalized, the baseline FNO and the selected PI-FNO ($\lambda = 1.0$) were evaluated once on the 50 previously unseen test geometries. These results constitute the definitive performance metrics reported in this project.

## Low-Data Analysis

To investigate the effect of physics-based constraints under limited training data, an additional experiment was conducted using only 25 training geometries. The experiment was repeated using three different random seeds to verify that the observed accuracy penalty of approximately **0.00175** was consistent and not caused by statistical variation.
