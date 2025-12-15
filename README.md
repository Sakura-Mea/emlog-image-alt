**图片Alt属性自动添加插件（emlog-image-alt）**是由苏酷伊（sukuy.com）为Emlog博客系统设计开发的SEO优化工具，支持提取全站所有缺失alt属性的文章和图片，支持自动为文章图片添加alt/title属性，支持批量自定义处理和按文章标题自动生成博客文章中的图片添加alt和title属性，提升网站的SEO效果和可访问性。

## Gitee国内加速镜像仓库： [https://gitee.com/Munsea/emlog-image-alt](https://gitee.com/Munsea/emlog-image-alt)

## 功能特性

### 1. 自动添加功能
- **文章保存时自动处理**：当发布或更新文章时，自动为缺少alt属性的图片添加描述
- **智能内容生成**：
  - 优先从图片文件名提取描述（移除文件扩展名，将下划线/连字符转换为空格）
  - 当文件名无法提供有效描述时，使用文章标题加序号（如："文章标题 - 图1"）
  - 同时设置alt和title属性，确保完全一致
- **智能保留**：已有的alt属性不会被修改，只处理空白或缺失的属性

### 2. 统计分析功能
- **全面统计**：分析网站所有文章中图片的alt属性使用情况
- **详细数据**：
  - 文章总图片数
  - 缺少alt属性的图片数
  - 含有缺失alt属性图片的文章数
  - 缺失比例百分比
- **实时更新**：点击统计按钮即可获取最新数据

### 3. 批量处理功能
- **一键修复**：为网站所有文章中缺少alt属性的图片自动添加描述
- **安全可靠**：只修改缺失或空白的alt属性，保留已有内容
- **进度可视化**：批量处理过程中显示进度条和状态信息
- **结果反馈**：处理完成后显示详细的处理结果统计

### 4. 自定义编辑功能
- **可视化列表**：查看所有缺少alt属性的图片列表，包括预览、来源文章和URL
- **分页浏览**：支持分页查看大量图片，每页默认20张
- **自定义输入**：为每张图片手动输入自定义的alt属性
- **批量保存**：一次性保存所有自定义的alt属性到对应文章
- **图片预览**：查看图片缩略图，方便准确描述

## 插件下载

