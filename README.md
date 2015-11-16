# sd_mount
----------------------------------------------------------------

ls /dev/sd*
sudo fdisk -l

1.

sudo fdisk /dev/sdb

a. 按n添加分区，选p(主分区);

b. 选1，也就是sdb1;

c. 然后就是空间划分，一路回车。默认是使用整个磁盘空间。

d. 然后按w写入分区信息

2.

sudo mkfs.ext3 /dev/sdb1  （之前我用mkfs -t ext3 /dev/sdb1，当启动时总是失败）

3. 

创建需要mount的目录

mkdir -p /opt

sudo mount /dev/sdb1 /opt -o rw

4. 

如果需要每次启动加载，修改/etc/fstab文件

在fstab文件里面添加一行：

/dev/sdb1 /opt ext3 defaults 1 1

--------------------------------------------------------

sudo -S mount -t vboxsf androidsrc ~/mnt/share
sudo mount /dev/sdb1 ~/mnt/androidsrc -o rw
