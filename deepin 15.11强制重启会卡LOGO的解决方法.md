# deepin 15.11强制重启会卡LOGO的解决方法

如果遇到在深度deepin 15.10.1系统桌面中卡死，然后强制重启，会出现卡LOGO的情况，那以下解决方法很适合你的情况，请按说明去处理。 

 

**背景**

deepin 15.11重启后卡在logo上了，无法进入登录界面，按Ctrl+alt+F1之后能看见以下lightdm启动失败警告：

![在deepin 15.10.1桌面中会卡死，然后强制重启会卡LOGO的解决方法](https://ywnz.com/uploads/allimg/19/1-1Z613215G63R.JPG)

找网上的解决方法基本都是针对N卡显卡问题的卡logo，对于这个错误`根本没用`。

要声明的是：首先碰到这种问题不要强制重启，千万不要强制重启，否则后果更糟糕。

因为我们需要tty去操作，而重启之后进入tty（不管Ctrl+Alt+F几）都是光标在闪，根本没有提示login，所以不要重启之后再进tty，应该直接在卡死的时候进tty（Ctrl+alt+F2就行），输入用户名密码之后先尝试重启lightdm（我没有重试而是直接KILL掉了，所以我建议你们试一下，万一就好使了呢）：

sudo systemctl restart lightdm

如果启动不了的话就可以按以下方法处理。

 

**解决方法**

1. 进入deepin的recovery
2. 卸载dde、lightdm：

```
sudo apt-get remove dde
sudo apt-get remove lightdm
```

3. 修改软件源：

   这一点还是要看你那里安装dde的时候速度，你可以先执行第3步看一下下载速度，如果速度不够就可以先kill了apt-get进程，修改了软件源之后重新安装。备份原系统软件源（稳一点）。保存之后执行：

   ```
   sudo apt-get update
   ```

4. 安装dde、lightdm：

```
sudo apt-get install dde
sudo apt-get install lightdm
```

5. 决定命运的时候到了，执行reboot重启：

```
reboot
```

