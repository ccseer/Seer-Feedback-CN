​
大部分 Seer 已内部兼容的第三方程序都会存在运行权限不一致的问题。

查看 Seer 是否有管理员权限，可打开 关于 Seer 窗口，版本号中带有  + 的就代表当前是以管理员权限运行。

<img src="https://raw.githubusercontent.com/wiki/ccseer/Seer/res/2022-12-17-20-59-05.png" width="500">

### Everything： 需要 Seer 有相同或者更高的权限

- 如果 Everything 是管理员权限，Seer 需要是管理员权限。
- 如果 Everything 不是管理员权限，Seer 有或者没有管理员权限都可以。
- 对于 Everything-1.5a，列的排序不影响 Seer 预览
- 对于 Everything-1.4.0 需要第一列是文件名，第二列是路径  
   ![image](https://github.com/user-attachments/assets/3ef3f62c-00a1-4bf2-93d6-76356041b312)

### 文件资源管理器“打开/保存”弹窗

- 同 Everything。
- 微软商店版本不支持此功能。

### Directory Opus

- Seer-2.8.6 更新之后，唯一无法工作的情况： DOpus 是管理员权限。（Seer 有没有管理员权限都不影响结果）
- 权限不一致时出现的现象：在 DO 中按空格后 Seer 没有任何反应，回到桌面和系统的资源管理器也无法触发，大概四五分钟后，程序恢复正常。

### 腾讯桌面整理

- 需要 腾讯桌面整理 的版本号为 3.2.1448.127 或以上。

### 两种自定义触发方式

#### 1. 命令行

- 网站安装版需要完整 Seer 执行文件路径，具体路径根据你的安装位置有所不同: `"C:\Program Files(x86)\Seer\seer.exe"
"C:\example.pdf"`

- 微软商店版直接在命令行输入  Seer.exe 即可响应：`Seer.exe "C:\example.pdf"`

#### 2.编程调用方式

- [Integration with 3rd party software](https://github.com/ccseer/Seer/wiki/4.-Integration-with-3rd-party-software)
- 遇到兼容 Seer 的代码疑问可以直接发邮件

---

### 一个 Tip：

对于大部分程序，在软件 A 中启动另一个软件 B 时，B 会拥有和 A 一样的权限。也就是说，当 A 有管理员权限，在 A 中打开 B，B 也会默认带有管理员权限。

举个栗子：

1. 假设你的 Everything 是管理员权限运行；

   <img src="https://github.com/user-attachments/assets/c50fbaca-1528-43a9-bcf1-193cfda24365" width="500">

2. 搜索 Seer.exe 然后在 Everything 中双击打开程序，此时 Seer 也会带有和 Everything 一样的管理员权限；
   - 同样的道理，在运行安装包程序时会请求管理员权限，完成后安装包程序会默认打开 Seer.exe ，此时 Seer 也会自动带有管理员权限。退出 Seer 后再手动打开 Seer 即可还原。
3. 看懂掌声。

​
