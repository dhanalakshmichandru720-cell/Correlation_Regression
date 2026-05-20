# Correlation and regression for data analysis
# Aim : 

To analyse given data using coeffificient of correlation and regression line
![image](https://user-images.githubusercontent.com/104613195/168224136-d6b64e64-7d3d-4775-9337-c8f96fe41f2d.png)


# Software required :  
Python

# Theory:

Correlation describes the strength of an association between two variables, and is completely symmetrical, the correlation between A and B is the same as the correlation between B and A. However, if the two variables are related it means that when one changes by a certain amount the other changes on an average by a certain amount.  

If y represents the dependent variable and x the independent variable, this relationship is described as the regression of y on x. The relationship can be represented by a simple equation called the regression equation. The regression equation representing how much y changes with any given change of x can be used to construct a regression line on a scatter diagram, and in the simplest case this is assumed to be a straight line.

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
# Result
<img width="779" height="596" alt="Screenshot 2026-05-20 082805" src="https://github.com/user-attachments/assets/04504768-067f-4cf8-8683-fc810d2af12d" />


# Output 
