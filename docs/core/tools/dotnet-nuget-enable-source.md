---
title: dotnet nuget enable source 命令
description: dotnet nuget enable source 命令在 NuGet 配置文件中启用现有源。
ms.date: 03/20/2020
ms.openlocfilehash: b727844dd7d7cc82476e94a3f0ec4ecc6559d5ed
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537929"
---
# <a name="dotnet-nuget-enable-source"></a><span data-ttu-id="177d2-103">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="177d2-103">dotnet nuget enable source</span></span>

<span data-ttu-id="177d2-104">**本文适用于：** ✔️ .NET Core 3.1.200 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="177d2-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="177d2-105">“属性”</span><span class="sxs-lookup"><span data-stu-id="177d2-105">Name</span></span>

<span data-ttu-id="177d2-106">`dotnet nuget enable source` - 启用 NuGet 源。</span><span class="sxs-lookup"><span data-stu-id="177d2-106">`dotnet nuget enable source` - Enable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="177d2-107">摘要</span><span class="sxs-lookup"><span data-stu-id="177d2-107">Synopsis</span></span>

```dotnetcli
dotnet nuget enable source <NAME> [--configfile <FILE>]

dotnet nuget enable source -h|--help
```

## <a name="description"></a><span data-ttu-id="177d2-108">描述</span><span class="sxs-lookup"><span data-stu-id="177d2-108">Description</span></span>

<span data-ttu-id="177d2-109">`dotnet nuget enable source` 命令在 NuGet 配置文件中启用现有源。</span><span class="sxs-lookup"><span data-stu-id="177d2-109">The `dotnet nuget enable source` command enables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="177d2-110">自变量</span><span class="sxs-lookup"><span data-stu-id="177d2-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="177d2-111">源的名称。</span><span class="sxs-lookup"><span data-stu-id="177d2-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="177d2-112">选项</span><span class="sxs-lookup"><span data-stu-id="177d2-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="177d2-113">NuGet 配置文件。</span><span class="sxs-lookup"><span data-stu-id="177d2-113">The NuGet configuration file.</span></span> <span data-ttu-id="177d2-114">如果指定，则只使用此文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="177d2-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="177d2-115">如果不指定，将使用当前目录中的配置文件的层次结构。</span><span class="sxs-lookup"><span data-stu-id="177d2-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="177d2-116">有关详细信息，请参阅[常见的 NuGet 配置](/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="177d2-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="177d2-117">示例</span><span class="sxs-lookup"><span data-stu-id="177d2-117">Examples</span></span>

- <span data-ttu-id="177d2-118">启用名为 `mySource` 的源：</span><span class="sxs-lookup"><span data-stu-id="177d2-118">Enable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="177d2-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="177d2-119">See also</span></span>

- [<span data-ttu-id="177d2-120">NuGet.config 文件中的包源部分</span><span class="sxs-lookup"><span data-stu-id="177d2-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="177d2-121">sources 命令 (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="177d2-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
