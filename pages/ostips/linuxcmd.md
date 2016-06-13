# linux 常用命令


## 把 .jpe 文件后缀修改为 .jpg

```bash
rename 's/\.jpe$/\.jpg/' *.jpe
```
Or
```bash
rename 's/\.jpe$/\.jpg/' *
```

## 在linux中就可以递归批量修改文件及子文件夹后缀扩展名

find . -type f -name "*.sh" -print0 | xargs -0 rename .sh .bash {}

> 本案例查找当前目录及其子目录下所有扩展名为.sh的文件，将其扩展名修改为.bash
> 使用find的-print0和 xargs的-0选项，可以解决文件名中包含空格的问题。
> 你是用的时候只需把sh 和bash全部对应改掉就可以了。
