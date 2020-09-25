# Python-for-Data-Analysis
#!/usr/bin/env python
# coding: utf-8

# In[2]:


get_ipython().run_line_magic('matplotlib', 'inline')


# In[16]:


import numpy as np
import pandas as pd
from pandas import Series, DataFrame
import matplotlib.pyplot as plt


# In[ ]:





# In[44]:


voiture= pd.read_csv("cars.csv",sep=";")
voiture


# In[45]:


voiture=voiture.drop([0])


# In[46]:


voiture.describe()
voiture["Car"]


# In[47]:


voiture.head(10)


# In[48]:


voiture.tail(10)


# In[56]:


voiture['Cylinders'] = pd.to_numeric(voiture['Cylinders'])


# In[57]:


#What is the average cylinders for different cars ?
voiture.groupby("Car")["Cylinders"].mean()


# In[58]:


voiture['Weight'] = pd.to_numeric(voiture['Weight'])
#Which cars weigh more than 3500 kg?
voiture[voiture['Weight'] > 3500 ]


# In[69]:


#How many cars are from the United States 
voiture[voiture.Origin=="US"].count()


# In[82]:


voiture['Model'] = pd.to_numeric(voiture['Model'])
plt.rcParams['figure.figsize'] = [15, 6] # Taille du graphique en pouces
plt.rcParams['figure.dpi'] = 200 # résolution en points par pouce
voiture[(voiture.Origin=="US")].groupby("Model").Cylinders.sum().plot()


# In[ ]:





# In[74]:


voiture['Model'] = pd.to_numeric(voiture['Model'])


# In[77]:


r=voiture.pivot_table(index='Model',columns='Origin',aggfunc=sum)


# In[78]:


r


# In[81]:


plt.rcParams['figure.figsize'] = [15, 6] # Taille du graphique en pouces
plt.rcParams['figure.dpi'] = 200 # résolution en points par pouce
r.plot(title="Répartition des modèles dans le monde")


# In[93]:


voiture[(voiture.Weight<3000)].groupby("Weight").Cylinders.sum().plot()


# In[ ]:
