# demo code
```py
import matplotlib.pyplot as plt
import numpy as np
%matplotlib inline
A = np.arange(1,5) 
B = A**2
C = A**3
fig, ax = plt.subplots(figsize=(14,7))
# fig, ax = plt.subplots(2,1,figsize(14,7))
# ax[0].***
# ax[1].***
ax.plot(A,B)
ax.plot(B,A)
ax.set_title('Title',fontsize=18)
ax.set_xlabel('xlabel', fontsize=18,fontfamily = 'sans-serif',fontstyle='italic')
ax.set_ylabel('ylabel', fontsize='x-large',fontstyle='oblique')
ax.legend()

ax.set_aspect('equal') 
ax.minorticks_on() 
ax.set_xlim(0,16) 
ax.grid(which='minor', axis='both')

ax.xaxis.set_tick_params(rotation=45,labelsize=18,colors='w') 
start, end = ax.get_xlim() 
ax.xaxis.set_ticks(np.arange(start, end,1)) 
ax.yaxis.tick_right()
```



# plt.subplots()

fig, ax = plt.subplots(nrows, ncols)

The two integer arguments to this function specify the number of rows and columns of the subplot grid. The function returns a figure object and a tuple containing axes objects equal to nrows*ncols. Each axes object is accessible by its index. 

```py
import matplotlib.pyplot as plt
fig,a =  plt.subplots(2,2)
import numpy as np
x = np.arange(1,5)
a[0][0].plot(x,x*x)
a[0][0].set_title('square')
a[0][1].plot(x,np.sqrt(x))
a[0][1].set_title('square root')
a[1][0].plot(x,np.exp(x))
a[1][0].set_title('exp')
a[1][1].plot(x,np.log10(x))
a[1][1].set_title('log')
plt.show()
```

前面我们看到只要一个plot()函数就能画出整个图啦，但其实 matplotlib在背后做了很多事。

首先，matplotlib自动创建了一个Figure对象，然后在Figure之上有创建了一个Axes对象，在Axes对象之上才用plot()函数创建了一个Line2D对象。


numpy.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None, axis=0)[source]
Return evenly spaced numbers over a specified interval.

Returns num evenly spaced samples, calculated over the interval [start, stop].

The endpoint of the interval can optionally be excluded.

Changed in version 1.16.0: Non-scalar start and stop are now supported.

# zorder
https://matplotlib.org/3.1.1/gallery/misc/zorder_demo.html

数字越大，显示优先级越高
默认：patch,line,text由低到高

#  animation Funcanimation
https://matplotlib.org/3.2.0/api/_as_gen/matplotlib.animation.FuncAnimation.html#matplotlib.animation.FuncAnimation

# atrist中animated property的功能

# collection

# plt.tight_layout()

调整多个subplot的位置，防止标签相互重叠