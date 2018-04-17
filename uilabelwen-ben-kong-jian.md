## UILabel控件

#### UILabel文本显示过长时的展示

```cpp
lineBreakMode：设置标签文字过长时的显示方式。   

label.lineBreakMode = NSLineBreakByCharWrapping;    //以字符为显示单位显示，后面部分省略不显示。

label.lineBreakMode = NSLineBreakByClipping;        //剪切与文本宽度相同的内容长度，后半部分被删除。  

label.lineBreakMode = NSLineBreakByTruncatingHead;  //前面部分文字以……方式省略，显示尾部文字内容。  

label.lineBreakMode = NSLineBreakByTruncatingMiddle;    //中间的内容以……方式省略，显示头尾的文字内容。 

label.lineBreakMode = NSLineBreakByTruncatingTail;  //结尾部分的内容以……方式省略，显示头的文字内容。 

label.lineBreakMode = NSLineBreakByWordWrapping;    //以单词为显示单位显示，后面部分省略不显示

sizeToFit//方法的使用
```

#### sizeTOFit方法的使用

#### 

#### UILable文本字体大小以及自定义字体的设置



#### UILabel文件内容的自适应



#### UILabel边框阴影效果



#### UILabel根据内容获取合适的宽高





