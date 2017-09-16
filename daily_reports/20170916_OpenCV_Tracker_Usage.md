在网络上公开的调用OpenCV的跟踪算法源代码，调用最新的OpenCV3.30分支时，发现编译会失败，出现类没有定义的情况。
主要原因是OpenCV代码进行了重构，Tracker类的构造方法不再适用于最新的sdk，下面是详细的代码对比：

3.3.0以前（或者3.0.0,没有做更深入的调查)的代码,如这篇文章介绍的https://www.learnopencv.com/object-tracking-using-opencv-cpp-python/
```C++
// Set up tracker. 
// Instead of MIL, you can also use 
// BOOSTING, KCF, TLD, MEDIANFLOW or GOTURN  
Ptr<Tracker> tracker = Tracker::create( "MIL" );
```
这是一个工厂模式，根据不同的算法，如TLD,BOOSTING作为参数，来构造对象

而在3.3.0上，每一个Tracker是一个单独的Class,都继承于Tracker类，代码如下：
```C++
// Set up tracker.
// Instead of MIL, you can also use
// BOOSTING, KCF, TLD, MEDIANFLOW or GOTURN
Ptr<TrackerMIL > tracker = TrackerMIL::create();
```

OpenCV的代码不同的版本变化很大，例如有些代码已经从主分支上迁移到contrib上，这种不稳定也给开发者挖了不少坑。
不过总的来说，OpenCV还是图像处理工程师的福音，还是目前最好的轮子。
