https://cloud.tencent.com/developer/article/1398000

# 文件和目录
- #### cd：切换到的目录的路径，可以是绝对路径，也可以是相对路径
> cd ~user1   进入个人的主目录 
cd /home    进入 '/ home' 目录

- #### pwd：显示工作路径

- #### ls：查看文件与目录的命令，list之意
> ls -l 显示文件和目录的详细资料 
ls -a 列出全部文件，包含隐藏文件

- #### cp：复制文件

- #### mv：移到文件

- #### rm：删除文件

- #### touch：创建文件  如：touch test.txt

- #### mkdir：创建文件夹

# 文件搜索 
- #### find / -name file1 从 '/' 开始进入根文件系统搜索文件和目录 
- #### find / -user user1 搜索属于用户 'user1' 的文件和目录 
- #### find /home/user1 -name \*.bin 在目录 '/ home/user1' 中搜索带有'.bin' 结尾的文件 
- #### find /usr/bin -type f -atime +100 搜索在过去100天内未被使用过的执行文件 
- #### find /usr/bin -type f -mtime -10 搜索在10天内被创建或者修改过的文件 
- #### find / -name \*.rpm -exec chmod 755 '{}' \; 搜索以 '.rpm' 结尾的文件并定义其权限 
- #### find / -xdev -name \*.rpm 搜索以 '.rpm' 结尾的文件，忽略光驱、捷盘等可移动设备 
- #### locate \*.ps 寻找以 '.ps' 结尾的文件 - 先运行 'updatedb' 命令 
- #### whereis halt 显示一个二进制文件、源码或man的位置 
- #### which halt 显示一个二进制文件或可执行文件的完整路径

# 文件中内容查看、搜索 
- #### cat 文件名 #显示全部文件内容，将几个文件合并为一个文件:cat file1 file2 > file
- #### more 文件名 #分页显示文件内容
- #### less 文件名 #与 more 相似，更好的是可以往前翻页
- #### tail 文件名 #仅查看尾部，还可以指定行数
- #### head 文件名 #仅查看头部,还可以指定行数
- #### grep：在文本文件中查找某个字符串
> grep test *file : #查找前缀有“test”的文件包含“test”字符串的文件
> testfile1:This a Linux testfile! #列出testfile1 文件中包含test字符的行 
> grep -r update /etc/acpi 下所有文件中包含字符串"update"的文件


# 文件的权限
- #### chmod : 修改权限，"+" 设置权限，使用 "-" 用于取消
> chmod ugo+rwx directory1 设置目录的所有人(u)、群组(g)以及其他人(o)以读（r，4 ）、写(w，2)和执行(x，1)的权限 
> chmod go-rwx directory1  删除群组(g)与其他人(o)对目录的读写执行权限
 
- #### chown : 修改文件的拥有者
> chown user1 file1 改变一个文件的所有人属性 
> chown -R user1 directory1 改变一个目录的所有人属性并同时改变改目录下所有文件的属性 
> chown user1:group1 file1 改变一个文件的所有人和群组属性



 


