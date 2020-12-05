## Generate MySQL Data Dictionary (生成MySQL数据字典)

### 方式一、通过SQL生成数据字典
```sql
USE information_schema;
SELECT
	T.TABLE_SCHEMA AS '数据库名称',
	T.TABLE_NAME AS '表名称',
	T.TABLE_COMMENT AS '表说明',
	T.TABLE_TYPE AS '表类型',
	T.ENGINE AS '数据库引擎',
	C.ORDINAL_POSITION AS '序号',
	C.COLUMN_NAME AS '字段名',
	C.COLUMN_TYPE AS '数据类型',
	C.IS_NULLABLE AS '允许为空',
	C.EXTRA AS '自增属性',
	C.CHARACTER_SET_NAME AS '编码名称',
	C.COLUMN_DEFAULT AS '默认值',
	C.COLUMN_COMMENT AS '字段说明' 
FROM
	COLUMNS C
	INNER JOIN TABLES T ON C.TABLE_SCHEMA = T.TABLE_SCHEMA 
	AND C.TABLE_NAME = T.TABLE_NAME 
WHERE
	T.TABLE_SCHEMA = 'db_name' -- 此处修改为你要导出的数据库名称
```

### 生成样例
![数据字典](images/mysql-data-dictionary.png)

### 导出结果
![导出结果](images/mysql-export-dictionary.png)

**缺点：** 排版和样式一团糟，所有表字段全部一个表格里，阅读困难



### 方式二、通过Python生成数据字典
Python环境装好后，安装以下驱动
- pip install pymysql
- pip install python-docx
- pip install mysql-connector-python

### 生成样例

通过Python生成的markdown文档，可以使用功能强大的[Typora](https://www.typora.io/)编辑器打开，也可以通过该编辑器生成不同类型的文档

![数据字典](images/python-data-dictionary.png)


### 导出结果

![导出结果](images/python-export-dictionary.png)

### 方式三、MySQL-Front

### ~~方式四、DBExportDoc~~
