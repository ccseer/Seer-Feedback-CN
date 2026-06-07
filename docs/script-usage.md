- 此模块主要为了在扩展 预览/控制栏/属性列表 时更加方便容易
- 程序使用了  Python-3.8.10-embed-win32 作为解释器
  - 如果你的电脑上已安装 python 并且你知道自己在做什么，可在设置中添加自己的版本

## 使用方法

### 安装解释器

1. 进入 `设置 - 脚本` 界面，设置脚本解释器的 exe 路径。
2. 如果你已经安装了 Python，并且知道自己在做什么，可以直接选择自己的 `python.exe`。
   - 但官方发布的脚本默认只会以 `Python-3.8.10-embed-win32` 为测试基准。
3. 如果你不想自己折腾环境，直接点击 `下载` 按钮，程序会使用默认浏览器下载解释器压缩包。
4. 解压到一个你之后不会移动或删除的位置，再回到 Seer 中定位 `python.exe`。
   - 添加成功后再移动该文件夹会导致脚本功能失效。
   - 解释器存放路径尽量不要包含中文字符。

### 安装脚本

1. 打开 [Seer-Scripts](https://github.com/ccseer/Seer-Scripts/blob/main/README.md) 仓库，找到你需要的脚本。
2. 下载脚本并解压到本地。
3. 回到 Seer `设置 - 脚本`，点击 `从本地添加脚本`。
4. 选择脚本后确认，即可开始使用。

### 下载地址

- [下载解释器](http://1218.io/seer/python-3.8.10-embed-win32.zip)
- [下载脚本](https://github.com/ccseer/Seer-Scripts/blob/main/README.md)

## 示例

### 控制栏脚本

#### [unzip](https://github.com/ccseer/Seer-Scripts/blob/main/controls/unzip/)

- 控制栏会显示一个脚本按钮。
- 点击按钮后，Seer 会按脚本定义执行对应命令。
- 鼠标悬停在按钮上时，可以看到将要执行的具体命令。

    <img src="https://raw.githubusercontent.com/wiki/ccseer/Seer/res/2022-12-25-18-48-48.png" width="500">

### 属性脚本

#### [sha512](https://github.com/ccseer/Seer-Scripts/blob/main/property/sha512/)

- 脚本会自动计算当前预览文件的 SHA512 值。

    <img src="https://raw.githubusercontent.com/wiki/ccseer/Seer/res/2022-12-25-18-53-01.png" width="500">

<!-- - ipynb - 预览 - OIT

    <img src="https://raw.githubusercontent.com/wiki/ccseer/Seer/res/2022-12-28-15-06-41.png" width="500">

- epub - 预览 - 转换

    <img src="https://raw.githubusercontent.com/wiki/ccseer/Seer/res/2022-12-28-21-38-33.png" width="500"> -->

​
