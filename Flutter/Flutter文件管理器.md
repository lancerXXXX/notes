---
title: Flutter文件管理器开发
index_img: /post_index_img/Flutter.png
date: 2020-1-29
categories: 
    - Flutter
tags:
    - flutter
---

# 1. 参考

[参考这个项目,并在此基础上开发](https://github.com/huang-weilong/flutter_file_manager)

# 2. Andriod Studio 创建项目
- 我也在VScode上配置了Flutter开发环境, 但是到了一些需要原生交互的部分还是需要用到AS, 所以就选择了AS
我们先解读一下`main.dart`

- `import 'package:flutter/material.dar`
    新建项目import的唯一一个包
    `Material`: 标准的移动端和web端的视觉设计语言
    `flutter`提供了一套丰富的Material widegets
    
- `pubspec.yaml`: 管理程序的assets(资源: 图片,package)

    - yaml: 类似XML, JSON的标记性语言

# 3. 把布局搭出来

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
            StatelessWidget-->|传递自身引用|StatelessElement
            StatelessElement-->|中使用StatelessWidget的build方法将自身作为参数|StatelessWidget
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

## 3.1. 获取读取权限

<center>

![](Flutter%E6%96%87%E4%BB%B6%E7%AE%A1%E7%90%86%E5%99%A8/2020-02-16-21-49-23.png)

</center>

```xml
<manifest...>
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <application...>
```

## 3.2. 创建MyHomePage

`MyHomePage` 放在`Myapp` 的 home参数下, 就是应用默认显示的界面
是一个`Stateful Widget`,

现在的结构

- MyApp`(StatelessWidget)`
  - MyHomePage(`StatefullWidget`)
    - _MyHomePageState(`State<>`)


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

    `_MyHomePageState`放入一个`List<FileSystemEntity> files = [];`用来存放要显示的文件,文件夹
    新建一个`Common.dart`用来存放`根目录`,`根据文件尾缀返回图标路径`

    ``` Dart
    class Common{
      factory Common()=>_getInstance();

      static Common _instance;

      static Common _getInstance(){
        if(_instance==null){
          _instance=Common._internal();
        }
        return _instance;
      }
    Common._internal();
      ...
    }
    ```
这里使用了`工厂构造函数: factory`,和`单例模设计式`,有时候不需要每次新建都创建新的实例, 而是每次都只需要同一个实例,
    具体的做法就是有一个静态的实例对象`static Common _instance`, 作为缓存,用来存放这唯一的一个实例对象,
    然后写`工厂构造函数`, 关键字为`factory`: `factory Common()=>_getInstance()`,
    这里面做一个判断,如果没有实例的话,初始化一个新的对象赋值给`_instance=Common._internal()`, `internal是一个空的初始化函数`

## 3.3.  获取跟路径和读取权限

这里使用了Flutter也就是dart中的异步

[参考](https://www.jianshu.com/p/a4affde4c8ca)

总结一下就是:  

- Dart: 单线程模式

  - 是`Event-Looper`以及`Event-Queue`的模型 : 事件通过`EventLooper`(事件循环)执行
    ![img](Flutter%E6%96%87%E4%BB%B6%E7%AE%A1%E7%90%86%E5%99%A8/1941624-5cd24aaf768a8b97.webp)

  - isolate(隔离): 没有线程概念,但是有隔离

    - 各个isolate相互隔离

    - 之间不会共享内存

    - 程序从main()开始:Main isolate

    - 接着处理Event Queue中的Event

  - Event Queue & Microtask Queue
    - Main Isolate只有一个Event looper
    - 但是有两个Event Queue: 
        - Event Queue & Microtask Queue((优先执行)处理稍晚一些的事情(但是下一个消息来之前要处理完的),处理这个Queue时停止Event Queue的处理)
- 异步任务调度:
    - Future: 任务加到Event Queue队尾
    - scheduleMidrotask: 任务加到Microtask Queue队尾(要避免过大--阻塞其他事件的处理)
- Future.then: 大人物拆分成小任务一步步执行
- Future.delayed: 任务延迟执行

- ```java
  //future: Future<T>对象--Dart内置,有自己的队列策略(EventQueue)
  //async: 声明函数为异步,不阻塞当前进程,来等待该线程处理完任务再执行其他任务
  //await: 等待,声明运算为延迟进行
  ```

```dart
void main() {
  //1. 获取跟路径
  Future<void> getSDCardDir() async{
    //1.1 插件path_provider提供函数getExternalStorageDirectory
    //1.2 获取SD卡根路径
    Common().sDCardDir=(await getExternalStorageDirectory()).path;
  }

  //2. 获取权限
  Future<void> getPermission() async {
    //2.1 安卓平台
    if (Platform.isAndroid) {
      PermissionStatus permission = await PermissionHandler().checkPermissionStatus(PermissionGroup.storage);
      if (permission != PermissionStatus.granted) {
        await PermissionHandler().requestPermissions([PermissionGroup.storage]);
      }
      await getSDCardDir();
    //2.2 IOS平台
    } else if (Platform.isIOS) {
      await getSDCardDir();
    }
  }

```

