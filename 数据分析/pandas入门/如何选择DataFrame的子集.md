```
In [1]: import pandas as pd
```

- 泰坦尼克号数据
	本教程使用存储为 CSV 格式的泰坦尼克数据集。数据包含以下数据列：
	- PassengerId: 每位乘客的 ID。
	- Survived：乘客是否存活。用 `0` 表示存活，用 `1` 表示未存活。
	- Pclass：乘客的票类，分为 `1` 、 `2` 和 `3` 三种票类。
	- Name: 乘客的姓名。
	- 性别：乘客性别。
	- Age：乘客的年龄（以年为单位）。
	- 兄弟姐妹：船上的兄弟姐妹或配偶数量。
	- Parch：乘客船上的父母或子女数量。
	- 票号：乘客的票号。
	- 票价：表示票价。
	- 船舱：乘客的船舱号。
	- 登船港口。
	```
	In [2]: titanic = pd.read_csv("data/titanic.csv")
	In [3]: titanic.head()
	Out[3]: 
	   PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
	0            1         0       3  ...   7.2500   NaN         S
	1            2         1       1  ...  71.2833   C85         C
	2            3         1       3  ...   7.9250   NaN         S
	3            4         1       1  ...  53.1000  C123         S
	4            5         0       3  ...   8.0500   NaN         S
	[5 rows x 12 columns]
	```

## 我如何选择一个 DataFrame 的子集？#

## 我如何从 DataFrame 中选择特定列？#

