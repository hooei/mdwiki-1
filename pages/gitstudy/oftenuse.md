# 常用的git命令 记录

** 目 录 **

* 1 [删除本地/远程分支](oftenuse.md#1_删除本地/远程分支)
* 2 [提交之前撤销git add](oftenuse.md#2_提交之前撤销git_add)


## 1 删除本地/远程分支

- 查看分支
	- 查看本地分支 
		```bash
		git branch
		```
	- 查看远程分支
		```bash
		git branch -a
		```

- 删除分支
	- 删除本地分支
		```bash
		git branch -d branch-name
		```
	- 删除远程分支
		```bash
		git branch -r -d origin/branch-name
		git push origin :branch-name
		```

## 2 提交之前撤销git add

如果你往暂存区（staging area）中加入了一些错误的文件，但是还没有提交代码。你可以使用一条简单的命令就可以撤销。如果只需要移除一个文件，那么请输入：

- 撤销某个文件

```bash
$ git reset <文件名>
```

- 撤销所有文件
或者如果你想从暂存区移除所有没有提交的修改：

```bash
$ git reset
```
