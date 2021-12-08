import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
print('National')
import csv
National = pd.read_csv(r"D:\Studies\Pace\Courses\2021_fall\CS668\Project\Data\national_data\national_data.csv",'r',delimiter=",")
National.shape
National
National.dtypes
National.isnull().any()
National = National.interpolate()
National = National.bfill()
National
National.columns
from statsmodels.formula.api import ols
lm_national = ols('birth_rate ~ GDP100million_yuan + education_no_schooling + education_primary_school + education_junior_secondary_school + education_senior_secondary_school + education_college_and_higher + health_care_institutions + average_house_price + total_population', data=National).fit()
lm_national.summary()
lm_national.params
sns.pairplot(National, x_vars=['GDP100million_yuan', 'education_no_schooling',
       'education_primary_school', 'education_junior_secondary_school',
       'education_senior_secondary_school', 'education_college_and_higher',
       'health_care_institutions', 'total_population', 'average_house_price'], y_vars='birth_rate', height=10, aspect=0.8, kind='reg') 

sns.pairplot(National, x_vars=['education_junior_secondary_school','education_senior_secondary_school','health_care_institutions'], y_vars='birth_rate', height=10, aspect=0.8, kind='reg') 

def vif(Shanghai, col_i):
    cols = list(Shanghai.columns)
    cols.remove(col_i)
    cols_noti = cols
    formula = col_i + '~' + '+'.join(cols_noti)
    r2 = ols(formula, Shanghai).fit().rsquared
    return 1. / (1. - r2)
test_data = Shanghai[['College_and_Higher', 'Junior_Secondary_School', 'No_Schooling',
       'Primary_School', 'Senior_Secondary_School',
       'Number_of_Health_Care_Instituti', 'Resident_Population',
       'GRP100millionyuan', 'Average_Price_Residential_Building']]
for i in test_data.columns:
    print(i, '\t', vif(Shanghai=test_data, col_i=i))

plt.figure(figsize = (10, 8 ))
sns.scatterplot( x = 'birth_rate', y = 'average_house_price', hue = 'total_population', size = 'total_population',data = National)
sns.despine(trim=True,left=True);plt.grid(True)

print('Tibet')
Tibet = pd.read_csv(r"D:\Studies\Pace\Courses\2021_fall\CS668\Project\Data\Province_data\Tibet.csv",'r',delimiter=",")
Tibet.shape
Tibet
Tibet.dtypes
Tibet.isnull().any()
Tibet = Tibet.interpolate()
Tibet = Tibet.bfill()
Tibet
Tibet.columns
from statsmodels.formula.api import ols
lm_Tibet = ols('Birth_Rate ~ College_and_Higher + Junior_Secondary_School + No_Schooling + Primary_School + Senior_Secondary_School + Number_of_Health_Care_Instituti + Resident_Population + GRP100millionyuan + Average_Price_Residential_Building', data=Tibet).fit()
lm_Tibet.summary()
lm_Tibet.params

print('Ningxia')
Ningxia = pd.read_csv(r"D:\Studies\Pace\Courses\2021_fall\CS668\Project\Data\Province_data\Ningxia.csv",'r',delimiter=",")
Ningxia.shape
Ningxia
Ningxia.dtypes
Ningxia.isnull().any()
Ningxia = Ningxia.interpolate()
Ningxia = Ningxia.bfill()
Ningxia
Ningxia.columns
from statsmodels.formula.api import ols
lm_Ningxia = ols('Birth_Rate ~ College_and_Higher + Junior_Secondary_School + No_Schooling + Primary_School + Senior_Secondary_School + Number_of_Health_Care_Instituti + Resident_Population + GRP100millionyuan + Average_Price_Residential_Building', data=Ningxia).fit()
lm_Ningxia.summary()
lm_Ningxia.params


