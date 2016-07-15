# 一键直达目录神器: autojump

autojump是一个命令行工具，它允许你可以直接跳转到你喜爱的目录，而不用管你现在身在何处。对于大多数的标准 Linux 发行版本，能够在软件仓库中下载得到，它们包括 Debian (testing/unstable), Ubuntu, Mint, Arch, Gentoo, Slackware, CentOS, RedHat 和 Fedora。也能在其他平台中使用，例如 OS X(使用 Homebrew) 和 Windows (通过 Clink 来实现)使用 autojump 你可以跳至任何特定的目录或一个子目录。你还可以用文件管理器打开某个目录，并查看你在某个目录中所待时间的统计数据。

## 安装autojump 

源码安装
```bash
$ git clone git://github.com/joelthelion/autojump.git
```
接着，使用 cd 命令切换到下载目录。
```bash
$ cd autojump
```
下载，赋予安装脚本文件可执行权限，并以 root 用户身份来运行安装脚本。
```bash
# chmod 755 install.py
# ./install.py
```

系统安装

在 Debian, Ubuntu, Mint 及类似系统中安装 autojump :

```bash
# apt-get install autojump
```

为了在 Fedora, CentOS, RedHat 及类似系统中安装 autojump, 你需要启用 EPEL 软件仓库。
```bash
# yum install epel-release
# yum install autojump
```
##  安装后的配置

先找到 autojump.sh  或 autojump.zsh 的位置

```bash
whereis autojump.zsh
```

假设 autojump.zsh 所在路经：/usr/share/autojump/autojump.zsh , 如果你的不是hedge路经，请使用自己的路经。

要以常规用户身份运行下面的命令:

```bash
$ source /usr/share/autojump/autojump.sh on startup
```
为了使得 autojump 在 BASH shell 中永久有效，你需要运行下面的命令。

```bash
$ echo '. /usr/share/autojump/autojump.sh' >> ~/.bashrc
```

或者 配置.zshrc

```bash
[[ -s /usr/share/autojump/autojump.zsh ]] && . /usr/share/autojump/autojump.    zsh 
```

## 使用

需要记住的一点 : j 是 autojump 的一个封装，你可以使用 j 来代替 autojump， 相反亦可。

使用 -v 选项查看安装的 autojump 的版本。
```bash
$ j -v
```
或
```bash
$ autojump -v
```

智能跳转，安装了autojump之后，zsh 会自动记录你访问过的目录，通过 j + 目录名 可以直接进行目录跳转，而且目录名支持模糊匹配和自动补全，例如你访问过hadoop-1.0.0目录，输入j hado 即可正确跳转。j –stat 可以看你的历史路径库。

目录浏览和跳转：输入 d，即可列出你在这个会话里访问的目录列表，输入列表前的序号，即可直接跳转。

在当前目录下输入 .. 或 … ，或直接输入当前目录名都可以跳转，你甚至不再需要输入 cd 命令了。

跳到先前到过的目录 ‘/var/www‘。
```bash
$ j www
```

跳到先前到过的子目录‘/home/avi/autojump-test/b‘ 而不键入子目录的全名。

```bash
$ jc b
```

查看每个文件夹的权重和全部文件夹计算得出的总权重的统计数据。文件夹的权重代表在这个文件夹中所花的总时间。 文件夹权重是该列表中目录的数字。(LCTT 译注: 在这一句中，我觉得原文中的 if 应该为 is)
```bash
$ j --stat
```
支持tab键补全
```bash
$ autojump d
```
然后敲击tab键，将会返回/root/home/doc或者/root/home/ddl。


最后，对于高级用户，你可以访问目录数据库，并修改它的内容。可以使用下面的命令来手动添加一个目录：

```bash
$ autojump -a [目录]
```

如果你突然想要把当前目录变成你的最爱和使用最频繁的文件夹，你可以在该目录通过命令的参数 i 来手工增加它的权重

```bash
$ autojump -i [权重]
```

这将使得该目录更可能被选择跳转。相反的例子是在该目录使用参数 d 来减少权重：

```bash
$ autojump -d [权重]
```

要跟踪所有这些改变，输入：

```bash
$ autojump -s
```

这会显示数据库中的统计数据。而以下：

```bash
$ autojump --purge
```
命令将会把不再存在的目录从数据库中移除。


更多help 

```bash
$ j --help
```
