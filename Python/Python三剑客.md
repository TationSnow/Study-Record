# Python Matplotlib

---

## PyPlot Paint - 绘图

大多数Matplotlib应用程序位于pyplot子模块下，通常以pit别名导入

```python
import matplotlib.pyplot as plt
```



### 1. 绘制x和y点

plot()函数用于在图表中绘制点（标记）

默认情况下，plot()函数从

```python
# 在图中从位置（0,0）到位置（6,255）画一条线
import numpy as np
xpoints = np.array([0,6])
ypoints = np.array([0,255])

plt.plot(xpoints,ypoints)
plt.show()
```



### 2. 无线绘图

仅绘制标记，可以使用快捷字符串符号参数o，这意味着环

```python
plt.plot(xpoints,ypoints,'o')
plt.show()
```



### 3. 多点绘图

可以根据需要绘制任意数量的点，执行保持两个轴上的点数相同即可

```python
xpoints = np.array([1,2,6,8])
ypoints = np.array([3,8,1,10])

plt.plot(xpoints,ypoints)
plt.show()
```



### 4. 默认X点

如果不指定x轴上的点，它们将获得默认值0,1,2,3（等等，取决于y点的长度）



```python
ypoints = np.array([3,8,1,10,7,19])

plt.plot(ypoints)
plt.show()
```





---

## Markers - 标记



### 1. 标记参考

| 标记 | 介绍   |
| ---- | ------ |
| o    | 圆     |
| *    | 星     |
| .    | 点     |
| ,    | 像素   |
| x    | x      |
| X    | 大X    |
| +    | Plus   |
| P    | Plus   |
| s    |        |
| D    | 钻石   |
| d    | 小钻石 |
| p    |        |
| H    |        |
| h    |        |
| v    |        |
| ^    |        |
| <    |        |
| >    |        |
| 1    | 上     |
| 2    | 下     |
| 3    | 左     |
| 4    | 右     |
| \|   | 垂直线 |
| _    | 平行线 |

---

### 2. 线参考

| 符号 | 介绍     |
| ---- | -------- |
| -    | 实线     |
| :    | 点线     |
| --   | 线段线   |
| -.   | 一实一虚 |

---

### 3. 颜色参考

| 符号 | 介绍 |
| ---- | ---- |
| r    | 红色 |
| g    | 绿色 |
| b    | 蓝色 |
| c    |      |
| m    |      |
| y    | 黄色 |
| k    | 黑色 |
| w    | 白色 |

---

### 4. 格式化字符串 fmt

语法格式：marker | line | color

```Python
ypoints = np.array([3,8,1,10])
# o代表圆点 :代表点线段 r代表红色
plt.plot(ypoints,'o:r')
plt.show()
```

---

### 5.标记尺寸

关键字：marksize 或 ms

只对Market标记点有效

```Python
ypoints = np.array([3,8,1,10])
# o代表圆点 :代表点线段 r代表红色
plt.plot(ypoints,'o:r',ms= 20)
plt.show()
```

---

### 6. 标记颜色

关键字：mec（边框）和mfc（内部）

设置market标记的颜色，支持十六进制也支持140多种颜色名称

```Python
ypoints = np.array([3,8,1,10])
# o代表圆点 :代表点线段 r代表红色
plt.plot(ypoints,'o:r',ms= 20,mec = 'b',mfc='y')
plt.show()
```

---





## Line - 线段

### 1. 线型

可以使用关键字linestyle或ls来更改绘制线的样式

```python
import matplotlib.pyplot as plt
import numpy as np
```

```python
ypoints = np.array([3,8,1,10])
plt.plot(ypoints,linestyle='dashed',marker='o')
plt.show()
```

### 2. 线条颜色

使用关键字color或c来设置线条颜色

```python
ypoints = np.array([3,8,1,10])
plt.plot(ypoints,linestyle='-.',marker='o',c='red')
plt.show()
```

### 3. 线的宽度

关键字：linewidth或lw，该值是一个浮点数，以磅为单位

```python
ypoints = np.array([3,8,1,10])
plt.plot(ypoints,linestyle='-.',marker='o',c='red',lw=3)
plt.show()
```



### 4. 多行

绘制多条线段

