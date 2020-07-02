---
title: 安装和管理 SDK 模板 - .NET Core
description: 了解如何在 Windows、Linux 和 macOS 上安装 .NET Core 模板。
author: adegeo
ms.author: adegeo
ms.date: 04/24/2020
zone_pivot_groups: operating-systems-set-one
no-loc:
- dotnet new
- dotnet nuget add source
ms.openlocfilehash: 09acae1409eb0492be10bd3a61b14da5be57c6c7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324496"
---
# <a name="manage-net-project-and-item-templates"></a><span data-ttu-id="6278a-103">管理 .NET 项目和项模板</span><span class="sxs-lookup"><span data-stu-id="6278a-103">Manage .NET project and item templates</span></span>

<span data-ttu-id="6278a-104">.NET Core 提供了一个模板系统，允许用户从 NuGet、NuGet 包文件或文件系统目录中安装或卸载模板。</span><span class="sxs-lookup"><span data-stu-id="6278a-104">.NET Core provides a template system that enables users to install or uninstall templates from NuGet, a NuGet package file, or a file system directory.</span></span> <span data-ttu-id="6278a-105">本文介绍如何通过 .NET Core SDK CLI 管理 .NET Core 模板。</span><span class="sxs-lookup"><span data-stu-id="6278a-105">This article describes how to manage .NET Core templates through the .NET Core SDK CLI.</span></span>

<span data-ttu-id="6278a-106">若要详细了解如何创建模板，请参阅[教程：创建模板](../tutorials/cli-templates-create-item-template.md)。</span><span class="sxs-lookup"><span data-stu-id="6278a-106">For more information about creating templates, see [Tutorial: Create templates](../tutorials/cli-templates-create-item-template.md).</span></span>

## <a name="install-template"></a><span data-ttu-id="6278a-107">安装模板</span><span class="sxs-lookup"><span data-stu-id="6278a-107">Install template</span></span>

<span data-ttu-id="6278a-108">使用 `-i` 参数通过 [dotnet new](../tools/dotnet-new.md) SDK 命令安装模板。</span><span class="sxs-lookup"><span data-stu-id="6278a-108">Templates are installed through the [dotnet new](../tools/dotnet-new.md) SDK command with the `-i` parameter.</span></span> <span data-ttu-id="6278a-109">可以提供模板的 NuGet 包标识符或包含模板文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="6278a-109">You can either provide the NuGet package identifier of a template, or a folder that contains the template files.</span></span>

### <a name="nuget-hosted-package"></a><span data-ttu-id="6278a-110">NuGet 托管包</span><span class="sxs-lookup"><span data-stu-id="6278a-110">NuGet hosted package</span></span>