print('Qinghai')
Qinghai = pd.read_csv(r"D:\Studies\Pace\Courses\2021_fall\CS668\Project\Data\Province_data\Qinghai.csv",'r',delimiter=",")
Qinghai.shape
Qinghai
Qinghai.dtypes
Qinghai.isnull().any()
Qinghai = Qinghai.interpolate()
Qinghai = Qinghai.bfill()
Qinghai
Qinghai.columns
from statsmodels.formula.api import ols
lm_Qinghai = ols('Birth_Rate ~ College_and_Higher + Junior_Secondary_School + No_Schooling + Primary_School + Senior_Secondary_School + Number_of_Health_Care_Instituti + Resident_Population + GRP100millionyuan + Average_Price_Residential_Building', data=Qinghai).fit()
lm_Qinghai.summary()
lm_Qinghai.params

print('Xinjiang')
Xinjiang = pd.read_csv(r"D:\Studies\Pace\Courses\2021_fall\CS668\Project\Data\Province_data\Xinjiang.csv",'r',delimiter=",")
Xinjiang.shape
Xinjiang
Xinjiang.dtypes
Xinjiang.isnull().any()
Xinjiang = Xinjiang.interpolate()
Xinjiang = Xinjiang.bfill()
Xinjiang
Xinjiang.columns
from statsmodels.formula.api import ols
lm_Xinjiang = ols('Birth_Rate ~ College_and_Higher + Junior_Secondary_School + No_Schooling + Primary_School + Senior_Secondary_School + Number_of_Health_Care_Instituti + Resident_Population + GRP100millionyuan + Average_Price_Residential_Building', data=Xinjiang).fit()
lm_Xinjiang.summary()
lm_Xinjiang.params

print('Hainan')Hainan = pd.read_csv(r"D:\Studies\Pace\Courses\2021_fall\CS668\Project\Data\Province_data\Hainan.csv",'r',delimiter=",")
Hainan.shape
Hainan
Hainan.dtypes
Hainan.isnull().any()
Hainan = Hainan.interpolate()
Hainan = Hainan.bfill()
Hainan
Hainan.columns
from statsmodels.formula.api import ols
lm_Hainan = ols('Birth_Rate ~ College_and_Higher + Junior_Secondary_School + No_Schooling + Primary_School + Senior_Secondary_School + Number_of_Health_Care_Instituti + Resident_Population + GRP100millionyuan + Average_Price_Residential_Building', data=Hainan).fit()
lm_Hainan.summary()
lm_Hainan.params

print('Heilongjiang')
Heilongjiang = pd.read_csv(r"D:\Studies\Pace\Courses\2021_fall\CS668\Project\Data\Province_data\Heilongjiang.csv",'r',delimiter=",")
Heilongjiang.shape
Heilongjiang
Heilongjiang.dtypes
Heilongjiang.isnull().any()
Heilongjiang = Heilongjiang.interpolate()
Heilongjiang = Heilongjiang.bfill()
Heilongjiang
Heilongjiang.columns
from statsmodels.formula.api import ols
lm_Heilongjiang = ols('Birth_Rate ~ College_and_Higher + Junior_Secondary_School + No_Schooling + Primary_School + Senior_Secondary_School + Number_of_Health_Care_Instituti + Resident_Population + GRP100millionyuan + Average_Price_Residential_Building', data=Heilongjiang).fit()
lm_Heilongjiang.summary()
lm_Heilongjiang.params

print('Jilin')
Jilin = pd.read_csv(r"D:\Studies\Pace\Courses\2021_fall\CS668\Project\Data\Province_data\Jilin.csv",'r',delimiter=",")
Jilin.shape
Jilin
Jilin.dtypes
Jilin.isnull().any()
Jilin = Jilin.interpolate()
Jilin = Jilin.bfill()
Jilin
Jilin.columns
from statsmodels.formula.api import ols
lm_Jilin = ols('Birth_Rate ~ College_and_Higher + Junior_Secondary_School + No_Schooling + Primary_School + Senior_Secondary_School + Number_of_Health_Care_Instituti + Resident_Population + GRP100millionyuan + Average_Price_Residential_Building', data=Jilin).fit()
lm_Jilin.summary()
lm_Jilin.params

