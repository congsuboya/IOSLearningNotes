# OC中类的创建和说明

OC中创建一个类，会生成两个文件，一个是 类名.h 文件，一个是 类名.m 文件。而Android 中创建一个类就是只会生成一个 类名.java的文件



### 类文件的说明

.h 表示头文件，用来声明各种成员变量，方法，属性之类的。在import的时候用头文件。示例如下

      .h的文件一定是在@interface 和@end之间。类似Android中的类方法最外面的大括号（{ }）。只有在这两个之间的代码才是类的真正代码。其中如果不指定，默认创建的类集成于NSObject。NSObjec 类似于Android 中的Object对象。并且OC中创建的新类默认会导入Foundation.h系统头文件。而Android中并不会,只是用class关键字来进行修饰。



OC .h文件示例

```cpp
import <Foundation/Foundation.h> //头文件 
@interface Person : NSObject
  ...声明成员变量，方法、属性等
@end
```

Android 类文件示例

```java
public class Person{
  ...声明成员变量，方法、属性等
}
```



