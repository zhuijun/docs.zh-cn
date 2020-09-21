---
title: dotnet nuget add source 命令
description: Dotnet nuget add source 命令将新的包源添加到 NuGet 配置文件中。
ms.date: 03/20/2020
ms.openlocfilehash: b847d987de2d88cb3452d32d1bc84232a1e20b6e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537968"
---
# <a name="dotnet-nuget-add-source"></a><span data-ttu-id="13cd4-103">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="13cd4-103">dotnet nuget add source</span></span>

<span data-ttu-id="13cd4-104">**本文适用于：** ✔️ .NET Core 3.1.200 SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="13cd4-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="13cd4-105">“属性”</span><span class="sxs-lookup"><span data-stu-id="13cd4-105">Name</span></span>

<span data-ttu-id="13cd4-106">`dotnet nuget add source` - 添加 NuGet 源。</span><span class="sxs-lookup"><span data-stu-id="13cd4-106">`dotnet nuget add source` - Add a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="13cd4-107">摘要</span><span class="sxs-lookup"><span data-stu-id="13cd4-107">Synopsis</span></span>

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a><span data-ttu-id="13cd4-108">描述</span><span class="sxs-lookup"><span data-stu-id="13cd4-108">Description</span></span>

<span data-ttu-id="13cd4-109">`dotnet nuget add source` 命令将新的包源添加到 NuGet 配置文件中。</span><span class="sxs-lookup"><span data-stu-id="13cd4-109">The `dotnet nuget add source` command adds a new package source to your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="13cd4-110">自变量</span><span class="sxs-lookup"><span data-stu-id="13cd4-110">Arguments</span></span>

- **`PACKAGE_SOURCE_PATH`**

  <span data-ttu-id="13cd4-111">包源的路径。</span><span class="sxs-lookup"><span data-stu-id="13cd4-111">Path to the package source.</span></span>

## <a name="options"></a><span data-ttu-id="13cd4-112">选项</span><span class="sxs-lookup"><span data-stu-id="13cd4-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="13cd4-113">NuGet 配置文件。</span><span class="sxs-lookup"><span data-stu-id="13cd4-113">The NuGet configuration file.</span></span> <span data-ttu-id="13cd4-114">如果指定，则只使用此文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="13cd4-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="13cd4-115">如果不指定，将使用当前目录中的配置文件的层次结构。</span><span class="sxs-lookup"><span data-stu-id="13cd4-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="13cd4-116">有关详细信息，请参阅[常见的 NuGet 配置](/nuget/consume-packages/configuring-nuget-behavior)。</span><span class="sxs-lookup"><span data-stu-id="13cd4-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-n|--name <SOURCE_NAME>`**

  <span data-ttu-id="13cd4-117">源的名称。</span><span class="sxs-lookup"><span data-stu-id="13cd4-117">Name of the source.</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="13cd4-118">连接到已验证源时要使用的密码。</span><span class="sxs-lookup"><span data-stu-id="13cd4-118">Password to be used when connecting to an authenticated source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="13cd4-119">通过禁用密码加密允许存储可移植包源凭据。</span><span class="sxs-lookup"><span data-stu-id="13cd4-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="13cd4-120">连接到已经过身份验证的源时要使用的用户名。</span><span class="sxs-lookup"><span data-stu-id="13cd4-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="13cd4-121">此源的有效身份验证类型的逗号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="13cd4-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="13cd4-122">如果服务器公布 NTLM 或协商，并且你必须使用基本机制发送凭据（例如，在本地 Azure DevOps Server 中使用 PAT 时），则将此项设置为 `basic`。</span><span class="sxs-lookup"><span data-stu-id="13cd4-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="13cd4-123">其他有效值包括 `negotiate`、`kerberos`、`ntlm` 和 `digest`，但这些值不太可能有用。</span><span class="sxs-lookup"><span data-stu-id="13cd4-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="13cd4-124">示例</span><span class="sxs-lookup"><span data-stu-id="13cd4-124">Examples</span></span>

- <span data-ttu-id="13cd4-125">将 `nuget.org` 添加为源：</span><span class="sxs-lookup"><span data-stu-id="13cd4-125">Add `nuget.org` as a source:</span></span>

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- <span data-ttu-id="13cd4-126">将 `c:\packages` 添加为本地源：</span><span class="sxs-lookup"><span data-stu-id="13cd4-126">Add `c:\packages` as a local source:</span></span>

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- <span data-ttu-id="13cd4-127">添加需要身份验证的源：</span><span class="sxs-lookup"><span data-stu-id="13cd4-127">Add a source that needs authentication:</span></span>

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- <span data-ttu-id="13cd4-128">添加需要身份验证的源（然后继续安装凭据提供程序）：</span><span class="sxs-lookup"><span data-stu-id="13cd4-128">Add a source that needs authentication (then go install credential provider):</span></span>

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a><span data-ttu-id="13cd4-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="13cd4-129">See also</span></span>

- [<span data-ttu-id="13cd4-130">NuGet.config 文件中的包源部分</span><span class="sxs-lookup"><span data-stu-id="13cd4-130">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="13cd4-131">sources 命令 (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="13cd4-131">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
