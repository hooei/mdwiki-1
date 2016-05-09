# 常用的git命令 记录

** 目 录 **

* 1 [删除本地/远程分支](oftenuse.md#1_删除本地/远程分支)


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


