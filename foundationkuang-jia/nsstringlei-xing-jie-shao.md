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

#### 2、类型之间的转换

虽然字符串类型是对象，但是再OC和Android中可以与其他基本类型互相转化。OC中其他类型转为字符串主要是使用NSString类的stringWithFormat方法，格式为\[NSString stringWithFormat:@"xx", yy\]；其中xx为要转为字符串的其他类型的缩写如int为%i float类型为 %f等,yy为实际值。

oc代码:

```cpp
NSString *str1 = [NSString stringWithFormat:@"%d",123];//str1的值为“123”；
NSString *str2 = [NSString stringWithFormat:@"%f",123.21];//str1的值为“123.21”；
```

Android 代码:

```java
String str1 = 123 + "";//
String str2 = String.valueOf(123);
String str3 = String.valueOf(12.21);
```



