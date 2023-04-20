# EDMSorta: A Machine Learning Electronic Dance Music Subgenre Classification Model
### Author: Diego M. Fernández



<p align="center"><img src="images/EDMSorta Logo.png" width=650></p>

## Project Overview

The classification of Electronic Dance Music (EDM) on a wide scale requires intimate knowledge of hundreds of niche sub-genres. Experts capable of characterizing any EDM song are incredibly difficult to find, so companies like Spotify need alternative methodologies. In this work, I develop a machine learning model that establishes sub-genre classification proof of concept. This model uses a convolutional neural network (CNN) - a deep learning image classification architecture - and a dataset of 300 songs split across three genres: Big Room House, Drum and Bass, and Techno. The model performs with 49% accuracy on this three class dataset, indicating great possibilities going forward, with a larger dataset being the key next step. 

## Navigating This Repository

| Folder/File Name | Contents    |
| ----------- | ----------- |
| data | The dataset breakdown as csvs. Please message the author for full dataset |
| notebooks   | Notebooks developed throughout the project & model grid search results |
| images      | Images used in the presentation and README.md     |
| research_papers  | The research papers this work uses for inspiration |
| venb  | Where the virtual environment parameters are stored in a YAML file |
| high_res_spectrograms_dataset_creation | The notebook creating the dataset and splits |
| model_gridsearch_visualization | The modeling, grid searching, and model visualization notebook |

## Background
Water is the most essential substance for life on Earth, and many people around the world have limited access. In Tanzania, 16 out of 59 million people lack access to safe water, and can be forced to travel long distances (>3 miles on average) to collect water for basic needs every day. 

## Motivation
Gaining a better understanding of where wells need repair can help direct funding and resources to the places of greatest need, thus ensuring people in dire need of water can gain safe access.

## Data Understanding and Business Goals

Nearly half the wells in the Ministry of Water's dataset were completely non-functional or in need of repair.
<p align="center"><img src="plots/training_set_values.png" width=600></p>

Using these labels of *functional*, *non-functional*, or *functional needs repair*, we can develop machine learning models that classify well functionality with some key well features, including location, water level, construction year, and type. 

We have determined three key business goals to help Well Aware:
1. Insert our predictive model into the Well Beyond app to help NGOs better allocate resources for maintenance operations.
2. Determine key features with the highest predictive power on well functionality to decide what data needs to be gathered.
3. Recommend features of wells that may be useful for gaining better predictability of well status.

## Modeling and Evaluation

Model development underwent 8 phases. From the first model to the last, we increased overall accuracy by more than 30%. 

The final model dealt with the imbalanced dataset by oversampling the minority classes (*functional needs repair* and *non-functional*) and using grid search to determine the best hyperparameters for a classification decision tree.

| Model       | Description | Accuracy |
| ----------- | ----------- | ----------- |
| Baseline Model      | Always predicts functional | 54.9% |
| Logistic Regression | Trained on population data | 54.8% |
| Baseline Decision Tree| Using attributes amount_tsh and waterpoint_type | 64.4% |
| Decision Tree with OHE | One hot encoded the categorical attributes | 72.6% |
| Random Forest       | Trained with the top 20 Predictive Attributes | 79.4%|
| Random Forest w/ Undersampling   | Balanced the previous model with undersampling  | 70.7% |
| Random Forest w/ Oversampling    | Balanced the previous model with oversampling   | 84.3% |
| Tuned Random Forest w/ Oversampling | Determined the best hyperparameters for the previous model | 86.4% |

4 key attributes explained nearly 50% of the predictive power of the model:
- Location
- Water Level
- Year
- Well Type

## Conclusion

We recommend that Well Aware look into providing greater monetary incentives for the gathering of additional well data, primarily with regard to the construction year. Some useful additional information that could improve model performance, would be to find out the amount of water extracted from a well each day as well as the date of most recent maintenance. 

Overall, however, our model proves an excellent future feature for the Well Beyond app, with a well functionality predictive power of 86.4%. On top of this, since the focus is in determining whether a well needs repair, the respective classification accuracy of 94.4% shows that this will be incredibly useful to Well Aware.








## Research Inspiration 
- Deep Learning Based EDM Subgenre Classification using Mel-Spectrogram and Tempogram Features
  - Authors: Wei Han Hsu, Bo-Yu Chen, Yi-Hsuan Yang
  - [Paper](https://arxiv.org/abs/2110.08862)
  - [GitHub](https://github.com/ddman1101/EDM-subgenre-classifier)
- Automatic Subgenre Classification in an Electronic Dance Music Taxonomy
  - Authors: Antonio Caparrini, Javier Arroyo, Laura Pérez-Molina, Jaime Sánchez-Hernández
  - [Paper](https://www.tandfonline.com/doi/full/10.1080/09298215.2020.1761399)
  - [GitHub](https://github.com/Caparrini/pyGenreClf)

