# Blender Add-on Development Framework and Packaging Tool

This project provides a basic framework for developing Blender add-ons and a packaging tool. The main features include:

1. A single command to create a template add-on, facilitating quick development.
2. Integration with an IDE, allowing you to run and test your add-on in Blender with a single command.
3. A single command to package the add-on into an installable package, making it easier for users to install. The
   packaging tool automatically detects and includes any dependencies required by the add-on.
4. A framework supporting simultaneous development of multiple add-ons, enabling code reuse across different add-ons.
5. Handy development tools, like an auto-load utility for automatic class loading and an internationalization (i18n)
   tool, to assist even new developers in creating high-quality add-ons.

Install the following external library to use this project in an IDE:
https://github.com/nutti/fake-bpy-module

## Basic Framework

- [main.py](main.py): Configures the Blender path, add-on installation path, default add-on, package ignore files, and
  add-on release path, among other settings.
- [test.py](test.py): A testing tool to run and test add-ons.
- [create.py](create.py): A tool to create add-ons, allowing you to quickly create an add-on based on the `sample_addon`
  template.
- [release.py](release.py): A packaging tool that packages add-ons into an installable package.
- [addons](addons): A directory to store add-ons, with each add-on in its own sub-directory. Use `create.py` to quickly
  create a new add-on.
- [common](common): A directory to store shared utilities.

## Framework Development Guidelines

Each add-on, while adhering to the basic structure of a Blender add-on, should include a `config.py` file to configure
the add-on's package name, ensuring it doesn't conflict with other add-ons.
When importing dependencies, always use the full package name, such
as `from addons.sample_addon.config import __addon_name__`.
Avoid relative imports, such as `from .config import __addon_name__`.

## Usage

1. Clone this repository.
2. Open this project in your IDE. Optional: Configure the IDE to use the same python interpreter as Blender.
3. Install necessary requirements:
   ```bash
   pip install -r requirements.txt
   ```
4. Configure the Blender executable path (BLENDER_EXE_PATH) and addon path (BLENDER_ADDON_PATH) in [main.py](main.py).
5. Configure the name of the addon you want to create (ACTIVE_ADDON) in [main.py](main.py).
6. Run create.py to create a new addon in your IDE
7. Develop your addon in the newly created addon directory.
8. Run test.py to test your addon in Blender.
9. Run release.py to package your addon into an installable package. The packaged addon path will appears in the
   terminal when packaged successfully.

# Blender 插件开发框架及打包工具

本项目是一个基础的Blender插件开发框架和打包工具. 主要功能包括：

1. 一条命令创建一个模版插件插件，方便进行快速开发
2. 与IDE集成，在IDE中可以通过一条命令在Blender上运行插件的测试
3. 一条命令将插件打包成一个安装包，方便用户安装，打包工具自动检测插件的依赖关系，自动打包插件所需的依赖文件
4. 提供了一个支持多个插件同时开发的框架，方便插件开发者进行跨插件的功能复用
5. 提供了常用的插件开发工具，比如自动加载类的auto_load工具，提供国际化翻译的i18n工具，方便新手开发者进行高水平插件开发

请安装以下外部库以便在IDE中使用本项目：
https://github.com/nutti/fake-bpy-module

## 基础框架

[main.py](main.py): 可以配置Blender路径，插件安装路径，当前默认插件，打包ignore文件，插件发布路径等

[test.py](test.py): 测试工具，可以运行插件的测试

[create.py](create.py): 创建插件的工具，可以根据sample_addon模版快速创建一个插件

[release.py](release.py): 打包工具，可以将插件打包成一个安装包

[addons](addons): 存放插件的目录，每个插件一个目录，使用create.py可以快速创建一个插件

[common](common): 存放公共工具的目录

## 框架开发要求

每个插件在符合Blender插件的结构基础上，需要有一个config.py文件用于配置插件的包名，避免与其他插件冲突。
在导入依赖时需要书写完整包名，比如 `from addons.sample_addon.config import __addon_name__`
避免使用相对路径导入，比如 `from .config import __addon_name__`

## 使用说明

1. 克隆此项目。
2. 在您的 IDE 中打开此项目。你可以将IDE使用的Python.exe配置成与Blender相同。
3. 安装必要的依赖：
   ```bash
   pip install -r requirements.txt
   ```
4. 在 [main.py](main.py) 中配置 Blender 可执行文件路径（BLENDER_EXE_PATH）和插件安装路径（BLENDER_ADDON_PATH）。
5. 在 [main.py](main.py) 中配置您想要创建的插件名称（ACTIVE_ADDON）。
6. 运行 create.py 在您的 IDE 中创建一个新的插件。
7. 在新创建的插件目录中开发您的插件。
8. 运行 test.py 在 Blender 中测试您的插件。
9. 运行 release.py 将您的插件打包成可安装的包。成功打包后，终端中将显示打包插件的路径。