## 编写自定义脚本

### 准备脚本信息

在 Seer 中添加脚本时，程序会先读取变量 `SCRIPT_INFO`。

- 如果不存在 `SCRIPT_INFO`，则会尝试调用 `script_info()` 函数。
- 两者都不存在，或者返回值不是字典类型时，添加会失败。

### 必填字段

- `name`：脚本名称
- `type`：脚本类型
- `extensions`：匹配的后缀名列表
- `arguments`：命令行参数，不包含 `python.exe` 和 `py` 文件名本身

`type` 目前有三个值：

- `0`：预览
- `1`：控制栏
- `2`：属性列表

`extensions` 必须是列表类型。

- 当你需要匹配文件夹时，使用 `${type_folder}`。

示例：

```python
SCRIPT_INFO = {
    "name": "unzip",
    "type": 1,
    "extensions": ["zip", "rar", "7z"],
    "arguments": ["-e", "${7z}", "-i", "${input_file}", "-o", __save_path, "-w"],
    # optional below
    "author": "Corey",
    "version": "1.0.1",
    "description": "unzip archive file here",
    # Controls only
    "icon_path": "icon.png",
}
```

### 编写功能

#### 预览

转换类型脚本会先读取输入文件，再把结果转换为 Seer 内置支持的格式，例如 PDF、图片或 HTML。

- 例如 [epub](https://github.com/ccseer/Seer-Scripts/blob/main/preview/epub/) 脚本，就是把输入文件转换成 HTML 再交给 Seer 预览。

#### 控制栏

当预览加载成功后，Seer 会在控制栏左侧显示一个对应按钮。

- 点击按钮后，就会执行该脚本。
- 例如 [zipfolder](https://github.com/ccseer/Seer-Scripts/tree/main/controls/zipfolder) 会把当前预览的文件夹压缩成 zip，并保存到当前目录。

#### 属性列表

当预览成功后，Seer 会自动调用属性脚本。

- 脚本负责解析输入文件。
- 然后把用于显示的数据保存为指定位置的 json 文件。
- Seer 再读取这个 json 并显示到属性面板里。
- 例如 [sha512](https://github.com/ccseer/Seer-Scripts/tree/main/property/sha512) 用于计算 exe 和 dll 文件的 sha512 值。

### 变量说明

这些占位符会在运行前被替换成真实值，并作为参数传给脚本。

- `${7z}`：Seer 附带的 `7z.exe` 绝对路径

  `C:/Program Files (x86)/Seer/plugins/7z.exe`

- `${seer_exe}`：`Seer.exe` 的绝对路径

  `C:/Program Files (x86)/Seer/Seer.exe`

- `${seer_dir}`：`Seer.exe` 所在目录

  `C:/Program Files (x86)/Seer/`

- `${input_file}`：当前目标文件路径，可以是文件，也可以是文件夹

  `/file/to/the_preview_file`

- `${output_file}`：输出文件路径，一般是临时目录加随机文件名，且不带扩展名

  `/path/to/temp_folder/random_str`

  - 当脚本类型是 `Property` 时，这个值是必须的。
  - 当脚本类型是 `Preview`，且脚本要把未知格式转换成内置格式时，这个值也是必须的。

- `${no_cache}`：仅用于 `Preview`

  - 用来通知 Seer 在预览关闭后删除临时文件。
  - 这是给 Seer 的标记，不会作为命令行参数传给脚本。

- `${type_folder}`：仅用于 `Controls`

  - 由于文件夹没有后缀名，所以用它来匹配文件夹类型。

- `${use_backslash}`

  - 用反斜杠 `\` 代替正斜杠 `/`。
