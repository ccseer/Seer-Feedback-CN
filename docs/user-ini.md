### 修改方法

0. 在程序 `设置 - 高级设置` 中可找到自定义配置按钮，点击后即可打开文件，或在 `%USERPROFILE%\AppData\Local\Corey\Seer` 中找到该文件；
1. 退出 Seer 程序；
2. 打开后找到需要修改的字段，修改等号后面的数据并保存文本；
   - 若需要还原某一个数据，可删除该行，下次启动时会写入默认值
   - 若需要还原全部数据，清空 user.ini 内容即可，下次启动时程序会生成新的默认配置
3. 重新打开 Seer 后即可生效。

### 字段说明

##### [General]

- `tray_icon_style`: 系统托盘图标样式，default/dark/light/blue
- `use_trigger_key_close`: 当主预览窗口有焦点时，是否使用空格键隐藏窗口，true/false
- `temp_file_expire_days`: 如果当前时间减去临时文件的创建时间大于这个值，此临时文件将在程序退出时被删除
- `enable_esc_key`: 当主预览窗口可见时，是否使用 esc 键隐藏窗口，不论窗口是否有输入焦点，true/false
- `load_cloud_files`: 是否加载离线文件，设置为 true 后程序会尝试完整加载，导致云盘将文件下载到本地
<!-- -   `accept_injected_trigger` 此键用于决定 Seer 是否响应“注入”的键盘事件 —— 通常是由软件生成的模拟按键，而非物理键盘输入。true/false
    -   当设置为 true 时，Seer 会接受模拟（注入）的键盘消息作为有效触发器。这对于一些自动化工具或辅助功能程序（如虚拟键盘）可能非常有用。
    -   当设置为 false 时，只有真实的物理按键事件才会触发 Seer，这有助于防止被软件模拟输入意外激活。 -->

##### [Media]

- `decoders:` 视频解码方式，"MFT:d3d=11", D3D11, DXVA, CUDA, FFmpeg, dav1d
- `log`: 是否生成视频预览的解码日志文件，true/false
- `show_mute_button`: 控制栏是否显示静音按钮，true/false
- `show_time_indication`: 控制栏是否显示时间指示器，true/false
- `audio_remember_playback_pos`: 是否保存音频播放记录，true/false
- `video_remember_playback_pos`: 是否保存视频播放记录，true/false
- `audio_extra_support`: 同 [PDF - extra_support]
- `video_extra_support`: 同 [PDF - extra_support]
- `window_size` 用于单独设置特定模块的预览大小， _[0.01, 0.95]_
  - 默认值 `1`: auto-sizing
  - 实际结果会介于 **程序硬编码的最小窗口大小** 和 **设置-高级-最大预览大小** 之间
  - 比如对于文本模块，程序默认会基于字体大小和实际预览内容返回一个大小。假如 [Text] 组的这个值设置为了 0.9，程序将不再基于内容动态计算，而是每次返回同一个值： 0.9 \* 屏幕大小。
- `exclude`: 用于排除内置文件类型的预览
  - 大小写不敏感，多个后缀名用逗号分隔：`extra_support = xps, eps`
  - 设置成功后，在 **设置 > 类型** 中不显示该后缀名，并且在预览时不会加载该类型的文件

##### [PDF]

- `fit_width_at_first`: 是否默认显示页宽，true/false
- `show_outline_button`:  控制栏是否显示大纲按钮，true/false
- `show_sidebar_left`:  是否将侧边栏放到左边
- `window_size`： 同 [Media - window_size]
- `exclude`: 同 [Media - exclude]
- `extra_support`: 额外的后缀名支持
  - 当确定文件可以被 PDF 模块预览但不在默认支持格式列表中时，添加到此处可告知 Seer 进行尝试。
  - 大小写不敏感，多个后缀名用逗号分隔：`extra_support = xps, eps`
  - 若和其他预览器的后缀名重复，Seer 会根据 **设置 > 类型** 中的预览器排列顺序进行加载
  - 设置成功后，在 **设置 > 类型** 中会显示该后缀名

##### [Text]

- `view_threshold`: 文件大小阈值，小于这个值的文本会有语法高亮和换行等功能，大于这个值得会使用纯文本显示以保证流畅性和稳定性
- `line_threshold`: 单行最大字数，当单行字数过大时，界面会有明显卡顿
- `minimap_scale`: 缩略图内容缩放系数，范围为 [0.5, 2.0]，默认为 1.0
- `custom_font`: 自定义字体 family name，需要该字体已安装到本机
- `window_size`： 同 [Media - window_size]
- `extra_support`: 同 [PDF - extra_support]
- `exclude`: 同 [Media - exclude]
- `custom_theme` 设置文本代码高亮主题
  - 默认情况, Seer 基于当前软件颜色使用 `"GitHub Dark"` 或者 `"GitHub Light"`。
  - "Atom One Dark", "Atom One Light", "Breeze Dark", "Breeze Light", "Catppuccin Frappé", "Catppuccin Latte", "Catppuccin Macchiato", "Catppuccin Mocha", "Dracula", "Falcon", "GitHub Dark", "GitHub Light", "Homunculus", "Monokai", "Nord", "Oblivion", "Printing", "Radical", "Solarized Dark", "Solarized Light", "Tokyo Night", "Tokyo Night Light", "Tokyo Night Storm", "VSCodium Dark", "Vim Dark", "ayu Dark", "ayu Light", "ayu Mirage", "gruvbox Dark", "gruvbox Light"
  - 主题预览： https://github.com/ccseer/Seer/issues/460

##### [Image]

- `max_read_size`: 文件大小阈值，当文件大小大于此值，程序仅加载预览大小（当前可显示的宽和高），不会加载完整的图片大小
- `use_internal_exif_reader`：用于读取 jpg 的元数据，当脚本模块安装 exif 后，功能会重复，可将此字段设置为 false 关闭内置 exif 功能
- `accelerate`: 是否开启硬件加速渲染
- `minimap_scale`: 缩略图内容缩放系数，范围为 [0.5, 2.0]，默认为 1.0
- `window_size`： 同 [Media - window_size]
- `raw_extra_support`: 同 [PDF - extra_support]
- `exclude`: 同 [Media - exclude]

##### [WebView]

- `markdown_use_heti`: 用于渲染 markdown，中文用户专属，没有指定自定义 css 时默认使用 [heti](https://github.com/sivan/heti)，true/false
- `window_size`： 同 [Media - window_size]
- `extra_support`: 同 [PDF - extra_support]
- `exclude`: 同 [Media - exclude]

##### [Folder]

- `window_size`： 同 [Media - window_size]
- `extra_support`: 同 [PDF - extra_support]
- `exclude`: 同 [Media - exclude]
