# 为什么 Linux 的压缩包都是以.tar.gz为后缀？

[为什么 Linux 的压缩包都是以.tar.gz为后缀？_为什么是tar.gz_greedy-hat的博客-CSDN博客](https://blog.csdn.net/qq_41638851/article/details/123130193)



**`gzip` 只是一个流压缩程序，输入一个流，输出压缩后的数据流。**
给它一个文件，文件本身自然就是一个流，读入、压缩、输出，还是保存成一个文件，没有问题。
然而，如果是一个文件夹、多个文件，该怎么办呢？按什么顺序？怎么存储文件以外的信息？（例如路径、权限。）
操作系统没有提供一种可以把若干个文件组织成一个流的 API ，`gzip` 就无能为力。

**`tar` 则相反，它就是一个打包程序。**天生就是为了处理打包多个文件的问题，它有专门的 `manifest` 来存储一些 `metadata` ，包括包里有什么文件、（相对）路径是什么、在包里的偏移量是什么……
不过，它（最早）没有压缩功能。**想要打包多个文件，很简单，先 `tar` 再 `gzip` ，一个管道就搞定了。**
后缀名自然而然就是 `.tar.gz` 了。
以上说的都是历史上最早的 UNIX 工具。
这些工具的设计很好地体现了 UNIX `一个工具只做一件事情、使用管道组合多个工具`的思想。

当然，到了后来，大家也都觉得这样很麻烦，而且这个功能太过常用了。
所以 GNU 项目在复刻 `UNIX tar` 的时候，选择了把各种常用的压缩解压都集成进 `tar` ，然后提供了一套（丧心病狂的）命令行参数。
现在一条命令就可以完成打包加压缩了，解压也是一样，使用 GNU 的 `tar` 的话，一条命令就可以自动完成压缩加解包，不需要先 `gunzip` 。

> Linux gunzip 命令用于解压文件。