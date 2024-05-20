# 检测硬盘
lsblk
 
# 假设新硬盘识别为 /dev/sdb，分区硬盘
sudo fdisk /dev/sdb
 
# 在fdisk提示下创建新分区
# 输入 'n' 创建新分区
# 输入 'w' 写入并退出fdisk
 
# 格式化新分区为ext4文件系统
sudo mkfs.ext4 /dev/sdb1
 
# 创建挂载点
sudo mkdir /mnt/newdisk
 
# 挂载新分区
sudo mount /dev/sdb1 /mnt/newdisk
 
# 为了使得开机自动挂载，需要编辑 /etc/fstab 文件
# 添加一行如下：
echo '/dev/sdb1 /mnt/newdisk ext4 defaults 0 0' | sudo tee -a /etc/fstab