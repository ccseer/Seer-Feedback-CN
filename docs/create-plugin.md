## 转换类型

这是目前大部分插件的运行方式。简单来说就是插件程序接收两个参数，把输入文件解析后以内置格式的形式保存。

1. 假设你需要预览一个安卓安装包文件，但  Seer 还不支持。在添加  ApkMetaInfo2Json 插件后对 weixin.apk 文件进行预览
2. Seer 响应时会先根据设置里的插件配置对文件后缀名进行匹配，找到  apk 后，运行对应的插件程序 ApkMetaInfo2Json.exe ，并对命令行的参数进行替换
   - `${input_file}` 会被替换为 weixin.apk 的完整路径
   - `${output_file}`  为 Seer 的临时目录加上指定文件名，通常临时目录为 **%TEMP%/Seer**，指定文件名为触发文件的 md5 值（不含后缀名）
   - 对于 ApkMetaInfo2Json 插件来说，最后的运行命令为  `"/path/to/ApkMetaInfo2Json.exe" "/path/to/weixin.apk" "%TEMP%/Seer/__md5value__.json"`
3. 在 ApkMetaInfo2Json 程序运行完成退出后，Seer 会去寻找  `${output_file}` 文件，然后对其进行加载显示。

<br/>

- 插件可为任何可执行文件
  - CMD 脚本：https://github.com/ccseer/Seer-plugins/tree/master/cmd_rename
  - BAT 脚本：https://github.com/ccseer/Seer-plugins/tree/master/bat_epub
  - 任何提供转换功能的第三方程序
    - dll_lib_exports： 这是从 Windows 系统的不知名角落找到的
    - ImageMagick：https://imagemagick.org/index.php
    - exiftool： https://exiftool.org/
  - 自定义程序
    - Torrent2Json：https://github.com/ccseer/Seer-plugins/tree/master/Qt_Torrent2Json
    - ApkMetaInfo2Json： https://github.com/ccseer/Seer-plugins/tree/master/Qt_ApkMetaInfo2Json
- 通常转换类型的插件都会生成一个临时文件，也就是转换后的文件
  - Seer 会自动删除超过 20 天的临时文件
  - 在命令行里添加  `${no_cache}` 会让 Seer 在预览结束时删掉临时文件
    - 优点是没有硬盘占用
    - 缺点是遇到了同样的文件，每次都需要调用插件进行转换
    - 此参数是通知  Seer 的，不会当成命令行参数传给插件。适用于那些文件内容会频繁被修改的文件类型。

## DLL 类型

通过 Qt/C++ 编写插件编译成动态库。

- 运行效率上有优势，it's cpp
- 发布时由于共享主程序的运行环境，所以分发插件时依赖更少，包更小

### Reference Projects

You can refer to the following example plugins:

- [F3DViewer](https://github.com/ccseer/f3dviewer) - 3D file viewer plugin
- [OfficeViewer](https://github.com/ccseer/OfficeViewer) - Office document viewer plugin
- [FontViewer](https://github.com/ccseer/FontViewer) - Font preview plugin
- [JsonTreeViewer](https://github.com/ccseer/JsonTreeViewer) - JSON structure viewer plugin
