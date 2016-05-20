# Taskwarrior TODO工具

## 什么是TASKWARRIOR
[Taskwarrior](https://taskwarrior.org)是一个终端下的任务管理工具，功能极其强大。 具体信息在它的官方网站上面已经介绍的很详尽了。下面就列一段概述：

It maintains a task list, allowing you to add/remove, and otherwise manipulate your tasks. Task has a rich set of subcommands that allow you to do sophisticated things. You’ll find it has customizable reports, charts, GTD features, device synching, documentation, extensions, themes, holiday files and much more.

它维护一个任务列表，允许你针对你的任务列表进行添加、移除或者一些其他的操作。任务由丰富的子命令设定，允许你进行精准复杂的控制。它还有可制定报告，报表，时间管理，设备同步，文档，扩展，主题，假期文件（译注：一个假期时间 表配置，针对不同的国家与区域）以及更多。

## 安 装
```bash
sudo apt-get install task
```

## 基础用法

### 新增一个任务
添加一个任务很简单，直接task add后面跟上任务的描述就可以了。
```bash
$ task add Buy a vps!
$ task list
 
ID Project Pri Due Active Age Description
 1                         3s Buy a vps!
 
1 task
```
### 删除一个任务
删除一个任务，需要做的是运行task <filter> delete。这里的<filter>暂时可以简单 的看做这个任务的ID，后面会详细介绍<filter>的用法。:)

```bash
$ task
[task next]
 
ID Project Pri Due A Age Urgency Description
 1                   29s       0 Buy a vps!
 
1 task
$ task 1 delete
Permanently delete task 1 'Buy a vps!'? (yes/no) yes
Deleting task 1 'Buy a vps!'.
Deleted 1 task.
```
### 按紧急程度排序项目
```bash
$ task next 
```

### 将任务标记为完成
完成一个任务和删除一个任务很相似，运行task <filter> done。
```bash
$ task add Buy a vps!
Created task 2.
$ task
[task next]
 
ID Project Pri Due A Age Urgency Description
 1                    1s       0 Buy a vps!
 
1 task
$ task 1 done
Completed task 1 'Buy a vps!'.
Completed 1 task.
```
### 将任务纳入隶属的项目
askwarrior的功能很强大，可以简单的为每个任务创建一个隶属的项目。可以有很多种方 法创建或修改任务隶属的项目组。

#### 1. 可以在添加任务的同时指定任务所隶属的项目
```bash
$ task add project:company Fix a bug
$ task add proj:company Fix a bug # taskwarrior 会自动匹配唯一的子命令
$ task add pro:company Fix a bug # taskwarrior 会自动匹配唯一的子命令
$ task add project:company.server Fix a bug # 项目可以分类成子项目
```

#### 2. 可以使用task <filter> modify proj:xx命令在已经创建的任务上添加或修改它的隶 属项目。
```bash
$ task 2 modify proj:company
```
#### 3. 查看指定项目下的任务
```bash
$ task proj:company list
```

#### 4. 删除任务的隶属项目
```bash
$ task 1 modify proj:
```
**注意:** 删除的隶属项目会作为一个独立到项目列在任务表中

## 高级用法

### 优先级（priority）
Taskwarrior允许设置任务的优先级。分别有L(Low)，M(Middle)和H(High)三个级别 。
```bash
$ task add project:Home priority:H Find the adjustable wrench
$ task 1 modify priority:M
$ task 1 modify pri:L # 同样的Taskwarrior可以自动理解子命令的简称
$ task 1 modify pri: # 删除任务的优先级
```
此外，还可以针对优先级对项目进行显示
```bash
$ task pri.below:H # High等级以下的任务
$ task pri.over:L # Low等级以上的任务
$ task pri.not:M # 不是Middle等级的其他所有任务
```
### 截止日期（due）

#### 为一个任务添加截止日期
```bash
$ task add This is an urgent task due:tomorrow # 将到期时间设置为明天
$ task 1 modify due:tomorrow # 将到期时间设置为明天
$ task 1 modify due:2013-03-12 # 将到期时间设置为指定时间
$ task 1 modify due:eom # 将到期时间设置为当月的最后一天（end-of-mouth）
$ task 1 modify due:eoy # 将到期时间设置为今年的最后一天（end-of-year）
$ task 1 modify due: # 删除任务的到期时间
```

#### due过滤器的使用方法
```bash
$ task due:tomorrow # 明天截止的任务
$ task due:eom # 当月月末截止的任务
$ task due.before:today # 今天之前截止的任务
$ task overdue # 已过期的任务
```

### 注释（annotate/denotate）
```bash
$ task add Create a blog.
$ task 1 annotate I need a linux server
$ task 1 annotate I gotta learn php
$ task 1
[task next 1]
 
ID Project Pri Due A Age Urgency Description
 1                   15s     0.9 Create a blog.
                                 8/8/2013 I need a linux server
                                 8/8/2013 I gotta learn php
 
1 task
```

### 标签
```bash
$ task add Create a blog.
$ task 1 modify +blog # 为任务添加标签
$ task +blog list # 标签过滤器
$ task 1 modify -blog # 删除任务的某一个标签
```

### 追加（prepend/append）
有时候，想要给任务追加一些描述，但是又不想重新把任务的描述打一次的话，可以使用prepend和append功能。
```bash
task add music
$ task 1 prepend Download some
$ task 1 append into my iPod
$ task 1
[task next 1]
 
ID Project Pri Due A Age Urgency Description
 1                   13s       0 Download some music into my iPod
 
1 task
```

### 重复任务（recur/until）
```bash
$ task 1 modify due:eom recur:monthly
$ task 2 modify due:eom recur:yearly
$ task 3 modify due:eom recur:monthly until:eoy
$ task recurring
```

### 日历（cal）
```bash
$ task cal
```

## MORE
```bash
$ man task
```