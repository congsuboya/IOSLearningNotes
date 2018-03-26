## NSString类型

也就是字符串类型，应该是OC中使用比较频繁的基本类型。

#### 1、创建与初始化

创建与初始化与Android 区别不大，都是可以先声明对象或者是直接赋值。

oc代码：

```
NSString *str1 = [[NSString alloc]init]//声明string串,这个时候虽然声明了一个String串类型但是值是nil;
NSString *str2 = @"123abc";//直接赋值的方式
```

Android 代码

```
String str = new String();
String str = "123abc";
```