```python
y1 = np.array([3,8,1,10])
y2 = np.array([6,2,7,11])
plt.plot(y1)
plt.plot(y2)
plt.show()
```



## Labels - 标签

### 1. 为绘图创建标签 

在Pyplot中可以使用xlabel()和ylabel()函数为x轴和y轴设置标签

```python
import numpy as np
import matplotlib
import matplotlib.pypolot as plt
```

```Python
x = np.array([80,85,90,95,100,105,110,115,120,125])
y = np.array([240,250,260,270,280,290,300,310,320,330])

plt.plot(x,y)
plt.xlabel("平均脉搏")
plt.ylabel("卡路里消耗量")

plt.show()
```



### 2. 为绘图创建标题

```python
x = np.array([80,85,90,95,100,105,110,115,120,125])
y = np.array([240,250,260,270,280,290,300,310,320,330])

plt.plot(x,y)
plt.title("运动手表数据")
plt.xlabel("平均脉搏")
plt.ylabel("卡路里消耗量")

plt.show()
```



### 3. 设置标题和标签的字体属性

### 

```python
x = np.array([80,85,90,95,100,105,110,115,120,125])
y = np.array([240,250,260,270,280,290,300,310,320,330])

font1 = {'family':'serif','color':'blue','size':20}
font1 = {'family':'serif','color':'darkred','size':15}

plt.plot(x,y)
plt.title("运动手表数据",fontdict = fint1)
plt.xlabel("平均脉搏",fontdict = font2)
plt.ylabel("卡路里消耗量", fontdict = font2)

plt.show()
```

### 4. 定位标题

使用title()中的loc参数来定位标题

合法值是left、right和center，默认值是center

```python
x = np.array([80,85,90,95,100,105,110,115,120,125])
y = np.array([240,250,260,270,280,290,300,310,320,330])

plt.plot(x,y)
plt.title("运动手表数据",loc = 'left')
plt.xlabel("平均脉搏")
plt.ylabel("卡路里消耗量")

plt.show()
```



## Mesh - 网格

### 1. 向绘图中添加网格线

使用Pyplot 使用grid()函数将网格线添加到绘图中

```python
import numpy as np
import matplotlib
import matplotlib.pypolot as plt
```

```Python
x = np.array([80,85,90,95,100,105,110,115,120,125])
y = np.array([240,250,260,270,280,290,300,310,320,330])

plt.plot(x,y)
plt.xlabel("平均脉搏")
plt.ylabel("卡路里消耗量")

plt.grid()

plt.show()
```



### 2. 指定要显示的网格线

使用grid()函数中的axis轴参数来指定要显示的网格线

合法值为:"x"、"y"和"both"，默认值为“both”

```Python
x = np.array([80,85,90,95,100,105,110,115,120,125])
y = np.array([240,250,260,270,280,290,300,310,320,330])

plt.xlabel("平均脉搏")
plt.ylabel("卡路里消耗量")

plt.plot(x,y)

plt.grid(axis = 'x')

plt.show()
```



### 3. 设置网格的线属性

可以设置网格的线条属性，如下所示：grid(color='color',linestyle='linestyle',lindwidth=number)

```Python
x = np.array([80,85,90,95,100,105,110,115,120,125])
y = np.array([240,250,260,270,280,290,300,310,320,330])

plt.xlabel("平均脉搏")
plt.ylabel("卡路里消耗量")

plt.plot(x,y)

grid(color='green',linestyle='-',lindwidth=1.5)

plt.show()
```

## Multi Image - 多图

### 1. 显示多张图

使用subplots()函数可以在一张图中绘制绘制多个图

```python
# plot 1
x = np.array([0,1,2,3])
y = np.array([3,8,1,10])
plt.subplot([1,2,1])
plt.plot(x,y)

# plot 2 
x = np.array([0,1,2,3])
y = np.array([10,20,30,40])
plt.subplot([1,2,2])
plt.plot(x,y)

plt.show()
```



### 2 .subplots()函数

subplots()函数采用三个参数来描述图形的布局

布局按照行和列组织，由第一个参数和第二参数表示，第三个参数表示当前绘图的索引。

如果我们想要一个2行1列的图形，这意味这这两个图将会垂直显示而不是并排显示，我们可以按下列写法

