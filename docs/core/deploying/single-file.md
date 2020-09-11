---
title: 单文件应用程序
description: 了解单文件应用程序的本质以及应考虑使用此应用程序部署模型的原因。
author: lakshanf
ms.author: lakshanf
ms.date: 08/28/2020
ms.openlocfilehash: 795ea98a9fd9d672b199eb2d9b24151340ef8246
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495742"
---
# <a name="single-file-deployment-and-executable"></a><span data-ttu-id="9ce50-103">单文件部署和可执行文件</span><span class="sxs-lookup"><span data-stu-id="9ce50-103">Single file deployment and executable</span></span>

<span data-ttu-id="9ce50-104">通过将所有依赖应用程序的文件捆绑到一个二进制文件中，为应用程序开发人员提供一个具有吸引力的选项，那就是将应用程序作为单个文件进行部署和分发。</span><span class="sxs-lookup"><span data-stu-id="9ce50-104">Bundling all application-dependent files into a single binary provides an application developer with the attractive option to deploy and distribute the application as a single file.</span></span> <span data-ttu-id="9ce50-105">此部署模型从 .NET Core 3.0 开始提供，在 .NET 5.0 中进行了增强。</span><span class="sxs-lookup"><span data-stu-id="9ce50-105">This deployment model has been available since .NET Core 3.0 and has been enhanced in .NET 5.0.</span></span> <span data-ttu-id="9ce50-106">之前在 .NET Core 3.0 中，当用户运行单文件应用时，.NET Core 主机先将所有文件提取到一个临时目录，然后再运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="9ce50-106">Previously in .NET Core 3.0, when a user runs your single-file app, .NET Core host first extracts all files to a temporary directory before running the application.</span></span> <span data-ttu-id="9ce50-107">.NET 5.0 改进了这一体验，它可直接运行代码，无需从应用中提取文件。</span><span class="sxs-lookup"><span data-stu-id="9ce50-107">.NET 5.0 improves this experience by directly running the code without the need to extract the files from the app.</span></span>