print('Liaoning')
Liaoning = pd.read_csv(r"D:\Studies\Pace\Courses\2021_fall\CS668\Project\Data\Province_data\Liaoning.csv",'r',delimiter=",")
Liaoning.shape
Liaoning
Liaoning.dtypes
Liaoning.isnull().any()
Liaoning = Liaoning.interpolate()
Liaoning = Liaoning.bfill()
Liaoning
Liaoning.columns
from statsmodels.formula.api import ols
lm_Liaoning = ols('Birth_Rate ~ College_and_Higher + Junior_Secondary_School + No_Schooling + Primary_School + Senior_Secondary_School + Number_of_Health_Care_Instituti + Resident_Population + GRP100millionyuan + Average_Price_Residential_Building', data=Liaoning).fit()
lm_Liaoning.summary()

lm_Liaoning.params

print('Tianjin')
Tianjin = pd.read_csv(r"D:\Studies\Pace\Courses\2021_fall\CS668\Project\Data\Province_data\Tianjin.csv",'r',delimiter=",")
Tianjin.shape
Tianjin
Tianjin.dtypes
Tianjin.isnull().any()
Tianjin = Tianjin.interpolate()
Tianjin = Tianjin.bfill()
Tianjin
Tianjin.columns
from statsmodels.formula.api import ols
lm_Tianjin = ols('Birth_Rate ~ College_and_Higher + Junior_Secondary_School + No_Schooling + Primary_School + Senior_Secondary_School + Number_of_Health_Care_Instituti + Resident_Population + GRP100millionyuan + Average_Price_Residential_Building', data=Tianjin).fit()
lm_Tianjin.summary()
lm_Tianjin.params

print('Shanghai')
Shanghai = pd.read_csv(r"D:\Studies\Pace\Courses\2021_fall\CS668\Project\Data\Province_data\Shanghai.csv",'r',delimiter=",")
Shanghai.shape
Shanghai
Shanghai.dtypes
Shanghai.isnull().any()
Shanghai = Shanghai.interpolate()
Shanghai = Shanghai.bfill()
Shanghai
Shanghai.columns
from statsmodels.formula.api import ols
lm_Shanghai = ols('Birth_Rate ~ College_and_Higher + Junior_Secondary_School + No_Schooling + Primary_School + Senior_Secondary_School + Number_of_Health_Care_Instituti + Resident_Population + GRP100millionyuan + Average_Price_Residential_Building', data=Shanghai).fit()
lm_Shanghai.summary()
lm_Shanghai.params

def vif(Shanghai, col_i):
    cols = list(Shanghai.columns)
    cols.remove(col_i)
    cols_noti = cols
    formula = col_i + '~' + '+'.join(cols_noti)
    r2 = ols(formula, Shanghai).fit().rsquared
    return 1. / (1. - r2)

test_data = Shanghai[['College_and_Higher', 'Junior_Secondary_School', 'No_Schooling',
       'Primary_School', 'Senior_Secondary_School',
       'Number_of_Health_Care_Instituti', 'Resident_Population',
       'GRP100millionyuan', 'Average_Price_Residential_Building']]
for i in test_data.columns:
    print(i, '\t', vif(Shanghai=test_data, col_i=i))
    
print('Beijing')
Beijing = pd.read_csv(r"D:\Studies\Pace\Courses\2021_fall\CS668\Project\Data\Province_data\Beijing.csv",'r',delimiter=",")
Beijing.shape
Beijing
Beijing.dtypes
Beijing.isnull().any()
Beijing = Beijing.interpolate()
Beijing = Beijing.bfill()
Beijing
Beijing.columns
from statsmodels.formula.api import ols
lm_Beijing = ols('Birth_Rate ~ College_and_Higher + Junior_Secondary_School + No_Schooling + Primary_School + Senior_Secondary_School + Number_of_Health_Care_Instituti + Resident_Population + GRP100millionyuan + Average_Price_Residential_Building', data=Beijing).fit()
lm_Beijing.summary()
lm_Beijing.params
