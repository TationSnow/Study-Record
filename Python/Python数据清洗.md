



```Python
import pandas as pd
import numpy as np
```

```python
df = pd.read_csv(".csv文件路径")
df.head()
```



##  删除无用列

drop函数:

drop(columns = [列表] ,inplace = 布尔)

| 属性    | 值       | 作用                  |
| ------- | -------- | --------------------- |
| columns | 列表     | 可删除多列            |
| inplace | 布尔类型 | 是否在DataFrame中删除 |

```Python
df.drop(columns="列名").head(5)
```

```Python
df.head(5)
```

Tip：此时并没有在DataFrame中彻底删除这一列，需要添加上inplace属性

| 属性    | 值       | 作用                  |
| ------- | -------- | --------------------- |
| columns | 列表     | 可删除多列            |
| inplace | 布尔类型 | 是否在DataFrame中删除 |

```Python
df.drop(columns=["列名0","列名1"],inplace=True).head(5)
```

```Python
df.head(5)
```






## 类型转换







## 删除重复行





## 