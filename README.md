# Write-A-Data-Science-Blog-Post
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from IPython import display
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import r2_score, mean_squared_error
import WhatHappened as t
import seaborn as sns
%matplotlib inline

pr= pd.read_csv('./listings.csv')
pr.head()

# What type of homes are used and which once are used the most
# Is there a bias for house or appartment in housing reviews
# on average how many people does the different room type accommodate 

set(pr.columns[np.sum(pr.isnull())>.75])

status_vals = pr['property_type'].value_counts()

status_vals

(status_vals/pr.shape[0]).plot(kind="bar");
plt.title("What type of homes are used and which once are used the most?");

status_vals.head()

# What type of homes are used and which once are used the most I chose the bar because once the count is over, I want to see
# a clear picture of the room types and which onces are used the most, and looking at the graph appartmentsare used the most by a clear win

# Is there a bias for house or appartment in housing reviews
pr.groupby('property_type').mean()['review_scores_location'].sort_values()

# This was a flow up question to the first one and as you can see 
# ther is a clear bias to for Entire Floors and Guest houses but this must
# a part of why is due to the them having less people ranking it.  

# On average how many people does the different room type accommodate 
pr.groupby('property_type').mean()['accommodates'].sort_values()

# This quetion was a way to nirrow the search depending of the person
# i wanted to see the average for houses and appartments and the both were
# around 3
