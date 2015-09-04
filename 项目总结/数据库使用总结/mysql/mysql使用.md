#mysql的语法和使用

##1.select语句

select语句用于从数据表中检索数据。

语法如下：

SELECT 所选字段列表 FROM 数据表名

WHERE 条件表达式 GROUP BY 字段名 HAVING 条件表达式（指定分组的条件）

ORDER BY 字段名[ASC|DESC];

##2.insert语句

insert语句用于向表中插入新数据。

语法如下：

INSERT INTO 表名[(字段名1，字段名2，…)]

VALUES(属性值1，属性值2，……);

##3.update语句

update语句用于更新数据表中的某些记录。

语法如下：

UPDATE 数据表名 SET 字段名 = 新的字段值 WHERE 条件表达式;

##4.delete语句

delete语句用于删除数据。

语法如下：

DELETE FROM 数据表名 WHERE 条件表达式;
