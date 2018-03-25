## 方法的声明、实现以及调用

oc中的方法分类方法和对象方法。两者创建标示不同，并且调用的时候也是有区别的。在.h文件中声明时必须再@interface与@end之间，在.m文件中进行实现时必须再@implementation与@end之间。同Android相比，OC中的类方法相当于Android的静态方法，用static修饰，对象方法则相当于普通类方法，没有static来进行修饰。

类方法声明格式 ：+ \(返回值\)方法名称:\(参数类型\)参数名1 参数名2:\(参数类型\) 参数名2 ....；

对象方法声明格式：- \(返回值\)方法名称:\(参数类型\)参数名1 参数名2:\(参数类型\) 参数名2 ....；

.h文件内代码示例：

```cpp
import <Foundation/Foundation.h> //头文件 

@interface Person : NSObject

  +(void)clearClassRoom;//类方法
  -(void)study:(NSString *)subject time:(int)time;//对象方法
@end
```

.m文件内代码示例：

```cpp
import "Person.h"

@implementation Person
+(void)clearClassRoom{//类方法
    NSLog(@"我是一个学生，我应该打扫教室");
}

-(void)study:(NSSting*)subjcect time:(int)time{//对象方法
    NSLog(@"我正在学习%@,我已经学习了%i小时了",subject,time);
}
@end
```

## 方法的调用

OC中类方法直接通过类名来进行调用，而对象方法直接通过示例的对象进行调用

调用代码如下：

```cpp
#import <Foundation/Foundation.h>
#import "Person.h"//引入定义的类的头文件

int main(int argc, const char * argv[]){

    @autoreleasepool{
        Person *per = [[Person alloc]init];
        [per study:@"Object-c" time:18]//对象方法的调用

        [Person clearClassRoom];//类方法的调用
    }
    return 0;
}
```

输出：

```
我正在学习Object-c,我已经学习了18个小时
我是一个学生，我应该打扫教室
```

Android代码示例

```java
public class Person{

    //类似OC中对象方法的声明与定义
    public void study(String subject,int time){
        Log.e("study","我正在学习" + subject + ",我已经学习了" + time + "小时");
    }

    //类似OC中类方法的声明与定义    
    public static void clearClassRoom(){
        Log.e("study","我是一个学生，我应该打扫教室");
    }
}

.........

import android.app.study.Person;//导入定义的类
.....

public class MainActivity extends Activity{
    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main_demo);

        Person per = new Person();
        per.study("Object-c",18);//类似OC中的对象方法的调用

        Person.clearClassRoom();//类似OC中的类方法
    }
}
```

输出：

```
study,我正在学习Object-c,我已经学习了18个小时
study,我是一个学生，我应该打扫教室
```

## 函数的声明、实现以及调用

在

