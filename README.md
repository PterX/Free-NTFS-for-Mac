# Nigate

一款支持苹果芯片的Free NTFS for Mac小工具软件。[oxfuse](https://osxfuse.github.io)、[ntfs-3g](https://github.com/osxfuse/osxfuse/wiki/NTFS-3G#installation)方案集成整合，与[ezntfs CLI](https://github.com/lezgomatt/ezntfs)异曲同工。

## 实机演示

视频：https://www.bilibili.com/video/BV1XG4y1f79N

![Watch the video](https://fastly.jsdelivr.net/gh/hoochanlon/free-mac-ntfs/shashin/example.png)

## 先决条件

安装homebrew

```shell
/bin/bash -c "$(curl -fsSL https://gitee.com/ineo6/homebrew-install/raw/master/install.sh)"
```

安装python

```shell
brew install python
```

最后[关闭SIP](https://www.pcbiji.com/212402.html)与[“允许任何来源”](https://jingyan.baidu.com/article/49ad8bce2f5cee1834d8faaa.html)；如果你了解过python的话，可直接运行[ntfs_supprot.py](helpdesk/ntfs_supprot.py)脚本使用。

## 报错解答

“文件损坏扔入废纸篓”，是苹果对软件迁移主机进行了限制，将命令复制到终端回车

```shell
sudo xattr -d com.apple.quarantine /Applications/nigate.app
```

![](https://fastly.jsdelivr.net/gh/hoochanlon/free-mac-ntfs/shashin/fileberak.png)


出现“busy”等无法写入的错误提示，先卸载掉U盘，disk4s1为当前的U盘设备序列名，[官网如是，此类同理](https://github.com/osxfuse/osxfuse/wiki/NTFS-3G)。

![](https://fastly.jsdelivr.net/gh/hoochanlon/free-mac-ntfs/shashin/umount-3g.png)

```shell
sudo umount /dev/disk4s1
```

```shell
sudo /System/Volumes/Data/opt/homebrew/bin/ntfs-3g /dev/disk4s1 /Volumes/NTFS -olocal -oallow_other -o auto_xattr
```

<!--

***Error loading Python lib***

目前版本已解决；pyinstaller制作的程序受限于所在主机环境环境的问题，网上有说配置虚拟环境，但我还是在app程序内嵌入python源文件才搞定。

-->

## 完全免费软件清单

***Free NTFS for Mac list***

* [easyuefi ntfs（支持macOS13.0）](https://www.easyuefi.com/ntfs-for-mac/ntfs-for-mac.html)
* [mounty（仅限macOS12及以下）](https://mounty.app)
* [ntfstool（2020.5.20停止更新）](https://ntfstool.com)
* [paragon ntfs for Mac（希捷客户支持版）](https://www.seagate.com/cn/zh/support/software/paragon/#downloads)
* [Omi NTFS磁盘专家（最后的完全免费版-吾爱破解存档 v1.1.1）](https://www.52pojie.cn/thread-1513314-1-1.html)

**注意**
