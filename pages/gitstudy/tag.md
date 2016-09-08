#  git tag — 标签相关操作

标签可以针对某一时间点的版本做标记，常用于版本发布。

## 列出标签
```bash
$ git tag # 在控制台打印出当前仓库的所有标签
$ git tag -l ‘v0.1.*’ # 搜索符合模式的标签
```

## 打标签

git标签分为两种类型：轻量标签和附注标签。轻量标签是指向提交对象的引用，附注标签则是仓库中的一个独立对象。建议使用附注标签。
###  创建轻量标签

```bash
$ git tag v0.1.2-light
```

### 创建附注标签

```bash
$ git tag -a v0.1.2 -m “0.1.2版本”
```

创建轻量标签不需要传递参数，直接指定标签名称即可。
创建附注标签时，参数`a`即`annotated`的缩写，指定标签类型，后附标签名。参数`m`指定标签说明，说明信息会保存在标签对象中。

## 切换到标签
与切换分支命令相同，用`git checkout [tagname]`

## 查看标签信息

用`git show`命令可以查看标签的版本信息：

```bash
$ git show v0.1.2
```

## 删除标签

误打或需要修改标签时，需要先将标签删除，再打新标签。

```bash
$ git tag -d v0.1.2 # 删除标签
```

参数`d`即`delete`的缩写，意为删除其后指定的标签。

给指定的`commit`打标签
打标签不必要在`head`之上，也可在之前的版本上打，这需要你知道某个提交对象的校验和（通过`git log`获取）。

## 补打标签

你甚至可以在后期对早先的某次提交加注标签。比如在下面展示的提交历史中：

$ git log --pretty=oneline
15027957951b64cf874c3557a0f3547bd83b3ff6 Merge branch 'experiment'
a6b4c97498bd301d84096da251c98a07c7723e65 beginning write support
0d52aaab4479697da7686c15f77a3d64d9165190 one more thing
6d52a271eda8725415634dd79daabbc4d9b6008e Merge branch 'experiment'
0b7434d86859cc7b8c3d5e1dddfed66ff742fcbc added a commit function
4682c3261057305bdd616e23b64b0857d832627b added a todo file
166ae0c4d3f420721acbb115cc33848dfcc2121a started write support
9fbc3d0d0ae598e95dc970b74767f19372d61af8 updated rakefile
964f16d36dfccde844893cac5b347e7b3d44abbc commit the todo
8a5cbc430f1a9c3d00faaeffd07798508422908a updated readme
我们忘了在提交 “updated rakefile” 后为此项目打上版本号 v0.1.1，没关系，现在也能做。只要在打标签的时候跟上对应提交对象的校验和（或前几位字符）即可：

```bash
$ git tag -a v0.1.1 9fbc3d0
```

## 标签发布

通常的`git push`不会将标签对象提交到`git`服务器，我们需要进行显式的操作：

```bash
$ git push origin v0.1.2 # 将v0.1.2标签提交到git服务器
$ git push origin --tags # 将本地所有标签一次性提交到git服务器
```

### 注意：如果想看之前某个标签状态下的文件，可以这样操作

- 1.`git tag`   查看当前分支下的标签

- 2.`git  checkout v0.21`   此时会指向打`v0.21`标签时的代码状态，（但现在处于一个空的分支上）

