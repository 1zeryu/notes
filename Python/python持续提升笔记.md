# python程序提升笔记

## {\*}args和**kargs的区别

​	args和kargs只是一种人为规定的写法，并没有特别的作用，真正起作用的是* 和 * 两个符号，* 表示后续的是不定的参数， **表示不定键值对，如果你像传入带名参数，那么要用 * *

并且在实际使用中，标准参数，不定参数，不定键值对参数按顺序调用

## map，filter，reduce三件套函数

### map

* 使用规范：map(function_to_apply, list_of_inputs)

比如说我们要使列表中的数据加1

```python
# a 表示我们已有的列表
a = map(lambda x: x+1,a)
```

### filter 过滤函数

* 用于保留一个列表中满足条件的数据

比如说我们要保留列表中为偶数的数据

```python
# a是列表
a = filter(lambda x: x%2==0,a)
```

## format格式化输出方法

https://www.cnblogs.com/lovejh/p/9201219.html

