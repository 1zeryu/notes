# HTML表单

## 文本框text

代码语法: 

```css
<input type="text" value="" size="" placeholder="">
/* size设置文本框大小，value设置初始值，placeholder设置背景文字 */
```

## 密码框password

代码语法：

```css
<input type="password">
/* 密码框的输入会自动变为*号 */
```

## 表单form

表单元素用于向服务器提交数据，比如账号密码

```html
<form method=”“ action=" ">
    账号：<input type="text" name="name"> <br/>
    密码：<input type="password" name="password"> <br/>
    <input type="submit" value="登录">
</form>
<!-- method属性用于给定提交数据的方式，action属性用于指定提交数据的地址-->
```

常用的提交方式有get(默认方法) 和 post，post'的安全性更好，所以一般的密码提交是用post, get方式不可以提交二进制数据

## 单选框radio

代码语法：

```html
<input type="radio" checked name="" value="">
<!-- 单选框的checked是布尔属性，表示是否默认选中，name表示分组信息，value表示向服务器提交的值 -->
```

## 复选框checkbox

代码语法：

```html
<input type="checkbox" checked name="" value="">
```

属性同单选框相同

## 下拉列表select

select 标签是下拉列表的总标签，option标签表示下拉标签的选项

select属性：

* size属性：值为数，表示显示的选项个数

* multiple：布尔属性，表示是否可以多选

  

option属性：

* selected：布尔属性，表示是否选中

## 文本域textarea

与文本框不同的是，文本域可以有多行，并且可以有滚动条

属性：

* cols与rows：指定有多少行和列

## 普通按钮button

代码语法：

```html
<input type="button" value="">
```

普通按钮不具备提交表单的功能

## 提交按钮submit

用于提交form，把数据交到远端

## 重置按钮reset

用于把输入框复原

