---
title: '将包管理与 F # 一起用于 Azure'
description: '使用 Paket 或 Nuget 管理 F # Azure 依赖项'
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 011a363b264079599e8b7d402fe9896045b1fe04
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100108"
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="ea650-103">F# Azure 依赖项的包管理</span><span class="sxs-lookup"><span data-stu-id="ea650-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="ea650-104">使用包管理器时，可轻松为 Azure 开发获取包。</span><span class="sxs-lookup"><span data-stu-id="ea650-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="ea650-105">这两个选项是 [Paket](https://fsprojects.github.io/Paket/) 和 [NuGet](https://www.nuget.org/)。</span><span class="sxs-lookup"><span data-stu-id="ea650-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="ea650-106">使用 Paket</span><span class="sxs-lookup"><span data-stu-id="ea650-106">Using Paket</span></span>

<span data-ttu-id="ea650-107">如果使用 [Paket](https://fsprojects.github.io/Paket/) 作为依赖关系管理器，可以使用 `paket.exe` 工具添加 Azure 依赖关系。</span><span class="sxs-lookup"><span data-stu-id="ea650-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="ea650-108">例如：</span><span class="sxs-lookup"><span data-stu-id="ea650-108">For example:</span></span>

```console
> paket add nuget WindowsAzure.Storage
```

<span data-ttu-id="ea650-109">或者，如果使用 [Mono](https://www.mono-project.com/) 进行跨平台 .net 开发：</span><span class="sxs-lookup"><span data-stu-id="ea650-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

```console
> mono paket.exe add nuget WindowsAzure.Storage
```

<span data-ttu-id="ea650-110">这会将添加 `WindowsAzure.Storage` 到当前目录中的项目的包依赖项集，修改该 `paket.dependencies` 文件，然后下载包。</span><span class="sxs-lookup"><span data-stu-id="ea650-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="ea650-111">如果以前设置了依赖项，或者正在使用的项目的依赖项已由其他开发人员进行了设置，则可以按以下方式解析和安装依赖项：</span><span class="sxs-lookup"><span data-stu-id="ea650-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> paket install
```

<span data-ttu-id="ea650-112">或者，对于 Mono 开发：</span><span class="sxs-lookup"><span data-stu-id="ea650-112">Or, for Mono development:</span></span>

```console
> mono paket.exe install
```

<span data-ttu-id="ea650-113">可以将所有包依赖项更新到最新版本，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ea650-113">You can update all your package dependencies to the latest version like this:</span></span>

```console
> paket update
```

<span data-ttu-id="ea650-114">或者，对于 Mono 开发：</span><span class="sxs-lookup"><span data-stu-id="ea650-114">Or, for Mono development:</span></span>

```console
> mono paket.exe update
```

## <a name="using-nuget"></a><span data-ttu-id="ea650-115">使用 Nuget</span><span class="sxs-lookup"><span data-stu-id="ea650-115">Using Nuget</span></span>

<span data-ttu-id="ea650-116">如果使用 [NuGet](https://www.nuget.org/) 作为依赖关系管理器，可以使用 `nuget.exe` 工具添加 Azure 依赖关系。</span><span class="sxs-lookup"><span data-stu-id="ea650-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="ea650-117">例如：</span><span class="sxs-lookup"><span data-stu-id="ea650-117">For example:</span></span>

```console
> nuget install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="ea650-118">或者，对于 Mono 开发：</span><span class="sxs-lookup"><span data-stu-id="ea650-118">Or, for Mono development:</span></span>

```console
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="ea650-119">这会将添加 `WindowsAzure.Storage` 到当前目录中的项目的包依赖项集，并下载包。</span><span class="sxs-lookup"><span data-stu-id="ea650-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="ea650-120">如果以前设置了依赖项，或者正在使用的项目的依赖项已由其他开发人员进行了设置，则可以按以下方式解析和安装依赖项：</span><span class="sxs-lookup"><span data-stu-id="ea650-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> nuget restore
```

<span data-ttu-id="ea650-121">或者，对于 Mono 开发：</span><span class="sxs-lookup"><span data-stu-id="ea650-121">Or, for Mono development:</span></span>

```console
> mono nuget.exe restore
```

<span data-ttu-id="ea650-122">可以将所有包依赖项更新到最新版本，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ea650-122">You can update all your package dependencies to the latest version like this:</span></span>

```console
> nuget update
```

<span data-ttu-id="ea650-123">或者，对于 Mono 开发：</span><span class="sxs-lookup"><span data-stu-id="ea650-123">Or, for Mono development:</span></span>

```console
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a><span data-ttu-id="ea650-124">引用程序集</span><span class="sxs-lookup"><span data-stu-id="ea650-124">Referencing Assemblies</span></span>

<span data-ttu-id="ea650-125">若要在 F # 脚本中使用包，需要使用指令引用包中包含的程序集 `#r` 。</span><span class="sxs-lookup"><span data-stu-id="ea650-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="ea650-126">例如：</span><span class="sxs-lookup"><span data-stu-id="ea650-126">For example:</span></span>

```fsharp
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

<span data-ttu-id="ea650-127">如您所见，您需要指定 DLL 的相对路径和完整的 DLL 名称，这些路径可能与包名称不完全相同。</span><span class="sxs-lookup"><span data-stu-id="ea650-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="ea650-128">该路径将包括一个框架版本，还可能包含一个包版本号。</span><span class="sxs-lookup"><span data-stu-id="ea650-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="ea650-129">若要查找所有已安装的程序集，可以在 Windows 命令行中使用如下所示的内容：</span><span class="sxs-lookup"><span data-stu-id="ea650-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

```console
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

<span data-ttu-id="ea650-130">或在 Unix shell 中，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ea650-130">Or in a Unix shell, something like this:</span></span>

```console
> find packages/WindowsAzure.Storage -name "*.dll"
```

<span data-ttu-id="ea650-131">此时将显示已安装的程序集的路径。</span><span class="sxs-lookup"><span data-stu-id="ea650-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="ea650-132">在该处，你可以为 framework 版本选择正确的路径。</span><span class="sxs-lookup"><span data-stu-id="ea650-132">From there, you can select the correct path for your framework version.</span></span>
