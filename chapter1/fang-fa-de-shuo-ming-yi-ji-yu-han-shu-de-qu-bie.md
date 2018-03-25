## OC中的方法

oc中的方法分类方法和对象方法。两者创建标示不同，并且调用的时候也是有区别的。

1、方法都是以 - \(对象方法\) 或者 + \(类方法\)开头。

2、方法的声明必须写在.h文件中的@interface和@end之间。

3、方法的实现必须写在.m文件中的@implementation和@end之间。

4、对象方法只能由对象来调用，类方法只能由类来调用。

5、对象方法归对象所有，类方法归类所有。

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

#### 与Android的区别

同Android相比，OC中的类方法相当于Android的静态公共方法，用public和 static修饰，对象方法则相当于普通类方法，没有static来进行修饰。

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

## OC中的函数

1、函数能写在文件中的任意位置\(@interface和@end之间\)，函数归文件所有

2、函数调用不依赖于对象，所有函数不存在隶属关系

3、函数内部不能直接通过成员变量名访问某个对象的成员变量

代码示例如下：

```cpp
#import <Foundation/Foundation.h>

void eating(){
    NSLog(@"我是一个函数，我要吃饭");
}

int main(int argc, const char * argv[]){

    @autoreleasepool{
        Person *per = [[Person alloc]init];
        [per study:@"Object-c" time:18]//对象方法的调用

        [Person clearClassRoom];//类方法的调用
    }
    return 0;
}
```