```python
# plot 1
x = np.array([0,1,2,3])
y = np.array([3,8,1,10])

# 该图有2行1列 该子图是第1张图
plt.subplot([1,2,1])
plt.plot(x,y)

# plot 2 
x = np.array([0,1,2,3])
y = np.array([10,20,30,40])

# 该图有2行1列 该子图是第2张图
plt.subplot([1,2,2])
plt.plot(x,y)

plt.show()
```



### 3. 标题

使用title()函数为每个图添加标题

```python
# plot 1
x = np.array([0,1,2,3])
y = np.array([3,8,1,10])
plt.subplot([1,2,1])
plt.plot(x,y)
plt.title("Sales")

# plot 2 
x = np.array([0,1,2,3])
y = np.array([10,20,30,40])
plt.subplot([1,2,2])
plt.plot(x,y)
plt.title("Income")

plt.show()
```





### 4. 超级标题

可以使用suptitle()函数为整个图形添加标题

```python
# plot 1
x = np.array([0,1,2,3])
y = np.array([3,8,1,10])
plt.subplot([1,2,1])
plt.plot(x,y)
plt.title("Sales")

# plot 2 
x = np.array([0,1,2,3])
y = np.array([10,20,30,40])
plt.subplot([1,2,2])
plt.plot(x,y)
plt.title("Income")

plt.suptitle("My Shop")

plt.show()
```

---

## Point Image - 散点图

### 1. 创建散点图

借助Pyplot 可以使用scatter()函数绘制散点图

scatter()函数为每个观察绘制一个点。他需要两个长度相同的数组，一个用于x轴的值，另外一个用于y轴的值



```python
import matpplotlib.pyplot as plt
import numpy as np
```



```python
x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])

plt.scatter(x,y)
pt.show()
```



### 2. 颜色

使用color或c参数为每个散点图设置自己的颜色

```Python
x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])
plt.scatter(x,y,color = 'hotpink')


x = np.array([2,2,8,1,15,8,12,9,7,3,11,4,7,14,12])
y = np.array([100,105,84,105,90,99,90,95,94,100,79,112,91,80,85])

plt.scatter(x,y,color = '#88c999')
plt.show()

```



### 3. 给每个点上色

可以通过使用颜色数组作为c的参数值，来为每个点设置特定颜色

不能为此使用color参数，只能使用c参数（即使用这种方案时）

```Python
x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])

# 使用数组方式存放颜色
colors = np.array(['red','green','blue','yellow','pink','black','orange','purple','beige','brown','gray','cyan','magenta'])

plt.scatter(x,y,c = colors)
plt.show()

```



### 4. 颜色图

Matplotlib模块有许多可以使用的颜色图

颜色图就像一个颜色列表，其中每种颜色都有一个范围 0 - 100的值

可以使用带有颜色图值的关键字参数cmap指定颜色图，在本例子中为"viridis",它是Matplotlib中可用的内置颜色图之一。

此外，必须创建一个包含值（从0-100）的数组，散点图中每个点都有一个值

colorbar()函数能够在图表右侧展示一条颜色条

```python
# 通过plt.colorbar()语句在绘图中包含颜色图
x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])
colors = np.array([0,10,20,30,40,50,60,70,80,90,100])

plt.scatter(x,y,c=colors,cmap='viridis')

plt.colorbar()
plt.show()
```



### 5. 尺寸

使用s参数改变更改点的大小

就像颜色一样，确保大小数组的长度与x和y轴的数组长度保持一致



```python
x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])
sizes = np.array([20,50,100,200,500,1000,60,90,10,300,600,800,75])

plt.scatter(x,y,s=sizes)

plt.colorbar()
plt.show()
```



### 6. 透明度

可以使用alpha参数调整点的透明度

```python
x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])
sizes = np.array([20,50,100,200,500,1000,60,90,10,300,600,800,75])

plt.scatter(x,y,s=sizes,alpha=0.5)

plt.colorbar()
plt.show()
```





### 7. 组合颜色、大小和透明度

在点上组合具有不同大小的颜色图



```python
x = np.random.randint(100,size=(100))
y = np.random.randint(100,size=(100))
colors = np.random.randint(100,size=(100))
sizes = 10 * np.random.randint(100,size = (100))

plt.scatter(x,y,c=colors,s=sizes,alpha=0.5,cmap='nipy_spectral')

plt.colorbar()

plt.show()
```



