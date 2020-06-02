```py
import numpy as np
my_array=np.array([1,2,3,4])

# 
np.zeros((5))
np.zeros((5,4))

# 
np.ones((5))
np.ones((5,4))

#
np.array([[1,2],[3,4]])

## numpy的数组乘法,a,b都是一个ndarray
a*b  #逐元素相乘
a.dot(b) # 矩阵相乘

## four ways to create an array
a=np.array([0,1,2,3,4])  # any sequence can be passed to np.array
b=np.array((0,1,2,3,4))  # tuple is also allowed
c=np.arange(5)
d=np.linspace(0,2*np.pi,5)
```