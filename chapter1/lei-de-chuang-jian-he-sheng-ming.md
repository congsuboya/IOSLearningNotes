# OC中类的创建和说明

OC中创建一个类，会生成两个文件，一个是 类名.h 文件，一个是 类名.m 文件。而Android 中创建一个类就是只会生成一个 类名.java的文件

### 类文件的说明

.h 表示头文件，用来声明各种成员变量，方法，属性之类的。在import的时候用头文件。

.h的文件一定是在**@interface **和**@end**之间。类似Android中的类方法最外面的大括号**（{ }）**。只有在这两个之间的代码才是类的真正代码。其中如果不指定，默认创建的类集成于**NSObject**。NSObjec 类似于Android 中的**Object**对象。并且OC中创建的新类默认会导入**Foundation.h**系统头文件。而Android中并不会,只是用**class**关键字来进行修饰。

OC .h文件示例

```cpp
import <Foundation/Foundation.h> //头文件 
@interface Person : NSObject
  ...声明成员变量，方法、属性等
  -(void) study;
  -(void) study:(NSString *)subject;
  -(void) study:(NSString *)subject time:(int)time;
@end
```

.m 主要用来实现.h 里声明的方法。举个例子，如果要写一个方法，你要在.h里先声明。并且.m文件创建是默认导入.h文件，通过这个方式与.h文件互相关联。并且.m文件的代码被**@implementation**和**@end**包裹。注意：oc中方法接受的参数的书写方式与Android的方法是有区别的，当oc方法没有参数时直接后面跟{}再里面实现方法，当有参数时也是:\(参数类型\) 参数名1 参数名2:\(参数类型\) 参数名2... ;

OC .m文件示例

```cpp
import "Person.h"

@implementation Person
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

上述OC的两个文件表达的方法，再Android中一个文件就可以表达，这也是两端的不同。示例代码如下：

Android代码示例：

```java
public class Person{
    public void study(){
        Log.e("study","我正在学习");
    }

    public void study(String subject){
        Log.e("study","我正在学习"+subject);
    }

    public void study(String subject,int time){
        Log.e("study","我正在学习" + subject +  ",我已经学习了" + time + "小时");
    }
}
```





