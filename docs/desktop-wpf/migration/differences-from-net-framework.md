---
title: .NET Framework 与 .NET Core 之间的差异
description: 介绍 Windows Presentation Foundation (WPF) 的 .NET Framework 实现与 .NET Core WPF 之间的差异。 迁移应用时，你应考虑以下不兼容性。
author: adegeo
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 3bedc30046c36d4c5430feedf5854276ebaef8aa
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325688"
---
# <a name="differences-in-wpf"></a><span data-ttu-id="29dae-104">WPF 中的差异</span><span class="sxs-lookup"><span data-stu-id="29dae-104">Differences in WPF</span></span>

<span data-ttu-id="29dae-105">本文介绍了 .NET Core 上的 Windows Presentation Foundation (WPF) 与 .NET Framework 之间的差异。</span><span class="sxs-lookup"><span data-stu-id="29dae-105">This article describes the differences between Windows Presentation Foundation (WPF) on .NET Core and .NET Framework.</span></span> <span data-ttu-id="29dae-106">WPF for .NET Core 是一个[开放源代码框架](https://github.com/dotnet/wpf)，它是从原始 WPF for .NET Framework 源代码派生而来的。</span><span class="sxs-lookup"><span data-stu-id="29dae-106">WPF for .NET Core is an [open-source framework](https://github.com/dotnet/wpf) forked from the original WPF for .NET Framework source code.</span></span>

<span data-ttu-id="29dae-107">.NET Framework 有一些 .NET Core 不支持的功能。</span><span class="sxs-lookup"><span data-stu-id="29dae-107">There are a few features of .NET Framework that .NET Core doesn't support.</span></span> <span data-ttu-id="29dae-108">关于不支持的技术的详细信息，请参阅 [.NET Framework 技术在 .NET Core 上不可用](../../core/porting/net-framework-tech-unavailable.md)。</span><span class="sxs-lookup"><span data-stu-id="29dae-108">For more information on unsupported technologies, see [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md).</span></span>

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a><span data-ttu-id="29dae-109">SDK 样式项目</span><span class="sxs-lookup"><span data-stu-id="29dae-109">SDK-style projects</span></span>

<span data-ttu-id="29dae-110">.NET Core 使用 SDK 样式项目文件。</span><span class="sxs-lookup"><span data-stu-id="29dae-110">.NET Core uses SDK-style project files.</span></span> <span data-ttu-id="29dae-111">这些项目文件与 Visual Studio 管理的传统 .NET Framework 项目文件不同。</span><span class="sxs-lookup"><span data-stu-id="29dae-111">These project files are different from the traditional .NET Framework project files managed by Visual Studio.</span></span> <span data-ttu-id="29dae-112">要将 .NET Framework WPF 应用迁移到 .NET Core，必须转换项目。</span><span class="sxs-lookup"><span data-stu-id="29dae-112">To migrate your .NET Framework WPF apps to .NET Core, you must convert your projects.</span></span> <span data-ttu-id="29dae-113">有关详细信息，请参阅[将 WPF 应用迁移到 .NET Core 3.0](convert-project-from-net-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="29dae-113">For more information, see [Migrate WPF apps to .NET Core 3.0](convert-project-from-net-framework.md).</span></span>

## <a name="nuget-package-references"></a><span data-ttu-id="29dae-114">NuGet 包引用</span><span class="sxs-lookup"><span data-stu-id="29dae-114">NuGet package references</span></span>

<span data-ttu-id="29dae-115">如果 .NET Framework 应用在 packages.config  文件中列出其 NuGet 依赖项，请迁移为 [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 格式：</span><span class="sxs-lookup"><span data-stu-id="29dae-115">If your .NET Framework app lists its NuGet dependencies in a *packages.config* file, migrate to the [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) format:</span></span>

1. <span data-ttu-id="29dae-116">在 Visual Studio 中，打开“解决方案资源管理器”  窗格。</span><span class="sxs-lookup"><span data-stu-id="29dae-116">In Visual Studio, open the **Solution Explorer** pane.</span></span>
1. <span data-ttu-id="29dae-117">在 WPF 项目中，右键单击“packages.config”   > “将 packages.config 迁移到 PackageReference”  。</span><span class="sxs-lookup"><span data-stu-id="29dae-117">In your WPF project, right-click **packages.config** > **Migrate packages.config to PackageReference**.</span></span>

![正在升级到 PackageReference](media/differences-from-net-framework/package-reference-migration.png)

<span data-ttu-id="29dae-119">将出现一个对话框，显示计算出的顶级 NuGet 依赖关系，并询问应将其他哪些 NuGet 包提升到顶级。</span><span class="sxs-lookup"><span data-stu-id="29dae-119">A dialog will appear showing calculated top-level NuGet dependencies and asking which other NuGet packages should be promoted to top level.</span></span> <span data-ttu-id="29dae-120">选择“确定”  ，然后将“packages.config”  文件从项目中删除，并将 `<PackageReference>` 元素添加到项目文件中。</span><span class="sxs-lookup"><span data-stu-id="29dae-120">Select **OK** and the *packages.config* file will be removed from the project and `<PackageReference>` elements will be added to the project file.</span></span>

<span data-ttu-id="29dae-121">当项目使用 `<PackageReference>` 时，包不会存储在本地“Packages”  文件夹中，而是全局存储。</span><span class="sxs-lookup"><span data-stu-id="29dae-121">When your project uses `<PackageReference>`, packages aren't stored locally in a *Packages* folder, they're stored globally.</span></span> <span data-ttu-id="29dae-122">打开项目文件，删除任何引用到“Packages”  文件夹的 `<Analyzer>` 元素。</span><span class="sxs-lookup"><span data-stu-id="29dae-122">Open the project file and remove any `<Analyzer>` elements that referred to the *Packages* folder.</span></span> <span data-ttu-id="29dae-123">这些分析器会自动包含在 NuGet 包引用中。</span><span class="sxs-lookup"><span data-stu-id="29dae-123">These analyzers are automatically included with the NuGet package references.</span></span>

## <a name="code-access-security"></a><span data-ttu-id="29dae-124">代码访问安全性</span><span class="sxs-lookup"><span data-stu-id="29dae-124">Code Access Security</span></span>

<span data-ttu-id="29dae-125">.NET Core 或 WPF for .NET Core 不支持代码访问安全性 (CAS)。</span><span class="sxs-lookup"><span data-stu-id="29dae-125">Code Access Security (CAS) is not supported by .NET Core or WPF for .NET Core.</span></span> <span data-ttu-id="29dae-126">在完全信任的前提下，处理所有与 CAS 相关的功能。</span><span class="sxs-lookup"><span data-stu-id="29dae-126">All CAS-related functionality is treated under the assumption of full-trust.</span></span> <span data-ttu-id="29dae-127">WPF for .NET Core 会删除与 CAS 相关的代码。</span><span class="sxs-lookup"><span data-stu-id="29dae-127">WPF for .NET Core removes CAS-related code.</span></span> <span data-ttu-id="29dae-128">这些类型的公共 API 表面仍然存在，以确保对这些类型的调用成功。</span><span class="sxs-lookup"><span data-stu-id="29dae-128">The public API surface of these types still exists to ensure that calls into these types succeed.</span></span>

<span data-ttu-id="29dae-129">公开定义的 CAS 相关类型被移出 WPF 程序集，并移入 Core .NET 库程序集中。</span><span class="sxs-lookup"><span data-stu-id="29dae-129">Publicly defined CAS-related types were moved out of the WPF assemblies and into the Core .NET library assemblies.</span></span> <span data-ttu-id="29dae-130">WPF 程序集将类型转发设置为移动类型的新位置。</span><span class="sxs-lookup"><span data-stu-id="29dae-130">The WPF assemblies have type-forwarding set to the new location of the moved types.</span></span>

| <span data-ttu-id="29dae-131">源程序集</span><span class="sxs-lookup"><span data-stu-id="29dae-131">Source assembly</span></span> | <span data-ttu-id="29dae-132">目标程序集</span><span class="sxs-lookup"><span data-stu-id="29dae-132">Target assembly</span></span> | <span data-ttu-id="29dae-133">类型</span><span class="sxs-lookup"><span data-stu-id="29dae-133">Type</span></span>                |
| --------------- | --------------- | ------------------- |
| <span data-ttu-id="29dae-134">*WindowsBase.dll*</span><span class="sxs-lookup"><span data-stu-id="29dae-134">*WindowsBase.dll*</span></span> | <span data-ttu-id="29dae-135">*System.Security.Permissions.dll*</span><span class="sxs-lookup"><span data-stu-id="29dae-135">*System.Security.Permissions.dll*</span></span> | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| <span data-ttu-id="29dae-136">*System.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="29dae-136">*System.Xaml.dll*</span></span> | <span data-ttu-id="29dae-137">*System.Security.Permissions.dll*</span><span class="sxs-lookup"><span data-stu-id="29dae-137">*System.Security.Permissions.dll*</span></span> | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| <span data-ttu-id="29dae-138">*System.Xaml.dll*</span><span class="sxs-lookup"><span data-stu-id="29dae-138">*System.Xaml.dll*</span></span> | <span data-ttu-id="29dae-139">*System.Windows.Extension.dll*</span><span class="sxs-lookup"><span data-stu-id="29dae-139">*System.Windows.Extension.dll*</span></span>    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> <span data-ttu-id="29dae-140">为了最大限度地减少移植摩擦，`XamlAccessLevel` 类型中保留了用于存储和检索与以下属性有关的信息的功能。</span><span class="sxs-lookup"><span data-stu-id="29dae-140">In order to minimize porting friction, the functionality for storing and retrieving information related to the following properties was retained in the `XamlAccessLevel` type.</span></span>
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a><span data-ttu-id="29dae-141">后续步骤</span><span class="sxs-lookup"><span data-stu-id="29dae-141">Next steps</span></span>

- [<span data-ttu-id="29dae-142">了解如何将 .NET Framework WPF 应用移植到 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="29dae-142">Learn how to port a .NET Framework WPF app to .NET Core.</span></span>](convert-project-from-net-framework.md)
