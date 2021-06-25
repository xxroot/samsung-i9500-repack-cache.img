# samsung-i9500-repack-cache.img
三星I9500官方在system.img做了手脚，以前的打包方法会导致无法刷入，国外xda-developers开发者Chainfire已经破解了此限制。
同时感谢@xiaolu。
下面分享i9500的cache.img打包和解包方法;
第一步，你需要安装linux环境，建议安装ubuntu10.10版本，比较稳定和tar后方便三星机型刷入，高于此版本打包tar格式可能导致刷机失败；
第二步，安装好ubuntu10.10系统后建议开启root用户，开启方法可以百度或谷歌下；
第三步，按照下面命令进行打包和解包：
下载解包和打包所需工具，然后如下步骤进行操作即可，打包工具下载：i9500_unpack_repack_tools_cofface
1.   cd work_rom/           //进入cache.img目录，我的是将cache.img放到work_rom目录下
2.  ./simg2img cache.img cache_tmp.img          //转换cache.img格式
3.  mkdir /mnt/rom             //mnt目录下创建rom目录
4.  mount -o loop cache_tmp.img /mnt/rom                          //挂载cache_tmp.img到/mnt/rom目录下，此时你可以进去/mnt/rom目录进行修改cache目录下的文件
5.  ./mkuserimg.sh -s /mnt/rom /root/work_rom/new_cache.img ext4 ./temp 2072m     //重新打包
6.  umount /mnt/rom     //卸载mnt/rom挂载
7.  rm cache.img       //删除旧的cache.img文件
7.  ./sgs4ext4fs –bloat new_cache.img cache.img
