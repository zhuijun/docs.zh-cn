---
title: dotnet nuget list source 命令
description: dotnet nuget list source 命令列出 NuGet 配置文件中的所有现有源。
ms.date: 03/20/2020
ms.openlocfilehash: 071061e32aa1bf888e197ec6bf97f4e4f6859f0b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537884"
---
# <a name="dotnet-nuget-list-source"></a><span data-ttu-id="9595f-103">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="9595f-103">dotnet nuget list source</span></span>

<span data-ttu-id="9595f-104">**本文适用于：** ✔️ .NET Core 3.1.200 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="9595f-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9595f-105">“属性”</span><span class="sxs-lookup"><span data-stu-id="9595f-105">Name</span></span>

<span data-ttu-id="9595f-106">`dotnet nuget list source` - 列出所有配置的 NuGet 源。</span><span class="sxs-lookup"><span data-stu-id="9595f-106">`dotnet nuget list source` - Lists all configured NuGet sources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9595f-107">摘要</span><span class="sxs-lookup"><span data-stu-id="9595f-107">Synopsis</span></span>

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a><span data-ttu-id="9595f-108">描述</span><span class="sxs-lookup"><span data-stu-id="9595f-108">Description</span></span>

<span data-ttu-id="9595f-109">`dotnet nuget list source` 命令列出 NuGet 配置文件中的所有现有源。</span><span class="sxs-lookup"><span data-stu-id="9595f-109">The `dotnet nuget list source` command lists all existing sources from your NuGet configuration files.</span></span>

## <a name="options"></a><span data-ttu-id="9595f-110">选项</span><span class="sxs-lookup"><span data-stu-id="9595f-110">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="9595f-111">NuGet 配置文件。</span><span class="sxs-lookup"><span data-stu-id="9595f-111">The NuGet configuration file.</span></span> <span data-ttu-id="9595f-112">如果指定，则只使用此文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="9595f-112">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="9595f-113">如果不指定，将使用当前目录中的配置文件的层次结构。</span><span class="sxs-lookup"><span data-stu-id="9595f-113">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="9595f-114">有关详细信息，请参阅[常见的 NuGet 配置](/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="9595f-114">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--format [Detailed|Short]`**

  <span data-ttu-id="9595f-115">list 命令输出的格式为：`Detailed`（默认值）和 `Short`。</span><span class="sxs-lookup"><span data-stu-id="9595f-115">The format of the list command output: `Detailed` (the default) and `Short`.</span></span>

## <a name="examples"></a><span data-ttu-id="9595f-116">示例</span><span class="sxs-lookup"><span data-stu-id="9595f-116">Examples</span></span>

- <span data-ttu-id="9595f-117">列出当前目录中的已配置源：</span><span class="sxs-lookup"><span data-stu-id="9595f-117">List configured sources from the current directory:</span></span>

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a><span data-ttu-id="9595f-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="9595f-118">See also</span></span>

- [<span data-ttu-id="9595f-119">NuGet.config 文件中的包源部分</span><span class="sxs-lookup"><span data-stu-id="9595f-119">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="9595f-120">sources 命令 (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="9595f-120">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
