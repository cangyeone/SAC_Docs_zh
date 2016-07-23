## 2012-01-08 1.0版 {#版 .unnumbered}

-   第一版发布，由DOC转换为PDF

-   参考《数字地震波形分析》一书，翻译了大部分官方文档中的内容

-   结合SAC 101.4版本，增加、删除和修改了一些命令

-   增加了书签，方便定位，支持全文搜索

## 2012-09-03 1.1版 {#版-1 .unnumbered}

-   重新格式化整个文档，使得其看上去更规范，也易于以后的修改

-   代码从NotePad++中直接导出，支持语法高亮

-   代码及正文英文字体采用Consolas字体

-   增加了“在脚本中调用SAC”一节

-   新增命令 `transfer`、`traveltime`、`saveimg`、`datagen`

-   更新至SAC v101.5c

-   公式用公式编辑器编辑

## 2012-09-18 1.2版 {#版-2 .unnumbered}

-   增加了封面配图

## 2013-03-29 2.0版 {#版-3 .unnumbered}

-   用 LaTeX重新排版文档

## 2013-04-06 2.1版 {#版-4 .unnumbered}

-   重新整理了第一章

-   修复bugs

## 2013-04-12 2.2版 {#版-5 .unnumbered}

-   重新排版了全部命令

-   重新设计了封面

## 2014-02-22 2.3版 {#版-6 .unnumbered}

-   使用git管理源码

-   整理结构和布局的修改

-   新增小节：“SAC IO升级版”、“黑板变量的读写”、“SAC保存图像”

-   修复bugs

## 2014-04-18 3.0版 {#版-7 .unnumbered}

-   重写了教程部分的大多数内容

-   教程部分根据SAC v101.6a进行修正

-   修复bugs

## 2014-09-25 3.1版 {#版-8 .unnumbered}

-   重新整理了大部分命令的语法说明

-   对“SAC图像”一章进行了修订

-   新增章节：“信号迭加子程序”、“谱估计子程序”、“在Python中调用SAC”

-   修复bugs

## 2015-05-02 3.2版 {#版-9 .unnumbered}

-   修复bugs和typos

-   命令整理：`systemcommand`、`transfer`

-   新增章节

    -   波形排序

    -   标记震相理论走时的三种方法

    -   图像格式转换

    -   SAC初始化宏文件

    -   SAC命令的长度上限

    -   字节序

    -   新增附录“仪器响应”，整理了“去仪器响应”一节

-   新增示例：调用SAC的Hilbert函数

## 2015-06-06 3.3版 {#版-10 .unnumbered}

-   修改bugs和typos

-   命令整理：`hilbert`、`transfer`

-   新增内容：

    -   四个文件重命名脚本

    -   读取某个目录下全部文件遇到的问题

    -   使用Tab遇到的问题

    -   数据命名规则

    -   时区校正

    -   错误与警告消息

    -   未定义变量

    -   SAC debug

    -   `wh` 与 `w over` 的区别

## 2015-09-15 3.4版 {#版-11 .unnumbered}

-   调整与修订：

    -   将命令的“错误消息”和“警告消息”集中整理到附录中

    -   将文件重命名脚本移动到“在脚本中调用SAC”一章

    -   重新整理了“震相拾取”一节的内容

-   新增内容：

    -   在Mac OS X 10.10中安装SAC

    -   在C程序中调用SAC提供的 `distaz` 函数

    -   数据处理中使用 `decimate` 和 `interpolate` 进行数据重采样

    -   Python中修改发震时刻

    -   在C程序中读写SAC文件

    -   在Fortran程序中读写SAC文件

    -   在Python脚本中读写SAC文件

    -   在matlab中读写SAC文件

    -   修改SAC所能读取的文件数目的上限

    -   文档维护与更新并征集维护者

-   命令整理：`mtw`、`markptp`、`markvalue`、`readcss`

-   修正Bugs和Typos

## 2016-01-09 3.5版 {#版-12 .unnumbered}

-   增加示例：绘制滤波器的时间响应和频率响应

-   增加示例：一次性修改多个波形数据的发震时刻

-   新增章节：`rdseed` 的选项及其用法

-   新增章节：介绍IRIS等地震数据中心

-   新增章节：介绍数据申请：连续波形数据和事件波形数据

-   新增章节：IRIS波形数据申请工具

-   新增章节：SAC与脚本运行速度差异导致的陷阱

-   新增Perl脚本：数据提取、合并、重命名、修改发震时刻、去仪器响应、分量旋转、重采样

-   新增Python脚本：数据提取、合并、重命名、修改发震时刻、去仪器响应、分量旋转、重采样

-   更新命令说明：`plotpk`、`plot1`、`plot2`、`datagen`

-   新增命令：`writecss`

-   修正Bugs和Typos

