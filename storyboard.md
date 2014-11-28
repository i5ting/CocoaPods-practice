# storyboard

用于梳里流程

## UINavViewController

是幌子，实际是它的rootviewcontroller起作用，所以不要给UINavViewController指定类

看一下oc里如何创建UINavViewController你就明白了

```objective-c
NewsViewController *news2 = [[NewsViewController alloc] init];
UINavViewController *nc2 = [[UINavViewController alloc] initWithRootViewController:news2];
nc2.tabBarItem.title = @"栏目2";
nc2.tabBarItem.image = [UIImage imageNamed:@"menu_icon_main.png"];
[nc2.tabBarItem.title sizeWithFont:[UIFont systemFontOfSize:20]];
```

# tableview

## 静态cell

## 动态cell


屏幕尺寸兼容，几个重点

1. 避免绝对像素定位，使用Auto Layout
2. 如果你用navigation bar/tab bar, 可以考虑给中间的内容加入以下代码

	view.autoresizingMask = UIViewAutoresizingFlexibleWidth | UIViewAutoresizingFlexibleHeight;

[table setFrame:CGRectMake(0,0,320,self.view.frame.size.height)]


# Size Classes Design Help

https://developer.apple.com/library/prerelease/ios/recipes/xcode_help-IB_adaptive_sizes/chapters/AboutAdaptiveSizeDesign.html#//apple_ref/doc/uid/TP40014436-CH6-SW1


http://blog.callmewhy.com/2014/09/12/learn-ios8-size-class/


Size Class 的作用是将不同尺寸的屏幕进行分类处理，而最后进行布局管理的还是Autolayout


## 宽度和高度

对于宽度和高度而言，都有三种情况

- 紧凑 (Compact) 
- 任意 (Any) 
- 正常 (Regular)

所以一共有9个类别，变化的时候会有提示的

https://developer.apple.com/library/ios/documentation/userexperience/conceptual/mobilehig/LayoutandAppearance.html

## 安装view与不安装view





