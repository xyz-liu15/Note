## 安装



![[Miniconda_1.png]]

![[Miniconda_2.png]]

![[Miniconda_3.png]]


![[Miniconda_4.png]]

![[Miniconda_5.png]]

出现以下弹窗直接关闭即可。
![[proceed.png]]![[Miniconda_6.png]]
## 配置Miniconda

首先，打开Anaconda PowerShell Prompt或者Anaconda Prompt。依次运行以下代码以配置清华镜像源：
```shell
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
conda config --set show_channel_urls yes
```

### 解释：
- `conda config`：conda 的配置管理命令
- `--add channels`：添加一个新的软件源(channel)
- `https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/`：清华大学提供的 conda-forge 镜像源地址
### 作用：
将清华大学的 conda-forge 镜像源添加到你的 conda 配置中，这样当你安装或更新软件包时，conda 会从这个国内的镜像源下载，速度会比从国际源下载快很多。

### 解释：

- `--set`：设置一个配置选项
- `show_channel_urls`：控制是否显示软件包来源的URL
- `yes`：启用此选项

### 作用：

当这个选项设置为 yes 后：

1. 在执行 `conda install` 或类似命令时，会显示每个软件包是从哪个具体的软件源URL下载的
2. 在创建新环境或安装软件包时，输出信息会更详细，方便你确认软件包来源
3. 有助于调试软件源配置问题

验证配置：

```shell
conda config --show channels
conda config --show custom_channels
```

### 解释：

- `conda config`：conda 的配置管理命令
- `--show`：显示配置信息
- `channels`：指定要查看的配置项名称

### 作用：

显示当前 conda 配置中 `channels` 的值，即 conda 搜索和安装软件包时使用的软件源列表及其优先级顺序。

### 解释：

- `custom_channels`：查看自定义命名的软件源配置

### 作用：

显示所有自定义命名的 channel 及其对应的 URL 映射关系。

![[images/channels.png]]

创建虚拟环境：

```shell
conda create --name python_dev python=3.12.7
```

## 命令结构解析

- `conda create`：创建新环境的基础命令
- `--name python_dev`：指定新环境的名称为 "python_dev"
- `python=3.12.7`：指定要安装的 Python 版本为 3.12.7

![[conda_activate.png]]

激活虚拟环境：

```shell
conda activate python_dev
```

安装所需模块：

```shell
conda install jupyterlab pyecharts pandas numpy matplotlib
```

## 命令结构解析

- `conda install`：conda 包安装命令
- `jupyterlab pyecharts pandas numpy matplotlib`：要安装的包列表（多个包用空格分隔）

安装成功后，运行**jupyter lab**命令，创建python_dev文件夹以及一个data_analyse.ipynb文件。
![[data_analyse.png]]
