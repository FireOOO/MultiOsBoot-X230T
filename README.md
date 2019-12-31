# 多系统启动EFI分区文件，ThinkPad X230 Tablet 

BIOS设置为UEFI启动，使用GPT分区，安装的系统有：
- Windows 7
- Windows 10
- MacOS 10.15.2
- Ubuntu
- Linux Mint
- Manjaro
- Phoenix OS

## 启动UEFI图示
![](https://github.com/KyleTang/MultiOsBoot-X230T/raw/master/启动UEFI图示.png)

## 分区表
![](https://github.com/KyleTang/MultiOsBoot-X230T/raw/master/分区表.png)

		备注：OS：windows 10

## 特别提示
- 分区表使用GPT分区
- Linux Mint因为是基于Ubuntu的发行版，默认它会使用Ubuntu作为启动目录和BIOS里UEFI启动项名称。这里将EFI的Ubuntu目录修改为lxmint。