![../../_images/03_subset_columns.svg](https://pandas.pydata.org/docs/_images/03_subset_columns.svg)
- 我对泰坦尼克号乘客的年龄感兴趣。
	```
	In [4]: ages = titanic["Age"]
	In [5]: ages.head()
	Out[5]: 
	0    22.0
	1    38.0
	2    26.0
	3    35.0
	4    35.0
	Name: Age, dtype: float64
	```
	要选择单个列，使用方括号 `[]` 并填写目标列的列名。

DataFrame 中的每一列都是一个 [`Series`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html#pandas.DataFrame "pandas.DataFrame") 。选择单列时，返回的对象是 pandas 的 [`Series`](https://pandas.pydata.org/docs/reference/api/pandas.Series.html#pandas.Series "pandas.Series") 。我们可以通过检查输出类型来验证这一点：

```
In [6]: type(titanic["Age"])
Out[6]: pandas.core.series.Series
```

查看输出的 `shape` ：

```
In [7]: titanic["Age"].shape
Out[7]: (891,)
```

[`DataFrame.shape`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.shape.html#pandas.DataFrame.shape "pandas.DataFrame.shape") 是 pandas `Series` 和 `DataFrame` 的一个属性（记得 [读取和写入教程](https://pandas.pydata.org/docs/getting_started/intro_tutorials/02_read_write.html#min-tut-02-read-write) ，属性不要用括号），包含行数和列数： *(nrows, ncolumns)* 。pandas Series 是一维的，只返回行数。

- 我对泰坦尼克号乘客的年龄和性别很感兴趣。
	```
	In [8]: age_sex = titanic[["Age", "Sex"]]
	In [9]: age_sex.head()
	Out[9]: 
	    Age     Sex
	0  22.0    male
	1  38.0  female
	2  26.0  female
	3  35.0  female
	4  35.0    male
	```
	要选择多个列，请在选择括号 `[]` 内使用列名的列表。

返回的数据类型是 pandas DataFrame：

```
In [10]: type(titanic[["Age", "Sex"]])
Out[10]: pandas.core.frame.DataFrame
```

```
In [11]: titanic[["Age", "Sex"]].shape
Out[11]: (891, 2)
```

选择返回了一个包含 891 行和 2 列的 `DataFrame` 。记住， `DataFrame` 是二维的，具有行和列两个维度。

To user guide

关于索引的基础信息，请参阅用户指南中关于 [索引和数据选择](https://pandas.pydata.org/docs/user_guide/indexing.html#indexing-basics) 的部分。

## 我该如何筛选特定行（来自一个 DataFrame）？#

![../../_images/03_subset_rows.svg](https://pandas.pydata.org/docs/_images/03_subset_rows.svg)
- 我对年龄超过35岁的乘客感兴趣。
	```
	In [12]: above_35 = titanic[titanic["Age"] > 35]
	In [13]: above_35.head()
	Out[13]: 
	    PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
	1             2         1       1  ...  71.2833   C85         C
	6             7         0       1  ...  51.8625   E46         S
	11           12         1       1  ...  26.5500  C103         S
	13           14         0       3  ...  31.2750   NaN         S
	15           16         1       2  ...  16.0000   NaN         S
	[5 rows x 12 columns]
	```
	要根据条件选择行，请在选择括号内使用条件 `[]` 。

选择括号内的条件 `titanic["Age"] > 35` 检查 `Age` 列的值是否大于35：

```
In [14]: titanic["Age"] > 35
Out[14]: 
0      False
1       True
2      False
3      False
4      False
       ...  
886    False
887    False
888    False
889    False
890    False
Name: Age, Length: 891, dtype: bool
```

The output of the conditional expression (`>`, but also `==`,`!=`, `<`, `<=`,… would work) is actually a pandas `Series` of boolean values (either `True` or `False`) with the same number of rows as the original `DataFrame`. Such a `Series` of boolean values can be used to filter the `DataFrame` by putting it in between the selection brackets `[]`. Only rows for which the value is `True` will be selected.

We know from before that the original Titanic `DataFrame` consists of 891 rows. Let’s have a look at the number of rows which satisfy the condition by checking the `shape` attribute of the resulting `DataFrame` `above_35`:

```
In [15]: above_35.shape
Out[15]: (217, 12)
```

- 我对来自2等舱和3等舱的泰坦尼克号乘客感兴趣。
	```
	In [16]: class_23 = titanic[titanic["Pclass"].isin([2, 3])]
	In [17]: class_23.head()
	Out[17]: 
	   PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
	0            1         0       3  ...   7.2500   NaN         S
	2            3         1       3  ...   7.9250   NaN         S
	4            5         0       3  ...   8.0500   NaN         S
	5            6         0       3  ...   8.4583   NaN         Q
	7            8         0       3  ...  21.0750   NaN         S
	[5 rows x 12 columns]
	```
	与条件表达式类似， [`isin()`](https://pandas.pydata.org/docs/reference/api/pandas.Series.isin.html#pandas.Series.isin "pandas.Series.isin") 条件函数对于值在提供的列表中的每一行返回 `True` 。要根据这样的函数过滤行，请在选择括号 `[]` 内使用条件函数。在这种情况下，选择括号内的条件 `titanic["Pclass"].isin([2, 3])` 检查哪些行的 `Pclass` 列是 2 或 3。

上述内容等同于通过行进行筛选，其中类别为 2 或 3，并结合两个语句使用 `|` （或）运算符

```
In [18]: class_23 = titanic[(titanic["Pclass"] == 2) | (titanic["Pclass"] == 3)]

In [19]: class_23.head()
Out[19]: 
   PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
0            1         0       3  ...   7.2500   NaN         S
2            3         1       3  ...   7.9250   NaN         S
4            5         0       3  ...   8.0500   NaN         S
5            6         0       3  ...   8.4583   NaN         Q
7            8         0       3  ...  21.0750   NaN         S

[5 rows x 12 columns]
```

To user guide

请参阅用户指南中关于 [布尔索引](https://pandas.pydata.org/docs/user_guide/indexing.html#indexing-boolean) 或关于 [isin 函数](https://pandas.pydata.org/docs/user_guide/indexing.html#indexing-basics-indexing-isin) 的专门部分。

- 我想处理年龄已知乘客的数据。
	```
	In [20]: age_no_na = titanic[titanic["Age"].notna()]
	In [21]: age_no_na.head()
	Out[21]: 
	   PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
	0            1         0       3  ...   7.2500   NaN         S
	1            2         1       1  ...  71.2833   C85         C
	2            3         1       3  ...   7.9250   NaN         S
	3            4         1       1  ...  53.1000  C123         S
	4            5         0       3  ...   8.0500   NaN         S
	[5 rows x 12 columns]
	```
	[`notna()`](https://pandas.pydata.org/docs/reference/api/pandas.Series.notna.html#pandas.Series.notna "pandas.Series.notna") 条件函数对于每行值不是 `  空值  ` 的地方返回 `True` 。因此，这可以与选择括号 `[]` 结合使用来过滤数据表。

你可能会想实际发生了什么变化，因为前五行仍然是相同的值。一种验证方法是通过检查形状是否发生了变化：

```
In [22]: age_no_na.shape
Out[22]: (714, 12)
```

To user guide

关于缺失值的更多专用函数，请参阅用户指南中关于 [处理缺失数据](https://pandas.pydata.org/docs/user_guide/missing_data.html#missing-data) 的部分。

## How do I select specific rows and columns from a DataFrame?

![../../_images/03_subset_columns_rows.svg](https://pandas.pydata.org/docs/_images/03_subset_columns_rows.svg)
- I’m interested in the names of the passengers older than 35 years.
	```
	In [23]: adult_names = titanic.loc[titanic["Age"] > 35, "Name"]
	In [24]: adult_names.head()
	Out[24]: 
	1     Cumings, Mrs. John Bradley (Florence Briggs Th...
	6                               McCarthy, Mr. Timothy J
	11                             Bonnell, Miss. Elizabeth
	13                          Andersson, Mr. Anders Johan
	15                     Hewlett, Mrs. (Mary D Kingcome) 
	Name: Name, dtype: object
	```
	In this case, a subset of both rows and columns is made in one go and just using selection brackets `[]` is not sufficient anymore. The `loc` / `iloc` operators are required in front of the selection brackets `[]`. When using `loc` / `iloc`, the part before the comma is the rows you want, and the part after the comma is the columns you want to select.

在使用列名、行标签或条件表达式时，在选取括号 `loc` 前使用 `[]` 。在逗号前后，你可以使用单个标签、标签列表、标签切片、条件表达式或冒号。使用冒号表示你想选取所有行或列。

- 我对第10行到第25行和第3列到第5列感兴趣。
	```
	In [25]: titanic.iloc[9:25, 2:5]
	Out[25]: 
	    Pclass                                 Name     Sex
	9        2  Nasser, Mrs. Nicholas (Adele Achem)  female
	10       3      Sandstrom, Miss. Marguerite Rut  female
	11       1             Bonnell, Miss. Elizabeth  female
	12       3       Saundercock, Mr. William Henry    male
	13       3          Andersson, Mr. Anders Johan    male
	..     ...                                  ...     ...
	20       2                 Fynney, Mr. Joseph J    male
	21       2                Beesley, Mr. Lawrence    male
	22       3          McGowan, Miss. Anna "Annie"  female
	23       1         Sloper, Mr. William Thompson    male
	24       3        Palsson, Miss. Torborg Danira  female
	[16 rows x 3 columns]
	```
	再次，行和列的子集是同时选择的，仅使用选择括号 `[]` 已经不够了。当特别关注基于其在表格中的位置的特定行和/或列时，请在选择括号 `[]` 前使用 `iloc` 运算符。

当使用 `loc` 或 `iloc` 选择特定的行和/或列时，可以给选定的数据分配新值。例如，要将名称 `anonymous` 分配给第四列的前三个元素：

```
In [26]: titanic.iloc[0:3, 3] = "anonymous"

In [27]: titanic.head()
Out[27]: 
   PassengerId  Survived  Pclass  ...     Fare Cabin  Embarked
0            1         0       3  ...   7.2500   NaN         S
1            2         1       1  ...  71.2833   C85         C
2            3         1       3  ...   7.9250   NaN         S
3            4         1       1  ...  53.1000  C123         S
4            5         0       3  ...   8.0500   NaN         S

[5 rows x 12 columns]
```

To user guide

查看用户指南中关于 [不同的索引选择](https://pandas.pydata.org/docs/user_guide/indexing.html#indexing-choice) 的部分，以更深入地了解 `loc` 和 `iloc` 的使用。

To user guide

用户指南页面 [索引和选择数据](https://pandas.pydata.org/docs/user_guide/indexing.html#indexing) 提供了索引的完整概述。