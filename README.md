### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program:
```python
import pandas as pd
df=pd.read_csv('/content/clustervisitor.csv')
df
```
```
cluster={"Young":(df['Age']<=30),"Middle":(df['Age']>30)&(df['Age']<=50),"Old":(df['Age']>50)}
for group,condition in cluster.items():
  visitors=df[condition]
  print(f"The visitors on {group} are :")
  print(visitors)
  print(len(visitors))
  print("count=",len(visitors))
```
```
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
df1=df['Age']
df2=df['Income']
df3=pd.concat([df1,df2],axis=1)
s=StandardScaler()
newdf=s.fit_transform(df3)
k=KMeans(n_clusters=3,random_state=42)
df3['cluster']=k.fit_predict(newdf)
df3
```
### Output:
<img width="572" height="647" alt="image" src="https://github.com/user-attachments/assets/49e22e89-43df-47d0-8368-4cec3d65d3f3" />

<img width="328" height="765" alt="image" src="https://github.com/user-attachments/assets/829c7f37-3400-4519-ad55-67381d6d4996" />

### Visualization:
```python
import matplotlib.pyplot as plt
counts = [len(df[cluster[label]]) for label in ['Young', 'Middle', 'Old']]
age_group_labels = ['Young', 'Middle', 'Old']

plt.figure(figsize=(8, 6))
plt.bar(age_group_labels, counts, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
```
import matplotlib.pyplot as plt
plt.figure(figsize=(10, 6))
scatter = plt.scatter(df3['Age'], df3['Income'], c=df3['cluster'], cmap='viridis', s=100, edgecolors='k')
plt.xlabel('Age ')
plt.ylabel('Income')
plt.title('Visitor Distribution Across Age Group')
plt.colorbar(scatter, label='Cluster')
plt.show()
```
### Output:
<img width="714" height="457" alt="image" src="https://github.com/user-attachments/assets/5fae2018-04de-409b-83e1-33a14e739ba5" /
<img width="719" height="454" alt="image" src="https://github.com/user-attachments/assets/ca721144-7d5a-45f8-ba1a-3b66056dc74f" />


### Result:
Thus, cluster and Visitor Segmentation for Navigation patterns have been implemented successfully.
