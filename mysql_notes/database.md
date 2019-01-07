连接与断开服务器

```mysql
mysql -h 地址 -P 端口 -u 用户名 -p 密码
SHOW PROCESSLIST -- 显示哪些线程正在运行
SHOW VARIABLES -- 显示系统变量信息
```

数据库操作

```mysql
-- 查看当前数据库
    SELECT DATABASE();
```

```mysql
-- 显示当前时间、用户名、数据库版本
    SELECT now(), user(), version();
```

```mysql
-- 创建库
    CREATE DATABASE[ IF NOT EXISTS] 数据库名 数据库选项
    数据库选项：
        CHARACTER SET charset_name
        COLLATE collation_name
```

```mysql
-- 查看已有库
    SHOW DATABASES[ LIKE 'PATTERN']
```

```mysql
-- 查看当前库信息
    SHOW CREATE DATABASE 数据库名
-- 修改库的选项信息
    ALTER DATABASE 库名 选项信息
-- 删除库
    DROP DATABASE[ IF EXISTS] 数据库名
        同时删除该数据库相关的目录及其目录内容
```

