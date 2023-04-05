# CentOS忘记密码如何重置

1. 在CentOS启动时按下Esc键，进入grub启动菜单。
2. 在grub启动菜单界面中，选中要启动的CentOS内核，并按下E键进入编辑模式。
3. 在编辑模式中，找到以“linux16”开头的行，将其中的“ro”改为“rw init=/sysroot/bin/sh”，然后按下Ctrl+X组合键启动CentOS。
4. 当进入系统的单用户模式时，使用以下命令重新挂载文件系统：`chroot /sysroot`。
5. 执行命令`passwd`，设置新的root用户密码。
6. 执行命令`touch /.autorelabel`，更新SELinux上下文，以防止重启后无法登录。
7. 执行命令`exit`，退出chroot环境。
8. 执行命令`reboot`，重启CentOS系统。