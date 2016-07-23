## plotpm {#cmd:plotpm}

### 概要

针对一对数据文件产生一个“质点运动”图

### 语法

P`LOT`PM

### 说明

在一个质点运动图中，一个等间距文件相对于另一个等间距文件绘图。对于没有
自变量的值，第一个文件的因变量的值将沿着y轴绘制，第二个文件的因变量值
沿着x轴绘制。对于一对地震图来说，这种图展示了一个质点在两个地震图所确定
的平面内随时间的运动。它将产生一个方形图，每个轴的范围为因变量的极大
极小值。注释轴沿着底部和左边绘制。轴标签以及标题可以通过
[xlabel](/commands/xlabel.html)、 [ylabel](/commands/ylabel.html) 和
[title](/commands/title.html) 命令设置。如果未设置x、y标签，
则台站名和方位角将用作轴标签。[xlim](/commands/xlim.html)
可以用于控制文件的 哪些部分需要被绘制。

### 示例

创建一个两个地震图的质点运动图：

``` {.bash}
SAC> read xyz.t xyz.r
SAC> xlabel 'radial component'
SAC> ylabel 'transverse component'
SAC> title 'particle-motion plot for station xyz'
SAC> plotpm
```

如果你想要值绘制每个文件在初动附近的一部分，你可以使用
[xlim](/commands/xlim.html) 命令：

``` {.bash}
SAC> xlim a -0.2 2.0
SAC> PLOTPM
```

也可以使用 [plotpk](/commands/plotpk.html)
在之前的绘图窗口中设置新的区域，然后绘制 命令如下：

``` {.bash}
SAC> beginwindow 2
SAC> plotpk
 ... mark the portion you want using X and S
 ... terminate PLOTPK with a Q
SAC> beginwindow 1
SAC> plotpm
```