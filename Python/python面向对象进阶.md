# python面向对象进阶

## 私有属性和私有方法

### 引用场景

* 在实际开发中，对象的属性和方法可能只希望在对象的内部使用，而不希望在外部被访问到，称为私有属性，私有方法
* 私有属性和方法，不能再类定义外部访问，可以再内部访问

定义方式： 在属性名前添加__（两个下划线）

### 伪私有属性和私有方法

​	再python中，没有真正意义上的私有属性和私有方法，而是做了以下处理：在名称前加上   _类名__私有方法

## 面向对象三大特性：

封装：根据对象的职责把属性和方法封装到一个抽象的类中

继承：实现代码的重写，减少不必要的编写

多态：不同的对象调用相同方法名的方法，产生不同的结果，减少取名忧愁，增加灵活度

## 继承

语法： 

```python
class Animal:
    pass
class Dog(Animal):
# Dog类继承了Animal类的方法和属性
```

专业术语：

子类==派生类，父类==基类，继承==派生

继承的传递性：

子类拥有父类的父类的封装的方法和属性

### 方法的重写

当父类的方法不能满足子类的需求时，可以对方法进行重写

* 覆盖父类的方法
* 对父类的方法进行扩展

覆盖父类的方法

重新编写父类方法，只需要在子类中定义一个和父类同名的方法，在执行时，只执行子类的方法

扩展父类的方法

父类原来的封装方法是子类方法的一部分，具体方式是使用super函数

```python
class Animal:
    def bark(self):
        pass
class Dog(Animal):
    def bark(self):
        super().bark()
        print("叫")
# 在super位置先调用了父类的bark方法，在继续进行扩展的方法
```

### super类

super是一个特殊的类，super()是创建一个父类的方法

## 继承下的私有方法和私有属性

* 子类不能直接访问父类的私有属性和私有方法，但是可以通过公有方法间接访问

## 多继承

```python
class A(父类1，父类2,...):
    pass
```

注意事项：不同的父类有同名的方法，如果父类拥有同名的属性和方法，应该避免多继承

面对多继承且出现父类同名方法时，python解释器通过MRO顺序来搜索方法，可以通过内置函数mro来查看搜索顺序

```python 
class A(B,C):
	pass
A.__mro__()
```

## 多态

* 继承加重写

## 类对象

类在python中是一个特殊的对象，在运行过程中，类也会被加载到内存中，访问类属性是类名.类属性，

查找类属性是向上查找机制

类方法：类方法不是对象的实例方法，而是相当于Java的抽象方法，不需要实例化类就可以调用，

```python
class Animal:
    @classmethod
    def 类方法名(cls,...):
        pass
   # 第一个参数是cls，class的缩写，他是类对象的引用，@后是一个修饰器
```

### 静态方法

* 在调用方法时，不需要访问对象属性
* 也不访问类属性

```python
class Dog:
    @staticmethod
	def run():
        print("")
```

## 一些BIF

* issubclass(B,A) 判定B是否是A类的子类
* isinstance(B,A) 判断B是否是A类的实例
* hasattr(object,name) ,  getattr(object,name,default) ,  setattr(object, name, value), delattr()
* property(fget=None,fset=None,fdel=None)

## 属性访问魔法方法

* __getattribute__(self,name)：访问存在的属性时，调用的方法
* __setattr__(self,name,value)：设置属性时调用的方法
* __getattr__(self,name)：访问不存在的属性时调用的方法
* __delattr__(self,name)：删除属性时调用的方法

常用于扩展方法，最后要加super().__方法名__(name)

