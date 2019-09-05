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

# 文件中内容搜索 
- #### grep：在文本文件中查找某个字符串
- #### tail：查看输出文件的最后几行的内容 或 实时输出
> tail -2 file1 查看一个文件的最后两行 
tail -f /var/log/messages 实时查看被添加到一个文件中的内容


 



 


