# **Pandas Tutorial**

Pandas is a powerful Python library for data manipulation and analysis. It provides data structures like **Series** (1D) and **DataFrames** (2D) that make working with structured data easy.



## **1. Installation**
To install Pandas, run:
```bash
pip install pandas
```
For Anaconda users:
```bash
conda install pandas
```

---

## **2. Pandas Data Structures**
### **Series**
A **Series** is a one-dimensional labeled array.

```python
import pandas as pd

# Create a Series
data = pd.Series([1, 2, 3, 4], index=['a', 'b', 'c', 'd'])
print(data)
```
Output:
```
a    1
b    2
c    3
d    4
dtype: int64
```

### **DataFrame**
A **DataFrame** is a 2D labeled data structure (like a table).

```python
data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'City': ['NY', 'LA', 'SF']
}

df = pd.DataFrame(data)
print(df)
```
Output:
```
      Name  Age City
0    Alice   25   NY
1      Bob   30   LA
2  Charlie   35   SF
```

---

## **3. Reading & Writing Data**
### **Reading Data**
```python
# Read CSV
df = pd.read_csv('data.csv')

# Read Excel
df = pd.read_excel('data.xlsx')

# Read from SQL
import sqlite3
conn = sqlite3.connect('database.db')
df = pd.read_sql('SELECT * FROM table', conn)
```

### **Writing Data**
```python
# Save to CSV
df.to_csv('output.csv', index=False)

# Save to Excel
df.to_excel('output.xlsx', index=False)
```

---

## **4. Data Selection & Indexing**
### **Selecting Columns**
```python
df['Name']  # Single column
df[['Name', 'Age']]  # Multiple columns
```

### **Selecting Rows**
```python
df.loc[0]  # By label
df.iloc[0]  # By position
df[df['Age'] > 25]  # Conditional selection
```

### **Slicing**
```python
df[1:3]  # Rows 1 to 2
```

---

## **5. Data Cleaning**
### **Handling Missing Data**
```python
df.dropna()  # Drop rows with missing values
df.fillna(0)  # Fill missing values with 0
df.isna()  # Check for missing values
```

### **Removing Duplicates**
```python
df.drop_duplicates()
```

### **Renaming Columns**
```python
df.rename(columns={'Name': 'FullName'}, inplace=True)
```

---

## **6. Data Manipulation**
### **Adding a New Column**
```python
df['Salary'] = [50000, 60000, 70000]
```

### **Applying Functions**
```python
df['Age'] = df['Age'].apply(lambda x: x + 1)
```

### **Sorting**
```python
df.sort_values('Age', ascending=False)
```

---

## **7. Grouping & Aggregation**
```python
# Group by 'City' and calculate mean age
df.groupby('City')['Age'].mean()

# Multiple aggregations
df.groupby('City').agg({'Age': ['mean', 'max'], 'Salary': 'sum'})
```

---

## **8. Merging & Joining DataFrames**
### **Concatenation**
```python
pd.concat([df1, df2], axis=0)  # Stack vertically
```

### **Merging (Like SQL JOIN)**
```python
pd.merge(df1, df2, on='key', how='inner')
```

### **Joining**
```python
df1.join(df2, how='left')
```

---

## **9. Time Series Operations**
```python
# Create a time series
dates = pd.date_range('2023-01-01', periods=5)
ts = pd.Series([1, 2, 3, 4, 5], index=dates)

# Resampling (daily to monthly)
ts.resample('M').mean()
```

---

## **10. Visualization with Pandas**
Pandas integrates with Matplotlib for quick plotting.

```python
df.plot(kind='bar', x='Name', y='Age')
df['Age'].plot(kind='hist')
```
