[合集 \- Rive(6\)](https://github.com)[1\.【Rive】Rive在Android上的简单应用12\-21](https://github.com/zhyan8/p/18621010)[2\.【Rive】动画12\-21](https://github.com/zhyan8/p/18621011)[3\.【Rive】混合动画12\-22](https://github.com/zhyan8/p/18621012)[4\.【Rive】Android与Rive交互12\-22](https://github.com/zhyan8/p/18621013):[FlowerCloud机场节点订阅](https://dahelaoshi.com)[5\.【Rive】事件回调12\-23](https://github.com/zhyan8/p/18621014)6\.【Rive】波动文字12\-23收起
# 1 前言


​ 本文将使用文本修改器（Text Modifiers）做文字动画，实现文字波动效果。


​ 按以下步骤可以创建一个 Modifier Group 和 Range。


![img](https://img2024.cnblogs.com/blog/3135663/202412/3135663-20241221212614356-1409021762.png)


​ 部分参数的释义如下。


* **Range**: Modifier 作用的范围。
* **Falloff**: Modifier 在最大值时的范围，Falloff 一般是 Range 的子集。
* **Offset**: Range 的偏移。


​ 本节完整资源详见 → [Android中使用Rive实现文字波动特效](https://github.com)。


# 2 第一种波形


​ **1）Modifier 配置**


![img](https://img2024.cnblogs.com/blog/3135663/202412/3135663-20241221212614318-1213171715.png)


​ **2）时间线**


​ 将 Modifier 的 PostionY、Offset 参数添加到时间线中，如下。


![img](https://img2024.cnblogs.com/blog/3135663/202412/3135663-20241221212614350-1036017598.png)


​ PositionY 对应的 4 帧的值分别为 100、\-100、100、\-100，4 帧的插值器都是 S 型；Offset 对应的 2 帧的值分别为 \-0\.4、1。


# 3 第二种波形


​ **1）Modifier 配置**


![img](https://img2024.cnblogs.com/blog/3135663/202412/3135663-20241221212614367-857977436.png)


​ **2）时间线**


​ 将 Modifier Group 1 和 Modifier Group 2 的 Offset 参数添加到时间线中，如下。


![img](https://img2024.cnblogs.com/blog/3135663/202412/3135663-20241221212614363-728326604.png)


​ Modifier Group 1 的 Offset 对应的 4 帧的值分别为 0、1、\-1、0，第 2 、3 两帧相隔 1 帧，第 2 帧的插值器是 Z 型；Modifier Group 2 的 Offset 对应的 4 帧的值分别为 \-0\.5、1、\-1、\-0\.5，第 2 、3 两帧相隔 1 帧，第 2 帧的插值器是 Z 型。


# 4 Android 中代码


​ Rive 在 Android 中的环境配置详见 → [Rive在Android上的简单应用](https://github.com)。


​ **1）MainActivity**



```
package com.zhyan8.waveText

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
    }
}

```

​ **2）layout\_main.xml**



```
xml version="1.0" encoding="utf-8"?
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context="com.zhyan8.waveText.MainActivity"
    android:orientation="vertical"
    android:gravity="center">

    <app.rive.runtime.kotlin.RiveAnimationView
        android:layout_width="match_parent"
        android:layout_height="200dp"
        app:riveFit="COVER"
        app:riveResource="@raw/wave_text"
        app:riveArtboard="Artboard_1"/>

    <app.rive.runtime.kotlin.RiveAnimationView
        android:layout_width="match_parent"
        android:layout_height="200dp"
        android:layout_marginTop="20dp"
        app:riveFit="COVER"
        app:riveResource="@raw/wave_text"
        app:riveArtboard="Artboard_2"/>

LinearLayout>

```

# 5 运行效果


![img](https://img2024.cnblogs.com/blog/3135663/202412/3135663-20241221212614474-1329961103.gif)


​ 声明：本文转自[【Rive】波动文字](https://github.com)。


