# python设计模式

* 设计模式

设计模式是前人通过工作总结和提炼，针对某一个问题而形成的成熟的解决方案

* 单例设计模式

让类创建的对象，只有一个实例

### ——new——方法

* 使用类名()创建对象时，完成了两个过程，分配空间和初始化，分别是__new__,__init__完成，我们可以重写new方法，来达成单例的效果
* 注意点：重写new方法一定要return super().__new__(cls)

```python
class A:
    instance = None
    # 创建类属性
	def __new__(cls,*args,**kwargs):
        if cls.instance is None:
            cls.instance = super().new(cls)
       	return cls.instance
	# 分配空间的过程只被执行一次
    init_flag = False
    def __init__(self):
        if A.init_flag:
            return
        A.init_flag = True
```

