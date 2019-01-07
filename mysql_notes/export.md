导出

```mysql
select * into outfile 文件地址 [控制格式] from 表名;   -- 导出表数据

load data [local] infile 文件地址 [replace|ignore] into table 表名 [控制格式]; -- 导入数据
    生成的数据默认的分隔符是制表符
    local未指定，则数据文件必须在服务器上
    replace 和 ignore 关键词控制对现有的唯一键记录的重复的处理

```

```mysql
-- 控制格式
fields  控制字段格式
默认：fields terminated by '\t' enclosed by '' escaped by '\\'
    terminated by 'string'  -- 终止
    enclosed by 'char'      -- 包裹
    escaped by 'char'       -- 转义
    -- 示例：
        SELECT a,b,a+b INTO OUTFILE '/tmp/result.text'
        FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"'
        LINES TERMINATED BY '\n'
        FROM test_table;
lines   控制行格式
默认：lines terminated by '\n'
    terminated by 'string'  -- 终止
```

