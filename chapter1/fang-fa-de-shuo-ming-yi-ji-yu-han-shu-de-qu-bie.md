# OC中的方法

oc中的方法分类方法和对象方法。两者创建标示不同，并且调用的时候也是有区别的。在.h文件中声明时必须再@interface与@end之间，在.m文件中进行实现时必须再@implementation与@end之间。同Android相比，OC中的类方法相当于Android的静态方法，用static修饰，对象方法则相当于普通类方法，没有static来进行修饰。

类方法声明格式 ：+ \(返回值\)方法名称:\(参数类型\)参数名1 参数名2:\(参数类型\) 参数名2 ....；

对象方法声明格式：- \(返回值\)方法名称:\(参数类型\)参数名1 参数名2:\(参数类型\) 参数名2 ....；

.h文件内代码示例：

```
import <Foundation/Foundation.h> //头文件 

@interface Person : NSObject

  +(void)clearClassRoom;//类方法
  -(void)study;//对象方法
  -(void)study:(NSString *)subject;//对象方法
  -(void)study:(NSString *)subject time:(int)time;
@end
```

.m文件内代码示例：

```
import "Person.h"

@implementation Person

+(void)clearClassRoom{
    NSLog(@"我是一个学生，我应该打扫教室");
}

-(void)study{//实现.h文件中声明的方法，如果没有参数不需要写()直接在方法后面跟{}即可。
    NSLog(@"我正在学习");
}

-(void)study:(NSString*)subject{
    NSLog(@"我正在学习%@",subject);
}
-(void)study:(NSSting*)subjcect time:(int)time{
    NSLog(@"我正在学习%@,我已经学习了%i小时了",subject,time);
}
@end
```



