---
title: 管理 .NET Core 中的依赖项
description: 介绍如何管理 .NET Core 应用程序的项目依赖项。
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.topic: how-to
ms.date: 02/25/2020
ms.openlocfilehash: 2aeedb56f774b51076764c2772eb02b2fa095d92
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062855"
---
# <a name="manage-dependencies-in-net-core-applications"></a><span data-ttu-id="5b2a3-103">管理 .NET Core 应用程序中的依赖项</span><span class="sxs-lookup"><span data-stu-id="5b2a3-103">Manage dependencies in .NET Core applications</span></span>

<span data-ttu-id="5b2a3-104">本文介绍如何通过编辑项目文件或使用 CLI 来添加和删除依赖项。</span><span class="sxs-lookup"><span data-stu-id="5b2a3-104">This article explains how to add and remove dependencies by editing the project file or by using the CLI.</span></span>

## <a name="the-packagereference-element"></a><span data-ttu-id="5b2a3-105">\<PackageReference> 元素</span><span class="sxs-lookup"><span data-stu-id="5b2a3-105">The \<PackageReference> element</span></span>

<span data-ttu-id="5b2a3-106">`<PackageReference>` 项目文件元素具有以下结构：</span><span class="sxs-lookup"><span data-stu-id="5b2a3-106">The `<PackageReference>` project file element has the following structure:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

<span data-ttu-id="5b2a3-107">`Include` 特性指定要添加到项目的包的 ID。</span><span class="sxs-lookup"><span data-stu-id="5b2a3-107">The `Include` attribute specifies the ID of the package to add to the project.</span></span> <span data-ttu-id="5b2a3-108">`Version` 特性指定要获取的版本。</span><span class="sxs-lookup"><span data-stu-id="5b2a3-108">The `Version` attribute specifies the version to get.</span></span> <span data-ttu-id="5b2a3-109">版本根据 [NuGet 版本规则](/nuget/create-packages/dependency-versions#version-ranges)进行指定。</span><span class="sxs-lookup"><span data-stu-id="5b2a3-109">Versions are specified as per [NuGet version rules](/nuget/create-packages/dependency-versions#version-ranges).</span></span>

> [!NOTE]
> <span data-ttu-id="5b2a3-110">如果不熟悉“项目-文件”语法，可参阅 [MSBuild 项目参考](/visualstudio/msbuild/msbuild-project-file-schema-reference)文档了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="5b2a3-110">If you're not familiar with project-file syntax, see the [MSBuild project reference](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation for more information.</span></span>

<span data-ttu-id="5b2a3-111">使用条件来添加仅在特定目标中可用的依赖项，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="5b2a3-111">Use conditions to add a dependency that's available only in a specific target, as shown in the following example:</span></span>

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

<span data-ttu-id="5b2a3-112">上述示例中的依赖项只有在对给定目标生成时才有效。</span><span class="sxs-lookup"><span data-stu-id="5b2a3-112">The dependency in the preceding example will only be valid if the build is happening for that given target.</span></span> <span data-ttu-id="5b2a3-113">条件中的 `$(TargetFramework)` 是将在项目中设置的 MSBuild 属性。</span><span class="sxs-lookup"><span data-stu-id="5b2a3-113">The `$(TargetFramework)` in the condition is an MSBuild property that's being set in the project.</span></span> <span data-ttu-id="5b2a3-114">对于大多数常见的 .NET Core 应用程序，无需这样做。</span><span class="sxs-lookup"><span data-stu-id="5b2a3-114">For most common .NET Core applications, you don't need to do this.</span></span>

## <a name="add-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="5b2a3-115">通过编辑项目文件添加依赖项</span><span class="sxs-lookup"><span data-stu-id="5b2a3-115">Add a dependency by editing the project file</span></span>

<span data-ttu-id="5b2a3-116">若要添加依赖项，请在 `<ItemGroup>` 元素内添加 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="5b2a3-116">To add a dependency, add a `<PackageReference>` element inside an `<ItemGroup>` element.</span></span> <span data-ttu-id="5b2a3-117">可以添加到现有 `<ItemGroup>`，也可以新建一个元素。</span><span class="sxs-lookup"><span data-stu-id="5b2a3-117">You can add to an existing `<ItemGroup>` or create a new one.</span></span> <span data-ttu-id="5b2a3-118">下面的示例使用 `dotnet new console` 创建的默认控制台应用程序项目：</span><span class="sxs-lookup"><span data-stu-id="5b2a3-118">The following example uses the default console application project that's created by `dotnet new console`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="3.1.2" />
  </ItemGroup>

</Project>
```

## <a name="add-a-dependency-by-using-the-cli"></a><span data-ttu-id="5b2a3-119">使用 CLI 添加依赖项</span><span class="sxs-lookup"><span data-stu-id="5b2a3-119">Add a dependency by using the CLI</span></span>

<span data-ttu-id="5b2a3-120">若要添加依赖项，请运行 [dotnet add package](dotnet-add-package.md) 命令，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="5b2a3-120">To add a dependency, run the [dotnet add package](dotnet-add-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a><span data-ttu-id="5b2a3-121">通过编辑项目文件删除依赖项</span><span class="sxs-lookup"><span data-stu-id="5b2a3-121">Remove a dependency by editing the project file</span></span>

<span data-ttu-id="5b2a3-122">若要删除依赖项，请从项目文件中删除其 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="5b2a3-122">To remove a dependency, remove its `<PackageReference>` element from the project file.</span></span>

## <a name="remove-a-dependency-by-using-the-cli"></a><span data-ttu-id="5b2a3-123">使用 CLI 删除依赖项</span><span class="sxs-lookup"><span data-stu-id="5b2a3-123">Remove a dependency by using the CLI</span></span>

<span data-ttu-id="5b2a3-124">若要删除依赖项，请运行 [dotnet remove package](dotnet-remove-package.md) 命令，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="5b2a3-124">To remove a dependency, run the [dotnet remove package](dotnet-remove-package.md) command, as shown in the following example:</span></span>

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a><span data-ttu-id="5b2a3-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="5b2a3-125">See also</span></span>

* [<span data-ttu-id="5b2a3-126">项目文件中的包引用</span><span class="sxs-lookup"><span data-stu-id="5b2a3-126">Package references in project files</span></span>](../project-sdk/msbuild-props.md#reference-properties-and-items)
* [<span data-ttu-id="5b2a3-127">dotnet list package 命令</span><span class="sxs-lookup"><span data-stu-id="5b2a3-127">dotnet list package command</span></span>](dotnet-list-package.md)
