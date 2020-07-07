---
ms.openlocfilehash: ea2883912907843e4b6d65db5ba186af43f27aaa
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85805543"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

除了使用包管理器，还可以下载并手动安装 SDK 和运行时。 手动安装通常作为持续集成测试的一部分执行，或在不支持的 Linux 分发版上执行。 对于开发人员或用户，一般使用包管理器会更好。

如果安装 .NET Core SDK，则无需安装相应的运行时。 首先，从以下站点之一下载 SDK 或运行时的二进制版本：

- ✔️ [.NET 5.0 预览版下载](https://dotnet.microsoft.com/download/dotnet/5.0)
- ✔️ [.NET Core 3.1 下载](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- ✔️ [.NET Core 2.1 下载](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [所有 .NET Core 下载项](https://dotnet.microsoft.com/download/dotnet-core)

接下来，提取已下载的文件并使用 `export` 命令设置 .NET Core 使用的变量，然后确保 .NET Core 在 PATH 中。

若要提取运行时并使 .NET Core CLI 命令可用于终端，请先下载 .NET Core 二进制版本。 然后，打开终端并从保存文件的目录运行以下命令。 根据下载内容，存档文件名称可能不同。

**使用以下命令来提取运行时**：

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

**使用以下命令来提取 SDK**：

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-linux-x64.tar.gz -C "$HOME/dotnet"
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
