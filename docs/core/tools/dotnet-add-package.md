---
title: dotnet add package 命令
description: “dotnet add package”命令可便于添加对项目的 NuGet 包引用。
ms.date: 02/14/2020
ms.openlocfilehash: bc79fe8adf5f775ddce62f3877a8de945c6a18ab
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840892"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="fd47b-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="fd47b-103">dotnet add package</span></span>

<span data-ttu-id="fd47b-104">**本文适用于：** ✔️ .NET Core 2.x SDK 及更高版本</span><span class="sxs-lookup"><span data-stu-id="fd47b-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="fd47b-105">“属性”</span><span class="sxs-lookup"><span data-stu-id="fd47b-105">Name</span></span>

<span data-ttu-id="fd47b-106">`dotnet add package` - 向项目文件添加包引用。</span><span class="sxs-lookup"><span data-stu-id="fd47b-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fd47b-107">摘要</span><span class="sxs-lookup"><span data-stu-id="fd47b-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a><span data-ttu-id="fd47b-108">描述</span><span class="sxs-lookup"><span data-stu-id="fd47b-108">Description</span></span>

<span data-ttu-id="fd47b-109">使用 `dotnet add package` 命令可方便地向项目文件添加包引用。</span><span class="sxs-lookup"><span data-stu-id="fd47b-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="fd47b-110">运行该命令后，还有一个兼容性检查，确保包与项目中的框架兼容。</span><span class="sxs-lookup"><span data-stu-id="fd47b-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="fd47b-111">如果通过了该检查，则将 `<PackageReference>` 元素添加到项目文件并运行 [dotnet 还原](dotnet-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="fd47b-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

<span data-ttu-id="fd47b-112">例如，将 `Newtonsoft.Json` 添加到 ToDo.csproj 后的输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="fd47b-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```console
Writing C:\Users\me\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\Temp\projects\consoleproj\consoleproj.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 79ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg 232ms
log  : Installing Newtonsoft.Json 12.0.1.
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '12.0.1' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

<span data-ttu-id="fd47b-113">*ToDo.csproj* 文件现包含用于引用的包的 [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 元素。</span><span class="sxs-lookup"><span data-stu-id="fd47b-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a><span data-ttu-id="fd47b-114">隐式还原</span><span class="sxs-lookup"><span data-stu-id="fd47b-114">Implicit restore</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="fd47b-115">自变量</span><span class="sxs-lookup"><span data-stu-id="fd47b-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="fd47b-116">指定项目文件。</span><span class="sxs-lookup"><span data-stu-id="fd47b-116">Specifies the project file.</span></span> <span data-ttu-id="fd47b-117">如果未指定，此命令会搜索当前目录来获取一个项目文件。</span><span class="sxs-lookup"><span data-stu-id="fd47b-117">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="fd47b-118">要添加的包引用。</span><span class="sxs-lookup"><span data-stu-id="fd47b-118">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="fd47b-119">选项</span><span class="sxs-lookup"><span data-stu-id="fd47b-119">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="fd47b-120">仅在以特定[框架](../../standard/frameworks.md)为目标时添加包引用。</span><span class="sxs-lookup"><span data-stu-id="fd47b-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="fd47b-121">打印出有关命令的简短帮助。</span><span class="sxs-lookup"><span data-stu-id="fd47b-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="fd47b-122">允许命令停止并等待用户输入或操作（例如，完成身份验证）。</span><span class="sxs-lookup"><span data-stu-id="fd47b-122">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="fd47b-123">从 .NET Core 2.1 SDK，版本 2.1.400 或更高版本开始可用。</span><span class="sxs-lookup"><span data-stu-id="fd47b-123">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="fd47b-124">在不执行还原预览和兼容性检查的情况下添加包引用。</span><span class="sxs-lookup"><span data-stu-id="fd47b-124">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="fd47b-125">要在其中还原包的目录。</span><span class="sxs-lookup"><span data-stu-id="fd47b-125">The directory where to restore the packages.</span></span> <span data-ttu-id="fd47b-126">Windows 上的默认包还原位置为 `%userprofile%\.nuget\packages`，macOS 和 Linux 上的默认包还原位置为 `~/.nuget/packages`。</span><span class="sxs-lookup"><span data-stu-id="fd47b-126">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="fd47b-127">有关详细信息，请参阅[在 NuGet 中管理全局包、缓存和临时文件夹](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)。</span><span class="sxs-lookup"><span data-stu-id="fd47b-127">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="fd47b-128">要在还原操作期间使用的 NuGet 包源的 URI。</span><span class="sxs-lookup"><span data-stu-id="fd47b-128">The URI of the NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="fd47b-129">包的版本。</span><span class="sxs-lookup"><span data-stu-id="fd47b-129">Version of the package.</span></span> <span data-ttu-id="fd47b-130">请参阅 [NuGet 包版本控制](https://docs.microsoft.com/nuget/reference/package-versioning)。</span><span class="sxs-lookup"><span data-stu-id="fd47b-130">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="fd47b-131">示例</span><span class="sxs-lookup"><span data-stu-id="fd47b-131">Examples</span></span>

- <span data-ttu-id="fd47b-132">将 `Newtonsoft.Json` NuGet 包添加到项目：</span><span class="sxs-lookup"><span data-stu-id="fd47b-132">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="fd47b-133">向项目添加特定版本的包：</span><span class="sxs-lookup"><span data-stu-id="fd47b-133">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="fd47b-134">使用特定的 NuGet 源添加包：</span><span class="sxs-lookup"><span data-stu-id="fd47b-134">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="fd47b-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="fd47b-135">See also</span></span>

- [<span data-ttu-id="fd47b-136">在 NuGet 中管理全局包、缓存和临时文件夹</span><span class="sxs-lookup"><span data-stu-id="fd47b-136">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="fd47b-137">NuGet 包版本控制</span><span class="sxs-lookup"><span data-stu-id="fd47b-137">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)