## Bars - 柱状图



### 1. 创建柱状图

在Pyplot包中，使用bar()函数绘制柱状图：

```Python
import matplotlib.pyplot as plt
import numpy as np
```

```Python
x = np.array(["A","B","C","D"])
y = np.array([3,8,1,10])
plt.bar(x,y)
plt.show()
```

bar()函数采用描述条形布局的参数

类别及其值由第一个和第二个参数表示为数组

```python
x = ["Apples","Bananas"]
y = [400,350]
plt.bar(x,y)
```



### 2. 水平柱状图

如果想要柱状图水平显示而不是垂直显示，请使用barh()函数

```python
x = np.array(["A","B","C","D"])
y = np.array([3,8,1,10])
plt.barh(x,y)
plt.show()
```

### 3. 柱状图颜色

bar() 和 barh()使用关键字参数color来设置颜色

```Python
x = np.array(["A","B","C","D"])
y = np.array([3,8,1,10])
plt.bar(x,y,color="red")
plt.show()
```

其中，颜色支持使用140种颜色名称中的任意一种

```Python
x = np.array(["A","B","C","D"])
y = np.array([3,8,1,10])
plt.bar(x,y,color="hotpink")
plt.show()
```

其中，颜色也支持十六进制

```Python
x = np.array(["A","B","C","D"])
y = np.array([3,8,1,10])
plt.bar(x,y,color="#4C5F50")
plt.show()
```



### 4. 条形宽度（水平柱状图）

bar()使用关键字 width()来设置宽度

```Python
x = np.array(["A","B","C","D"])
y = np.array([3,8,1,10])
plt.bar(x,y,width = 0.1)
plt.show()
```



### 5. 条形高度（垂直柱状图）

barh()关键字使用参数Height来设置条形的高度

```python
x = np.array(["A","B","C","D"])
y = np.array([3,8,1,10])
plt.barh(x,y,height = 0.1)
plt.show()
```



## Histograms  - 直方图

在Matplotlib中，我们使用hist()函数来创建直方图

hist()函数将使用一个数字数组来创建直方图，该数组作为参数发送到函数中。

为简单起见，我们使用NumPy随机生成一个包含250个值的数组，其中值将集中在170左右，标准差为10.

```python
import matplotlib.pyplot as plt
import numpy as np
```

```python
x = np.random.normal(170,10,250)
print(x)
```

```python
plt.hist(x)
plt.show()
```

## Pie Charts - 饼图

### 1. 创建饼图

在Pyplot包中，可以使用pie()函数绘制饼图

```python
import matplotlib.pyplot as plt
import numpy as np
```

```python
y = np.array([35,25,25,15])

plt.pie(y)
plt.show()
```



### 2. 标签

使用Label参数为饼图添加标签

label参数必须是一个数组，每个楔形都有一个标签

```python
# 注意 此处必须等于100
y = np.array([35,25,25,15])
mylabels = ["Apples","Bananas","Cherries","Dates"]

plt.pie(y,labels = mylabels)
plt.show()
```



### 3. 起始角度

如前所述，默认起始角度位于x轴，但是可通过指定startangle参数来更改起始角度

startangle参数定义为 以度为单位的角度，默认角度为0

```python
# 注意 此处必须等于100
y = np.array([35,25,25,15])
mylabels = ["Apples","Bananas","Cherries","Dates"]

plt.pie(y,labels = mylabels,startangle = 90)
plt.show()
```



### 4. Explode

也许可以让其中一个楔子脱颖而出？此时可以使用explode参数

如果制定了explode参数，而不是None，则必须是一个数组，每个楔形都有一个值

每个值表示每个楔形显示的距离中心多远



```python
# 注意 此处必须等于100
y = np.array([35,25,25,15])
mylabels = ["Apples","Bananas","Cherries","Dates"]
myexplode =[0.2,0,0,0]

plt.pie(y,labels = mylabels,startangle = 90,explode = myexplode)
plt.show()
```



### 5. 阴影

通过将shadows参数设置为true为饼图添加阴影



