#`table`

```markdown
create table tableName (
column_Name column_type,
    .
    .
    .
column_Name column_type
);    创建表
show table status;查看表类型

```
```markdown
修改语句
alter table tableName rename newName; 修改表名
alter table tableName add column newColumnName newColumnType;添加列
alter table tableName drop column columnName;删除列
alter table tableName modify columnName newColumnType;修改列类型
alter table tableName change columnName columnName newColumnType;修改列类型
alter table tableName change column columnName new columnName columnType;修改表列名
修改字段时可以对null值和默认值的影响
可以指定是否包含值或者是否设置默认值 default
alter table tableName alter fieldName set default value; 修改字段默认值
alter table tableName alter fieldName drop default;删除字段默认值
```
```markdown
not null 
auto_increment 
primary key
engine设置存储引擎 charset设置编码
```
```markdown
drop tabel tableName; 删除数据库
```
##`表的增删改查`
```markdown
insert into tableNme(field1,field2...fieldn) values(value1,value2..valuen);
如果数据是字符型，必须使用单引号或者双引号
```
```markdown
select column_Name,column_Name from table_Name [where (Clause)][limit n][offset m];
limit设定返回的记录数
offset指定select语句开始查询数据偏移量，默认是0
```
```markdown
select语句
SELECT field1, field2,...fieldN FROM table_name1, table_name2...
[WHERE condition1 [AND [OR]] condition2.....
where子句的字符串是不区分大小写，可以使用BINARY关键字来设定where子句的字符串比较是区分大小写的
select from tableName where BINARY columnName='value';
```
```markdown
update语句
update tableName set fieldName1 = new value1,fieldName2=new value2 [where clause];
```
```markdown
delete语句
delete from table_Name [where clause];
```
```markdown
like子句 模糊查询
_ %
```
```markdown
union操作符
连接多个select语句组合到一个结果集合中，多个select会删除重复的数据SELECT expression1, expression2, ... expression_n
 FROM tables
[WHERE conditions]
UNION [ALL | DISTINCT]
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions];
expression1, expression2, ... expression_n: 要检索的列。

也可以在select 后面加上distinct 去重

tables: 要检索的数据表。
WHERE conditions: 可选， 检索条件。
DISTINCT: 可选，删除结果集中重复的数据。默认情况下 UNION 操作符已经删除了重复数据，所以 DISTINCT 修饰符对结果没啥影响。
ALL: 可选，返回所有结果集，包含重复数据。
```
```markdown
order by 排序语句用在where语句中
dest逆序
asc升序
```
```markdown
group by语句
在where子句中可以根据一个或多个列对结果集进行分组，在分组的列上可以使用count,sum,avg...函数
```
##`join`
```markdown
inner join 获取两个表中字段匹配关系的记录
left join 左连接 获取左表中的记录，即使右表没有对应记录
right join 右链接 
```
```markdown
select a.name,b.sex,a.age from table1 t1 inner join table2 t2 on t1.name = t2.name;
等价于
select a.name ,b.sex,a.age from table1 t1 ,table2 t2 where t1.name = t2.name; 
```
`NULl值处理`
```markdown
is null 
not null
<=>
```
~~不是很明白~~