# Gaussian Elimination

## AIM:
To write a program to find the solution of a matrix using Gaussian Elimination.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Moodle-Code Runner

## Algorithm
1. Read the order of the matrix and its elements.
2. Convert the matrix into upper triangular form using forward elimination.
3. Calculate the unknown variables using back substitution.
4. Display the values of the unknown variables.

## Program:
```python
'''Program to solve a matrix using Gaussian elimination without partial pivoting.
Developed by: SUJITH A
RegisterNumber: 212224230278
'''

 
import os
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np
import sys

# Reading number of unknowns
n = int(input())

# Making numpy array of n x n+1 size and initializing 
# to zero for storing augmented matrix
a = np.zeros((n,n+1))

# Making numpy array of n size and initializing 
# to zero for storing solution vector
x = np.zeros(n)

# Reading augmented matrix coefficients
for i in range(n):
    for j in range(n+1):
        a[i][j] = float(input())

# Applying Gauss Elimination
for i in range(n):
    if a[i][i] == 0.0:
        sys.exit('Divide by zero detected!')
        
    for j in range(i+1, n):
        ratio = a[j][i]/a[i][i]
        
        for k in range(n+1):
            a[j][k] = a[j][k] - ratio * a[i][k]

# Back Substitution
x[n-1] = a[n-1][n]/a[n-1][n-1]

for i in range(n-2,-1,-1):
    x[i] = a[i][n]
    
    for j in range(i+1,n):
        x[i] = x[i] - a[i][j]*x[j]
    
    x[i] = x[i]/a[i][i]

# Displaying solution
for i in range(n):
    print('X%d = %0.2f' %(i,x[i]), end = ' ')

```
## Output:
<img width="586" height="308" alt="image" src="https://github.com/user-attachments/assets/fa50952e-b599-4bb2-819b-df68a05d742d" />



## Result:
Thus the program to find the solution of a matrix using Gaussian Elimination is written and verified using python programming.