```python
# 注意 此处必须等于100
y = np.array([35,25,25,15])
mylabels = ["Apples","Bananas","Cherries","Dates"]
myexplode =[0.2,0,0,0]

plt.pie(y,labels = mylabels,startangle = 90,explode = myexplode,shadow = True)
plt.show()
```





### 6. 颜色

使用colors参数设置每个楔形的颜色

如果指定了颜色参数，则必须是一个数组，每个楔形都有一个值



```python
# 注意 此处必须等于100
y = np.array([35,25,25,15])
mylabels = ["Apples","Bananas","Cherries","Dates"]
myexplode =[0.2,0,0,0]
mycolors = ["black","hotpink","b","#1CAF50"]

plt.pie(y,labels = mylabels,startangle = 90,explode = myexplode,shadow = True,colors = mycolors)
plt.show()
```



### 7. 图例

要求为每个楔形添加解释列表，请使用legend()函数

```python
# 注意 此处必须等于100
y = np.array([35,25,25,15])
mylabels = ["Apples","Bananas","Cherries","Dates"]
myexplode =[0.2,0,0,0]
mycolors = ["black","hotpink","b","#1CAF50"]

plt.pie(y,labels = mylabels,startangle = 90,explode = myexplode,shadow = True,colors = mycolors)
plt.legend()
plt.show()
```



要向图例中添加标题，可以将标题参数添加到图例函数中

```python
# 注意 此处必须等于100
y = np.array([35,25,25,15])
mylabels = ["Apples","Bananas","Cherries","Dates"]
myexplode =[0.2,0,0,0]
mycolors = ["black","hotpink","b","#1CAF50"]

plt.pie(y,labels = mylabels,startangle = 90,explode = myexplode,shadow = True,colors = mycolors)
plt.legend(title ="Four Fruits:")
plt.show()
```



# Python Numpy

在Python中，我们有列表，可以达到数组的目的，但是他们的处理很慢

- Numpy旨在提供一个数组对象，它比传统的Python列表快50倍

- NumPy中的数组对象被称为ndarray，它提供了很多支持性的函数，使得使用ndarray非常容易

- 数组在数据科学中使用的非常频繁，速度和资源都非常重要



为何NumPy比列表更快？

- 与列表不同，NumPy的数组被存储在内存中的一个连续区域，所以进程可以非常有效的访问和操作他们。
- 这种行为在计算机科学中被称为引用的位置性
- 这就是NumPy比列表更快的原因，此外他还被优化以适用于最新的CPU架构



NumPy用何语言编写？

- NumPy是一个Python库，部分是由Python编写的
- 但大部分需要快速计算的部分使用C或者C++编写的

NumPy的代码库在哪里？

- NumPy源代码位于https://github.com/numpy/nunmpy



安装NumPy

- 如果已经在系统上安装了Python和PIP，那么安装NumPy很容易
- 用这条命令 pip install numpy



检查NumPy版本

- 版本字符串存储在__version__属性中

  

  ```python
  import numpy as np
  Print(np.__version__)
  ```


## Array - 数组

  

### 1. 创建 NumPy ndarray 对象

NumPy用于处理数组，NumPy中的数组对象被称为ndarray

我们可以使用array()函数来创建一个NumPy 的 ndarray对象

```python
import numpy as np

arr = np.array([1,2,3,4,5])

print(arr)
print(type(arr))

```



type()这个内置的Python函数告诉我们传递给他的对象的类型，像上面的代码一样，它表明，arr是numpy.array类型。

要创建ndarray，我们可以将列表、元组或任意类似数组的对象传递给array()方法，然后它将被转换为ndarray



```python
# 使用元组创建创建NumPy数组
arr = np.array(1,2,3,4,5)
print(arr)
```



### 2. 数组中的维

数组中的维是指数组深度（嵌套数组）的一个级别

嵌套数组：指的是将数组作为元素的数组

#### 2.1  Array 0 - D

0 - D 数组，或标量（Scalars），是数组中的元素，数组中每个值都是一个 0 - D数组

```python
# 用值61创建 0-D数组
arr = np.array(61)
print(arr)
```

#### 2.2  Array 1 - D

其元素为 0 - D 数组的数组，称为一维或者1-D数组

```python
# 创建 1-D数组
arr = np.array([1,2,3,4,5,6])
print(arr)
```

#### 2.3  Array 2 - D

