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

虽然字符串类型是对象，但是再OC和Android中可以与其他基本类型互相转化。OC中其他类型转为字符串主要是使用NSString类的stringWithFormat方法。**格式为\[NSString stringWithFormat:@"xx", yy\] **其中xx为要转为字符串的其他类型的缩写，如int为%i float类型为 %f等,yy为实际值。

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

字符串转为其他类型OC主要是使用NSString类的自身属性，NSString类自身有只读类型的属性分别为intValue、floatValue、doubleValue，三者分别对应于int类型、float类型以及double类型。相对于Android  OC中字符串转为其他类型更方便，并且，即使字符串不能转为其他类型，也不会报异常而只是赋值为对应类型的基本值。

oc代码:

```cpp
NSString *str1 = [NSString stringWithFormat:@"%d",123];//str1的值为“123”；
str1.intValue;//int类型123
str1.floatValue;//float类型123.00000
str1.doubleValue;//double类型123.00000

//字符串不能转为其他基本类型
NSString *str2 = @"sdfwer";
str2.intValue;//int类型0
str2.floatValue;//float类型0.00000
str2.doubleValue;//double类型0.00000
```

Android 代码:Android 中利用基本数据类型的包装类自带的valueOf方法，可以方便的互相转换。但是当要转换的类型并不能转为制定数据类型时强制转换，则Android会抛出异常xxxFormatException

```java
String str1 = "123";
int num = Integer.valueOf(123);
float f = Float.valueOf(12.21);
```

#### 3、字符串的比较与大小写转换

OC中比较也可以用==，这里的定义与Android中一样，是比较引用内存地址变量是否相等，相等时才会返回true。

像Android 中一样OC中也有只比较内容的方法，为NSString的对象方法 isEqualToString，但是只有这一个方法，并没有提供像Android中忽视大小写的比较方法。

大小写的转换和Android也很想都是提供对象方法，只是OC比Android多一个方法把首字母大写其他都小写。

OC代码：

```cpp
NSString *str1 = [NSString stringWithFormat:@"%@",@"Abc"];
NSString *str2 = @"Abc";
NSString *str3 = @"123";
str1 == str2 //false;比较内存引用地址
[str1 isEqualToString:str2]//true  比较内容
[str1 isEqualToString:str3]//false  比较内容

[str1 lowercaseString]//转为小写 abc
[str1 uppercaseString]//转为大写 ABC
[str1 capitalizedString]//首字母大写其他小写 Abc
```

Android代码:

```java
 String str1 = "Hello World";
 String str2 = "hello world";
 Object objStr = str;

 System.out.println( str1.compareTo(str2) );//返回false
 System.out.println( str.compareToIgnoreCase(str2) );  //忽略大小写 true
 System.out.println( str.compareTo(objStr.toString()));//true
 str1.toLowerCase();//hello world
 str1.toUpperCase();//HELLO WORLD
```

#### 4、字符串中的索引

索引分为内容索引和位置索引，这点OC引入了结构体类型NSRange。其中提供两个方法 rangeOfString 和substringWithRange。

其实rangeOfString特别像Android中的indexOf方法，调用此方法返回字符串1在字符串2中的位置，rangeOfString方法返回一个结构体NSRange，里面有两个属性一个length代表要比较的字符串的长度，一个location代码字符串的位置。理解了结构体的概念以及内部的两个属性，substringWithRange就比较好理解了，就是传入一个结构体，按这个结构体的属性来切割字符串。

OC代码

```cpp
  NSString *str1 = @"abcdefg";
  NSString *str2 = @"cde";
  NSRange rang;//结构体 字符串的长度 和位置 
  rang = [str1 rangeOfString:str2];
  NSLog(@"%lu %lu",(unsigned long)rang.length,(unsigned long)rang.location);

  NSString *str1 = @"abcdefg";
  NSRange rang;
  rang.length = 2;
  rang.location = 3;
  NSString *str2 = [str1 substringWithRange:rang];
  NSLog(@"%@",str2);//de
```

Android代码

```
String str1 = "abcdefg";
String str2 = "cde";
int num = str1.indexOf(str2);//返回为3不存在时返回-1
```



