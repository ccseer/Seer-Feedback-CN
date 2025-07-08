## Seer 在什么情况下会连接到互联网？

#### 隐式连接

- 当您预览 Markdown 文件时，程序会请求网络以加载在线图片。这适用于所有 HTML 内容。
- **仅限桌面版**，Seer 需要网络来验证您的许可证密钥，但仅在您尝试**激活** Seer 时会发生。一旦激活完成，后续不会再进行网络请求来验证。
- **仅限桌面版**，Seer 启动时会在一分钟内发送一次网络请求以检查更新。
  - 如果未勾选“自动检查更新”选项，则不会发送该请求。

#### 显式连接

- 下载插件或进行类似操作时，连接由第三方软件（如默认浏览器）发起。

<br/>

## 版本说明

<img src="https://raw.githubusercontent.com/wiki/ccseer/Seer/res/2022-12-17-20-59-05.png" width="500">

- 带有 `U`：表示您正在使用来自 [Microsoft Store](https://apps.microsoft.com/store/detail/seer-pro/9PGVFJBVBZWX?hl=zh-cn&gl=cn) 的版本。
- 不带 `U`：表示这是从 [官网](http://1218.io) 下载的桌面版。
- 带有 `+`：表示 Seer 以管理员权限运行。
- 不带 `+`：表示 Seer 未以管理员权限运行。

<br/>

## 获取日志和崩溃文件

1. 打开文件资源管理器，按下 <kbd>Win + E</kbd>
2. 复制 `%TEMP%/Seer`，粘贴并按下回车键
   - <img src="https://raw.githubusercontent.com/wiki/ccseer/Seer/res/2022-12-17-20-54-33.png" width="350">
3. 如果一切正常，您会看到一个 `Seer.log` 文件；如果程序之前发生过崩溃，还会有一个 `dmp` 文件。
4. 打开 `关于` 窗口，最下方点击邮箱地址发送邮件。如果能提供详细的重现步骤就更好了~ 😊

<br/>

## 隐藏托盘图标后如何恢复
#### 方法 1
1. 预览任意文件
2. 点击预览窗口
3. 按快捷键： <kbd>Ctrl + ,</kbd>

#### 方法 2
1. 打开 任务管理器；
2. 找到 Seer 图标，点击 结束进程；
3. 等一会儿，大约是 250 毫秒后，再次运行程序；
4. 程序启动后的 8 秒内，图标是可见的，此时可进行设置操作。

- <img src="https://raw.githubusercontent.com/wiki/ccseer/Seer/res/2024-11-09-16-38-33.png" width="500">