其元素为 1 - D 数组的数组，称为二维或者2-D数组

它们通常用于表示矩阵或者二阶张量

NumPy有一个专门用于矩阵运算的完整子模块numpy.mat

```python
# 创建 2-D数组
arr = np.array([[1,2,3,4,5,6],[1,2,3,4,5,6]])
print(arr)
```

#### 2.4  Array 3 - D

其元素为 2- D 数组的数组，称为二维或者3-D数组

```python
# 创建 3-D数组
arr = np.array([[[1,2,3,4,5,6],[1,2,3,4,5,6]],[[1,2,3,4,5,6],[1,2,3,4,5,6]]])
print(arr)
```

#### 2.5 维度检查

NumPy数组提供了ndim属性,该属性返回一个整数，该整数会告诉我们数组有多少维度

```python
# 检查数组有多少维度
a = np.array(46)
b = np.array([1,2,3,4,5])
c = np.array([[1,2,3],[4,5,6]])
d = np.array([[[1,2,3],[4,5,6]],[[1,2,3],[3,4,5]]])

print(a.ndim)
print(b.ndim)
print(c.ndim)
print(d.ndim)
```



#### 2.6 更高维度的数组

数组可以拥有任意数量的维度。

在创建数组时，可以使用ndimn参数定义维度

```python
# 创建一个有5个维度的数组，并验证他有5个维度
arr = np.array([1,2,3,4,5],ndimn = 5)

print(arr)
print('number:',arr.ndim)
```



### 3. 数组索引

#### 3.1 访问数组元素

数组索引等同于访问数组元素

可以通过引用其索引号来访问数组元素

NumPy数组中的索引以0开头。

```python
arr = np.array([1,2,3,4])
print(arr[0])
```



#### 3.2 访问 2 - D 数组

要访问二维数组中的元素，可以使用逗号分隔的整数表示元素的维数和索引

```python
arr = np.array([[1,2,3,4,5],[6,7,8,9,10]])
print('2nd element on 1st dim:',arr[0,1])
print('5th element on 2nd dim:',arr[1,4])
```

#### 3.3 访问3 - D数组

要访问3 - D数组中的元素，我们可用逗号分隔的整数来表示元素的维数和索引

```python
arr = np.array([[[1,2,3,4,5],[6,7,8,9,10]],[[1,2,3,4,5],[6,7,8,9,10]]])
# 访问第一个数组的第二个数组的第三个元素
print(arr[0,1,2])
```

#### 

#### 3.4 负索引

```python
arr = np.array([[1,2,3,4,5],[6,7,8,9,10]])
print('Last element from 2nd dim:',arr[1,-1])
```



### 4. 数组裁剪

#### 4.1 裁切数组

Python中裁切的意思是将元素从一个给定的索引带到另一个给定的索引

我们可以向这样传递切片而不是索引：[start : end]

我们还可以定义步长：[start​ : end : ​step]

如果不传递start 默认为0

如果不传递end 默认为该维度内数组长度

如果不传递step 默认为1

```python
arr = np.array([1,3,4,5,6,7,8])

# 裁切索引1到5的元素
print(arr[1:5])

# 裁切数组中索引4到结尾的元素
print(arr[4:])

# 裁切从开头到索引4（不包括）的元素
print(arr[:4])
```



#### 4.2 负裁切

使用减号运算符来从末尾开始引用索引

```python
arr = np.array([1,3,4,5,6,7,8])

# 从末尾开始的索引3到末尾开始的索引1,，对数据进裁切
print(arr[-3:-1])
```



#### 4.3 STEP

使用step值确定裁切的步长

```python
arr = np.array([1,3,4,5,6,7,8])

# 从索引1到索引5，返回相隔的元素
print(arr[1:5:2])
# 返回数组中相隔的元素
print(arr[::2])
```



#### 4.4 裁切2 - D数组

```python
arr = np.array([[1,3,4,5,6,7,8],[1,3,4,5,6,7,8]])

# 从第二个元素开始，对从索引1到索引4（不包括）的元素进行裁切
print(arr[1,1:4])
# 从两个元素中返回索引2
print(arr[0:2,2])
# 从两个元素裁切索引1到索引4，这将返回一个2-D数组
print(arr[0:2,1:4])
```



