# linux文件基本属性

从左至右用0-9这些数字来表示。

第0位确定文件类型；  
当为[ d ]则是目录
当为[ - ]则是文件；
若是[ l ]则表示为链接文档(link file)；
若是[ b ]则表示为装置文件里面的可供储存的接口设备(可随机存取装置)；
若是[ c ]则表示为装置文件里面的串行端口设备，例如键盘、鼠标(一次性读取装置)。

第1-3位确定属主（该文件的所有者）拥有该文件的权限；
第4-6位确定属组（所有者的同组用户）拥有该文件的权限；
第7-9位确定其他用户拥有该文件的权限；

其中，第1、4、7位表示读权限，如果用"r"字符表示，则有读权限，如果用"-"字符表示，则没有读权限；  
第2、5、8位表示写权限，如果用"w"字符表示，则有写权限，如果用"-"字符表示没有写权限；  
第3、6、9位表示可执行权限，如果用"x"字符表示，则有执行权限，如果用"-"字符表示，则没有执行权限。
[ r ] 代表可读(read)
[ w ] 代表可写(write)
[ x ] 代表可执行(execute)
[ - ] 没有权限 

# 更改文件属性：

1、chgrp：更改文件属组

```
chgrp [-R] 属组名 文件名
```
参数选项
-R：递归更改文件属组，就是在更改某个目录文件的属组时，如果加上-R的参数，那么该目录下的所有文件的属组都会更改。 

2、chown：更改文件属主，也可以同时更改文件属组

```
chown [–R] 属主名 文件名
chown [-R] 属主名：属组名 文件名
```

3、chmod：更改文件9个属性

Linux文件属性有两种设置方法，一种是数字，一种是符号。

Linux文件的基本权限就有九个，分别是owner/group/others三种身份各有自己的read/write/execute权限。  

先复习一下刚刚上面提到的数据：文件的权限字符为：『-rwxrwxrwx』， 这九个权限是三个三个一组的！
其中，我们可以使用数字来代表各个权限，各权限的分数对照表如下：  
```
r:4  
w:2  
x:1  
```
每种身份(owner/group/others)各自的三个权限(r/w/x)分数是需要累加的，例如当权限为： [-rwxrwx---] 分数则是：  
```
owner = rwx = 4+2+1 = 7  
group = rwx = 4+2+1 = 7  
others= --- = 0+0+0 = 0  
```
所以等一下我们设定权限的变更时，该文件的权限数字就是770啦！变更权限的指令chmod的语法是这样的：  
```
chmod [-R] xyz 文件或目录  
```
选项与参数：  

xyz : 就是刚刚提到的数字类型的权限属性，为 rwx 属性数值的相加。

-R : 进行递归(recursive)的持续变更，亦即连同次目录下的所有文件都会变更