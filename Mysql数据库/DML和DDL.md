# 表

## 表的创建

建表的语法格式（DDL语句，包括create drop alter）

语法：create table 表名 （字段名1 数据类型，字段名2 数据类型，字段名3 数据类型）；

建议： 表名最好从t _ 开始，或者tbl_开始,字段名见名知意

### 给定默认值(default)

​	在创建表的字段时，可以在数据类型后加空格，再加default 默认值

```mysql
create table t_student(
	no int,
    name varchar(32),
    sex char(1) default 'm',
    age int(3),
    email varchar(255)
);
```



## 关于mysql的数据类型

> * varchar:可变长度的字符串，可以动态分配，节省空间但是效率较慢
> * char：定长字符串，固定空间可能造成空间浪费，但是执行效率高
> * int：数字中的整形，等同于java中的int
> * bigint：数字中的长整形，等同于java中的long
> * float：单精度浮点型
> * double：双精度浮点型
> * date：短日期类型
> * datetime：长日期
> * clob：字符大对象，最多可以存储4g的字符串，而char和varchar对多存255个字符
> * blob：二进制大对象，专门用来存图片，声音，视频等媒体数据

## 删除表

语法：drop table 表名; 这个语句如果表不存在就会报错

改进语法：drop table  if exists 表名;

## 插入数据insert（DML)

语法格式：

```mysql
insert into 
表名 (字段名1，字段名2，字段名3,...) values (值1,值2，值3,...);
```

注意：字段名和值要一一对应，数量对应，数据类型对应

insert字段名可以省略，这样默认就使用了所有字段

### insert插入一次多条记录

语法：

insert	into	表名(字段表) values(值表1),(值表2),()...;

### 插入日期

str_to_date(日期字符串，日期格式),日期格式%Y,%m,%d,%h,%i,%s，如果你提供的字符串格式是%Y-%m-%d，那么str_to_date可以省略

date_format可以将日期类型以特点的格式展示，date_format(birth,'%m/%d/%Y')

### date和datetime的区别

date是短日期：只包括年月日信息，datetime是长信息，包括年月日时分秒信息

默认格式：

* date：%Y-%m-%d
* datetime: %Y-%m-%d %h:%i:%s

在mysql中，获取当前时间信息可以用now()函数，返回datetime类型数据

## 修改表信息

语法格式：

​	update 表名 set 字段名=值1，字段名2=值2，字段名3=值3... where 条件；

注意：如果没有条件的话，会导致所有表信息更新

## 删除表中数据delete（DML)

语法格式：

​	delete	from	表名	where	条件；

注意：没有条件，整个表的数据会全部删除

删除整个表的语法：delect	from	表名;

这种删除的方式是将表中的数据删除，但是数据在硬盘上的真实存储空间不会释放，可以回滚，缺点是效率比较低

### 快速删除表中数据

truncate	table	表名

这种方式效率高，但是无法回滚

## 表的复制

create table 新的表名 as select * from 复制的表名;

原理：把select的结果作为处理对象来创建表，这个时候，旧表中的数据都会被复制

## 修改表的结构

什么是对表的结构：对字段的增删改

方式：可以通过工具修改，而且一般不会修改，如果要修改可以用到alter语句

## 约束constraint

概念：在创建表中，可以给表中字段加上一些约束，来保证表中数据的完整性，有效性

添加方式：在创建表时在字段后面加入约束关键字

类型：

* 非空约束	not null
* 唯一性约束   unique
* 主键约束   primary key
* 外键约束   foreign key
* 检查约束

### not null非空约束

表示必须在insert时，不能使该字段的值为空

### unique唯一性约束

唯一性约束的字段不能重复，但是可以为null

联合唯一性：表示两个值如果同时相同时，不符合联合唯一，要与各自唯一区别，方式如下代码

```mysql
create table t_vip{
	id int,
	name varchar(255),
	email varchar(255),
	unique(name,email)
};
```

约束添加到列后面，这种约束被称为表级约束，需要给多个字段联合起来添加某个约束的时候，需要使用表级约束

一个字段可以添加多个约束，比如说not null 和 unique，在mysql中，如果一个字段同时被not null 和 unique约束后，那么这个字段自动成为主键

### 主键约束（primary key，简称pk）

相关术语：

*  主键字段：具有主键约束的字段
* 主键值：主键字段中的每一个值，叫做主键值，主键值是每一行记录的唯一标识，相当于身份证号，通过主键我们可以找到唯一的数据

主键是表级约束，一个字段做主键叫做单一主键，可以多个字段联合起来做主键，叫复合主键

主键只能有一个，建议使用int bigint char类型

自然主键和业务主键：

* 自然主键：主键是一个自然数，和业务没有关系

* 业务主键：主键值和业务值紧密相关

  主键值可以采用自增的方式生成，关键字为auto_increment，这是一个列级修饰

## 外键约束（foreign key，简称FK）

外键约束相关术语：

* 外键字段
* 外键值

```mysql
create table t_class{
	classno int primary key,
	classname varchar(255),
}

create 	table t_student{
	no int primary key auto_incriment,
	name varchar(255),
	cno int ,
	foreign key(cno) references t_class(classno)
}
```

外键值必须为空，外键中父表的字段，不一定是主键，但是至少具有唯一性unique

对具有外键的表中，增加表和删除表的顺序需要注意，子表存在，父表一定要存在

