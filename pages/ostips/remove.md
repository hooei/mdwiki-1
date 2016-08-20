## unix 系统防止rm误删除

方法一：safe-rm软件
safe-rm 是一个开源软件用来替代不太安全的rm。
官方地址：http://freecode.com/projects/safe-rm，ubuntu可以直接apt-get安装，centos要下载源码安装。

方法二：建立回收站机制
它并不真正执行删除操作，而是将文件移动到一个特定目录，可以设置定时清楚回收站，或者在回收站里面的文件大小达到一定容量时（或者用时间做判断）执行删除操作以腾出空间。
可以写个shell脚本替换rm命令，或者在需要删除文件的时候使用mv命令将文件移动到回收站。　　
1） 在/Users/username/ 目录下新建一个目录，命名为：.Trash
2）在/Users/username/tools/目录下，新建一个shell文件，命名为： remove.sh
```bash
PARA_CNT=$#
TRASH_DIR="/Users/lihong/.Trash"

for i in $*; do
	STAMP=`date +"%Y-%m-%d_%H_%M_%S"`
	fileName=`basename $i`
	mv $i $TRASH_DIR/$fileName.$STAMP
done
```
3)修改.zshrc ， 增加一行
```bash
alias rm="sh /Users/lihong/tools/remove.sh"
```
4）设置crontab，定期清空垃圾箱，如：
0 0 * * * rm -rf /Users/lihong/.Trash/*
每天0点清空垃圾箱


