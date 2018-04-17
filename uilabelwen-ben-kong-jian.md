## UILabel控件

#### UILabel的创建

UILabel的创建遵循通用的UIView的创建过程，但是感觉UILabel样式配置上有一点没有Android 方便是不能设置居上 居中以及居下。既没有Android视图布局的gravity属性的设置。

```cpp
//创建的时候要通过一个CGRectMake(CGFloat x, CGFloat y, CGFloat width, CGFloat height)来规定文本的再父容器中的
//x和y轴的位置已经文本的宽高。
UILabel *label1 = [[UILabel alloc]initWithFrame:CGRectMake(20, 60, 300, 50)];
label1.backgroundColor = [UIColor grayColor];// 设置背景色
label1.text = @"www.imooc.com你好label";// 设置内容
label1.textColor = [UIColor blueColor];//设置字体颜色
```

#### UILabel文本显示过长时的展示

文本都有显示过长的处理，这里OC比Android 多了好几种处理方式，尤其是前省略已经中省略，个人觉得都是很好用的属性，各种类型如下：

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

#### sizeToFit方法的使用

当创建一个UILabel的时候可以先定义好宽高，但是在实际开发中有时候是需要自适应的，就是相当于Android中的宽高设置为“wrap\_content”属性来包裹内容。这个时候就可以通过sizeToFit方法来重置UILabel的Frame参数。实例如下：

```
UILabel *label1 = [[UILabel alloc]initWithFrame:CGRectMake(50, 100, 200, 50)];
label1.text =@"我是UILable练习;
label1.backgroundColor = [UIColor grayColor];
label1.backgroundColor = [UIColor grayColor];
label1.textColor = [UIColor greenColor];
[self.view addSubview:label1];

//调用sizeToFit方法
UILabel *label2 = [[UILabel alloc]initWithFrame:CGRectMake(50, 200, 200, 50)];
label2.text =@"我是UILable练习";
label2.backgroundColor = [UIColor grayColor];
label2.textColor = [UIColor greenColor];
//系统定义的字体
label2.font =[UIFont systemFontOfSize:20.0];
[label2 sizeToFit];
[self.view addSubview:label2];
```

运行效果如下：

```
                             ![](/assets/sizeTofit.png)
```

#### UILable文本字体大小以及自定义字体的设置

再Android中可以定义文本的姿态大小对于OC来说一样可以，只是Android是通过typeface属性，OC通过UIFont的fontWithName:\(NSstring \*\)fontName size:\(CGFloat\)fontSize \):方法来做。设置字体是用systemFontOfSize:\(CGFloat\)size;方法

```
UILabel *label2 = [[UILabel alloc]initWithFrame:CGRectMake(50, 200, 200, 50)];
label2.text =@"我是UILable练习";
//使用系统定义的字体并设置大小
label2.font =[UIFont systemFontOfSize:20.0];
//设置字体
label2.font =[UIFont fontWithName:@"Aril-BoldMT" size:15.0];
```

#### UILabel文件内容的自适应

因为UILabel 宽高不能设置“wrap\_content”属性，如果创建前不知道文本长度一般都是会设置好宽高，这个时候如果文本过长并不会折行或者是自适应文本大小，这个时候可以通过adjustsFontSizeToFitWidth属性设置文本根据一开始设置的宽高来设置文本大小。并且可以通过numberOfLines属性来设置文本自动折行。

```
  //label5.numberOfLines = 0; 如果设置为0则文本行数不固定只要展示不下就自动折行
  label5.numberOfLines = 2;
  label5.adjustsFontSizeToFitWidth = true;// 如果文本区域宽度不够则是自动缩小字体大小直到可以展示下为止。
```

#### UILabel边框阴影效果

UIView可以设置阴影属性，UiLabel继承与UIView自然也有阴影属性，并且设定方式和UIView一样，都是通过layer下面的shadow相关属性来设置。但是文本多了一个只是单纯文本添加阴影的效果属性。

```
UILabel *label3 = [[UILabel alloc]initWithFrame:CGRectMake(50, 300, 200, 50)];
label3.text =@"我是UILable练习";
label3.backgroundColor = [UIColor grayColor];
label3.textColor = [UIColor greenColor];
//系统定义的字体
label3.font =[UIFont systemFontOfSize:20.0];
//设置文本区域的阴影效果
label3.layer.shadowColor =[UIColor redColor].CGColor;
label3.layer.shadowOffset = CGSizeMake(5, 5);
label3.layer.shadowOpacity = 0.5;
//设置文本自身的阴影效果
label3.shadowOffset = CGSizeMake(2, 2);
label3.shadowColor = [UIColor yellowColor];
label3.alpha = 0.4;
[self.view addSubview:label3];
```

```
        效果：                        ![](/assets/uilabelShadow.png)
```

#### UILabel根据内容获取合适的宽高

再实际开发中更多时候是需要我们根据文本的长度来做一些逻辑操作，这个时候就需要获得要显示的文本的长宽大小，Android 可以通获得 OC自然也有方法获得

Android如下：

```java
String text ="测试文本";
TextView textView = (TextView) findViewById(R.id.test);
textView.setText(text);
// 调用TextView的getMeasureWidth;
int spec = MeasureSpec.makeMeasureSpec(0, MeasureSpec.UNSPECIFIED);
textView.measure(spec, spec);
// getMeasuredWidth
int measuredWidth = textView.getMeasuredWidth();

// 调用TextPaint的measureText方法  这种方法虽然当文本有英文的时候会有误差
// new textpaint measureText
TextPaint newPaint = new TextPaint();
float textSize = getResources().getDisplayMetrics().scaledDensity * 15;
newPaint.setTextSize(textSize);
float newPaintWidth = newPaint.measureText(text);

// textView getPaint measureText 这种方法最佳最准
TextPaint textPaint = textView.getPaint();
float textPaintWidth = textPaint.measureText(text);
```



