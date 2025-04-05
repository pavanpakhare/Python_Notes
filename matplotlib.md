# **Matplotlib Tutorial**

Matplotlib is the most widely used Python library for data visualization. It provides a flexible and powerful way to create **static, interactive, and animated visualizations** in Python. This tutorial covers everything from basic plots to advanced customization.

---

## **Table of Contents**
1. [Installation](#installation)
2. [Basic Plots](#basic-plots)
   - Line Plot
   - Bar Plot
   - Scatter Plot
   - Histogram
   - Pie Chart
3. [Customizing Plots](#customizing-plots)
   - Titles, Labels, and Legends
   - Colors, Markers, and Line Styles
   - Grids and Subplots
4. [Advanced Plots](#advanced-plots)
   - Box Plot
   - Violin Plot
   - Heatmap
   - 3D Plotting
5. [Saving Plots](#saving-plots)
6. [Interactive Plots](#interactive-plots)

---

## **1. Installation**
To install Matplotlib, run:
```bash
pip install matplotlib
```
For Anaconda users:
```bash
conda install matplotlib
```

---

## **2. Basic Plots**
### **Line Plot**
```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]

plt.plot(x, y)
plt.title("Simple Line Plot")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.show()
```
![Line Plot](https://matplotlib.org/stable/_images/sphx_glr_pyplot_001.png)

### **Bar Plot**
```python
categories = ['A', 'B', 'C', 'D']
values = [15, 20, 12, 18]

plt.bar(categories, values)
plt.title("Bar Plot")
plt.xlabel("Categories")
plt.ylabel("Values")
plt.show()
```
![Bar Plot](https://matplotlib.org/stable/_images/sphx_glr_barchart_001.png)

### **Scatter Plot**
```python
x = [1, 2, 3, 4, 5]
y = [2, 3, 5, 7, 11]

plt.scatter(x, y, color='red', marker='o')
plt.title("Scatter Plot")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.show()
```
![Scatter Plot](https://matplotlib.org/stable/_images/sphx_glr_scatter_001.png)

### **Histogram**
```python
data = [1, 2, 2, 3, 3, 3, 4, 4, 5]

plt.hist(data, bins=5, color='green')
plt.title("Histogram")
plt.xlabel("Values")
plt.ylabel("Frequency")
plt.show()
```
![Histogram](https://matplotlib.org/stable/_images/sphx_glr_hist_001.png)

### **Pie Chart**
```python
sizes = [30, 20, 25, 25]
labels = ['A', 'B', 'C', 'D']

plt.pie(sizes, labels=labels, autopct='%1.1f%%')
plt.title("Pie Chart")
plt.show()
```
![Pie Chart](https://matplotlib.org/stable/_images/sphx_glr_pie_001.png)

---

## **3. Customizing Plots**
### **Titles, Labels, and Legends**
```python
plt.plot(x, y, label='Linear')
plt.title("Customized Plot")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.legend()
plt.grid(True)
plt.show()
```

### **Colors, Markers, and Line Styles**
```python
plt.plot(x, y, color='red', linestyle='--', marker='o', markersize=8)
plt.show()
```

### **Subplots (Multiple Plots in One Figure)**
```python
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(10, 4))

ax1.plot(x, y, color='blue')
ax1.set_title("Plot 1")

ax2.scatter(x, y, color='red')
ax2.set_title("Plot 2")

plt.tight_layout()
plt.show()
```
![Subplots](https://matplotlib.org/stable/_images/sphx_glr_subplots_001.png)

---

## **4. Advanced Plots**
### **Box Plot (for Statistical Analysis)**
```python
data = [ [1, 2, 3, 4, 5], [2, 3, 4, 5, 6], [1, 3, 5, 7, 9] ]

plt.boxplot(data)
plt.title("Box Plot")
plt.xlabel("Groups")
plt.ylabel("Values")
plt.show()
```
![Box Plot](https://matplotlib.org/stable/_images/sphx_glr_boxplot_001.png)

### **Violin Plot (Box Plot + Distribution)**
```python
plt.violinplot(data)
plt.title("Violin Plot")
plt.show()
```
![Violin Plot](https://matplotlib.org/stable/_images/sphx_glr_violinplot_001.png)

### **Heatmap (for Correlation)**
```python
import numpy as np

matrix = np.random.rand(5, 5)
plt.imshow(matrix, cmap='hot')
plt.colorbar()
plt.title("Heatmap")
plt.show()
```
![Heatmap](https://matplotlib.org/stable/_images/sphx_glr_imshow_001.png)

### **3D Plotting**
```python
from mpl_toolkits.mplot3d import Axes3D

fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')

x = np.random.rand(50)
y = np.random.rand(50)
z = np.random.rand(50)

ax.scatter(x, y, z, c='r', marker='o')
plt.title("3D Scatter Plot")
plt.show()
```
![3D Plot](https://matplotlib.org/stable/_images/sphx_glr_scatter3d_001.png)

---

## **5. Saving Plots**
```python
plt.plot(x, y)
plt.savefig("plot.png", dpi=300, bbox_inches='tight')
```

---

## **6. Interactive Plots (with `%matplotlib notebook`)**
```python
%matplotlib notebook  # For Jupyter Notebook

plt.plot(x, y)
plt.title("Interactive Plot")
plt.show()
```

---

