---
ms.openlocfilehash: e7d35045892c62f759aad5067962ac5c15a9fb8b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602698"
---

<span data-ttu-id="e5680-101">在下载 .NET Core SDK 和 .NET Core 运行时后，可以手动安装它们。</span><span class="sxs-lookup"><span data-stu-id="e5680-101">Both .NET Core SDK and .NET Core Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="e5680-102">如果安装 .NET Core SDK，则无需安装相应的运行时。</span><span class="sxs-lookup"><span data-stu-id="e5680-102">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="e5680-103">首先，从以下站点之一下载 SDK 或运行时的二进制版本：</span><span class="sxs-lookup"><span data-stu-id="e5680-103">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="e5680-104">✔️ [.NET 5.0 预览版下载](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="e5680-104">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="e5680-105">✔️ [.NET Core 3.1 下载](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="e5680-105">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="e5680-106">❌ [.NET Core 3.0 下载](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="e5680-106">❌ [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>
- <span data-ttu-id="e5680-107">❌ [.NET Core 2.2 下载](https://dotnet.microsoft.com/download/dotnet-core/2.2)</span><span class="sxs-lookup"><span data-stu-id="e5680-107">❌ [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2)</span></span>
- <span data-ttu-id="e5680-108">✔️ [.NET Core 2.1 下载](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="e5680-108">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>

<span data-ttu-id="e5680-109">接下来，提取已下载的文件并使用 `export` 命令设置 .NET Core 使用的变量，然后确保 .NET Core 在 PATH 中。</span><span class="sxs-lookup"><span data-stu-id="e5680-109">Next, extract the downloaded file and use the `export` command to set variables used by .NET Core and then ensure .NET Core is in PATH.</span></span>

<span data-ttu-id="e5680-110">若要提取运行时并使 .NET Core CLI 命令可用于终端，请先下载 .NET Core 二进制版本。</span><span class="sxs-lookup"><span data-stu-id="e5680-110">To extract the runtime and make the .NET Core CLI commands available at the terminal, first download a .NET Core binary release.</span></span> <span data-ttu-id="e5680-111">然后，打开终端并从保存文件的目录运行以下命令。</span><span class="sxs-lookup"><span data-stu-id="e5680-111">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="e5680-112">前面的 `export` 命令只会使 .NET Core CLI 命令对运行它的终端会话可用。</span><span class="sxs-lookup"><span data-stu-id="e5680-112">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="e5680-113">你可以编辑 shell 配置文件，永久地添加这些命令。</span><span class="sxs-lookup"><span data-stu-id="e5680-113">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="e5680-114">Linux 提供了许多不同的 shell，每个都有不同的配置文件。</span><span class="sxs-lookup"><span data-stu-id="e5680-114">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="e5680-115">例如：</span><span class="sxs-lookup"><span data-stu-id="e5680-115">For example:</span></span>
>
> - <span data-ttu-id="e5680-116">**Bash Shell**：~/.bash_profile、~/.bashrc</span><span class="sxs-lookup"><span data-stu-id="e5680-116">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="e5680-117">**Korn Shell**：~/.kshrc 或 .profile</span><span class="sxs-lookup"><span data-stu-id="e5680-117">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="e5680-118">**Z Shell**：~/.zshrc 或 .zprofile</span><span class="sxs-lookup"><span data-stu-id="e5680-118">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="e5680-119">为 shell 编辑相应的源文件，并将 `:$HOME/dotnet` 添加到现有 `PATH` 语句的末尾。</span><span class="sxs-lookup"><span data-stu-id="e5680-119">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="e5680-120">如果不包含 `PATH` 语句，则使用 `export PATH=$PATH:$HOME/dotnet` 添加新行。</span><span class="sxs-lookup"><span data-stu-id="e5680-120">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="e5680-121">另外，将 `export DOTNET_ROOT=$HOME/dotnet` 添加至文件的末尾。</span><span class="sxs-lookup"><span data-stu-id="e5680-121">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="e5680-122">使用此方法可以将不同的版本安装到不同的位置，并明确选择应用程序要使用的对应版本。</span><span class="sxs-lookup"><span data-stu-id="e5680-122">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>
