如何使用tar命令来对文件进行压缩和解压操作？

-------------------------------------------

tar 命令在Linux环境中用于创建.tar.gz 或者 .tgz 档案文件。

1、压缩整个目录或者单个文件，其压缩是递归的。

tar -czvf name-of-archive.tar.gz /path/to/directory-or-file

其参数意义：

 -C: 创建一个archive
 
 -Z: 压缩该archive成gizp

 -V: 在创建过程中将进度显示在终端，也被称为"verbose" 模式，v指令是所有这些命令可以使用的。
 
 -f: 允许我们指定archive的文件名

比如，我们有一个名为“data”的目录，想把它压缩成名为“archive.tar.gz” 

 $ tar -czvf archive.tar.gz data

我们有一个目录 /usr/local/something 在当前系统中，我们想将其压缩成一个名为 archive.tar.gz 的文件。

 $ tar -czvf archive.tar.gz /usr/local/something


----------------------------------------------------------------------

解压文件：

 $ tar -xzvf archive.tar.gz

 -X: 该开关替代了-C, 表明我们想解压archive文件，而非压缩。

 我们想解压archive文件到特定的目录，则可以通过在指令最后添加 -C 开关来指定目标目录。

 $ tar -xzvf archive.tar.gz -C /tmp




