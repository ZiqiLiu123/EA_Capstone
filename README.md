# EA_Capstone
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
import csv
data = pd.read_csv(r"D:\Studies\Pace\Courses\2021_fall\CS668\Project\Data\national_data\national_data_clean.csv",'r',delimiter=",")
data.shape
data.head()
data.describe()
data.dropna(axis=0,how='any')
print(data.columns.values)
from statsmodels.formula.api import ols
lm = ols('natural_growth_rate ~ GDP100million_yuan + education_no_schooling + education_primary_school + education_junior_secondary_school + education_senior_secondary_school + education_college_and_higher + health_care_institutions + average_house_price', data=data).fit()
lm.summary()
lm.params