## Data Types - 数据类型

### 1. 数据类型

#### 1.1 Python中的数据类型

| 数据类型 | 描述                               | 示例       |
| -------- | ---------------------------------- | ---------- |
| strings  | 用于表示文本数据，文本用引号圈起来 | "ABCD"     |
| integer  | 用于表示整数                       | 12，-2     |
| float    | 用于表示实数                       | 1.2，42.42 |
| boolean  | 用于表示True或者False              |            |
| complex  | 用于表示复平面中的数字             | 1.0+2.0j   |

#### 1.2 NumPy中的数据类型

NumPy中有一些额外的数据类型，并通过一个字符引用数据类型，例如i表示整形，u代表无符号整数等

以下是NumPy中是所有数据类型的列表以及用于表示他们的字符。

| 符号 | 介绍                   |
| ---- | ---------------------- |
| i    | 整数                   |
| b    | 布尔                   |
| u    | 无符号整数             |
| f    | 浮点                   |
| c    | 复合浮点数             |
| m    | timedelta              |
| M    | datetime               |
| O    | 对象                   |
| S    | 字符串                 |
| U    | Unicode字符串          |
| V    | 固定的其他类型的内存块 |

#### 1.3 检查数组的数据类型

NumPy数组对象有一个名为dtype的属性，该属性返回数组的数据类型

```python
import numpy as np 
arr = np.array([1,2,3,4])
print(arr.dtype)
```

```python
arr = np.array(['apple'])
print(arr.dtype)
```

#### 1.4 使用已定义的数据类型创建数组

我们用array()函数来创建数组，该函数可以使用可选参数：dtype来定义我们数组元素的预期数据类型

```python
arr = np.array([1,2,3,4,5],dtype='S')
print(arr)
print(arr.dtype)
```

```python
# 创建数据类型为4字节整数的数组
arr = np.array([1,2,3,4,5],dtype='i4')
print(arr)
print(arr.dtype)
```

#### 1.5 假如值无法转换会怎么样？

如果给出了不能强制转换元素的类型，则NumPy将引发ValueError

ValueError在Python中是非预期或者错误的，则会引发ValueError

```python
arr = np.array(['a','2','3'],dtype='i')
# 报错 ValueError
```



#### 1.6 转换已有数组的数据类型

更改现有数组的数据类型的最佳方法是使用astype()方法复制该数组

astype()函数创建数组的副本，并允许您将数据类型指定为参数

数据类型可以使用字符串指定，例如f表示浮点数，i表示整数等，或者也可以直接使用数据类型：例如float或者int

```python
# 通过i作为参数值，将数据类型从浮点数更改为整数
arr = np.array([1.1,2.1,3.1])

newarr = arr.astype([i])
# newarr = arr.astype([int])

# arr = np.array([1,0,3])
# newarr = arr.astype([bool])
print(newarr)
print(newarr.dtype)
```





### 2. NumPy数组副本 vs 视图

#### 2.1 区别

副本和数组之间的主要区别在于副本是一个新数组，而这个视图只是原始数组的视图

副本拥有数据，对副本所做的任何更改都不会改变原始数组，对原始数组所做的任何更改也不会影响副本

视图不拥有数据，对视图所做的任何更改都会影响到原始数组，而对原始数组所做的任何更改都会影响视图



#### 2.2 副本

```python
arr = np.array([1,2,3,4,5,6])
x = arr.copy()
arr[0] = 61

print(arr)
print(x)
```

#### 2.3 视图

```Python
arr = np.array([1,2,3,4,5,6])
x = arr.view()
arr[0] = 61
print(arr)
print(x)
```

#### 2.4 检查数组是否拥有数据

如上所述，副本都拥有数据，而视图不拥有数据，但是该如何检查？

每个NumPy数组都有一个属性base，如果该数组拥有数据，则这个base属性返回None

否则，base属性将引用原始对象

```Python
arr = np.array([1,2,3,4,5])

x = arr.copy()
y = arr.view()

print(x.base)
print(y.base)

print(arr.base)
```





## Shape  - 形状



### 1. NumPy 数组形状

数组的形状是每个维中元素的数量

NumPy数组有一个名为shape的属性，该属性返回一个元组，每个索引都具有相应元素的数量。

