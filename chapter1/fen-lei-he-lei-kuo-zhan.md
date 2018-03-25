## 分类\(Category\)

分类文件也是有.h和.m两个文件，但是命名规则为  类名+分类名.h  和 类名+分类名.m。其主要作用是在不改变原来的类的内容的基础上，为类增加一些方法。

#### 使用注意

1、分类只能增加方法（包括类方法和对象方法），不能增加成员变量。

2、在分类方法的实现中可以访问原来类中的成员变量；

3、分类中可以重新实现原来类中的方法，但是会覆盖掉原来的方法，导致原来的方法无法再使用（警告）

4、方法调用的优先级：分类-&gt;原来的类-&gt;父类，若包含有多个分类，则最后参与编译的分类优先；

5、在很多的情况下，往往是给系统自带的类添加分类，如NSObject和NSString，因为有的时候，系统类可能并不能满足我们的要求。

6、在大规模的应用中，通常把相应的功能写成一个分类，可以有无限个分类，对原有类进行扩充，一般分模块写，一个模块一个分类

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



