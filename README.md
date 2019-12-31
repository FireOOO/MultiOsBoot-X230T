# 多系统启动EFI分区文件，ThinkPad X230 Tablet 

BIOS设置为UEFI启动，使用GPT分区，安装的系统有：
- Windows 7
- Windows 10
- MacOS 10.15.2
- Ubuntu
- Linux Mint
- Manjaro
- Phoenix OS

多系统引导选择画面
![](https://github.com/KyleTang/MultiOsBoot-X230T/raw/master/Assets/imgs/osSelect.jpg)

X230T
![](https://github.com/KyleTang/MultiOsBoot-X230T/raw/master/Assets/imgs/x230t.jpg)

## 目前效果
1. XorBoot会记住上次启动的系统
2. win10可以正常休眠，并从休眠恢复
3. Win7 不能使用休眠
4. MacOS 10.15.2最新版 ，完善情况见：https://forum.51nb.com/forum.php?mod=viewthread&tid=1923735&extra=
5. 三个发行版的linux系统
6. Phoenix OS 凤凰系统Android

## 启动UEFI图示
![](https://github.com/KyleTang/MultiOsBoot-X230T/raw/master/Assets/imgs/启动UEFI图示.png)

## 分区表
![](https://github.com/KyleTang/MultiOsBoot-X230T/raw/master/Assets/imgs/分区表.png)

		备注：OS：windows 10

## 特别提示
- 分区表使用GPT分区
- Linux Mint因为是基于Ubuntu的发行版，默认它会使用Ubuntu作为启动目录和BIOS里UEFI启动项名称。这里将EFI的Ubuntu目录修改为lxmint。

## 各系统EFI启动入口及配置
### ubuntu和Linux Mint
- EFI入口 \EFI\Ubuntu\bootx64.efi (这个文件里写死了\EFI\Ubuntu)
- 加载启动菜单配置文件 \EFI\Ubuntu\grub.cfg，这个文件里有配置ubuntu分区的UUID和GPT编号
- 再转到去该分区加载配置(,gptX)/boot/grub/grub.cfg
        
### 为了方便分开引导，将Linux Mint的目录调整（使用WinHex修改）
- EFI入口 \EFI\lxmint\bootx64.efi (这个文件里写死了\EFI\lxmint)
- 加载启动菜单配置文件 \EFI\lxmint\grub.cfg
        
### Manjaro
- EFI入口 \EFI\Manjaro\bootx64.efi
- 这个入口文件里写死了Manjaro的分区编号，例如gpt6，
- 然后去该分区加载配置(,gpt6)/boot/grub/grub.cfg

		特别说明：如果Manjaro分区gpt编号（非UUID）发生变化，需要修改\EFI\Manjaro\bootx64.efi里边的gpt6（使用WinHex修改）
        
### Phoenix OS凤凰系统
- EFI入口 \EFI\PhoenixOS\Boot\bootx64.efi
- 将启动权转给与bootx64.efi同目录的grubx64.efi，
- 加载启动菜单配置文件 \EFI\Boot\grub.cfg

## 参考
- Hackintosh黑苹果长期维护机型EFI及安装教程整理 https://github.com/daliansky/Hackintosh
- Clover EFI BootLoader https://sourceforge.net/projects/cloverefiboot/
- Hackintosh-X230-macOS https://github.com/littlegtplr/Hackintosh-X230-macOS
- Clover Configurator https://mackie100projects.altervista.org/download-clover-configurator/
- 分区工具Disk Genius http://www.diskgenius.cn/download.php
- 二进制文件修改WinHex
- 多系统引导工具XorBoot http://bbs.wuyou.net/forum.php?mod=viewthread&tid=157812&extra=page%3D1
- Windows启动编辑BOOTICE http://bbs.wuyou.net/forum.php?mod=viewthread&tid=57675&extra=page%3D1
