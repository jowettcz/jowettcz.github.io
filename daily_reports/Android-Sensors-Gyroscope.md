注：这是我2012写的一篇技术博客，现在看起来会觉得写的太浅，但对于陀螺仪的空间几何原理描述的比较清楚，也提供了可执行的代码例子；时间过去很久了，在上海搬了几次家，很多东西都丢弃了，但是这篇文章仍然在网上很轻易地找到了，文字比你身边的很多物件都要长久。


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

如果想要获得其他感应事件，只需要修改第二个参数为相应的传感器对应的枚举数值，第三个参数是感应事件的频率，设置感应事件频率，有四种频率模式可选，每个相差0.04s。然后设置一个监听器，利用监听接口onSensorChanged来读取具体感应的内容
```JAVA
public void  onSensorChanged(int sensor, float[] values)
{
       if(Config.DEBUG)
       {
            Log.d(TAG, "极方位角azimuth，" + values[0]);
 
            Log.d(TAG, "倾斜角pitch，" + values[1]);

            Log.d(TAG, "转角roll，" + values[2]);
       }

}
```
感应矢量的参照坐标系

对于矢量感应，比如方位角，磁场，陀螺仪等等，它们都有自己的参照坐标系，并且都不相同。必须理解它的坐标系，否则从事件中接收到的整数值对我们也是也没有任何用处的。这里以方位角的坐标系为例，参看下所示

把手机水平放置在桌面上，头部指向北，这时候所有的方位角都是零度。这里提到的北极是地球磁场的北极，与我们日常所说的正北方向之间有一个夹角，就是磁偏角。那么接下来对应到上图的位置，就是磁场的北方对应的就是Y轴的正半轴，水平方向转过的角度就是正向的极方位角azimuth，范围是【0，360】；以手机头部为轴，底部向正上抬起，现在的转向是从Y的正半轴转向Z的正半轴，转过的角度就是正向的倾斜角pitch，范围是【-180，180】；以手机右边为轴，左边向上抬起，现在的转向是从Z的正半轴转向X的正半轴，转过的角度就是正的转角roll，范围是【-90，90】。

如果大家如果觉得辨认它的每个转角的正负比较复杂，有一个简单的方法，从每种转角转动时所绕的轴（或者说与转动方向始终垂直的轴）的负半轴向正半轴看去，转动的顺时针方向就是正方向。比如，当水平方向有转动时，azimuth的正角度就是从Z轴的副半轴向正半轴望过去的顺时针方向。

指南针应用

编写一个指南针应用其实非常简单，只需要注册方位角传感器，然后获取其中的极方位角azimuth；如果现在极方位角发生偏移，让我们的指示针反方向偏转同样的角度就可以了。下面的程序代码没有使用图片资源，只是通过画笔paint在界面上的移动来实现指南针的图形。画布的背景是白色，每当极方位角发生移动时（手机在水平方向有转动），整个画布向反方向移动同样的角度，大家看起来就像是指南针图形在移动。同时在程序中我们打印出设备配置的所有的传感器，记录在日志中。

应用代码

```JAVA
package com.ijowett.example.SystemService;
import java.util.List;
import android.app.Activity;
import android.content.Context;
import android.graphics.Canvas;
import android.graphics.Color;
import android.graphics.Paint;

import android.graphics.Path;
import android.hardware.Sensor;
import android.hardware.SensorListener;
import android.hardware.SensorManager;
import android.os.Bundle;
import android.util.Config;
import android.util.Log;
import android.view.View;

public class  Compass extends Activity{
  private static  final  String TAG = "Compass";
  private SensorManager mSensorManager;
  private SampleView mView;
  private float[] mValues;
  private final  SensorListener mListener = new
  
  SensorListener() {
    public void  onSensorChanged(int sensor, float[] values) {

    if (Config.DEBUG)
      Log.d(TAG, "sensorChanged ("  + values[0] + ", "  + values[1] + ", "  + values[2] + ")");
      mValues = values;

    if (mView != null) {
      mView.invalidate();
    }
  }

  public void  onAccuracyChanged(int sensor, int accuracy) {
    // TODO Auto-generated method stub
  }
};

 
@Override
protected void  onCreate(Bundle icicle) {
    super.onCreate(icicle);
    mSensorManager = (SensorManager)getSystemService(Context.SENSOR_SERVICE);

    List sensors = mSensorManager.getSensorList(Sensor.TYPE_ALL);
    Log.d(TAG, "There are " + sensors.size() + " sensors.");
    for(Sensor sens : sensors)
    {
      Log.d(TAG, "Sensor name: " + sens.getType());
      Log.d(TAG, "Sensor name: " + sens.getName());
    }
    mView = new SampleView(this);
    setContentView(mView);
  }
  
  
  @Override
  protected void onResume()
  {
    if (Config.LOGD) Log.d(TAG, "onResume");
    super.onResume();
    mSensorManager.registerListener(mListener,
    SensorManager.SENSOR_ORIENTATION,
    SensorManager.SENSOR_DELAY_GAME);
  }
  
  @Override
  protected void onStop()
  {
    if (Config.LOGD) Log.d(TAG, "onStop");
    mSensorManager.unregisterListener(mListener);
    super.onStop();
  }
  
  private class SampleView extends View {
    private Paint mPaint = new Paint();
    private Path mPath = new Path();
    private boolean mAnimate;
    private long mNextTime;

    public SampleView(Context context) {
      super(context);
      // Construct a wedge-shaped path
      mPath.moveTo(0, -50);
      mPath.lineTo(-20, 60);
      mPath.lineTo(0, 50);
      mPath.lineTo(20, 60);
      mPath.close();
    }

    @Override 
    protected void onDraw(Canvas canvas) {
      Paint paint = mPaint;
      canvas.drawColor(Color.WHITE);
      paint.setAntiAlias(true);
      paint.setColor(Color.BLUE);
      paint.setStyle(Paint.Style.FILL);
      int w = canvas.getWidth();
      int h = canvas.getHeight();
      int cx = w / 2;
      int cy = h / 2;
      canvas.translate(cx, cy);
      
      if (mValues != null) {
        canvas.rotate(-mValues[0]);
      }
      canvas.drawPath(mPath, mPaint);
  }
  
  @Override
  protected void onAttachedToWindow() {
    mAnimate = true;
    super.onAttachedToWindow();
    }
    @Override
    protected void onDetachedFromWindow() {
      mAnimate = false;
      super.onDetachedFromWindow();
    }
  }
}
```

除非注明，乔伊特博客文章均为原创，转载请以链接形式标明本文地址
本文地址：https://github.com/jowettcz/jowettcz.github.io/edit/master/daily_reports/Android-Sensors-Introduction.md

