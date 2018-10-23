# Linux-Vim

查看ubuntu版本
sudo lsb_release -a
查看ubuntu是32bit还是64bit
sudo uname --m
sudo uname --s  显示内核名字s
sudo uname --r 显示内核版本
sudo uname --n 显示网络主机名
sudo uname --p 显示cpu 

vim+目录：打开某个文件
在某一行按i(insert)可以编辑

ESC+ZZ退出编辑并保存(按了ESC后，直接按shift+zz，或者切换到大写模式按ZZ)
ESC+:wq退出编辑并保存
ESC+:q退出不保存
ESC+:q!强制退出不保存

查看内容用cat 
pwd 显示当前目录

从普通用户切换超级用户权限：
sudo su
输入密码

从超级用户切换普通用户：
su 用户名

ls查看当前目录下的文件+tab会自动补齐
ls -a查看所有文件包括隐藏文件

修改权限：chmod XXX filename
sudo chmod a+x filename 给所有人加上可执行权限
-rw-------   (600) 只有所有者才有读和写的权限 
-rw-r--r--   (644) 只有所有者才有读和写的权限，组群和其他人只有读的权限 
-rwx------   (700) 只有所有者才有读，写，执行的权限 
-rwxr-xr-x   (755) 只有所有者才有读，写，执行的权限，组群和其他人只有读和执行的权限 
-rwx--x--x   (711) 只有所有者才有读，写，执行的权限，组群和其他人只有执行的权限 
-rw-rw-rw-   (666) 每个人都有读写的权限 
-rwxrwxrwx   (777) 每个人都有读写和执行的权限

删除文件夹及其子目录
rm -rf /var/log/httpd/access
删除文件
rm -f /var/log/httpd/access.log

查找某个文件
locate + name
创建文件
vim+name 有则编辑，没有则创建

列出进程
ps aux
sudo kill +pid杀掉进程

显示文件目录大小(以kb/mb/gb为单位) 会列出所有目录
du -k /home/linux
du -m /home/linux
du -g /home/linux

拷贝整个目录
cp -R /home/usera/. /mnt/temp(包括隐藏文件一起拷贝)
cp -R /home/usera/* /mnt/temp(不包括隐藏文件一起拷贝)
cp a.docx /media/a/a.docx(拷贝单个文件)

查看U盘硬盘等是否被识别
fdisk -l（可以查看到外设分区）
mount /dev/sdb1 /mnt 挂在外设分区

拷贝文件
cp -R /home/haixingx/chtsrc/. /mnt/chtsrc
退出外设
umount /mnt

查询内存：
sudo dmidecode -t memory(Number of Devices:共有几个内存插槽； Maximum Capacity:最大支持多大内存; 以及每个内存槽的情况)
查询Cpu信息
sudo dmidecode -t processor
查询各个分区大小
sudo fdisk -l

卸载 删除软件及其配置文件
apt-get --purge remove <package>
 删除没用的依赖包
apt-get autoremove <package>
 此时dpkg的列表中有“rc”状态的软件包，可以执行如下命令做最后清理：
dpkg -l |grep ^rc|awk '{print $2}' |sudo xargs dpkg -P


