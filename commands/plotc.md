## plotc {#cmd:plotc}

### 概要

使用光标标注SAC图形和创建图件

### 语法

P`LOT`C \[R`EPLAY`|C`REATE`\] \[F`ILE`|M`ACRO` filename\] \[B`ORDER`
ON|OFF\]

### 输入

REPLAY

:   重新显示或绘制一个已经存在的文件或宏，关于文件和宏的区别见下

CREATE

:   创建一个新的文件或宏

FILE filename

:   重新显示或创建一个文件。如果省略文件名则使用上一个文件

MACRO filename

:   重新显示或创建一个宏

BORDER ON|OFF

:   打开/关闭图形的边界

### 缺省值

plotc create file out border on

### 说明

这个命令让你可以注释一个SAC绘图或者创建一个用于会议或报告的图件。简单的
说就是一个简单的“画图”软件。你需要一个具有光标的图形设备。你可以通过在
终端屏幕上放置一个目标（比如圆、方）或者文本创建一个图件。光标的位置决定
了目标绘制的位置，敲入的字符决定了要绘制哪个目标。目标包括圆、矩形、多边形、
线、箭头、弧，还有多种放置文本的方法。

这个命令绘制出的图可以直接截图利用，绘制过程中用到的所有命令将作为输出
文件输出。这个命令有两种输出文件格式：简单文件或宏文件。两者都是字符
数字型文件，可以直接用文本编辑器修改。它们包含了 `plotc` 命令中
光标响应的历史以及位置。宏文件一旦被创建，可以用于更多的绘图。其比例和
旋转角度均可以修改。简单的 `plotc` 文件名以 `.PCF`为后缀， 宏文件名则以
`.PCM` 为后缀。这使得你可以区分你的目录下的这些文件。

当你创建一个新的文件或宏时，SAC在屏幕上绘制一个矩形，代表你可以绘图的区域，
你可以将光标移动到该区域内任何你想放置的位置，并输入代表你想绘制的目标或
你想要光标执行的动作所对应的字符。

有两种光标选项类型：动作类和参数设置类。动作类选项将做一些事情（绘制一个
矩形，放一些文本），他们如何执行这个操作部分基于当前参数设置选项的值（例
如多边形的边数，文本大小等）。这个区别与SAC自己的操作命令和参数设定命令
相同。下面会列出动作和参数设定选项。

当你重新显示一个文件或者宏时，图形在终端屏幕上将会重新绘制，光标也将打开。
你可以像你当初创建这个文件一样向其中加入目标。当你完成创建图件之后你可以
将其发送到不同的图形设备，使用
[begindevices](/commands/begindevices.html) 命令临时关闭
终端屏幕打开其他图形设备（比如
[sgf](/commands/sgf.html)），然后重新显示这个文件。

为了注释一个SAC绘图，要执行 [vspace](/commands/vspace.html)
命令设置正确的横纵比， 然后执行 [beginframe](/commands/beginframe.html)
命令关闭自动刷新，执行需要的SAC绘图命令， 执行
[plotc](/commands/plotc.html) 命令（创建或者重新显示），然后执行
[endframe](/commands/endframe.html) 命令恢复自动刷新。

### 示例

下面的例子展示了如何使用 `plotc` 命令给一个SAC标准绘图添加注释：

``` {.bash}
SAC> fg impulse npts 1024                      //生成文件
SAC> lp c2 n 7 c 0.2 t 0.25 a 10               //低通滤波
SAC> fft
 DC level after DFT is 1
SAC> axes only l b                             //左和下坐标轴设置
SAC> ticks only l b
SAC> border off
SAC> fileid off
SAC> qdp off
SAC> vspace 0.75                              //修改图形尺寸
SAC> beginframe                               //开始绘图
SAC> psp am linlin                            //绘图
SAC> plotc create file bandpass               //开始在图上做注释
...用光标和键盘进行各种操作...
SAC> endframe
```

[plotsp](/commands/plotsp.html)
用于绘制滤波响应曲线以及两个轴，[plotc](/commands/plotc.html)
用于交互式地添加注释。[vspace](/commands/vspace.html)
命令限制了图形中纵横比为3:4的
区域为绘图区域。这个对于之后将输出发送到具有纵横比3:4的SGF设备来说很有必要。
在这之后你将有一个叫做 `BANDPASS.PCF` 的文件，其中包很了这个图形的
注释信息。

为了将注释写入SGF文件：

``` {.bash}
SAC> begindevices sgf                  // 打开sgf设备
SAC> beginframe
SAC> plotsp
SAC> plotc replay                      // 重新绘制上一注释图
SAC> endframe
```

这样一个包含注释绘图的SGF文件就建立了。

### 注意

1.  只有当设置正方形视窗（`vspace 1.0`）时绘制的圆形和扇形
    才是正确的，否则只能产生一个椭圆，其纵横比等于视窗的纵横比。

2.  除文本之外的所有操作码都按比例适应图形窗口。

文本尺寸并不是当前标度的。当你生成一个图像并想要将文本放在一个矩形或圆中
时会产生一个问题。在这种情况下，图形窗口必须与输出页具有相同的尺寸，以
避免图形的偏差。这可以通过使用 [window](/commands/window.html)
命令设置窗的水平X
尺寸为0.75，垂直Y尺寸为0.69。例如：`WINDOW 1 X 0.05 0.80 Y 0.05 0.74`。
这个命令必须在窗口被创建之前执行。（即在
[beginwindow](/commands/beginwindow.html) 或
[begindevices](/commands/begindevices.html) 之前）

  字符   含义
  ------ --------------------------------------------------------------------------------------------------------------------
  A      绘制一条到ORIGIN到CURSOR的箭头
  B      在绘图区周围绘制边界的tick标记
  C      绘制一个圆心在ORIGIN，且经过CURSOR的圆
  D      从replay文件中删除最后一个动作选项
  G      设置ORIGIN，并将其全局化
  L      绘制一条从ORIGIN到CURSOR的线
  M      在CURSOR处插入一个宏文件(输入宏文件名，比例因子和旋转角。 若没有指定，则使用上一次的值，默认是OUT，1.0，0)
  O      设置ORIGIN为CURSOR
  N      绘制一个中心在ORIGIN，一个顶点位于CURSOR的n边形
  Q      退出PLOTC
  R      绘制对脚位于ORIGIN和CURSOR的长方形
  S      绘制一个圆心位于ORIGIN的扇形(用光标的移动来 指定扇形的角度，键入S来绘制一个小于180度的扇形，或者键入C绘制它的补集)
  T      在CURSOR处放置一行文本，文本以回车键结束
  U      在CURSOR处放置多行文本，文本以空白行结束

  : plotc命令表

### 关于PLOTC命令表的说明

-   `CURSOR` 表示当前光标位置

-   `ORIGIN` 一般为上次光标的位置

-   `G` 选项强制ORIGIN固定

-   `O` 选项再次允许ORIGIN移动

-   `Q` 选项不自动拷贝至文件，但是可以通过文本编辑器直接加入

如果SAC在replay模式没有在文件中看到Q选项，则其在显示文件内容之后回到光标
模式，这使得你可以在文件结束之后继续增加更多的选项。如果SAC在文件中看到
Q选项，则显示其内容并退出。文件中以星号开头的行为注释行。 `plotc`
还有一些更复杂的选项，但是运行起来好像有点问题，有兴趣的 可以试试
`help plotctable`。