<span data-ttu-id="9ce50-108">单文件部署可用于[依赖框架的部署模型](index.md#publish-framework-dependent)和[独立应用程序](index.md#publish-self-contained)。</span><span class="sxs-lookup"><span data-stu-id="9ce50-108">Single File deployment is available for both the [framework-dependent deployment model](index.md#publish-framework-dependent) and [self-contained applications](index.md#publish-self-contained).</span></span> <span data-ttu-id="9ce50-109">独立应用程序中单个文件的大小很大，因为它包含运行时和框架库。</span><span class="sxs-lookup"><span data-stu-id="9ce50-109">The size of the single file in a self-contained application will be large since it will include the runtime and the framework libraries.</span></span> <span data-ttu-id="9ce50-110">单文件部署选项可与 [ReadyToRun](../tools/dotnet-publish.md) 和 [Trim（.NET 5.0 中的一项试验功能）](trim-self-contained.md)发布选项结合使用。</span><span class="sxs-lookup"><span data-stu-id="9ce50-110">The single file deployment option can be combined with [ReadyToRun](../tools/dotnet-publish.md) and [Trim (an experimental feature in .NET 5.0)](trim-self-contained.md) publish options.</span></span>

<span data-ttu-id="9ce50-111">使用单文件时需要注意一些事项，首先是使用路径信息来查找相对于应用程序的位置的文件。</span><span class="sxs-lookup"><span data-stu-id="9ce50-111">There are some caveats that you need to be aware for single-file use, first of which is the use of path information to locate a file relative to the location of your application.</span></span> <span data-ttu-id="9ce50-112"><xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> API 将返回空字符串，这是从内存中加载的程序集的默认行为。</span><span class="sxs-lookup"><span data-stu-id="9ce50-112">The <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> API will return an empty string, which is the default behavior for assemblies loaded from memory.</span></span> <span data-ttu-id="9ce50-113">编译器将在生成时提供此 API 的警告，提醒开发人员注意特定行为。</span><span class="sxs-lookup"><span data-stu-id="9ce50-113">The compiler will give a warning for this API during build time to alert the developer to the specific behavior.</span></span> <span data-ttu-id="9ce50-114">如果需要应用程序目录的路径，则 <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> API 将返回 AppHost（单文件捆绑包本身）所在的目录。</span><span class="sxs-lookup"><span data-stu-id="9ce50-114">If the path to the application directory is needed, the <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> API will return the directory where the AppHost (the single-file bundle itself) resides.</span></span> <span data-ttu-id="9ce50-115">托管的 C++ 应用程序不太适合进行单文件部署，建议使用 C# 编写应用程序来使单文件兼容。</span><span class="sxs-lookup"><span data-stu-id="9ce50-115">Managed C++ applications aren't well suited for single-file deployment and we recommend that you write applications in C# to be single-file compatible.</span></span>

<span data-ttu-id="9ce50-116">默认情况下，单文件不捆绑本机库。</span><span class="sxs-lookup"><span data-stu-id="9ce50-116">Single-file doesn't bundle native libraries by default.</span></span> <span data-ttu-id="9ce50-117">在 Linux 上，我们将运行时预链接到捆绑包中，并且仅将应用程序本机库部署到单文件应用所在的目录中。</span><span class="sxs-lookup"><span data-stu-id="9ce50-117">On Linux, we prelink the runtime into the bundle and only application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="9ce50-118">在 Windows 上，我们仅预链接托管代码，而且运行时库和应用程序本机库都部署到单文件应用所在的目录中。</span><span class="sxs-lookup"><span data-stu-id="9ce50-118">On Windows, we prelink only the hosting code and both the runtime and application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="9ce50-119">目的是确保提供良好的调试体验，这要求将本机文件从单文件中排除。</span><span class="sxs-lookup"><span data-stu-id="9ce50-119">This is to ensure a good debugging experience, which requires native files to be excluded from the single file.</span></span> <span data-ttu-id="9ce50-120">可选择设置标志 `IncludeNativeLibrariesForSelfExtract`，从而在单文件捆绑包中包含本机库，但在运行单文件应用程序时，这些文件将被提取到客户端计算机上的临时目录中。</span><span class="sxs-lookup"><span data-stu-id="9ce50-120">There is an option to set a flag, `IncludeNativeLibrariesForSelfExtract`, to include native libraries in the single file bundle, but these files will be extracted to a temporary directory in the client machine when the single file application is run.</span></span>

## <a name="exclude-files-from-being-embedded"></a><span data-ttu-id="9ce50-121">将文件排除在嵌入之外</span><span class="sxs-lookup"><span data-stu-id="9ce50-121">Exclude files from being embedded</span></span>

<span data-ttu-id="9ce50-122">通过设置以下元数据，可明确指定不在单文件中嵌入某些文件：</span><span class="sxs-lookup"><span data-stu-id="9ce50-122">Certain files can be explicitly excluded from being embedded in the single-file by setting following metadata:</span></span>

```xml
<ExcludeFromSingleFile>true</ExcludeFromSingleFile>
```

<span data-ttu-id="9ce50-123">例如，若要将某些文件放置在发布目录中，但不将它们捆绑到单文件中：</span><span class="sxs-lookup"><span data-stu-id="9ce50-123">For example, to place some files in the publish directory but not bundle them in the single-file:</span></span>

```xml
<ItemGroup>
  <Content Update="Plugin.dll">
    <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
    <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
  </Content>
</ItemGroup>
```

## <a name="publish-a-single-file-app---cli"></a><span data-ttu-id="9ce50-124">发布单文件应用 - CLI</span><span class="sxs-lookup"><span data-stu-id="9ce50-124">Publish a single file app - CLI</span></span>

<span data-ttu-id="9ce50-125">使用 [dotnet publish](../tools/dotnet-publish.md) 命令发布单文件应用程序。</span><span class="sxs-lookup"><span data-stu-id="9ce50-125">Publish a single file application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="9ce50-126">发布应用时，请设置以下属性：</span><span class="sxs-lookup"><span data-stu-id="9ce50-126">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="9ce50-127">针对特定运行时进行发布：`-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="9ce50-127">Publish for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="9ce50-128">作为单个文件进行发布：`-p:PublishSingleFile=true`</span><span class="sxs-lookup"><span data-stu-id="9ce50-128">Publish as a single-file: `-p:PublishSingleFile=true`</span></span>

<span data-ttu-id="9ce50-129">以下示例将 Windows 应用作为独立的单文件应用程序发布。</span><span class="sxs-lookup"><span data-stu-id="9ce50-129">The following example publishes an app for Windows as a self-contained single file application.</span></span>

```dotnetcli
dotnet publish -r win-x64 -p:PublishSingleFile=true --self-contained true
```

<span data-ttu-id="9ce50-130">以下示例将 Linux 应用作为依赖框架的单文件应用程序发布。</span><span class="sxs-lookup"><span data-stu-id="9ce50-130">The following example publishes an app for Linux as a framework dependent single file application.</span></span>

```dotnetcli
dotnet publish -r linux-x64 -p:PublishSingleFile=true --self-contained false
```

<span data-ttu-id="9ce50-131">有关详细信息，请参阅[使用 .NET Core CLI 发布 .NET Core 应用](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="9ce50-131">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio"></a><span data-ttu-id="9ce50-132">发布单文件应用 - Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9ce50-132">Publish a single file app - Visual Studio</span></span>

<span data-ttu-id="9ce50-133">Visual Studio 创建可重用的发布配置文件，用于控制应用程序的发布方式。</span><span class="sxs-lookup"><span data-stu-id="9ce50-133">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="9ce50-134">在“解决方案资源管理器”窗格中，右键单击要发布的项目  。</span><span class="sxs-lookup"><span data-stu-id="9ce50-134">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="9ce50-135">选择“发布”。</span><span class="sxs-lookup"><span data-stu-id="9ce50-135">Select **Publish**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-solution-explorer.png" alt-text="解决方案资源管理器，其中右键单击菜单突出显示了“发布”选项。":::

    <span data-ttu-id="9ce50-137">如果还没有发布配置文件，请按照说明创建一个并选择“文件夹”目标类型  。</span><span class="sxs-lookup"><span data-stu-id="9ce50-137">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="9ce50-138">选择“编辑”  。</span><span class="sxs-lookup"><span data-stu-id="9ce50-138">Choose **Edit**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-edit-settings.png" alt-text="带有“编辑”按钮的 Visual Studio 发布配置文件。":::

01. <span data-ttu-id="9ce50-140">在“配置文件设置”对话框中，设置以下选项  ：</span><span class="sxs-lookup"><span data-stu-id="9ce50-140">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="9ce50-141">将“部署模式”设置为“自包含”   。</span><span class="sxs-lookup"><span data-stu-id="9ce50-141">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="9ce50-142">将“目标运行时”设置为要发布到的平台  。</span><span class="sxs-lookup"><span data-stu-id="9ce50-142">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="9ce50-143">选择“生成单个文件”。</span><span class="sxs-lookup"><span data-stu-id="9ce50-143">Select **Produce single file**.</span></span>

    <span data-ttu-id="9ce50-144">选择“保存”保存设置并返回到“发布”对话框   。</span><span class="sxs-lookup"><span data-stu-id="9ce50-144">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-single-file-properties.png" alt-text="“配置文件设置”对话框，其中突出显示了“部署模式”、“目标运行时”和“单个文件”选项。":::

01. <span data-ttu-id="9ce50-146">选择“发布”，将应用作为单个文件发布。</span><span class="sxs-lookup"><span data-stu-id="9ce50-146">Choose **Publish** to publish your app as a single file.</span></span>

<span data-ttu-id="9ce50-147">有关详细信息，请参阅[使用 Visual Studio 发布 .NET Core 应用](deploy-with-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="9ce50-147">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio-for-mac"></a><span data-ttu-id="9ce50-148">发布单文件应用 - Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="9ce50-148">Publish a single file app - Visual Studio for Mac</span></span>

<span data-ttu-id="9ce50-149">Visual Studio for Mac 不提供将应用作为单个文件发布的选项。</span><span class="sxs-lookup"><span data-stu-id="9ce50-149">Visual Studio for Mac doesn't provide options to publish your app as a single file.</span></span> <span data-ttu-id="9ce50-150">你需要按照[发布单文件应用 - CLI](#publish-a-single-file-app---cli) 部分中的说明手动发布。</span><span class="sxs-lookup"><span data-stu-id="9ce50-150">You'll need to publish manually by following the instructions from the [Publish a single file app - CLI](#publish-a-single-file-app---cli) section.</span></span> <span data-ttu-id="9ce50-151">有关详细信息，请参阅[使用 .NET Core CLI 发布 .NET Core 应用](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="9ce50-151">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9ce50-152">请参阅</span><span class="sxs-lookup"><span data-stu-id="9ce50-152">See also</span></span>

- <span data-ttu-id="9ce50-153">[.NET Core 应用程序部署](index.md)。</span><span class="sxs-lookup"><span data-stu-id="9ce50-153">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="9ce50-154">[使用 .NET Core CLI 发布 .NET Core 应用](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="9ce50-154">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="9ce50-155">[使用 Visual Studio 发布 .NET Core 应用](deploy-with-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="9ce50-155">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="9ce50-156">[`dotnet publish` 命令](../tools/dotnet-publish.md)。</span><span class="sxs-lookup"><span data-stu-id="9ce50-156">[`dotnet publish` command](../tools/dotnet-publish.md).</span></span>
