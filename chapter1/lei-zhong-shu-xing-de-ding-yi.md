## 类中的属性

类中的属性定义在.h文件中。属性以@property关键词声明，定义格式为

关键词 + 属性修饰词+属性类型+属性名称；

关键词为@property,

属性修饰词为

1、nonatomic 非原子性访问，不加同步，多线程并非访问会提高性能。与之对应的atomic是原子性，线程安全，但是性能较差。

2、assign表示的是直接复制非指针变量，不会产生内存管理的代码，当属性是一个基本数据类型时使用，如 int float bool等基本类型。

3、copy 用来修饰NSString的对象类型。建立一个引用计数为1的新对象，不对原对象的引用计数做改变，建立新对象释放旧对象。使用copy关键字必须要实现NSXopying协议。copy是内容拷贝。

4、retain用来修饰除了NSString的其他对象类型。释放旧的对象，将旧对象的值赋予输入对象，再提高输入对象的索引计数为1。retain是指针拷贝。

5、weak 对象的弱引用，不会增加对象的引用计数，也不会持有对象，当对象消失后指针自动指向nil,所以这里也就防止了野指针的存在。

6、strong 对象的强引用，会增加对象的引用计数，如果指向了一个空对象，会造成野指针，平常用的最多的也是strong。

代码示例如下：

```cpp
#import <Foundation/Foundation.h>

@interface Person :NSObject
    //属性的声明
    @property(nonatomic,assign) int age;
    @property(nonatomic,copy)NSString *name;

@end
```

OC中属性的声明其实就是Android中类的公共属性的定义，Android代码如下：

```java
public class Person{
    public int age;
    public String name;
}
```

## OC中的setter与getter方法

既然普通的属性定义是公共属性，那为了安全的私有属性定义OC也有，被称为内部属性。而这个内部属性的调用也是通过声明的setter和getter方法。这里与Android类中私有方法的定义和暴露如出一辙。

.h文件中的声明

```cpp
#import <Foundation/Foundation.h>

@interface Person :NSObject{ //内部属性的定义
    int age;
    NSString *name;
}
-(void)setAge:(int)newAge;//age属性对应的setter方法  定义格式为set + 变量名称(首字母大写)
-(int)age;//age属性对应的getter方法  定义格式为返回值类型 + 变量名称

@end
```

.m文件中的实现

```cpp
#import "Person.h"

@implementation Person
-(void)setAge:(int)newAge{//set方法的实现
    ...//这里可以加一些逻辑判断
    age = newAge;
}
-(int)age{//get方法的实现
    ...//这里可以加一些逻辑判断
    return age;
}
@end
```

主函数中的调用

```
#import <Foundation/Foundation.h>
#import "Person.h"

int main(int argc, const char * argv[]){

    @autoreleasepool{
        Person *per = [[Person alloc]init];
        per.age = 18;//调用set方法
        NSLog(@"age=%d",per.age);//调用get方法
    }
    return 0;
}
```



