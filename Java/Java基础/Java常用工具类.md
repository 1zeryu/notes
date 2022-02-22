# Java常用工具类

## Scanner类

使用步骤：

1. 导包
2. 创建对象
3. 接收数据

```java
import java.util.Scanner;

Scanner sc = new Scanner(System.in);
int a = sc.nextInt();
float f = sc.nextFloat();
```

## Random

作用：产生一个随机数

使用步骤：

1. 导包
2. 创建对象
3. 获取随机数

示例：

``` java
import java.util.Random;

Random r = new Random();
int x = r.nextInt(10);	// 获取0-10之间的数字
int y = r.nextInt(10) + 1; // 获取1-11之间的数字

```

