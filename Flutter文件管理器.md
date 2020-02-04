---
title: Flutter文件管理器开发
date: 2020-1-29
categories: 
    - Flutter
tags:
    - flutter
---

# 参考

[参考这个项目,并在此基础上开发](https://github.com/huang-weilong/flutter_file_manager)

# Andriod Studio 创建项目
- 我也在VScode上配置了Flutter开发环境, 但是到了一些需要原生交互的部分还是需要用到AS, 所以就选择了AS
我们先解读一下`main.dart`

- `import 'package:flutter/material.dar`
    新建项目import的唯一一个包
    `Material`: 标准的移动端和web端的视觉设计语言
    `flutter`提供了一套丰富的Material widegets
    
- `pubspec.yaml`: 管理程序的assets(资源: 图片,package)

    - yaml: 类似XML, JSON的标记性语言

- 为app添加存储权限

    - ```xml
        //android\app\src\main\AndroidManifest.xml
        <manifest xmlns:android="http://schemas.android.com/apk/res/android"
            package="com.lancer.file_manager">
        	//添加下面这两个:读取权限 
            <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
            <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
        
        
            <application
                         ...
                <activity
            			...
                    <meta-data
                    <intent-filter>
                    </intent-filter>
                </activity>
            </application>
        </manifest>
        ```

        有了这个第一次打开应用就应该会弹出对话框请求存储权限

# 把布局搭出来

`lib\main.dart`

```dart
class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.cyan,
      ),
      home: MyHomePage(title: 'ranger'),
    );
  }
}
```

新建项目只有有类似这么个玩意, 我们解读一下这段代码,看明白这里的每一句话

- `Widget`: Flutter几乎所有东西都是它: 可视组件,下面两种Widget
  - Stateless widgets 属性不可变 使用`SatelessWidget`构建
  - Stateful widgets , 有下面两部分
    - `StatefullWidget` 不可变
    - `Sate` 可变,也就是说变化性是靠这个来的
  - `BuildContext`
    - 在`build(StatelessWidget.build)`方法中有参数`BuildContext`(重写build方法来构建窗口`Widget`)
    - 实际上就是`Element`(所有`Element`实现了`BuildContext`抽象类): 阻止直接对`Element`进行操作
    - 每个`Widget`都有一个`BuildContext`, 每个`BuildContext`都属于唯一`Widget`
      - `BuildContext`是Widget在`Widget`树中的句柄
      - 也就是说 A是B的父widget, 那么A的`BuildContext`就是B的`BuildContext`的父`BuildContext`
      - `widget`的树就对应了`BuildContext`的树
  - `Flutter如何构建视图` 也就是我们要看一下`build(BuildContext context)`这句话是什么意思
    - Widget不是要显示在视图上的东西(虽然我们通过Widget来编写UI界面)
    - 是什么呢,显示在屏幕上的视图树是Element Tree
    - <font color=#FFD700>以StatelessWidget为例</font>,看<font color=#FF4500>源码</font>
        1. 先看`MyApp`继承的`StatelessWidget`
            ``` dart
            abstract class StatelessWidget extends Widget {
              const StatelessWidget({ Key key }) : super(key: key);
              @override
              StatelessElement createElement() => StatelessElement(this);
              @protected
              Widget build(BuildContext context);
            }
            ```
            <font color=#FF4500>①</font>首先是`creatElement()`方法: 创建`StatelessElement`,参数是当前`Widget`
            注意第三个函数就是我们重写的`build`方法
        2. 那么就继续看`StatelessElement`
            ``` dart
            StatelessElement(StatelessWidget widget) : super(widget);
              @override
              StatelessWidget get widget => super.widget;
              @override
              Widget build() => widget.build(this);
              @override
              void update(StatelessWidget newWidget) {
                super.update(newWidget);
                assert(widget == newWidget);
                _dirty = true;
                rebuild();
              }
            ```
            首先`get`方法: 保留`Widget`的引用
            <font color=#FF4500>②</font>然后`build`方法: 我们要看到搁这了,它将当前这个`StatelessElement`作为参数
            `Widget build(BuildContext context);`
            解释一下为什么传的是`StatelessElement`
            ```dart
            class StatelessElement extends ComponentElement
            ...
            abstract class ComponentElement extends Element
            ...
            abstract class Element extends DiagnosticableTree implements BuildContext 
            ```
            `StatelessElement`实现了`BuildContext`,所以,嗯

            图示
            ```mermaid
            graph LR
            StatelessWidget-->|创建|StatelessElement
            StatelessWidget-->|传递自身引用|StatelessElement-->|中使用StatelessWidget的build方法将自身作为参数|StatelessWidget
            ```

- `MaterialApp`

  ```dart
  class MyApp extends StatelessWidget {
    // This widget is the root of your application.
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        title: 'Flutter Demo',
        theme: ThemeData(
          primarySwatch: Colors.cyan,
        ),
        home: MyHomePage(title: 'ranger'),
      );
    }
  }
  ```
  然后是这里的`MaterialApp`,这个`Widget`封装了应用程序实现Metrial Design所需要的一些Wedget ([参考](https://www.jianshu.com/p/bb574d2cfb19))
  参数含义
  ```xml
  title ： 在任务管理窗口中所显示的应用名字
  theme ： 应用各种 UI 所使用的主题颜色
  color ： 应用的主要颜色值（primary color），也就是安卓任务管理窗口中所显示的应用颜色
  home ： 应用默认所显示的界面 Widget
  routes ： 应用的顶级导航表格，这个是多页面应用用来控制页面跳转的，类似于网页的网址
  initialRoute ：第一个显示的路由名字，默认值为 Window.defaultRouteName
  onGenerateRoute ： 生成路由的回调函数，当导航的命名路由的时候，会使用这个来生成界面
  onLocaleChanged ： 当系统修改语言的时候，会触发å这个回调
  navigatorObservers ： 应用 Navigator 的监听器
  debugShowMaterialGrid ： 是否显示 Material design 基础布局网格，用来调试 UI 的工具
  showPerformanceOverlay ： 显示性能标签
  checkerboardRasterCacheImages 、showSemanticsDebugger、debugShowCheckedModeBanner 各种调试开关
  ```
  这里用到了`title`,`theme`,`home`
## 创建MyHomePage

MyHomePage 放在home参数下, 就是应用默认显示的界面
是一个Stateful Widget,
两部分
1. `StatefulWidget`
```dart
class MyHomePage extends StatefulWidget {
  MyHomePage({Key key, this.title}) : super(key: key);

  final String title;

  @override
  _MyHomePageState createState() => _MyHomePageState();
}
```
2. `State`
```dart
class _MyHomePageState extends State<MyHomePage> {
  ...
  @override
  void initState() {
    ...
  }
```

`_MyHomePageState`放入一个`List<FileSystemEntity> files = [];`