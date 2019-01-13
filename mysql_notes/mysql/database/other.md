#`Mysql中的其他复杂的小东西`
```markdown
正则表达式 regexp
^ 匹配字符串开始位置
$ 匹配字符串的结束位置
. 匹配除了"\n"之外的任何单个字符 要包含"\n"在内的任何字符，使用'[.\n]'的模式
[...]字符集合，匹配未包含的任意字符 
[^...] 负值字符集合，匹配未包含的任意字符
p1|p2|p3 匹配p1,p2或p3  'z|food' 能匹配 "z" 或 "food"。'(z|f)ood' 则匹配 "zood" 或 "food"。
* 匹配前面的子表达式零次或多次 等价于{0,}
+ 匹配前面的子表达式一次或多次 等价于{1,}
{n,m} m m均为非负整数，其中 n<=m 最少匹配n次且最多匹配m次
```
##`事务`
```markdown
mysql中只有使用了innodb数据库引擎的数据库或表才支持事务
事务用来维护数据库的完整性，保证成批的sel语句要么全部执行,要么全部不执行
事务用来管理 insert update delete语句
应用场景
人员管理系统，删除一个人员，可能需要删除多个表，这些数据库操作语句就是一个事务
```
```markdown
事务必须满足4个条件 
原子性（Atomicity，或称不可分割性）、一致性（Consistency）、隔离性（Isolation，又称独立性）、持久性（Durability）
```
```markdown
原子性：一个事务（transaction）中的所有操作，要么全部完成，要么全部不完成，不会结束在中间某个环节。事务在执行过程中发生错误，会被回滚（Rollback）到事务开始前的状态，就像这个事务从来没有执行过一样。

一致性：在事务开始之前和事务结束以后，数据库的完整性没有被破坏。这表示写入的资料必须完全符合所有的预设规则，这包含资料的精确度、串联性以及后续数据库可以自发性地完成预定的工作。

隔离性：数据库允许多个并发事务同时对其数据进行读写和修改的能力，隔离性可以防止多个事务并发执行时由于交叉执行而导致数据的不一致。事务隔离分为不同级别，包括读未提交（Read uncommitted）、读提交（read committed）、可重复读（repeatable read）和串行化（Serializable）。

持久性：事务处理结束后，对数据的修改就是永久的，即便系统故障也不会丢失
```
_在 MySQL 命令行的默认设置下，事务都是自动提交的，即执行 SQL 语句后就会马上执行 COMMIT 操作。因此要显式地开启一个事务务须使用命令 BEGIN 或 START TRANSACTION，或者执行命令 SET AUTOCOMMIT=0，用来禁止使用当前会话的自动提交。_
```markdown
BEGIN或START TRANSACTION；显式地开启一个事务；

COMMIT；也可以使用COMMIT WORK，不过二者是等价的。COMMIT会提交事务，并使已对数据库进行的所有修改成为永久性的；

ROLLBACK；有可以使用ROLLBACK WORK，不过二者是等价的。回滚会结束用户的事务，并撤销正在进行的所有未提交的修改；

SAVEPOINT identifier；SAVEPOINT允许在事务中创建一个保存点，一个事务中可以有多个SAVEPOINT；

RELEASE SAVEPOINT identifier；删除一个事务的保存点，当没有指定的保存点时，执行该语句会抛出一个异常；

ROLLBACK TO identifier；把事务回滚到标记点；

SET TRANSACTION；用来设置事务的隔离级别。InnoDB存储引擎提供事务的隔离级别有READ UNCOMMITTED、READ COMMITTED、REPEATABLE READ和SERIALIZABLE。
```
##`MYSQL 事务处理主要有两种方法：`
1、用 BEGIN, ROLLBACK, COMMIT来实现
```markdown
BEGIN 开始一个事务
ROLLBACK 事务回滚
COMMIT 事务确认
```
2、直接用 SET 来改变 MySQL 的自动提交模式:
```markdown
SET AUTOCOMMIT=0 禁止自动提交
SET AUTOCOMMIT=1 开启自动提交
```
#`索引`
索引分为单列索引和多列索引
单列索引包含单个列，一个表可以有多个单列索引
组合索引包含多个列
