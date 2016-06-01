# linux 批量替换文件内容及查找某目录下所有包含某字符串的文件（批量修改文件内容）

1. sed
```bash
grep -rl matchstring somedir/ | xargs sed -i 's/string1/string2/g' 
```

Exp:
 
对象:文件夹

```bash
grep -rl 'windows' ./path | xargs sed -i 's/windows/linux/g'  
```
 
2. find
对象:文件

```bash
find -name 'test' | xargs perl -pi -e 's|windows|linux|g'  
```
这里使用了`perl`语言，使用`-e`加上一段代码，从而批量地将当前目录及所有子目录下的`file.log`文件中的`string1`替换成了`string2`;`string`支持正则表达式
 
3. awk
```bash
grep -i "windows" -r ./path | awk -F : '{print $1}' | sort | uniq | xargs sed -i 's/windows/linux/g'  
```

这里使用了`shell`命令，先查找出文件，再用`awk`分割（以`:`切分），再行替换！
**注意：** `grep`可以使用正则，也可以使用`\\`转义一些特殊字符，比如`“`等 
```bash
sed -i 's/\"localhost\"/\"10.2.2.2\"/g' /home/my.conf
```
 
4. sed replace word`/`string syntax
The syntax is as follows:
```bash
sed -i 's/old-word/new-word/g' *.txt  
```
 
GNU sed command can edit files in place (makes backup if extension supplied) using the`-i`option. If you are using an old UNIX sed command version try the following syntax:
```bash
sed 's/old/new/g' input.txt > output.txt  
```
 
You can use old sed syntax along with bash for loop:
```bash
#!/bin/bash  
OLD="xyz"  
NEW="abc"  
DPATH="/home/you/foo/*.txt"  
BPATH="/home/you/bakup/foo"  
TFILE="/tmp/out.tmp.$$"  
[ ! -d $BPATH ] && mkdir -p $BPATH || :  
for f in $DPATH  
do  
  if [ -f $f -a -r $f ]; then  
    /bin/cp -f $f $BPATH  
   sed "s/$OLD/$NEW/g" "$f" > $TFILE && mv $TFILE "$f"  
  else  
   echo "Error: Cannot read $f"  
  fi  
done  
/bin/rm $TFILE  
```

5. A Note About Bash Escape Character
A non-quoted backslash`\\`is the Bash escape character. It preserves the literal value of the next character that follows, with the exception of newline. If a`\newline` pair appears, and the backslash itself is not quoted, the `\newline` is treated as a line continuation (that is, it is removed from the input stream and effectively ignored). This is useful when you would like to deal with UNIX paths. In this example, the sed command is used to replace UNIX path` "/nfs/apache/logs/rawlogs/access.log" `with` "__DOMAIN_LOG_FILE__"`:
```bash
#!/bin/bash  
## Our path  
_r1="/nfs/apache/logs/rawlogs/access.log"  
   
## Escape path for sed using bash find and replace   
_r1="${_r1//\//\\/}"  
   
# replace __DOMAIN_LOG_FILE__ in our sample.awstats.conf  
sed -e "s/__DOMAIN_LOG_FILE__/${_r1}/" /nfs/conf/awstats/sample.awstats.conf  > /nfs/apache/logs/awstats/awstats.conf  
   
# call awstats  
/usr/bin/awstats -c /nfs/apache/logs/awstats/awstats.conf  
```
 
The`$_r1`is escaped using bash find and replace parameter substitution syntax to replace each occurrence of`/` with`\/`.
 
6. perl `-pie` Syntax For Find and Replace
The syntax is as follows:
```bash
perl -pie 's/old-word/new-word/g' input.file > new.output.file  
```
 
**from:** http://www.cyberciti.biz/faq/unix-linux-replace-string-words-in-many-files/
 
7. linux下查找某目录下所有文件包含某字符串的命令
```bash
#从文件内容查找匹配指定字符串的行：  
$ grep "被查找的字符串" 文件名  
  
#从文件内容查找与正则表达式匹配的行：  
$ grep –e “正则表达式” 文件名  
  
#查找时不区分大小写：  
$ grep –i "被查找的字符串" 文件名  
  
#查找匹配的行数：  
$ grep -c "被查找的字符串" 文件名  
  
#从文件内容查找不匹配指定字符串的行：  
$ grep –v "被查找的字符串" 文件名  
  
#从根目录开始查找所有扩展名为.txt的文本文件，并找出包含"linux"的行  
find . -type f -name "*.txt" | xargs grep "linux"   
```
