# git 忽略规则

git 通过在项目根目录下创建.gitignore文件来忽略不提交的文件

### 忽略文件的原则是：

1.所有空行或者以注释符号 ＃ 开头的行都会被 Git 忽略。
2.可以使用标准的 glob 模式匹配。
3.匹配模式最后跟反斜杠（/）说明要忽略的是目录。
4.要忽略指定模式以外的文件或目录，可以在模式前加上惊叹号（!）取反。
5.所谓的 glob 模式是指 shell 所使用的简化了的正则表达式。
6.星号（*）匹配零个或多个任意字符；[abc]匹配任何一个列在方括号中的字符（这个例子要么匹配一个 a，要么匹配一个 b，要么匹配一个 c）；问号（?）只匹配一个任意字符；如果在方括号中使用短划线分隔两个字符，表示所有在这两个字符范围内的都可以匹配（比如 [0-9] 表示匹配所有 0 到 9 的数字）

### 举个例子：

假设你在Windows下进行Python开发，Windows会自动在有图片的目录下生成隐藏的缩略图文件，如果有自定义目录，目录下就会有Desktop.ini文件，因此你需要忽略Windows自动生成的垃圾文件：

```bash
# Windows:
Thumbs.db
ehthumbs.db
Desktop.ini
```

然后，继续忽略Python编译产生的.pyc、.pyo、dist等文件或目录：

```bash
# Python:
*.py[cod]
*.so
*.egg
*.egg-info
dist
build
```

加上你自己定义的文件，最终得到一个完整的.gitignore文件，内容如下：

```bash
# Windows:
Thumbs.db
ehthumbs.db
Desktop.ini

# Python:
*.py[cod]
*.so
*.egg
*.egg-info
dist
build

# My configurations:
db.ini
deploy_key_rsa
```

最后一步就是把.gitignore也提交到Git，就完成了！当然检验.gitignore的标准是git status命令是不是说“working directory clean”。

使用Windows的童鞋注意了，如果你在资源管理器里新建一个.gitignore文件，它会非常弱智地提示你必须输入文件名，但是在文本编辑器里“保存”或者“另存为”就可以把文件保存为.gitignore了。

### 小结

#### 1.忽略某些文件时，需要编写.gitignore。
.gitignore文件本身要放到版本库里，并且可以对.gitignore做版本管理！

#### 2.从版本库中删除

```bash
$ git rm test.txt
rm 'test.txt'
$ git commit -m "remove test.txt"
```

#### 3.忽略文件夹写法

经测试发现，若要忽略一个文件夹下的部分文件夹，应该一个一个的标示。可能有更好的方法。
若test下有多个文件和文件夹。若要ignore某些文件夹，应该这个配置.gitignore文件。若test下有test1，test2,test3文件。要track test3，则.gitignore文件为：

```bash
test/test1
test/test2
!test/test3
```

若为：

```
test/
!test/test3 ，则不能track test3。
```

#### 4.Git 中的文件忽略

1.共享式忽略新建 .gitignore 文件，放在工程目录任意位置即可。.gitignore 文件可以忽略自己。忽略的文件，只针对未跟踪文件有效，对已加入版本库的文件无效。
2.独享式忽略针对具体版本库 ：.git/info/exclude针对本地全局：  git config --global core.excludefile ~/.gitignore

#### 5.忽略的语法规则：
(`#`) 表示注释
(`*`) 表示任意多个字符; 
(`?`) 代表一个字符;
(`[abc]`) 代表可选字符范围
如果名称最前面是路径分隔符 (`/`) ，表示忽略的该文件在此目录下。
如果名称的最后面是 (`/`) ，表示忽略整个目录，但同名文件不忽略。
通过在名称前面加 (`!`) ，代表不忽略。

例子如下：

```bash
# 这行是注释
*.a                   # 忽略所有 .a 伟扩展名的文件
!lib.a                # 但是 lib.a 不忽略，即时之前设置了忽略所有的 .a
/TODO            # 只忽略此目录下 TODO 文件，子目录的 TODO 不忽略 
build/               # 忽略所有的 build/ 目录下文件
doc/*.txt           # 忽略如 doc/notes.txt, 但是不忽略如 doc/server/arch.txt
```

