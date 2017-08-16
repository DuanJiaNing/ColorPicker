Android 自定义 View - 颜色选取器（水平、竖直）

### Android 自定义 View - 颜色选取器（水平、竖直）

类似 SeekBar 的方式通过滑动粗略选择颜色。

#### 效果图

![](https://raw.githubusercontent.com/DuanJiaNing/ColorPicker/master/record.gif)

#### xml 属性

1. indicatorColor 指示点颜色
2. indicatorEnable 是否使用指示点
3. orientation 方向
horizontal 水平
vertical 竖直

#### 使用

复制 \library\src\...\ColorPickerView.java 和 \library\src\main\res\values\attrs.xml 文件到你的项目中，就可以在使用啦。

示例：
在 xml 中使用：

```xml

    <com.duan.colorpicker.ColorPickerView <!--替换包名-->
        android:layout_width="50dp"
        android:layout_height="200dp"
        app:indicatorEnable="true"
        app:indicatorColor="#fff"
        app:orientation="vertical" />

```

在 java 中使用：

```java
...
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        ColorPickerView picker = (ColorPickerView) findViewById(R.id.colorPickerView);
        picker.setIndicatorColor(Color.GREEN);
        picker.setOrientation(ColorPickerView.Orientation.HORIZONTAL);
        picker.setColors(Color.DKGRAY,Color.RED,Color.WHITE);
        picker.setOnColorPickerChangeListener(new ColorPickerView.OnColorPickerChangeListener() {
            @Override
            public void onColorChanged(ColorPickerView picker, int color) {
                // TODO
            }

            @Override
            public void onStartTrackingTouch(ColorPickerView picker) {
                // TODO

            }

            @Override
            public void onStopTrackingTouch(ColorPickerView picker) {
                // TODO

            }
        });
        }
...
```
实现分析可参看博文：[ Android 自定义 View - 颜色选取器（水平、竖直）](http://blog.csdn.net/aimeimeiTS/article/details/77162143)

2017-08-16

1 修复 onLayout 重复执行时指示点位置重置和颜色条重置的错误<br>
2 添加 getColor 方法以获取当前指示点所指的颜色<br>
3 覆写 onRestoreInstanceState 和 onSaveInstanceState 方法，使能够在屏幕旋转时保存状态<br>