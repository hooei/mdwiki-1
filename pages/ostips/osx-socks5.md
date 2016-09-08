## Mac OSX 下 配置 shadowsocks 代理terminal 翻墙

首先在Mac 上安装shadowsocksX 在启用shadowsocksX翻墙时，软件默认开启了 socks5://127.0.0.1:1080代理。

在终端下使用 export  ALL_PROXY=socks5://127.0.0.1:1080
清除代理 unset ALL_PROXY

也可以在 .bash_profile 或  .zshrc 文件中 添加如下两个函数

```bash
function setproxy(){
	# export {HTTP,HTTPS,FTP}_PROXY="http://127.0.0.1:3128"
	export ALL_PROXY=socks5://127.0.0.1:1080
}

function unsetproxy(){
	# unset {HTTP,HTTPS,FTP}_PROXY
	unset ALL_PROXY
}
```

需要使用代理的时候$ setproxy，不用了就$ unsetproxy
就可以很方便的在shell环境下切换设置代理了。
为了测试是否成功可以curl -i http://ip.cn 查看ip。或者  curl -i http://ip.gs 也可以查看当前ip.

另一种方法
vim /usr/local/opt/myscripts/proxy.sh , 在proxy.sh 文件中写入如下内容
```bash
ALL_PROXY=socks5://127.0.0.1:1080 {HTTP, HTTPS, FTP}_PROXY=socks5://127.0.0.1:1080 "$@"
```
然后 
```bash
$ chmod +x proxy.sh
$ sudo ln -s /usr/local/opt/myscripts/proxy.sh  /usr/local/bin/proxy 
```
使用的时候就可以：
```bash
$ proxy curl www.youtube.com 
```
即可。

