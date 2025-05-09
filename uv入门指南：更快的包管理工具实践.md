# UV是什么？

UV是一款由 Rust 编写的现代化 Python 包管理工具，凭借其惊人的性能和直观的用户体验迅速崭露头角。作为传统 pip 的强力替代品，UV 不仅提供了极速的依赖解析能力，还带来了更智能的包管理体验和全方位的项目环境控制。

# UV的核心优势

- 极速安装：相比传统工具，依赖解析和包安装速度提升 10-100倍
- 一站式解决方案：一个工具替代 pip、pip-tools、pipx、poetry、pyenv、virtualenv 等多种工具
- 智能依赖管理：自动处理复杂依赖关系，有效避免版本冲突
- 虚拟环境集成：无缝创建和管理项目虚拟环境
- 通用锁文件支持：通过 uv.lock 确保环境一致性
- 全面的 Python 版本管理：轻松安装和切换不同 Python 版本
- 空间高效：全局缓存机制实现依赖项去重，节省磁盘空间
- 跨平台支持：完美支持 macOS、Linux 和 Windows

# 安装指南

**Windows系统**

```shell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

**MacOS 和 Linux 系统**

```shell
curl -LsSf https://astral.sh/uv/install.sh | sh
```

安装成功后，您将看到类似以下的输出：

```shell
PS D:\python\learn\uv_learn> powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
Downloading uv 0.6.16 (x86_64-pc-windows-msvc)
Installing to C:\Users\chenw\.local\bin
  uv.exe
  uvx.exe
everything's installed!

To add C:\Users\chenw\.local\bin to your PATH, either restart your shell or run:

    set Path=C:\Users\chenw\.local\bin;%Path%   (cmd)
    $env:Path = "C:\Users\chenw\.local\bin;$env:Path"   (powershell)
```

💡 **提示：** 按照提示将 UV 添加到系统环境变量，然后重启终端或电脑使其生效。

# UV实战指南

1. **Python版本管理**

```shell
uv python list
```

这个命令会列出所有支持的 Python 版本以及您本地已安装的版本。

2. **查找特定版本的Python**

```shell
uv python find 3.13
```

3. **安装新的Python版本**

```shell
uv python install 3.13
```

4. **项目初始化**

```shell
uv init 项目名称
```

*项目名称可选，不指定时使用当前文件夹名称。*

- 初始化后，UV 会自动创建项目配置文件，并识别系统中的 Python 版本：

![[项目初始化示例.png]]

# 包管理操作

1. **添加依赖包**

```shell
uv add langchain
```

执行此命令后，UV 会自动：
- 创建虚拟环境（.venv）
- 更新锁文件（uv.lock）
- 修改项目配置（pyproject.toml）

*⚠️ 注意：在 Trae/vscode 编辑器中使用时，建议先关闭 pyproject.toml 文件再安装第三方库，避免潜在冲突。*

![[包安装示例.png]]

2. **查看依赖树**

```shell
uv tree
```

输出示例:

```shell
PS D:\python\learn\uv_learn> uv tree
Resolved 7 packages in 0.84ms
uv-learn v0.1.0
├── numpy v2.2.5
└── pandas v2.2.3
    ├── numpy v2.2.5
    ├── python-dateutil v2.9.0.post0
    │   └── six v1.17.0
    ├── pytz v2025.2
    └── tzdata v2025.2
```

3. **移除依赖包**

```shell
uv remove langchain
```

此命令会自动更新所有相关文件，包括虚拟环境、锁文件和项目配置。

4. **同步项目环境**

```shell
uv sync
```

根据 pyproject.toml、.python-version 等配置文件更新虚拟环境，确保环境与配置一致。

# 脚本运行与工具集成

1. **内联依赖的脚本运行**

UV 支持在单文件脚本中声明依赖并运行：

```shell
# 创建一个简单的脚本并添加依赖
echo 'import requests; print(requests.get("https://astral.sh"))' > example.py

# 为脚本添加依赖
uv add --script example.py requests

# 在隔离环境中运行脚本
uv run example.py
```

2. **代码质量工具集成**

UV 提供了与常用开发工具的无缝集成：

**代码格式检查（Flake8）**

```shell
uv tool install flake8
uvx flake8  # 或使用 uv tool run flake8
```

**代码质量检查（Ruff）**

```shell
uv tool install ruff
uv tool run ruff check
```

*💡 小贴士：虽然现代 IDE 已经集成了类似功能，但 UV 的工具集成在 CI/CD 流程或团队协作中仍然非常有价值。*

3. **查询已安装的工具**

```shell
uv tool list
```

4. **项目打包与发布**

在 pyproject.toml 中添加脚本入口点：

```toml
[project.scripts]
simpleai = "main:main"
```

其中 simpleai = "main:main"，等号前是脚本名称，后面分别是脚本和函数名。

5. **打包项目**

```shell
uv build
```

这将项目打包为 whl 和 tar.gz 文件，whl 文件可发布为第三方库。

![[打包结果.png]]

6. **将本地 whl 作为工具安装**

```shell
uv tool install dist\uv_learn-0.1.1-py3-none-any.whl
```

安装后可直接使用 simpleai 命令：

![[工具安装后使用.png]]