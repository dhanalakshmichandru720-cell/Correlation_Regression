# Correlation and regression for data analysis
# Procedure :

![image](https://user-images.githubusercontent.com/104613195/168225866-ac8f6610-bdc3-4ac2-a24e-2b24ba08e189.png)

# Program :
```
import numpy as np
import math
import matplotlib.pyplot as plt
#Input x and y values
x = [int(i) for i in input("Enter x values (space separated): ").split()]
y = [int(i) for i in input("Enter y values (space separated): ").split()]
#Check equal length
if len(x) != len(y):
    raise SystemExit("Error: x and y must have the same number of values.")
N = len(x)
#Initialize sums
Sx = Sy = Sxy = Sx2 = Sy2 = 0
#Compute sums
for i in range(N):
    Sx += x[i]
    Sy += y[i]
    Sxy += x[i] * y[i]
    Sx2 += x[i] ** 2
    Sy2 += y[i] ** 2
#Correlation coefficient r
den = math.sqrt((N * Sx2 - Sx ** 2) * (N * Sy2 - Sy ** 2))
if den == 0:
    raise SystemExit("Denominator zero when computing correlation.")
r = (N * Sxy - Sx * Sy) / den
print("The Correlation coefficient is %0.3f" % r)
#Regression coefficient (slope) of Y on X
byx = (N * Sxy - Sx * Sy) / (N * Sx2 - Sx ** 2)
#Means
xmean = Sx / N
ymean = Sy / N
print("The Regression line Y on X is :::")
print("y = %.3f + %.3f (x - %.3f)" % (ymean, byx, xmean))
#Scatter plot
plt.scatter(x, y)
#Regression function
def Reg(xv):
    return ymean + byx * (xv - xmean)
#Regression line plot
x_plot = np.linspace(min(x), max(x), 100)
y_plot = Reg(x_plot)
plt.plot(x_plot, y_plot, 'r')
plt.xlabel('x-data')
plt.ylabel('y-data')
plt.legend(['Regression Line', 'Data Points'])
plt.grid(True)
plt.show()
```
# OUTPUT
<img width="1699" height="648" alt="image" src="https://github.com/user-attachments/assets/46387ef4-38d3-4abd-89da-ff907b8513c8" />

# RESULT
Implemented the correletion and regression for data analayst
