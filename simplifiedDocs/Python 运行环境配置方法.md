# Python 运行环境配置方法

该教程用于配置最基本的Python脚本运行环境，适用于Windows和macOS。在执行本教程中的命令时，除非特别说明需要"关闭当前窗口并新开一个窗口再运行下一条命令"，否则你可以直接在同一个窗口中继续执行后续命令。当然，如果你选择为每条命令都开启新窗口也不会造成问题，只是没有这个必要。

## Windows
1. 安装 Chocolatey
	1. 右键点击开始菜单，选择"终端管理员"。
	2. 运行以下命令安装 Chocolatey：
    ```powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
    ```
	3. 等待安装完成，你会看到提示信息说明安装已完成。
	4. 关闭窗口，再次右键点击开始菜单，选择"终端管理员"，然后输入`choco`或`choco -?`验证安装是否成功。

2. 安装 Python
	1. 继续运行以下命令安装 Python 3.11：
	```powershell
	choco install python --version=3.11
	```
	2. 当遇到下面提示时，输入`A`然后按 Enter 即可继续：
	```
	Do you want to run the script?([Y]es/[A]ll - yes to all/[N]o/[P]rint): 
	```
	3. 关闭窗口，再次右键点击开始菜单，选择"终端管理员"，然后输入`python --version`来验证安装是否成功。
	4. 运行以下命令以
	```powershell
	pip config set global.index-url https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple
	```
## macOS
1. 打开“终端”app，然后输入以下命令以安装 Homebrew：
	```bash
	/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
	````
	1. 如果弹出 Xcode CLI Tools 安装页面，要在安装完成后再次运行这个命令。可能会显示需要一天多才能完成安装，别担心，实际上大概五分钟就行
	2. 注意看运行过程中弹出的其他中文说明
2. 等待安装完成后，按下 Command + N 打开一个新的窗口，输入以下命令，如果没有`command not found`的报错，那么说明安装成功：
	```bash
	brew --version
	````
3. 然后继续安装 Python 3.11：
	```bash
	brew install python@3.11
	````
4. 等待安装完成后，按下 Command + N 打开一个新的窗口，输入以下命令，如果没有`command not found`的报错，那么说明安装成功：
	```bash
	python --version
	```
5. 配置环境变量：
	```bash
	echo 'export PATH="/opt/homebrew/opt/python@3.11/bin:$PATH"' >> ~/.zshrc
	source ~/.zshrc
	````
6. 配置 pip 镜像源：
	```bash
	pip config set global.index-url https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple
	```