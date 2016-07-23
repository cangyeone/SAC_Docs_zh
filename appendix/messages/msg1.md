执行 [load](/commands/load.html)
命令时找不到外部命令。产生该错误的原因很多，可能 是环境变量
`LD_LIBRARY_PATH` 不包含要载入的共享库的所在目录，或 `$SACSOLIST`
中不包含要载入的共享库的名字。

没有可用的帮助文档包，可能原因是没找到 `${SACAUX}/help` 目录。

对于每一行命令，SAC首先会检查是否是SAC内部的命令，如果不是，则检查是否是系统自带
的命令，比如 `ls`、`cp` 等。

一个例外是系统命令
`rm`。在SAC中直接执行rm命令会出现如上所示的错误。出现该
错误的原因是SAC禁用了系统命令 `rm`，主要目的是为了防止将 `r *.SAC`
误敲成 `rm *.SAC` 而导致数据的误删除。可以使用
[systemcommand](/commands/systemcommand.html) 命令显式
调用系统命令，如下：

``` {.bash}
SAC> rm BAD*.SAC
 ERROR 1106: Not a valid SAC command.
SAC> sc rm BAD*.SAC
```

内存中未读入数据。可能是未指定要读取的文件列表，或列表中的文件不可读。

该错误主要出现在写SAC文件时，出现该错误的原因是SAC文件的头段变量
`lovrok` 的值 为
`FALSE`，即磁盘中的数据不允许被覆盖。解决该问题的方法有两种：

-   以其他文件名写入磁盘，不覆盖磁盘文件；

-   修改 `lovrok` 的值为 `TRUE`；

对数据文件的非法操作。

某些命令无法对时间序列数据进行操作。

某些命令无法对不等间隔数据进行操作。

命令不能对内存中的谱文件进行操作。

没有要写入的文件列表。

通常在使用 [write](/commands/write.html)
命令时会出现该问题。出现该错误的原因是内存中的
波形文件的数目与write命令给出的文件名的数目不想匹配。在该错误信息的后面，紧接着
会给出write命令中给出的文件数目以及内存中的波形数目。

试图读入非SAC格式的文件所产生的错误。

系统内存不足。

[cut](/commands/cut.html)
命令中时间窗的起始参考头段未定义。默认情况下，会使用磁盘
文件的起始时间代替，也可以使用 [cuterr](/commands/cuterr.html)
命令控制该错误的处理方式。

[cut](/commands/cut.html)
命令中时间窗的结束参考头段未定义。默认情况下，会使用磁盘
文件的结束时间代替，也可以使用 [cuterr](/commands/cuterr.html)
命令控制该错误的处理方式。

[cut](/commands/cut.html)
命令中时间窗的开始时间早于磁盘文件的开始时间。默认情况下，
会使用磁盘文件的开始时间代替，也可以使用 [cuterr](/commands/cuterr.html)
命令控制该错误的 处理方式。

[cut](/commands/cut.html)
命令中时间窗的结束时间晚于磁盘文件的结束时间。默认情况下，
会使用磁盘文件的结束时间代替，也可以使用 [cuterr](/commands/cuterr.html)
命令控制该错误的 处理方式。

[cut](/commands/cut.html) 命令中时间窗的开始时间晚于文件结束时间。

文件中数据点的值超过了所允许的范围。比如 [log](/commands/log.html)
中要求数据为正。

使用了 [sort](/commands/sort.html) 命令，但未指定按照哪个参数排序。

[sort](/commands/sort.html) 命令中用于排序的参数太多。

无效的 [sort](/commands/sort.html) 参数。

排序失败。

SAC中与FFT相关的命令，所能允许的最大数据点数是$2^{24}=16777216$。

对数据进行滤波时，拐角频率超过了文件的Nyquist采样率。

在做Hilbert变换时，要求数据的最小长度是201个数据点。

除零的非法操作。

数据文件中存在非正值。

该错误出现在
[addf](/commands/addf.html)、[subf](/commands/subf.html)、[divf](/commands/divf.html)、[mulf](/commands/mulf.html)
以及 [merge](/commands/merge.html) 和 [beam](/commands/beam.html) 中。

出现该错误的原因是多个数据文件中的头段变量不匹配。该命令会明确给出不匹配的头段变量名，以及
出现不匹配的数据文件，以供用户查错。会出现不匹配的头段变量包括npts、delta、kstnm、knetwk、
kcmpnm。

要进行操作的两个数据的时间段不完全重合。

[addf](/commands/addf.html)、[subf](/commands/subf.html)、[merge](/commands/merge.html)
等命令需要先读入二进制数据，再对数据做操作。

使用 [merge](/commands/merge.html) 命令时，两段数据间存在时间间断。