```python
import numpy as np

arr = np.array([[1,2,3,4],[5,6,7,8],[5,6,7,8]])
print(arr.shape)
# 返回（3,4）意味着数组有两个维，每个维有4个元素
```

```python
# 利用ndimn使用值1,2,3,4的向量创建有5个维度的数据，并验证最后一个维度的值为4
arr = np.array([1,2,3,4,5],ndmin=5)

print(arr)
print(arr.shape)
```



### 2. 数组重塑

重塑意味着改变这个数组的形状

数组的形状是每个维中元素的数量

通过reshape()重塑我们可以添加或者删除维度或者更改每个维度中元素数量

#### 2.1 从1-D重塑为2-D

```python
# 将以下具有十二个元素的1-D数组转换为2-D数组
arr = np.array([1,2,3,4,5,6,7,8,9,10,11,12])

newarr = arr.reshape(4,3)
print(arr.shape)
print(newarr)
print(newarr.shape)
```



#### 2.2 从1-D重塑为2-D



```python
# 将以下具有十二个元素的1-D数组转换为3-D数组
arr = np.array([1,2,3,4,5,6,7,8,9,10,11,12])

newarr = arr.reshape(2,3,4)

print(newarr)
print(newarr.shape)
```



#### 2.3 重塑成任何形状

只需要重塑所需要的元素在两种形状中均相等即可

我们可以将8元素1D数组重塑为2行2D数组中的4个元素，但是不能将其重塑为3元素3行2D数组

```python
arr = np.array([1,2,3,4,5,6,7,8])

newarr = arr.reshape(3,3)

print(newarr)
# 报错，因为没有九个元素。此处只有8个
```



#### 2.4 返回副本还是视图？

```python
arr = np.array([1,2,3,4,5,6,7,8])

print(arr.reshape(2,4).base)
# 上面的例子返回原始数组，因此是一个视图
```



#### 2.5 未知的维度

可以使用一个未知的维度

这意味不必再reshape方法中为维度之一指定确切的数字

传递-1做为值，NumPy将为我们计算该数字



```python
arr = np.array([1,2,3,4,5,6,7,8])
newarr = arr.reshape(2,2,-1)
print(newarr)
```



#### 2.6 展平数组

展平数组是指将多维度的数组转换为1-D数组

我们可以使用reshape(-1)来做到

```python
arr = np.array([[1,2,3,4,5],[6,7,8,9,10]])
newarr = arr.reshape(-1)

print(newarr)
```



## Opeartion - 数组迭代

迭代意味着要逐一遍历数组

当我们在NumPy中处理多维数组的时候，可以使用Python中基本的for循环来实现此操作。

### 1. 迭代 1-D 数组

如果我们对1-D数组进行迭代，它将会逐一遍历每一个元素

```python
import numpy as np
```

```python
arr = np.array([1,2,3])
for x in arr:
    print(x)
```



### 2. 迭代 2-D数组

在2-D数组中，它将会遍历所有行

```python
arr = np.array([[1,2,3,4],[5,6,7,8]])
for x in arr:
    print(x)
# 如果我们迭代一个n-D数组 他将逐一遍历第n-1维
```



```python
arr = np.array([[1,2,3,4],[5,6,7,8]])
for x in arr:
    for y in x;
    	print(y)
```



### 3. 使用nditer()迭代数组

函数nditer()是一个辅助函数，从非常基本的迭代到非常高级的迭代都可以使用，他解决了我们在迭代中面临的一些基本问题，让我们通过一个例子来进行介绍

在基本的for循环中，迭代遍历数组的每个标量，我们需要使用n个for循环，对于具有更高维度的数组可能很难编写。

```python
arr = np.array([[[1,2,3],[1,1,2]],[[1,12],[3,4,1]]])

for x in np.nditer(arr)
	print(x)
```




### 4.迭代不同数据类型的数组

我们额可以使用op_dtypes参数，并传递期望的数据类型，以在迭代时改变元素的数据类型

NumPy不会就地更改元素的数据类型（元素位于数组中），因此它需要一些其他的空间来执行此操作，该额外空间被称为buffer，为了在nditer()中启用它，我们传参flags=['buffered']

```python
arr = np.array([1,2,3])

for x in np.nditer(arr)
```

