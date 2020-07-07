---
title: 在 macOS 上安装 .NET Core
description: 了解可在其上安装 .NET Core 的 macOS 版本。
author: adegeo
ms.author: adegeo
ms.date: 06/25/2020
ms.openlocfilehash: bb1a0fa24e2f6e8850cbe59378793ff846f04ba9
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85804447"
---
# <a name="install-net-core-on-macos"></a>在 macOS 上安装 .NET Core

> [!div class="op_single_selector"]
>
> - [在 Windows 上安装](windows.md)
> - [在 macOS 上安装](macos.md)
> - [在 Linux 上安装](linux.md)

在本文中，你将了解如何在 macOS 上安装 .NET Core。 .NET Core 由运行时和 SDK 组成。 运行时用于运行 .NET Core 应用，应用可能包含也可能不包含它。 SDK 用于创建 .NET Core 应用和库。 .NET Core 运行时始终随 SDK 一起安装。

最新版本的 .NET Core 是 3.1。

[下载 .NET Core。](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a>支持的版本

下表列出了当前支持的 .NET Core 版本以及支持它们的 macOS 版本。 无论哪个 [.NET Core 版本达到支持终止](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)，仍支持这些版本。

- ✔️ 指示 .NET Core 版本仍受支持。
- ❌ 指示 .NET Core 版本不受支持。

| 操作系统          | .NET Core 2.1 | .NET Core 3.1 | .NET 5 预览版 |
|---------------------------|---------------|---------------|----------------|
| macOS 10.15“Catalina”    | ✔️ 2.1（[发行说明][release-notes-21]） | ✔️ 3.1（[发行说明][release-notes-31]） | ✔️ 5.0 预览版（[发行说明][release-notes-50]） |
| macOS 10.14“Mojave”      | ✔️ 2.1（[发行说明][release-notes-21]） | ✔️ 3.1（[发行说明][release-notes-31]） | ✔️ 5.0 预览版（[发行说明][release-notes-50]） |
| macOS 10.13“High Sierra” | ✔️ 2.1（[发行说明][release-notes-21]） | ✔️ 3.1（[发行说明][release-notes-31]） | ✔️ 5.0 预览版（[发行说明][release-notes-50]） |
| macOS 10.12“Sierra”      | ✔️ 2.1（[发行说明][release-notes-21]） | ❌ 3.1（[发行说明][release-notes-31]） | ❌ 5.0 预览版（[发行说明][release-notes-50]） |

## <a name="unsupported-releases"></a>不支持的版本

以下 .NET Core 版本 ❌ 不再受支持。 这些版本的下载仍保持发布状态：

- 3.0（[发行说明][release-notes-30]）
- 2.2（[发行说明][release-notes-22]）
- 2.0（[发行说明][release-notes-20]）

## <a name="runtime-information"></a>运行时信息

运行时用于运行使用 .NET Core 创建的应用。 应用作者发布应用时，可以在其应用中包含运行时。 如果作者未包含运行时，则由用户安装运行时。

可以在 macOS 上安装三个不同的运行时：

*ASP.NET Core 运行时*\
运行 ASP.NET Core 应用。 包括 .NET Core 运行时。

*.NET Core 运行时*\
此运行时是最简单的运行时，不包括任何其他运行时。 强烈建议安装 ASP.NET Core 运行时，以最大限度地提升与 .NET Core 应用的兼容性。

[下载 .NET Core 运行时。](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a>SDK 信息

SDK 用于生成和发布 .NET Core 应用和库。 安装 SDK 会包含两个[运行时](#runtime-information)：ASP.NET Core 和 .NET Core。

[下载 .NET Core SDK。](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="dependencies"></a>依赖项

以下 macOS 版本支持 .NET Core：

> [!NOTE]
> `+` 表示最低版本。

| .NET Core 版本 | macOS                 | 体系结构 |     |
| ----------------- | --------------------- | --------------| --- |
| 3.1               | High Sierra (10.13+)  | X64 | [详细信息](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | High Sierra (10.13+)  | X64 | [详细信息](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | Sierra (10.12+)       | X64 | [详细信息](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | Sierra (10.12+)       | X64 | [详细信息](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

自 macOS Catalina（版本10.15）开始，所有在 2019 年 6 月 1 日之后生成并使用开发者 ID 扩散的软件都必须经过公证。 此要求应用于 .NET Core 运行时、.NET Core SDK 以及使用 .NET Core 创建的软件。

自 2020 年 2 月 18 日起，.NET Core（运行时和 SDK）版本 3.1、3.0 和 2.1 的安装程序都已经过公证。 以前发布的版本没有经过公证。 如果运行未经过公证的应用，将看到类似于下图的错误：

![macOS Catalina 公证警报](media/dependencies/macos-notarized-pkg-warning.png)

若要详细了解强制执行的公证要求对 .NET Core 和 .NET Core 应用的影响，请参阅[处理 macOS Catalina 公证](macos-notarization-issues.md)。

## <a name="libgdiplus"></a>libgdiplus

使用 System.Drawing.Common 程序集的 .NET Core 应用程序要求安装 libgdiplus。

获取 libgdiplus 的一个简单方法是使用适用于 macOS 的 [Homebrew (“brew”)](https://brew.sh/) 包。 在安装 brew 后，通过在终端（命令）提示符处执行以下命令来安装 libgdiplus：

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a>使用安装程序安装

macOS 具有独立的安装程序，可用于安装 .NET Core 3.1 SDK：

- [x64（64 位）CPU](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>下载并手动安装

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

除了使用适用于 .NET Core 的 macOS 安装程序，还可以下载并手动安装 SDK 和运行时。 手动安装通常作为持续集成测试的一部分执行。 对于开发人员或用户，一般使用[安装程序](https://dotnet.microsoft.com/download/dotnet-core)会更好。

如果安装 .NET Core SDK，则无需安装相应的运行时。 首先，从以下站点之一下载 SDK 或运行时的二进制版本：

- ✔️ [.NET 5.0 预览版下载](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.NET Core 3.1 下载](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [.NET Core 2.1 下载](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [所有 .NET Core 下载项](https://dotnet.microsoft.com/download/dotnet-core)

接下来，提取已下载的文件并使用 `export` 命令设置 .NET Core 使用的变量，然后确保 .NET Core 在 PATH 中。

若要提取运行时并使 .NET Core CLI 命令可用于终端，请先下载 .NET Core 二进制版本。 然后，打开终端并从保存文件的目录运行以下命令。 根据下载内容，存档文件名称可能不同。

**使用以下命令来提取运行时**：

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.5-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

**使用以下命令来提取 SDK**：

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> 前面的 `export` 命令只会使 .NET Core CLI 命令对运行它的终端会话可用。
>
> 你可以编辑 shell 配置文件，永久地添加这些命令。 Linux 提供了许多不同的 shell，每个都有不同的配置文件。 例如：
>
> - **Bash Shell**：~/.bash_profile、~/.bashrc
> - **Korn Shell**：~/.kshrc 或 .profile
> - **Z Shell**：~/.zshrc 或 .zprofile
>
> 为 shell 编辑相应的源文件，并将 `:$HOME/dotnet` 添加到现有 `PATH` 语句的末尾。 如果不包含 `PATH` 语句，则使用 `export PATH=$PATH:$HOME/dotnet` 添加新行。
>
> 另外，将 `export DOTNET_ROOT=$HOME/dotnet` 添加至文件的末尾。

使用此方法可以将不同的版本安装到不同的位置，并明确选择应用程序要使用的对应版本。

## <a name="install-with-visual-studio-for-mac"></a>使用 Visual Studio for Mac 安装

在选定“.NET Core”工作负载时，使用 Visual Studio for Mac 安装 .NET Core SDK。 若要开始在 macOS 上进行 .NET Core 开发，请参阅[安装 Visual Studio 2019 for Mac](/visualstudio/mac/installation)。 对于最新的版本 .NET Core 3.1，则必须使用 Visual Studio for Mac 8.4 预览版。

[![具有 .NET Core 工作负载功能的 macOS Visual Studio 2019 for Mac](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

## <a name="install-alongside-visual-studio-code"></a>随 Visual Studio Code 一起安装

Visual Studio Code 是一个功能强大的轻量级源代码编辑器，可在桌面上运行。 Visual Studio Code 适用于 Windows、macOS 和 Linux。

虽然 Visual Studio Code 不像 Visual Studio 一样附带自动的 .NET Core 安装程序，但添加 .NET Core 支持非常简单。

01. [下载并安装 Visual Studio Code](https://code.visualstudio.com/Download)。
01. [下载并安装 .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core)。
01. [从 Visual Studio Code 市场安装 C# 扩展](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)。

## <a name="install-with-bash-automation"></a>使用 Bash 自动化安装

[dotnet-install 脚本](../tools/dotnet-install-script.md)用于运行时的自动化和非管理员安装。 可从 [dotnet-install 脚本引用页](../tools/dotnet-install-script.md)下载该脚本。

此脚本默认安装最新的[长期支持 (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 版本，即 .NET Core 3.1。 可通过指定 `current` 开关以选择特定版本。 包括 `runtime` 开关以安装运行时。 否则，该脚本安装 [SDK](sdk.md)。

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> 以上命令安装 ASP.NET Core 运行时，用于实现最大的兼容性。 ASP.NET Core 运行时还包括标准 .NET Core 运行时。

## <a name="docker"></a>Docker

容器提供了一种将应用程序与主机系统的其余部分隔离的轻量级方法。 同一计算机上的容器只共享内核，并使用为应用程序提供的资源。

.NET Core 可在 Docker 容器中运行。 官方 .NET Core Docker 映像发布到 Microsoft 容器注册表 (MCR)，用户可以在 [Microsoft.NET Core Docker 中心存储库](https://hub.docker.com/_/microsoft-dotnet-core/)中找到这些映像。 每个存储库包含 .NET（SDK 或运行时）和可以使用的操作系统的不同组合的映像。

Microsoft 提供适合特定场景的映像。 例如，[ASP.NET Core 存储库](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/)提供针对在生产环境中运行 ASP.NET Core 应用生成的映像。

有关在 Docker 容器中使用 .NET Core 的详细信息，请参阅 [.NET 和 Docker 简介](../docker/introduction.md)和[示例](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)。

## <a name="next-steps"></a>后续步骤

- [如何检查是否已安装 .NET Core](how-to-detect-installed-versions.md?pivots=os-macos)。
- [处理 macOS Catalina 公证](macos-notarization-issues.md)。
- [教程：开始使用 macOS](../tutorials/using-on-mac-vs.md)。
- [教程：使用 Visual Studio Code 创建一个新应用](../tutorials/with-visual-studio-code.md)。
- [教程：使 .NET Core 应用容器化](../docker/build-container.md)。

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
