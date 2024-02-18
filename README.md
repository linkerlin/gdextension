# gdextension

GDExtension模板，可以自动构建成一个独立的插件，用于Godot资产库。

### 入门指南：
1. 克隆此存储库（或使用此模板创建一个新存储库）并包含子模块。
   - `git clone --recurse-submodules https://github.com/nathanfranke/gdextension.git`
   - `cd gdextension`
2. 更新到最新的`godot-cpp`。
   - `git submodule update --remote`
2. 为当前平台构建调试版本二进制文件。
   - `scons`
3. 使用Godot Engine 4+导入、编辑和播放`project/`中的内容。
   - `godot --path project/`
4. 检查输出：
   ```
   Hello GDScript!
   Hello GDExtension Node!
   Hello GDExtension Singleton!
   ```

### 存储库结构：
- `project/` - Godot项目的样板代码。
  - `addons/example/` - 要分发到其他项目的文件¹。
  - `demo/` - 用于内部测试的场景和脚本，不是必需的。
- `src/` - 此扩展的源代码。
- `godot-cpp/` - GDExtension编译所需的子模块。

¹ 在将其作为插件分发之前，必须构建并将所有平台的二进制文件复制到`bin/`目录中。GitHub Actions会自动完成此操作。

### 自定义扩展：
1. 重命名 `project/addons/example/` 和 `project/addons/example/example.gdextension`。
2. 替换 `LICENSE`、`README.md` 和 `src/` 中的代码。
3. 不是必需的，但如果您觉得有帮助的话，考虑留下一条关于此模板的说明！

### 使用GitHub Actions在Godot资产库上分发您的扩展：
1. 转到 Repository→Actions 并下载最新的 artifact。
2. 通过将插件解压到项目中来测试 artifact。
3. 在GitHub上创建一个新的发布版本，并将 artifact 作为附件上传。
4. 在附件上，右键单击→复制链接以获取直接的文件URL。不要直接使用来自GitHub Actions的 artifact，因为它们会过期。
5. 在提交/更新Godot资产库时，将 "Repository host" 更改为 `Custom`，将 "Download URL" 更改为您复制的链接。
