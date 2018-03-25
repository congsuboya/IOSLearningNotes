## 类别\(Category\)

分类文件也是有.h和.m两个文件，但是命名规则为  类名+分类名.h  和 类名+分类名.m。其主要作用是在不改变原来的类的内容的基础上，为类增加一些方法。

#### 使用注意

1、分类只能增加方法（包括类方法和对象方法），不能增加成员变量。

2、在分类方法的实现中可以访问原来类中的成员变量；

3、分类中可以重新实现原来类中的方法，但是会覆盖掉原来的方法，导致原来的方法无法再使用（警告）

4、方法调用的优先级：分类-&gt;原来的类-&gt;父类，若包含有多个分类，则最后参与编译的分类优先；

5、在很多的情况下，往往是给系统自带的类添加分类，如NSObject和NSString，因为有的时候，系统类可能并不能满足我们的要求。

6、在大规模的应用中，通常把相应的功能写成一个分类，可以有无限个分类，对原有类进行扩充，一般分模块写，一个模块一个分类

#### 代码示例

如给NSString类增加一个类方法，计算字符串中阿拉伯数字的个数；代码如下：

.h文件中的声明

```cpp
#import <Foundation/Foundation.h>

@interface NSString(NUmberOfs)
    +(int)NumberOfString:(NSString *) str;
    -(int)NUmberCount;
@end
```

.m文件中的实现

```cpp
#import "NSString+NumberOfs.h"

@implementation NSString (NumberOfs)
    +(int)NumberOfString:(NSString *)str{
        int count = 0;
        for(int i =0;i<str.length;i++){
            //取出字符串中的第i个位置的字符给c;
            unichar c=[str characterAtindex:i];
            //字符使用单引号，如果再数字范围内，则count自加
            if(c>='0'&&c<='9')
                count++;
        }
        return count;
    }

-(int)NumberCount{
    int count = 0;
    for(int i =0;i<str.length;i++){
            //取出字符串中的第i个位置的字符给c;
            unichar c=[str characterAtindex:i];
            //字符使用单引号，如果再数字范围内，则count自加
            if(c>='0'&&c<='9')
                count++;
        }
        return count;
    }
@end
```

扩展方法的使用

```cpp
#import <Foundation/Foundation.h>
#import "NSString+NumberOfs.h"

int main(int argc,const char * argv[]){
    int a = [NSString numberofString:@"1223123lkjiwwer9080"];
    NSLog(@"%d",a);

    int b = [@"oijlskj1231kljoij213412" NumberCount];
    NSLog(@"%d",b);
}

....输出
11
10
```

## 类扩展\(Extension\)

类扩展与类别明显的不同在于，类扩展可以添加属性，而类别不能添加属性，而且类扩展中添加的方法必须实现，而类别中声明的方法可以不用实现，只要不调用即可，如果没有实现而进行调用则会编译报错。

类扩展一般再.m文件中@implementation之前开始的部分，所谓的类的continue区域进行定义和声明。类扩展作用本来是用于私有函数的向前声明，但最新编译器无需声明也有相同的效果，因此私有方法可在.m文件中任意位置直接写实现而无需在此处进行前向声明，如果在此处声明函数那么一定要在后面进行实现，否则编译器会给出警告。**现在类扩展区域的作用主要是快速定义类的私有属性，即将暴露给外部的属性变量定义在头文件中，而不想暴露给外部的属性则直接定义在类扩展区域。**

代码示例如下：

.m文件中

```cpp
#import "Person.h"

@interface Person(){

    BOOL male;
}
@end

@implementation Person
-(id)init{
    self = [super init];
    if(self){
        male = true;
    }
    return self;
}
-(void)study{
    if(male){
        NSLog(@"我是男生，我喜欢学习数学");
    }else{
        NSLog(@"我是女生，我喜欢学习语文");
    }
}
@end
```





