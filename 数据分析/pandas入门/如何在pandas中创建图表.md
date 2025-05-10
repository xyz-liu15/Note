
![../../_images/04_plot_overview.svg](https://pandas.pydata.org/docs/_images/04_plot_overview.svg)

```
In [1]: import pandas as pd

In [2]: import matplotlib.pyplot as plt
```

- 空气质量数据
	对于这个教程，使用的是由 OpenAQ 提供并通过 py-openaq 包获取的关于 $NO2$ 的空气质量数据。 `air_quality_no2.csv` 数据集分别为巴黎、安特卫普和伦敦的测量站 FR04014、BETR801 和伦敦威斯敏斯特提供了 $NO2$ 值。
	```
	In [3]: air_quality = pd.read_csv("data/air_quality_no2.csv", index_col=0, parse_dates=True)
	In [4]: air_quality.head()
	Out[4]: 
	                     station_antwerp  station_paris  station_london
	datetime                                                           
	2019-05-07 02:00:00              NaN            NaN            23.0
	2019-05-07 03:00:00             50.5           25.0            19.0
	2019-05-07 04:00:00             45.0           27.7            19.0
	2019-05-07 05:00:00              NaN           50.4            16.0
	2019-05-07 06:00:00              NaN           61.9             NaN
	```

- 我想快速查看数据。
	```
	In [5]: air_quality.plot()
	Out[5]: <Axes: xlabel='datetime'>
	In [6]: plt.show()
	```
	![../../_images/04_airqual_quick.png](https://pandas.pydata.org/docs/_images/04_airqual_quick.png)
	使用 `DataFrame` ，pandas 默认为每个包含数值数据的列创建一条线形图。
- 我想仅绘制数据表中来自巴黎的列的数据。
	```
	In [7]: air_quality["station_paris"].plot()
	Out[7]: <Axes: xlabel='datetime'>
	In [8]: plt.show()
	```
	![../../_images/04_airqual_paris.png](https://pandas.pydata.org/docs/_images/04_airqual_paris.png)
	要绘制特定列，请使用子集数据教程中的选择方法，并结合 `plot()` 方法。因此， `plot()` 方法适用于 `Series` 和 `DataFrame` 。
- 我想直观比较在伦敦和巴黎测量的 $NO2$ 值。
	```
	In [9]: air_quality.plot.scatter(x="station_london", y="station_paris", alpha=0.5)
	Out[9]: <Axes: xlabel='station_london', ylabel='station_paris'>
	In [10]: plt.show()
	```
	![../../_images/04_airqual_scatter.png](https://pandas.pydata.org/docs/_images/04_airqual_scatter.png)

除了使用 `plot` 函数时的默认 `line` 图之外，还有许多其他方法可以用来绘制数据。让我们使用一些标准 Python 来了解可用的绘图方法：

```
In [11]: [
   ....:     method_name
   ....:     for method_name in dir(air_quality.plot)
   ....:     if not method_name.startswith("_")
   ....: ]
   ....: 
Out[11]: 
['area',
 'bar',
 'barh',
 'box',
 'density',
 'hexbin',
 'hist',
 'kde',
 'line',
 'pie',
 'scatter']
```

其中一个选项是 `DataFrame.plot.box()` ，它指的是箱线图。 `box` 方法适用于空气质量示例数据：

```
In [12]: air_quality.plot.box()
Out[12]: <Axes: >

In [13]: plt.show()
```

![../../_images/04_airqual_boxplot.png](https://pandas.pydata.org/docs/_images/04_airqual_boxplot.png)

To user guide

对于默认的线形图以外的其他图形的介绍，请参阅用户指南中关于支持图形样式的部分。

- 我想将每一列放在单独的子图中。
	```
	In [14]: axs = air_quality.plot.area(figsize=(12, 4), subplots=True)
	In [15]: plt.show()
	```
	![../../_images/04_airqual_area_subplot.png](https://pandas.pydata.org/docs/_images/04_airqual_area_subplot.png)
	`subplots` 函数的 `plot` 参数支持为每个数据列创建单独的子图。 值得查看 pandas 绘图函数中提供的内置选项。

To user guide

用户指南中的图表格式部分解释了更多格式化选项。

- 我想进一步自定义、扩展或保存生成的图表。
	```
	In [16]: fig, axs = plt.subplots(figsize=(12, 4))
	In [17]: air_quality.plot.area(ax=axs)
	Out[17]: <Axes: xlabel='datetime'>
	In [18]: axs.set_ylabel("NO$_2$ concentration")
	Out[18]: Text(0, 0.5, 'NO$_2$ concentration')
	In [19]: fig.savefig("no2_concentrations.png")
	In [20]: plt.show()
	```
	![../../_images/04_airqual_customized.png](https://pandas.pydata.org/docs/_images/04_airqual_customized.png)

pandas 创建的每个绘图对象都是 Matplotlib 对象。由于 Matplotlib 提供了大量的选项来自定义绘图，将 pandas 与 Matplotlib 的联系明确化能够使 Matplotlib 的全部功能应用于绘图。这种策略在之前的示例中得到了应用：

```
fig, axs = plt.subplots(figsize=(12, 4))        # Create an empty Matplotlib Figure and Axes
air_quality.plot.area(ax=axs)                   # Use pandas to put the area plot on the prepared Figure/Axes
axs.set_ylabel("NO$_2$ concentration")          # Do any Matplotlib customization you like
fig.savefig("no2_concentrations.png")           # Save the Figure/Axes using the existing Matplotlib method.
plt.show()                                      # Display the plot
```

To user guide

在可视化页面中提供了有关 pandas 绘图的全面概述。