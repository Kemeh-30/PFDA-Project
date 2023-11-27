# PFDA-Project 1

 This readme file  covers the key aspects of my  code, including what it does, how to set it up, and an overview of the analysis performed.
 
 PROJECT QUESTION
 
 create a data set by simulating a real-world phenomenon of
your choosing. You may pick any phenomenon you wish – you might pick one that is
of interest to you in your personal or professional life. Then, rather than collect data
related to the phenomenon, you should model and synthesise such data using Python.
We suggest you use the numpy.random package for this purpose.
Specifically, in this project you should:


• Choose a real-world phenomenon that can be measured and for which you could
   collect at least one-hundred data points across at least four different variables.
• Investigate the types of variables involved, their likely distributions, and their
   relationships with each other.
• Synthesise/simulate a data set as closely matching their properties as possible.
• Detail your research and implement the simulation in a Jupyter notebook – the
  data set itself can simply be displayed in an output cell within the notebook.
   Note that this project is about simulation – you must synthesise a data set. Some
   students may already have some real-world data sets in their own files. It is okay to
   base your synthesised data set on these should you wish (please reference it if you do),
   but the main task in this project is to create a synthesised data set. The next section
   gives an example project idea.

THE DATA AND PEHENOMENON I DECIDED TO WORK ON
Red Wine Quality Analysis
*lINK OF WHERE I GOT THE DATA FROM (https://www.kaggle.com/datasets/uciml/red-wine-quality-cortez-et-al-2009)


EXPLANATION OF THE CODE AND HOW THEY WORK
 
 This repository contains a Python script for analyzing red wine quality using the pandas, seaborn, and matplotlib libraries. The script reads a dataset (red-winequality.csv), explores its characteristics, visualizes relationships between variables, and generates synthetic data for further analysis.
 
 Getting Started
Prerequisites
Python installed (version 3.x)
Required libraries: numpy, pandas, seaborn, matplotlib
Installation

pip install numpy pandas seaborn matplotlib

1:Clone the repository:

git clone https://github.com/your_username/red-wine-analysis.git
cd red-wine-analysis

2:Run the script:


python wine_analysis.py


3:Overview of the Code
Data Loading and Exploration
The script loads the red wine quality dataset using pandas and displays the first few rows, summary statistics, and data types.

import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

data = pd.read_csv("red-winequality.csv")
data.head()
data.describe()
data.dtypes

4:Pair Plots and Correlation Heatmap
Visualizes relationships between variables and displays a correlation heatmap.

sns.pairplot(data, hue='quality')
realdata_cor = data.corr(method='pearson')
sns.heatmap(realdata_cor, annot=True)




5:Variable Selection and Correlation Analysis
Selects specific variables and performs correlation analysis.

sel_var = data.drop(columns=['volatile acidity', 'chlorides', 'free sulfur dioxide', 'total sulfur dioxide', 'density', 'pH'])
seldata_cor = sel_var.corr(method='pearson')
sns.heatmap(seldata_cor, annot=True)
sns.pairplot(sel_var, hue='quality')


6:Sampling and Distribution Plots
Generates a sample dataset and visualizes the distribution of selected variables.


sample_df = sel_var.sample(n=100)
sns.distplot(sample_df['fixed acidity'])
# Repeat for other variables



7:Synthetic Dataset Generation
Creates a synthetic dataset with random values for analysis purposes.



# Synthetic dataset generation
np.random.seed(42)
# ... (variable generation)
synthetic_data = np.column_stack((var_fc, var_ca, var_rs, var_sup, var_ach, var_qul))
syn_data = pd.DataFrame(synthetic_data, columns=['var_fc', 'var_ca', 'var_rs', 'var_sup', 'var_ach', 'var_qul'])
print("Synthetic Dataset:")
print(syn_data)


DATA SOURCE
A partial list of where these datasets originate from.

1:https://stackoverflow.com/questions/14827650/pyplot-scatter-plot-marker-size
2:https://matplotlib.org/stable/gallery/statistics/barchart_demo.html#sphx-glr-gallery-statistics-barchart-demo-py
3:https://numpy.org/doc/stable/reference/random/generated/numpy.random.uniform.html
4:https://www.kaggle.com/datasets/uciml/red-wine-quality-cortez-et-al-2009/data