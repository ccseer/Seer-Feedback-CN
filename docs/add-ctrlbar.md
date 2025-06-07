## 添加方法

<img src="https://raw.githubusercontent.com/wiki/ccseer/Seer/res/2022-12-17-18-08-09.png" width="500">

首先，这个是控制栏。

一般来说，左侧是文件级别的控制按钮，比如使用默认程序打开文件，定位文件路径到资源管理器等。这些按钮全部可在设置里进行隐藏。

右侧是预览级别的，主要用于控制显示内容，比如旋转、静音、还原大小等等。

控制栏启动程序属于左派。

<br/>

1. 打开设置窗口，输入一个后缀名；
   - <img src="https://raw.githubusercontent.com/wiki/ccseer/Seer/res/2022-12-17-18-11-00.png" width="500">
2. 点击右侧的 `+` 按钮，选择可以打开这个文件的执行程序路径；
3. 点确定。 此时预览该后缀名的文件，控制栏就多了一个按钮。很神奇。
   - <img src="https://raw.githubusercontent.com/wiki/ccseer/Seer/res/2022-12-17-18-11-58.png" width="500">

<br/>

## 注意事项

在进行自定义操作前，请确保您了解自己正在做什么，以及此功能的具体用途。

下面是第二个示例：

1. 输入扩展名：`zip`
   - <img src="https://raw.githubusercontent.com/wiki/ccseer/Seer/res/2022-12-17-18-13-10.png" width="350">
2. 点击旁边的 `+` 按钮，选择执行文件的路径。
   - <img src="https://raw.githubusercontent.com/wiki/ccseer/Seer/res/2022-12-17-18-13-34.png" width="500">
3. 点击 `+` 按钮旁的编辑按钮，修改调用参数。
   - <img src="https://raw.githubusercontent.com/wiki/ccseer/Seer/res/2022-12-17-18-14-01.png" width="500">
4. 在本示例中，程序将调用 `7z.exe`，并使用文件的完整路径替换占位符，后面跟随其他参数。示例参数为：`x "${input_file}" -r -y -o"C:\Users\corey\Downloads\"`
   - **_复制上述参数时，请记得修改路径中的用户名，因为您的用户名不是 Corey_**。
   - `x`：解压缩命令。
   - `"${input_file}"`：文件路径占位符。
   - `-r`：递归选项，确保文件夹内的子文件也被解压缩。
   - `-y`：自动默认确认所有询问，避免提示覆盖。
   - `-o`：指定输出路径。
   - `"C:\Users\corey\Downloads\"`：解压后的保存路径。
5. 点击 `确定`。
6. 点击控制栏中的刷新按钮，程序将调用 `7z.exe` 解压 zip 文件至刚刚填写的路径，即 `C:\Users\corey\Downloads\`。Amazing~
   - <img src="https://raw.githubusercontent.com/wiki/ccseer/Seer/res/2022-12-17-18-17-45.png" width="500">
