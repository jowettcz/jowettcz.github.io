Android平台支持的丰富的传感器是其亮点之一，虽然相比iPhone来说稍有逊色，但相对于原来占据智能市场的Synbian等手机平台有一个明显的飞跃。我们现在看到的旅游出行必备的指南针，甩一甩就显示火苗的模拟打火机都是基于Android内置的传感器。本文主要向大家介绍一下传感器的类型和调用方法，并根据Android官方实例打造一个纯手工的指南针程序。

传感器类型介绍

Android库中显示的可支持的传感器类型共有11种，但是并不是每部手机都装置了所有的传感器，比如我手头的这款HTC G7就只有5种传感器。这全部11种包括，加速度（accelerometer），磁场（magnetic field），方位角（orientation），陀螺仪（gyroscope），光线（light），压力（pressure），温度(temperature), 周围物体感应(proximity)，重力(gravity)，线性加速度(linear acceleration)，旋转矢量(rotation vector)。
在接下来的演示的代码中，我们从手机设备中读出所有的的传感器，下面是我的手机里面的传感器设备：加速度传感器（BMA150 3-axis Accelerometer），磁场传感器（AK8973 3-axis Magnetic field sensor），方位角传感器（AK8973 Orientation sensor），周围物体传感器（CM3602 Proximity sensor），光线传感器（CM3602 Light sensor）。

使用传感器

Android提供的API中对于不同传感器的调用都是用同一个接口，这样编程起来显得非常简单。先得到传感器的控制器，然后注册你感兴趣的感应事件，代码如下

```JAVA
SensorManager SensorManager= (SensorManager)getSystemService(Context.SENSOR_SERVICE);
//注册方位角传感器，感应事件的周期是0.12s产生一次报告
mSensorManager.registerListener(mListener,
             SensorManager.SENSOR_ORIENTATION,
             SensorManager.SENSOR_DELAY_NORMAL
);
```
