# UV是什么？

UV是一款由 Rust 编写的现代化 Python 包管理工具，凭借其惊人的性能和直观的用户体验迅速崭露头角。作为传统 pip 的强力替代品，UV 不仅提供了极速的依赖解析能力，还带来了更智能的包管理体验和全方位的项目环境控制。

## UV的核心优势

- 极速安装：相比传统工具，依赖解析和包安装速度提升 10-100倍
- 一站式解决方案：一个工具替代 pip、pip-tools、pipx、poetry、pyenv、virtualenv 等多种工具
- 智能依赖管理：自动处理复杂依赖关系，有效避免版本冲突
- 虚拟环境集成：无缝创建和管理项目虚拟环境
- 通用锁文件支持：通过 uv.lock 确保环境一致性
- 全面的 Python 版本管理：轻松安装和切换不同 Python 版本
- 空间高效：全局缓存机制实现依赖项去重，节省磁盘空间
- 跨平台支持：完美支持 macOS、Linux 和 Windows

## 安装指南

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

