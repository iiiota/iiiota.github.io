---
title: getstart
date: 2025-06-03 20:56:49
tags:
  - Python
  - Pandas
categories:
  - [ Python, Pandas ]
---

> [https://pandas.pydata.org/docs/getting_started/index.html#getting-started](https://pandas.pydata.org/docs/getting_started/index.html#getting-started)


# GetStart

推荐在 venv 虚拟环境中安装。

```shell
# pip>=19.3
pip install pandas
# 安装所有依赖，包含可选依赖
pip install "pandas[all]"
```

运行测试套件。

```shell
pip install "pandas[test]"
```
```python
import pandas as pd
pd.test()
```


## 依赖


必要依赖：

- [Numpy](https://numpy.org/)
- [python-dateutil](https://dateutil.readthedocs.io/en/stable/)
- [pytz](https://pypi.org/project/pytz/)
- [tzdata](https://pypi.org/project/tzdata/)

可选依赖，有许多只用于特定方法的依赖：

- `pandas.read.hdf()` 需要 `pytables` 依赖；
- `DataFrame.to.markdown()` 需要 `tabulate` 依赖；
- 若对应的依赖未安装，pandas会抛出 `ImportError` 异常；


### 性能

推荐安装，尤其在处理大数据集合时。

```shell
pip install "pandas[performance]"
```

- [numexpr](https://github.com/pydata/numexpr)：通过使用多核以及智能分块和缓存来加速某些数值运算，以实现较大的速度；
- [bottleneck](https://github.com/pydata/bottleneck)：通过使用专门的cpython协程来加速某些类型的nan，以实现较大的加速；
- [numba](https://github.com/numba/numba)：接受engine="numba"的操作的替代执行引擎，使用JIT编译器将Python函数转换为使用LLVM编译器优化的机器码；


### 可视化

```shell
pip install "pandas[plot, output-formatting]"
```

- matplotlib：绘图库；
- Jinja2：使用datafframe .style的条件格式；
- [tabulate](https://github.com/astanin/python-tabulate)：打印markdown友好的格式；


### 计算

```shell
pip install "pandas[computation]"
```

- SciPy：各种统计功能；
- xarray：处理N维数据的类pandas api；


### Excel

```shell
pip install "pandas[excel]"
```

- xlrd：读取excel；
- xlsxwriter：写入excel；
- openpyxl：读写xlsx文件；
- pyxlsb：读取xlsb文件；
- python-calamine：读取xls/xlsx/xlsb/ods文件；


### HTML

```shell
pip install "pandas[html]"
```

- BeautifulSoup4：HTML parser for read_html
- html5lib：HTML parser for read_html
- lxml：HTML parser for read_html


### XML

```shell
pip install "pandas[xml]"
```

- lxml：XML parser for read_xml and tree builder for to_xml


### SQL

```shell
# 传统的可安装驱动
pip install "pandas[postgresql, mysql, sql-other]"
```

- SQLAlchemy：SQL support for databases other than sqlite
- psycopg2：PostgreSQL engine for sqlalchemy
- pymysql：MySQL engine for sqlalchemy
- adbc-driver-postgresql：ADBC Driver for PostgreSQL
- adbc-driver-sqlite：ADBC Driver for SQLite


### 其他数据源

```shell
pip install "pandas[hdf5, parquet, feather, spss, excel]"
```

- PyTables：HDF5-based reading / writing
- blosc：Compression for HDF5; only available on `conda`
- zlib：Compression for HDF5
- fastparquet：Parquet reading / writing (pyarrow is default)
- pyarrow：Parquet, ORC, and feather reading / writing
- pyreadstat：SPSS files (.sav) reading
- odfpy：Open document format (.odf, .ods, .odt) reading / writing


### 从Cloud访问数据

```shell
python install "pandas[fss, aws, gcp]"
```

- fsspec：Handling files aside from simple local and HTTP (required dependency of s3fs, gcsfs).
- gcsfs：Google Cloud Storage access
- pandas-gbq：Google Big Query access
- s3fs：Amazon S3 access


### 剪贴板

> 依赖于操作系统，可能需要安装系统级别的包，如Linux中需要安装 `xclip` 或 `xsel` 的CLI工具。

```shell
pip install "pandas[clipboard]"
```

- PyQt4/PyQt5
- qtpy


### 压缩

```shell
pip install "pandas[compression]"
```

- Zstandard：Zstandard compression


## 数据类型

表格数据，定义内部类型有：
- `DataFrame`：二维数据结构，column可以存储的数据类型包括 字符、整型、浮点、分类数据等；
- `Series`：DateFrame中的每一column都是一个Series

```python
import pandas as pd

# 手动创建，column lable分别是 Name Age Sex
pd.DataFrame(
    {
        "Name": ["Aric", "Frank", "Max"],
        "Age": [22, 18, 30],
        "Sex": ["male", "male", "female"],
    }
)

# 访问Series
df["Age"]
df.Age

# 创建Series
ages = pd.Series([22, 18, 30], name="Age")

# 常见数据操作，很多方法都会返回DataFrame或Series
df["Age"].max() # 最大值
df.describe()   # 描述信息概览
```


## 读写


### DataFrame

pandas支持很多不同文件格式或数据源：csv、excel、sql、json、parquet等。

```python
import pandas as pd

# pd.read_*
titanic = pd.read_csv("data/titanic.csv")
titanic             # 打印前后5行
titanic.head(5)     # 前5行
titanic.tail(5)     # 后5行
titanic.dtypes      # column数据类型
titanic.info()      # 技术总结信息

# pd.to_*
titanic.to_excel("titanic.xlsx", sheet_name="passengers", index=False)
```


### Series

```python
import pandas as pd

titanic = pd.read_csv("data/titanic.csv")
ages = titanic["Age"]
ages.head()
type(titanic["Age"])

# 行列数
titanic.shape
titanic["Age"].shape

# 多列
titanic[["Age", "Sex"]]

# 过滤row > == != < <=
above_35 = titanic[titanic["Age"] > 35]     # Age > 35
above_35.head()

class_23 = titanic[titanic["Pclass"].isin([2, 3])]
class_23.head()

age_no_na = titanic[titanic["Age"].notna()] # Age非空
age_no_na.head()
```