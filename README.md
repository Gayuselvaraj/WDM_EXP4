### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 11/02/2026
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

### Program1:
```python
import pandas as pd
df = pd.read_csv(r"C:\Users\admin\Downloads\clustervisitor.csv")
cluster = {"Young": (df['Age'] <= 30),"Middle": ((df['Age'] > 30) & (df['Age'] <= 50)),"Old": (df['Age'] > 50)}
print(cluster)
count=[]
for g,c in cluster.items():
    visitors=df[c]
    count.append(len(visitors))
    print(f"visitors in {g} Group")
    print(visitors)
    print(count)
import matplotlib.pyplot as plt
plt.figure(figsize=(8, 6))
plt.bar(cluster.keys(),count, color='skyblue')
plt.xlabel('Age Groups')
plt.ylabel('Number of Visitors')
plt.title('Visitor Distribution Across Age Groups')
plt.show()
```
### Output:


<img width="559" height="842" alt="Screenshot 2025-09-19 054745" src="https://github.com/user-attachments/assets/88c0194b-e8fd-41a1-9224-3bb6f94d3eb5" />


<img width="1131" height="690" alt="Screenshot 2025-09-19 053218" src="https://github.com/user-attachments/assets/2dfa4c36-a15c-4580-933c-aae11b2c4c67" />


### Program 2:
```python
df = pd.read_csv(r"C:\Users\admin\Downloads\clustervisitor (Salary).csv")
df1 = df['Age']
df2 = df['Salary']
df3 = pd.concat([df1, df2], axis=1)
df3
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
sc=StandardScaler()
scaleddata=sc.fit_transform(df3)
print(scaleddata)
Kmeans=KMeans(n_clusters=3,random_state=42)
df3['cluster']=Kmeans.fit_predict(df3)
df3
plt.scatter(df3 ['Age'], df3 ['Salary'],c=df3['cluster'])
plt.xlabel("Age")
plt.ylabel("Income in thousands")
plt.show()
```
### Output:

<img width="556" height="838" alt="Screenshot 2025-09-19 054652" src="https://github.com/user-attachments/assets/1715d9d6-e2af-428f-8c70-7ba68dcfb7a8" />


<img width="1020" height="549" alt="Screenshot 2025-09-19 054510" src="https://github.com/user-attachments/assets/a0438212-7d66-48c8-b05c-8fcebcbcd28f" />


### Result:
 Cluster and Visitor Segmentation for Navigation patterns in Python created successfully.
