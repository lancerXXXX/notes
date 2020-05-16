---
title: SizeTransition使用
index_img: /post_index_img/Flutter.png
date: 2020-05-16 15:51:55
categories:
    - Flutter
    - Widget
tags:
    - Flutter
    - Widget
---

# SizeTransition使用

```dart
<!-- 以两个为例 -->
class Page extends StatefulWidget{
    ....
}
<!-- 1. 加入with TickerProviderStateMixin --> <!--  如果只要一个Animation就换成SingleTickerProviderStateMixin -->
class _PageSate extends State<Page> with TickerProviderStateMixin{
<!-- 1.end -->
    ...
    <!-- 2.定义AnimationController&Aniamtion -->
    AnimationController _controller1;
    AnimationController _controller2;

    Animation<double> _animation1
    Animation<double> _animation2;

    <!-- 用来判断是否展开 -->
    bool tabelIsExpand=false;

    <!-- 2.end-->
    ...
      @override
    void initState() {
        super.initState();
        <!-- 3.初始化 -->
        _controller1 = new AnimationController(vsync: this, duration: Duration(milliseconds: 500));
        _controller2 = new AnimationController(vsync: this, duration: Duration(milliseconds: 500));
        _animation1 = Tween(begin: 0.1, end: 1.0).animate(_controller);
        _animation2 = Tween(begin: 0.01, end: 1.0).animate(_controllerNews);
        <!-- 3.end-->
    }

    @override
    void dispose() {
        super.dispose();
        <!-- 4.销毁 -->
        _controller1.dispose();
        _controller2.dispose();
        <!-- 4.end-->
    }


    @override
    Widget build(BuildContext context) {
        ...
        <!--5. 使用的地方 -->
        SizeTransition(
            sizeFactor: _animation1,
            child: 放一个Widget,
        )
        <!-- 6.可以加一个button控制缩放 -->
        FlatButton(
            child: Icon(Icons.arrow_drop_down),
            onPressed: () {
                if (TableisExpand) {
                    <!-- 复原 -->
                    _controller.reset();
                    TableisExpand = false;
                    scrollController.jumpTo(
                    scrollController.position.minScrollExtent);
                } else {
                    <!-- 展开 -->
                    _controller.forward();
                    TableisExpand = true;
                }
            },
        )
        ...
    }

}
```