<span data-ttu-id="6278a-111">.NET CLI 模板上传到 [NuGet](https://www.nuget.org/) 以便进行广泛分发。</span><span class="sxs-lookup"><span data-stu-id="6278a-111">.NET CLI templates are uploaded to [NuGet](https://www.nuget.org/) for wide distribution.</span></span> <span data-ttu-id="6278a-112">还可以从专用源安装模板。</span><span class="sxs-lookup"><span data-stu-id="6278a-112">Templates can also be installed from a private feed.</span></span> <span data-ttu-id="6278a-113">如[本地 NuGet 包](#local-nuget-package)部分所述，可以分发和手动安装 nupkg 模板文件，而不是将模板上传到 NuGet 源。</span><span class="sxs-lookup"><span data-stu-id="6278a-113">Instead of uploading a template to a NuGet feed, *nupkg* template files can be distributed and manually installed, as described in the [Local NuGet package](#local-nuget-package) section.</span></span>

<span data-ttu-id="6278a-114">有关配置 NuGet 源的详细信息，请参阅 [dotnet nuget add source](../tools/dotnet-nuget-add-source.md)。</span><span class="sxs-lookup"><span data-stu-id="6278a-114">For more information about configuring NuGet feeds, see [dotnet nuget add source](../tools/dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="6278a-115">若要从默认 NuGet 源安装模板包，请使用 `dotnet new -i {package-id}` 命令：</span><span class="sxs-lookup"><span data-stu-id="6278a-115">To install a template pack from the default NuGet feed, use the `dotnet new -i {package-id}` command:</span></span>

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates
```

<span data-ttu-id="6278a-116">若要从默认 NuGet 源安装特定版本的模板包，请使用 `dotnet new -i {package-id}::{version}` 命令：</span><span class="sxs-lookup"><span data-stu-id="6278a-116">To install a template pack from the default NuGet feed with a specific version, use the `dotnet new -i {package-id}::{version}` command:</span></span>

```dotnetcli
dotnet new -i Microsoft.DotNet.Web.Spa.ProjectTemplates::2.2.6
```

### <a name="local-nuget-package"></a><span data-ttu-id="6278a-117">本地 NuGet 包</span><span class="sxs-lookup"><span data-stu-id="6278a-117">Local NuGet package</span></span>

<span data-ttu-id="6278a-118">创建模板包后，将生成一个 nupkg 文件。</span><span class="sxs-lookup"><span data-stu-id="6278a-118">When a template pack is created, a *nupkg* file is generated.</span></span> <span data-ttu-id="6278a-119">如果有包含模板的 nupkg 文件，则可以使用 `dotnet new -i {path-to-package}` 命令进行安装：</span><span class="sxs-lookup"><span data-stu-id="6278a-119">If you have a *nupkg* file containing templates, you can install it with the `dotnet new -i {path-to-package}` command:</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\Some.Templates.1.0.0.nupkg
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/Some.Templates.1.0.0.nupkg
```

::: zone-end

### <a name="folder"></a><span data-ttu-id="6278a-120">文件夹</span><span class="sxs-lookup"><span data-stu-id="6278a-120">Folder</span></span>

<span data-ttu-id="6278a-121">从 nupkg 文件安装模板的一个替代方法是使用 `dotnet new -i {folder-path}` 命令直接从文件夹安装模板。</span><span class="sxs-lookup"><span data-stu-id="6278a-121">As an alternative to installing template from a *nupkg* file, you can also install templates from a folder directly with the `dotnet new -i {folder-path}` command.</span></span> <span data-ttu-id="6278a-122">指定的文件夹将被视为找到的任何模板的模板包标识符。</span><span class="sxs-lookup"><span data-stu-id="6278a-122">The folder specified is treated as the template pack identifier for any template found.</span></span> <span data-ttu-id="6278a-123">安装指定文件夹的层次结构中找到的任何模板。</span><span class="sxs-lookup"><span data-stu-id="6278a-123">Any template found in the specified folder's hierarchy is installed.</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -i c:\code\nuget-packages\some-folder\
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -i ~/code/nuget-packages/some-folder/
```

::: zone-end

<span data-ttu-id="6278a-124">在命令中指定的 `{folder-path}` 将成为找到的所有模板的模板包标识符。</span><span class="sxs-lookup"><span data-stu-id="6278a-124">The `{folder-path}` specified on the command becomes the template pack identifier for all templates found.</span></span> <span data-ttu-id="6278a-125">如[模板列表](#list-templates)部分中指定的一样，可以使用 `dotnet new -u` 命令获取已安装的模板列表。</span><span class="sxs-lookup"><span data-stu-id="6278a-125">As specified in the [List templates](#list-templates) section, you can get a list of templates installed with the `dotnet new -u` command.</span></span> <span data-ttu-id="6278a-126">在此示例中，模板包标识符显示为用于安装的文件夹：</span><span class="sxs-lookup"><span data-stu-id="6278a-126">In this example, the template pack identifier is shown as the folder used for install:</span></span>

::: zone pivot="os-windows"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  /home/username/code/templates
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="uninstall-template"></a><span data-ttu-id="6278a-127">卸载模板</span><span class="sxs-lookup"><span data-stu-id="6278a-127">Uninstall template</span></span>

<span data-ttu-id="6278a-128">使用 `-u` 参数通过 [dotnet new](../tools/dotnet-new.md) SDK 命令卸载模板。</span><span class="sxs-lookup"><span data-stu-id="6278a-128">Templates are uninstalled through the [dotnet new](../tools/dotnet-new.md) SDK command with the `-u` parameter.</span></span> <span data-ttu-id="6278a-129">可以提供模板的 NuGet 包标识符或包含模板文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="6278a-129">You can either provide the NuGet package identifier of a template, or a folder that contains the template files.</span></span>

### <a name="nuget-package"></a><span data-ttu-id="6278a-130">NuGet 程序包</span><span class="sxs-lookup"><span data-stu-id="6278a-130">NuGet package</span></span>

<span data-ttu-id="6278a-131">安装 NuGet 模板包后，无论是从 NuGet 源还是从 nupkg 文件安装的，都可以通过引用 NuGet 包标识符将其卸载。</span><span class="sxs-lookup"><span data-stu-id="6278a-131">After a NuGet template pack is installed, either from a NuGet feed or a *nupkg* file, you can uninstall it by referencing the NuGet package identifier.</span></span>

<span data-ttu-id="6278a-132">若要卸载模板包，请使用 `dotnet new -u {package-id}` 命令：</span><span class="sxs-lookup"><span data-stu-id="6278a-132">To uninstall a template pack, use the `dotnet new -u {package-id}` command:</span></span>

```dotnetcli
dotnet new -u Microsoft.DotNet.Web.Spa.ProjectTemplates
```

### <a name="folder"></a><span data-ttu-id="6278a-133">文件夹</span><span class="sxs-lookup"><span data-stu-id="6278a-133">Folder</span></span>

<span data-ttu-id="6278a-134">如果通过[文件夹路径](#folder)安装模板，文件夹路径将成为模板包标识符。</span><span class="sxs-lookup"><span data-stu-id="6278a-134">When templates are installed through a [folder path](#folder), the folder path becomes the template pack identifier.</span></span>

<span data-ttu-id="6278a-135">若要卸载模板包，请使用 `dotnet new -u {package-folder-path}` 命令：</span><span class="sxs-lookup"><span data-stu-id="6278a-135">To uninstall a template pack, use the `dotnet new -u {package-folder-path}` command:</span></span>

::: zone pivot="os-windows"

```dotnetcli
dotnet new -u c:\code\nuget-packages\some-folder
```

::: zone-end

::: zone pivot="os-linux,os-macos"

```dotnetcli
dotnet new -u /home/username/code/templates
```

::: zone-end

## <a name="list-templates"></a><span data-ttu-id="6278a-136">模板列表</span><span class="sxs-lookup"><span data-stu-id="6278a-136">List templates</span></span>

<span data-ttu-id="6278a-137">通过使用不带包标识符的标准卸载命令，可以查看已安装模板的列表以及用于卸载每个模板的命令。</span><span class="sxs-lookup"><span data-stu-id="6278a-137">By using the standard uninstall command without a package identifier, you can see a list of installed templates along with the command that uninstalls each template.</span></span>

```console
dotnet new -u
Template Instantiation Commands for .NET Core CLI

Currently installed items:

... cut to save space ...

  c:\code\nuget-packages\some-folder
    Templates:
      A Template Console Class (templateconsole) C#
      Project for some technology (contosoproject) C#
    Uninstall Command:
      dotnet new -u c:\code\nuget-packages\some-folder
```

## <a name="install-templates-from-other-sdks"></a><span data-ttu-id="6278a-138">从其他 SDK 安装模板</span><span class="sxs-lookup"><span data-stu-id="6278a-138">Install templates from other SDKs</span></span>

<span data-ttu-id="6278a-139">如果已按顺序安装了每个版本的 SDK（例如安装了 SDK 2.0、SDK 2.1 等），则已安装每个 SDK 的模板。</span><span class="sxs-lookup"><span data-stu-id="6278a-139">If you've installed each version of the SDK sequentially, for example you installed SDK 2.0, then SDK 2.1, and so on, you'll have every SDK's templates installed.</span></span> <span data-ttu-id="6278a-140">但是，如果从更高版本的 SDK 版本（如 3.1）开始，则将仅包括 [LTS（长期支持）版本](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)的模板（在发布 SDK 3.1 版本时，为 SDK 2.1 和 SDK 3.1）。</span><span class="sxs-lookup"><span data-stu-id="6278a-140">However, if you start with a later SDK version, like 3.1, only the templates for [LTS (long term support) releases](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) are included, which at the time of the SDK 3.1 release is SDK 2.1 and SDK 3.1.</span></span> <span data-ttu-id="6278a-141">不包含任何其他版本的模板。</span><span class="sxs-lookup"><span data-stu-id="6278a-141">Templates for any other release aren't included.</span></span>

<span data-ttu-id="6278a-142">NuGet 上提供了 .NET Core 模板，你可以像安装任何其他模板一样安装它们。</span><span class="sxs-lookup"><span data-stu-id="6278a-142">The .NET Core templates are available on NuGet, and you can install them like any other template.</span></span> <span data-ttu-id="6278a-143">有关详细信息，请参阅[安装 NuGet 托管包](#nuget-hosted-package)。</span><span class="sxs-lookup"><span data-stu-id="6278a-143">For more information, see [Install NuGet hosted package](#nuget-hosted-package).</span></span>

| <span data-ttu-id="6278a-144">SDK</span><span class="sxs-lookup"><span data-stu-id="6278a-144">SDK</span></span>              | <span data-ttu-id="6278a-145">NuGet 包标识符</span><span class="sxs-lookup"><span data-stu-id="6278a-145">NuGet Package Identifier</span></span>                                                                                                      |
|------------------|-------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6278a-146">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6278a-146">.NET Core 2.1</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.1) |
| <span data-ttu-id="6278a-147">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="6278a-147">.NET Core 2.2</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.2.2) |
| <span data-ttu-id="6278a-148">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6278a-148">.NET Core 3.0</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.0) |
| <span data-ttu-id="6278a-149">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="6278a-149">.NET Core 3.1</span></span>    | [`Microsoft.DotNet.Common.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Common.ProjectTemplates.3.1) |
| <span data-ttu-id="6278a-150">ASP.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6278a-150">ASP.NET Core 2.1</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.2.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.1)       |
| <span data-ttu-id="6278a-151">ASP.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="6278a-151">ASP.NET Core 2.2</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.2.2`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.2.2)       |
| <span data-ttu-id="6278a-152">ASP.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6278a-152">ASP.NET Core 3.0</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.3.0`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.0)       |
| <span data-ttu-id="6278a-153">ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="6278a-153">ASP.NET Core 3.1</span></span> | [`Microsoft.DotNet.Web.ProjectTemplates.3.1`](https://www.nuget.org/packages/Microsoft.DotNet.Web.ProjectTemplates.3.1)       |

<span data-ttu-id="6278a-154">例如，.NET Core SDK 包含面向 .NET Core 2.1 和 .NET Core 3.1 的控制台应用的模板。</span><span class="sxs-lookup"><span data-stu-id="6278a-154">For example, the .NET Core SDK includes templates for a console app targeting .NET Core 2.1 and .NET Core 3.1.</span></span> <span data-ttu-id="6278a-155">如果要面向 .NET Core 3.0，则需要安装 3.0 模板。</span><span class="sxs-lookup"><span data-stu-id="6278a-155">If you wanted to target .NET Core 3.0, you would need to install the 3.0 templates.</span></span>

01. <span data-ttu-id="6278a-156">尝试创建面向 .NET Core 3.0 的应用。</span><span class="sxs-lookup"><span data-stu-id="6278a-156">Try creating an app that targets .NET Core 3.0.</span></span>

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    <span data-ttu-id="6278a-157">如果看到错误消息，则需要安装模板。</span><span class="sxs-lookup"><span data-stu-id="6278a-157">If you see an error message, you need to install the templates.</span></span>

    > <span data-ttu-id="6278a-158">找不到与输入匹配的已安装模板，正在联机搜索匹配的模板…</span><span class="sxs-lookup"><span data-stu-id="6278a-158">Couldn't find an installed template that matches the input, searching online for one that does...</span></span>

01. <span data-ttu-id="6278a-159">安装 .NET Core 3.0 项目模板。</span><span class="sxs-lookup"><span data-stu-id="6278a-159">Install the .NET Core 3.0 project templates.</span></span>

    ```dotnetcli
    dotnet new -i Microsoft.DotNet.Common.ProjectTemplates.3.0
    ```

01. <span data-ttu-id="6278a-160">再次尝试创建应用。</span><span class="sxs-lookup"><span data-stu-id="6278a-160">Try creating the app a second time.</span></span>

    ```dotnetcli
    dotnet new console --framework netcoreapp3.0
    ```

    <span data-ttu-id="6278a-161">应该会看到一条消息，指示项目已创建。</span><span class="sxs-lookup"><span data-stu-id="6278a-161">And you should see a message indicating the project was created.</span></span>

    > <span data-ttu-id="6278a-162">“控制台应用程序”模板已成功创建。</span><span class="sxs-lookup"><span data-stu-id="6278a-162">The template "Console Application" was created successfully.</span></span>
    >
    > <span data-ttu-id="6278a-163">正在处理创建后操作…正在 path-to-project-file.csproj 上运行“dotnet restore”…正在确定要还原的项目…path-to-project-file.csproj 的还原完成时间为 1.05 秒。</span><span class="sxs-lookup"><span data-stu-id="6278a-163">Processing post-creation actions... Running 'dotnet restore' on path-to-project-file.csproj... Determining projects to restore... Restore completed in 1.05 sec for path-to-project-file.csproj.</span></span>
    >
    > <span data-ttu-id="6278a-164">还原成功。</span><span class="sxs-lookup"><span data-stu-id="6278a-164">Restore succeeded.</span></span>

## <a name="see-also"></a><span data-ttu-id="6278a-165">请参阅</span><span class="sxs-lookup"><span data-stu-id="6278a-165">See also</span></span>

- [<span data-ttu-id="6278a-166">教程：创建项模板</span><span class="sxs-lookup"><span data-stu-id="6278a-166">Tutorial: Create an item template</span></span>](../tutorials/cli-templates-create-item-template.md)
- [dotnet new](../tools/dotnet-new.md)
- [dotnet nuget add source](../tools/dotnet-nuget-add-source.md)
