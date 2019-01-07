### mysql_user

用户的创建

```mysql
CREATE USER 'username'@'host' IDENTIFIED BY 'password';
```

用户的授权

```mysql
GRANT privileges ON databasename.tablename TO 'username'@'host' WITH GRANT OPTION;
```

修改密码

```mysql
SET PASSWORD FOR 'username'@'host' = PASSWORD('newpassword');
```

撤销用户权限

```mysql
REVOKE privilege ON databasename.tablename FROM 'username'@'host';
```

删除用户

```mysql
DROP USER 'username'@'host';
```

开启远程连接

```mysql
GRANT ALL PRIVILEGES ON databasename.tables TO 'username'@'%' IDENTIFIED BY 'password' WITH GRANT OPTION;
```

