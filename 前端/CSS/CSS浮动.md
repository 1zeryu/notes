# CSS浮动

## 浮动的作用

* 制造图文的环绕效果
* 排版文档

## 浮动的代码

```css
float: left;
float: right;
/* 分别是左浮动和右浮动 */
```

## 浮动的特点

1. 浮动元素会脱离标注流，在标准流中不占位置
2. 浮动元素标准流元素高半个级别，可以覆盖标准流中的元素
3. 浮动找浮动，下一个浮动元素会在上一个浮动元素后面左右浮动
4. 浮动元素有特殊的显示效果

## 清除浮动

原因：

​	元素子元素中运用浮动且父元素未定义height，那么子元素会覆盖其他元素

方法：

* 直接法： 给父元素添加height属性
* 额外标签法
* 单伪元素清除法
* 双伪元素清除法：可以解决塌陷问题
* 终极方法：overflow: hidden