**夸克网盘下载：**
- **[https://pan.quark.cn/s/7878a1c1cde6](https://pan.quark.cn/s/7878a1c1cde6 "https://pan.quark.cn/s/7878a1c1cde6")**

## 安装方法

### 方法一：通过Emlog插件页面安装
1. 登录Emlog后台管理界面
2. 进入"插件" -> "安装插件"
3. 上传"image_alt"插件压缩包
4. 启用插件

### 方法二：手动安装
1. 下载插件压缩包
2. 解压后将“image-alt”文件夹上传到Emlog的`content/plugins/`目录
3. 登录Emlog后台管理界面
4. 进入"插件" -> "已安装插件"
5. 找到"图片Alt属性自动添加"插件，点击"激活"

## 插件演示
![Emlog图片自动添加alt属性插件展示图](https://www.sukuy.com/images/202512/image-alt-1-20251215.webp "Emlog图片自动添加alt属性插件展示图")

![自定义单篇文章添加alt属性展示图](https://www.sukuy.com/images/202512/image-alt-3-20251215.webp "自定义单篇文章添加alt属性展示图")

## 使用指南

### 1. 自动添加功能使用

该功能无需手动操作，插件会自动在以下时机工作：
- 发布新文章时
- 更新已有文章时

**注意**：
- 只有博客文章类型（`type='blog'`）会被处理
- 已有的alt属性不会被覆盖
- 图片必须是直接嵌入在文章内容中的`<img>`标签

### 2. 统计分析功能使用

1. 登录Emlog后台管理界面
2. 进入"插件" -> "图片Alt属性自动添加"
3. 在插件设置页面，点击"开始统计图片"按钮
4. 等待统计完成，查看结果

### 3. 批量处理功能使用

**警告**：批量处理将修改网站所有文章的内容，请在执行前做好数据库备份！

1. 登录Emlog后台管理界面
2. 进入"插件" -> "图片Alt属性自动添加"
3. 在插件设置页面，点击"执行批量处理"按钮
4. 阅读警告信息，确认了解风险
5. 点击"确认执行"按钮开始批量处理
6. 等待处理完成，查看处理结果

### 4. 自定义编辑功能使用

1. 登录Emlog后台管理界面
2. 进入"插件" -> "图片Alt属性自动添加"
3. 点击"查看并编辑Alt属性"按钮
4. 在弹出的模态框中，浏览缺少alt属性的图片
5. 为需要自定义的图片输入alt属性
6. 点击"保存所有修改"按钮保存更改

**技巧**：
- 使用分页导航浏览大量图片
- 点击图片URL旁边的文章链接，可以直接编辑来源文章
- 图片预览功能帮助您更准确地描述图片内容

## 技术实现细节

### 1. 核心处理流程

```
文章内容 → HTML解析(DOMDocument) → 图片标签提取 → alt属性检查 → 智能生成 → 更新内容
```

### 2. 主要功能函数

| 函数名 | 功能描述 |
|--------|----------|
| `image_alt_init()` | 插件初始化，注册钩子 |
| `image_alt_auto_add()` | 自动为图片添加alt属性的核心函数 |
| `image_alt_count_missing()` | 统计缺少alt属性的图片 |
| `image_alt_batch_process()` | 批量处理所有文章图片 |
| `image_alt_get_missing_images()` | 获取缺少alt属性的图片列表 |
| `image_alt_save_custom_alt()` | 保存自定义的alt属性 |

### 3. 技术特点

- **DOMDocument处理**：使用PHP的DOMDocument类解析和修改HTML，确保HTML结构的完整性
- **UTF-8编码支持**：全面支持中文和其他非ASCII字符
- **安全处理**：
  - 对用户输入进行严格过滤
  - 使用参数化查询防止SQL注入
  - 保留原有HTML结构和属性
- **性能优化**：
  - 仅处理可见的已发布文章
  - 分页加载大量图片数据
  - 批量操作时的进度可视化

### 4. 钩子机制

插件通过Emlog的钩子机制实现自动化功能：
```php
// 挂载到文章保存前的钩子
addAction('pre_save_log', 'image_alt_auto_add');
```

## 常见问题解答

### Q: 插件会修改我已经添加的alt属性吗？
A: 不会。插件只会为没有alt属性或alt属性为空的图片添加描述，已有的alt属性会被完整保留。

### Q: 插件支持哪些类型的文章？
A: 目前插件仅支持博客文章类型（`type='blog'`），不包括页面（`type='page'`）。

### Q: 批量处理会影响网站性能吗？
A: 批量处理过程中会占用一定的服务器资源，建议在网站访问量较低的时候执行。对于大型网站，可能需要较长时间完成处理。

### Q: 我可以为图片添加自定义的alt属性吗？
A: 可以。插件提供了自定义编辑功能，您可以为每张图片手动输入个性化的alt属性。

### Q: 插件生成的alt属性遵循什么格式？
A: 插件使用以下格式生成alt属性：
- 如果图片文件名包含有效描述：`文章标题 - 图片描述（从文件名提取）`
- 如果文件名无法提供有效描述：
  - 单张图片：`文章标题`
  - 多张图片：`文章标题 - 图X`（X为图片序号）

### Q: 如何更新插件？
A: 目前通过**苏酷伊官网手动更新**，更新地址👉：[https://www.sukuy.com/image-alt](https://www.sukuy.com/image-alt "https://www.sukuy.com/image-alt")

## 更新日志

### 版本 1.0.1（2025-12-15）
- 添加缺失alt属性文章数量统计

### 版本 1.0 (2025-12-01)
- 初始版本发布
- 实现自动添加alt/title属性功能
- 添加统计分析功能
- 支持批量处理和自定义编辑
- 优化用户界面和交互体验

## 作者信息

- **作者**：苏酷伊
- **官方网站**：https://www.sukuy.com
- **插件更新**：[https://www.sukuy.com/image-alt](https://www.sukuy.com/image-alt "https://www.sukuy.com/image-alt")
- **Github**：[https://github.com/Sakura-Mea](https://github.com/Sakura-Mea "https://github.com/Sakura-Mea")
- **Gitee**：[https://gitee.com/Munsea](https://gitee.com/Munsea "https://gitee.com/Munsea")
- **联系邮箱**：sakura@sukuy.com

## 交流社群
- **QQ交流群**：884250547

## 开源许可证

本插件采用MIT许可证发布。

```
MIT License

Copyright (c) 2025 苏酷伊

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
