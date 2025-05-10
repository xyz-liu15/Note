
- 我想开始使用 pandas
	```
	In [1]: import pandas as pd
	```
	要加载 pandas 包并开始使用它，请导入该包。社区同意的 pandas 别名是 `pd` ，因此将 pandas 作为 `pd` 加载被认为是 pandas 文档的标准做法。

## pandas 数据表表示#

![../../_images/01_table_dataframe.svg](https://pandas.pydata.org/docs/_images/01_table_dataframe.svg)
- 我想存储泰坦尼克号乘客的数据。对于一些乘客，我知道他们的姓名（字符）、年龄（整数）和性别（男/女）数据。
	```
	In [2]: df = pd.DataFrame(
	   ...:     {
	   ...:         "Name": [
	   ...:             "Braund, Mr. Owen Harris",
	   ...:             "Allen, Mr. William Henry",
	   ...:             "Bonnell, Miss. Elizabeth",
	   ...:         ],
	   ...:         "Age": [22, 35, 58],
	   ...:         "Sex": ["male", "male", "female"],
	   ...:     }
	   ...: )
	   ...: 
	In [3]: df
	Out[3]: 
	                       Name  Age     Sex
	0   Braund, Mr. Owen Harris   22    male
	1  Allen, Mr. William Henry   35    male
	2  Bonnell, Miss. Elizabeth   58  female
	```
	要手动将数据存储在表中，请创建 `DataFrame` 。当使用 Python 字典列表时，字典的键将用作列标题，列表中的值将作为 `DataFrame` 的列。

[`DataFrame`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html#pandas.DataFrame "pandas.DataFrame") 是一个二维数据结构，可以在列中存储不同类型的数据（包括字符、整数、浮点值、分类数据等）。它与电子表格、SQL 表或 R 中的 `data.frame` 类似。

- 该表有 3 列，每列都有一个列标签。列标签分别是 `Name` 、 `Age` 和 `Sex` 。
- 列 `Name` 由文本数据组成，每个值都是字符串，列 `Age` 是数字，列 `Sex` 是文本数据。

在电子表格软件中，我们数据的表现形式会非常相似：

![../../_images/01_table_spreadsheet.png](https://pandas.pydata.org/docs/_images/01_table_spreadsheet.png)

## DataFrame 中的每一列都是一个 Series#

![../../_images/01_table_series.svg](https://pandas.pydata.org/docs/_images/01_table_series.svg)
- 我对处理 `Age` 列中的数据很感兴趣
	```
	In [4]: df["Age"]
	Out[4]: 
	0    22
	1    35
	2    58
	Name: Age, dtype: int64
	```
	当选择 pandas [`DataFrame`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html#pandas.DataFrame "pandas.DataFrame") 的单列时，结果是 pandas [`Series`](https://pandas.pydata.org/docs/reference/api/pandas.Series.html#pandas.Series "pandas.Series") 。要选择该列，请在方括号 `[]` 中使用列标签。

你也可以从零开始创建一个 `Series` ：

```
In [5]: ages = pd.Series([22, 35, 58], name="Age")

In [6]: ages
Out[6]: 
0    22
1    35
2    58
Name: Age, dtype: int64
```

pandas 的 `Series` 没有列标签，因为它只是一个 `DataFrame` 的单列。Series 却有行标签。

## 对 DataFrame 或 Series 做些事情#

- 我想知道乘客的最大年龄
	我们可以在 `DataFrame` 中通过选择 `Age` 列并应用 `max()` 来做到这一点：
	```
	In [7]: df["Age"].max()
	Out[7]: 58
	```
	或者应用于 `Series` ：
	```
	In [8]: ages.max()
	Out[8]: 58
	```

正如 `max()` 方法所说明的，你可以对 `DataFrame` 或 `Series` 执行操作。pandas 提供了许多功能，它们都是可以应用于 `DataFrame` 或 `Series` 的 *方法* 。由于方法是函数，请别忘了使用括号 `()` 。

- 我对我的数据表中数值数据的基本统计感兴趣
	```
	In [9]: df.describe()
	Out[9]: 
	             Age
	count   3.000000
	mean   38.333333
	std    18.230012
	min    22.000000
	25%    28.500000
	50%    35.000000
	75%    46.500000
	max    58.000000
	```
	[`describe()`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.describe.html#pandas.DataFrame.describe "pandas.DataFrame.describe") 方法提供了对 `DataFrame` 中数值数据的快速概览。由于 `Name` 和 `Sex` 列是文本数据，因此默认情况下它们不会被 [`describe()`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.describe.html#pandas.DataFrame.describe "pandas.DataFrame.describe") 方法考虑。

许多 pandas 操作返回一个 `DataFrame` 或一个 `Series` 。The [`describe()`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.describe.html#pandas.DataFrame.describe "pandas.DataFrame.describe") 方法是 pandas 返回 pandas `Series` 或 pandas `DataFrame` 的一个示例。

To user guide

在用户指南的 [使用 describe 进行聚合](https://pandas.pydata.org/docs/user_guide/basics.html#basics-describe) 部分，查看 `describe` 的更多选项

用户指南

对 `DataFrame` 和 `Series` 的更详细解释在 [数据结构介绍](https://pandas.pydata.org/docs/user_guide/dsintro.html#dsintro) 中提供。