# Ubuntu 常用软件推荐


* 1 [截图软件 Shutter](ubuntu.md#1_截图软件_Shutter)
* 2 [图像浏览器 gThumb](ubuntu.md#2_图像浏览器_gThumb)
* 3 [PDF查看工具 Okular](ubuntu.md#3_PDF查看工具_Okular)
* 4 [PDF编辑工具 Master PDF Editor](ubuntu.md#4_PDF编辑工具_Master_PDF_Editor)
* 5 [类似Alfred的软件Mutate](ubuntu.md#5_类似Alfred的软件Mutate)
* 6 [安装媒体解码器](ubuntu.md#6_安装媒体解码器)
* 7 [安装系统清理工具](ubuntu.md#7_安装系统清理工具)


**Env**

```bash
➜ sudo lsb_release -a
Distributor ID : Ubuntu
Description    : Ubuntu 16.04 LTS
Release        : 16.04
Codename       : xenial
```

## 1 截图软件 Shutter

Ubuntu自带的抓图软件使用窗口模式时经常不能包含窗口的外框，用Shutter即可解决这个问题，而且Shutter的功能比Ubuntu抓图更强大。

**优点:**

可以给图片加箭头、直线、方框、圆圈、荧光笔效果，插入文字、图标、序号标签，裁剪图片等。

**安装:**

```bash
sudo apt install shutter
```

## 2 图像浏览器 gThumb 

一个高级图像查看器和浏览器，有许多有用的功能，如：批量重命名图片、批量缩放图片、批量转换图片格式、创建网络相册等。

**安装:**

```bash
sudo apt install gthumb
```

## 3 PDF查看工具 Okular 

最近发现的DPF查看的工具，支持标记，评论等，还可以直接PDF截图等。可以作各种个性化设置，已经变成我的默认PDF查看器了，同时支持的格式众多。

**安装:**

```bash
sudo apt install okular
```

## 4 PDF编辑工具 Master PDF Editor 

有时候需要编辑PDF文件，[Master PDF Editor](https://code-industry.net/masterpdfeditor/)便是好工具之一。支持PDF和XPS文件的导入导出到JPG、TIFF、PNG、BMP等图片格式，可以添加按钮、文本、选择框等，对于原有的文本修改当然也不在话下，例如页面的删除，非常简单，对原有PDF的图片可以任意移动修改和保存等。同时对于常见的PDF阅读需求，如添加注释、高亮等也非常的强大。

这个软件是跨平台滴，Windowns、MAC、Ubuntu下都可以使用，而且，重点是Ubuntu下是免费。

**安装:**
从https://code-industry.net/masterpdfeditor/ 下载: sudo dpkg -i master-pdf-editor-3.7.10_amd64.deb

```bash
sudo dpkg -i master-pdf-editor-3.7.10_amd64.deb
```

## 5 类似Alfred的软件Mutate

Ubuntu中类似Alfred的软件[Mutate](https://github.com/qdore/Mutate)。Mutate还
支持Custom Scripts，自定义类似Alfred的workflow。

**安装:**
```bash
wget https://github.com/qdore/Mutate/releases/download/v2.3/Mutate-2.3.deb
sudo apt-get install gdebi
sudo gdebi Mutate-2.3.deb
```

## 6 安装媒体解码器

由于「法律限制」Ubuntu 无法集成「开箱即用」的 MP3、MP4 等多媒体文件解码支持,不过我们可以在系统安装好之后手动安装 Ubuntu Restricted Extras 来获取媒体解码器。

安装Ubuntu Restricted Extras
```bash
apt://ubuntu-restricted-extras
```
将上面的安装地址复制到浏览器地址栏回车即可。


## 7 安装系统清理工具

操作系统使用久了,越来越多的缓存和垃圾文件都会不断拖慢系统,在此推荐大家安装开源、免费的 BleachBit 工具来进行 Ubuntu 系统清理。

安装BleachBit on Ubuntu
```bash
apt://bleachbit
```
