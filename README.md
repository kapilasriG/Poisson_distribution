DATE : 04/02/2026 
# EXP : 2 Fitting Poisson  distribution
# Aim : 

To fit poisson distribution for the arrival of objects per minute from the feeder

# Software required :  

Python and Visual component tool

# Theory:

The Poisson distribution is the discrete probability distribution of the number of events occurring in a given time period, given the average number of times the event occurs over that time period.

![image](https://user-images.githubusercontent.com/104613195/166248326-fd042076-8b0b-40c4-8b11-1d8e8fcb74db.png)

 Conditions for Poisson Distribution:

1. An event can occur any number of times during a time period.
2. Events occur independently. I
3. The rate of occurrence is constant.
4. The probability of an event occurring is proportional to the length of the time period. 
 
# Procedure :

![image](https://user-images.githubusercontent.com/104613195/166251988-d0c53205-6080-4f7b-ae4c-398178586637.png)

# Experiment :

![image](https://user-images.githubusercontent.com/103921593/230282876-f4a5afbf-cac1-4648-a1b0-c78840638a8e.png)

# Program :
```
NAME : KAPILASRI G
REG NO : 212225040170

import numpy as np
import math

L=[int(i) for i in input().split()]
N=len(L)
M=max(L)

X=[]
f=[]

for i in range(M+1):
    c=0
    for j in range(N):
        if L[j]==i:
            c=c+1
    f.append(c)
    X.append(i)

Sff=np.sum(f)

p=[]
for i in range(M+1):
    p.append(f[i]/Sff)

mean=np.inner(X,p)

poisson_p=[]
E=[]
xi=[]

print("X P(X=x) Obs.Fr Exp.Fr xi")
print("--------------------------")

for x in range(M+1):
    poisson_p.append(math.exp(-mean)*mean**x/math.factorial(x))
    E.append(poisson_p[x]*Sff)
    xi.append((f[x]-E[x])**2/E[x])
    print("%2.2f %2.3f %4.2f %3.2f %3.2f"%(x,poisson_p[x],f[x],E[x],xi[x]))

print("--------------------------")

cal_chi2_sq=np.sum(xi)
print(f"Calculated value of Chi square is {cal_chi2_sq:.2f}")

table_chi2=11.34   # change according to df
print(f"Table value of chi square at 1% level is {table_chi2:.2f}")

if cal_chi2_sq<table_chi2:
    print("The given data can be fitted in Poisson Distribution at 1% LOS")
else:
    print("The given data cannot be fitted in Poisson Distribution at 1% LOS")
``` 

# Output : 
<img width="818" height="365" alt="Screenshot 2026-03-12 161234" src="https://github.com/user-attachments/assets/9baea932-60b1-4f40-b684-244fd7178fb6" />



# Results

The Poisson distribution is fitted for the objects arrived from feeder per minute and the data is tested using Chi-square test. 
 
