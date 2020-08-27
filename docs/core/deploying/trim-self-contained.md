---
title: 剪裁独立应用程序
description: 了解如何剪裁独立应用以减小其大小。 .NET Core 将运行时与独立发布的应用捆绑在一起，通常包含比所需更多的运行时。
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: 0fde409e9e5911213855ab206368d302b73eebb3
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720119"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="00de9-104">剪裁独立部署和可执行文件</span><span class="sxs-lookup"><span data-stu-id="00de9-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="00de9-105">自 .NET 问世以来，[依赖框架的部署模型](index.md#publish-framework-dependent)是最成功的部署模型。</span><span class="sxs-lookup"><span data-stu-id="00de9-105">The [framework-dependent deployment model](index.md#publish-framework-dependent) has been the most successful deployment model since the inception of .NET.</span></span> <span data-ttu-id="00de9-106">在这种情况下，应用程序开发人员仅将应用程序和第三方程序集捆绑在一起，期望 .NET 运行时库和框架库在客户端计算机中可用。</span><span class="sxs-lookup"><span data-stu-id="00de9-106">In this scenario, the application developer bundles only the application and third-party assemblies with the expectation that the .NET runtime and framework libraries will be available in the client machine.</span></span> <span data-ttu-id="00de9-107">此部署模型仍是 .NET Core 中的主导模型，但在某些情况下，依赖框架的模型并不是最佳模型。</span><span class="sxs-lookup"><span data-stu-id="00de9-107">This deployment model continues to be the dominant one in .NET Core as well but there are some scenarios where the framework-dependent model is not optimal.</span></span> <span data-ttu-id="00de9-108">替代方法是发布[自包含的应用程序](index.md#publish-self-contained)，其中 .NET Core 运行时和框架与应用程序和第三方程序集捆绑在一起。</span><span class="sxs-lookup"><span data-stu-id="00de9-108">The alternative is to publish a [self-contained application](index.md#publish-self-contained), where the .NET Core runtime and framework are bundled together with the application and third-party assemblies.</span></span>

<span data-ttu-id="00de9-109">剪裁自包含部署模型是自包含部署模型的专用版本，该模型已优化以减小部署大小。</span><span class="sxs-lookup"><span data-stu-id="00de9-109">The trim-self-contained deployment model is a specialized version of the self-contained deployment model that is optimized to reduce deployment size.</span></span> <span data-ttu-id="00de9-110">对于一些客户端场景（如 Blazor 应用程序），最大程度地减小部署大小是很重要的要求。</span><span class="sxs-lookup"><span data-stu-id="00de9-110">Minimizing deployment size is a critical requirement for some client-side scenarios like Blazor applications.</span></span> <span data-ttu-id="00de9-111">根据应用程序的复杂性，运行应用程序只需要框架程序集的子集。</span><span class="sxs-lookup"><span data-stu-id="00de9-111">Depending on the complexity of the application, only a subset of the framework assemblies is required to run the application.</span></span> <span data-ttu-id="00de9-112">不需要这些未使用的库部分，可以从打包的应用程序中进行剪裁。</span><span class="sxs-lookup"><span data-stu-id="00de9-112">These unused parts of the library are unnecessary and can be trimmed from the packaged application.</span></span> <span data-ttu-id="00de9-113">但是，由于无法可靠地分析各种有问题的代码模式（主要集中在反射使用），应用程序的生成时间分析可能会导致运行时失败。</span><span class="sxs-lookup"><span data-stu-id="00de9-113">However, there is a risk that the build time analysis of the application can cause failures at runtime, due to not being able to reliably analyze various problematic code patterns (largely centered on reflection use).</span></span> <span data-ttu-id="00de9-114">由于无法保证可靠性，此部署模型仅作为预览功能提供。</span><span class="sxs-lookup"><span data-stu-id="00de9-114">Because reliability can't be guaranteed, this deployment model is offered as a preview feature.</span></span> <span data-ttu-id="00de9-115">生成时间分析引擎向有问题的代码模式的开发人员发出警告，期望这些代码模式将得以修复。</span><span class="sxs-lookup"><span data-stu-id="00de9-115">The build time analysis engine provides warnings to the developer of code patterns that are problematic, with the expectation that these code patterns will be fixed.</span></span> <span data-ttu-id="00de9-116">如果可能，我们建议你使用满足相同要求的代码，将应用程序中的任何运行时反射依赖项移动到生成时间。</span><span class="sxs-lookup"><span data-stu-id="00de9-116">Where possible, we recommend that you move any runtime reflection dependencies in your application to build time by using code that meets the same requirements.</span></span>

<span data-ttu-id="00de9-117">可以通过 TrimMode 配置应用程序的剪裁模式，并使用默认值 (`copyused`) 绑定应用程序中使用的程序集。</span><span class="sxs-lookup"><span data-stu-id="00de9-117">The trim mode for the applications can be configured via the TrimMode and will default (`copyused`) to bundle assemblies that are used in the application.</span></span> <span data-ttu-id="00de9-118">Blazor WebAssembly 应用程序将使用更主动的模式 (`link`) 来剪裁程序集中未使用的代码。</span><span class="sxs-lookup"><span data-stu-id="00de9-118">Blazor WebAssembly applications will use a more aggressive mode (`link`) that will trim unused code within assemblies.</span></span> <span data-ttu-id="00de9-119">如果无法进行完整的依赖项分析，剪裁分析警告会提供代码模式信息。</span><span class="sxs-lookup"><span data-stu-id="00de9-119">Trim analysis warnings give information on code patterns where a full dependency analysis was not possible.</span></span> <span data-ttu-id="00de9-120">这些警告默认会被取消，可以通过将标志 (`SuppressTrimAnalysisWarnings`) 设置为 false 来启用。</span><span class="sxs-lookup"><span data-stu-id="00de9-120">These warnings are suppressed by default and can be turned on by setting the flag, `SuppressTrimAnalysisWarnings`, to false.</span></span> <span data-ttu-id="00de9-121">有关可用剪裁选项的详细信息，请参阅 [ILLinker 页面](https://github.com/mono/linker/blob/master/docs/illink-options.md)。</span><span class="sxs-lookup"><span data-stu-id="00de9-121">More information on the trim options available can be found at the [ILLinker page](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span></span>

> [!NOTE]
> <span data-ttu-id="00de9-122">剪裁是 .NET Core 3.1、5.0 中的实验性功能，只能用于独立发布的应用程序。</span><span class="sxs-lookup"><span data-stu-id="00de9-122">Trimming is an experimental feature in .NET Core 3.1, 5.0 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="00de9-123">防止剪裁程序集</span><span class="sxs-lookup"><span data-stu-id="00de9-123">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="00de9-124">在某些情况下，剪裁功能无法检测到引用。</span><span class="sxs-lookup"><span data-stu-id="00de9-124">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="00de9-125">例如，当应用程序或应用程序引用的库在运行时程序集上使用反射时，都不会直接引用该程序集。</span><span class="sxs-lookup"><span data-stu-id="00de9-125">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="00de9-126">剪裁不知道这些间接引用，并将从已发布文件夹中排除库。</span><span class="sxs-lookup"><span data-stu-id="00de9-126">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="00de9-127">当代码通过反射间接引用程序集时，可以防止使用 `<TrimmerRootAssembly>` 设置剪裁该程序集。</span><span class="sxs-lookup"><span data-stu-id="00de9-127">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="00de9-128">下面的示例演示如何防止剪裁名为 `System.Security` 程序集的程序集：</span><span class="sxs-lookup"><span data-stu-id="00de9-128">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="00de9-129">剪裁应用 - CLI</span><span class="sxs-lookup"><span data-stu-id="00de9-129">Trim your app - CLI</span></span>

<span data-ttu-id="00de9-130">使用 [dotnet publish](../tools/dotnet-publish.md) 命令剪裁应用程序。</span><span class="sxs-lookup"><span data-stu-id="00de9-130">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="00de9-131">发布应用时，请设定以下三个设置：</span><span class="sxs-lookup"><span data-stu-id="00de9-131">When you publish your app, set the following three settings:</span></span>

- <span data-ttu-id="00de9-132">发布为自包含：`--self-contained true`</span><span class="sxs-lookup"><span data-stu-id="00de9-132">Publish as self-contained: `--self-contained true`</span></span>
- <span data-ttu-id="00de9-133">启用剪裁：`p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="00de9-133">Enable trimming: `p:PublishTrimmed=true`</span></span>

<span data-ttu-id="00de9-134">以下示例将 Windows 应用发布为自包含，并剪裁输出。</span><span class="sxs-lookup"><span data-stu-id="00de9-134">The following example publishes an app for Windows as self-contained and trims the output.</span></span>

```xml
<ItemGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <PublishTrimmed>true</PublishTrimmed>
</ItemGroup>
```

<span data-ttu-id="00de9-135">下面的示例在主动剪裁模式下发布应用，在此模式下，将剪裁程序集中未使用的代码，并启用裁边器警告。</span><span class="sxs-lookup"><span data-stu-id="00de9-135">The following example publishes an app in the aggressive trim mode where unused code within assemblies will be trimmed and  trimmer warnings enabled.</span></span>

```xml
<ItemGroup>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</ItemGroup>
```

<span data-ttu-id="00de9-136">有关详细信息，请参阅[使用 .NET Core CLI 发布 .NET Core 应用](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="00de9-136">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="00de9-137">剪裁应用 - Visual Studio</span><span class="sxs-lookup"><span data-stu-id="00de9-137">Trim your app - Visual Studio</span></span>

<span data-ttu-id="00de9-138">Visual Studio 创建可重用的发布配置文件，用于控制应用程序的发布方式。</span><span class="sxs-lookup"><span data-stu-id="00de9-138">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="00de9-139">在“解决方案资源管理器”窗格中，右键单击要发布的项目  。</span><span class="sxs-lookup"><span data-stu-id="00de9-139">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="00de9-140">选择“发布…”  。</span><span class="sxs-lookup"><span data-stu-id="00de9-140">Select **Publish...**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="解决方案资源管理器，其中右键单击菜单突出显示了“发布”选项。":::

    <span data-ttu-id="00de9-142">如果还没有发布配置文件，请按照说明创建一个并选择“文件夹”目标类型  。</span><span class="sxs-lookup"><span data-stu-id="00de9-142">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="00de9-143">选择“编辑”  。</span><span class="sxs-lookup"><span data-stu-id="00de9-143">Choose **Edit**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="带有“编辑”按钮的 Visual Studio 发布配置文件。":::

01. <span data-ttu-id="00de9-145">在“配置文件设置”对话框中，设置以下选项  ：</span><span class="sxs-lookup"><span data-stu-id="00de9-145">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="00de9-146">将“部署模式”设置为“自包含”   。</span><span class="sxs-lookup"><span data-stu-id="00de9-146">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="00de9-147">将“目标运行时”设置为要发布到的平台  。</span><span class="sxs-lookup"><span data-stu-id="00de9-147">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="00de9-148">选择“剪裁未使用的程序集(预览版)”  。</span><span class="sxs-lookup"><span data-stu-id="00de9-148">Select **Trim unused assemblies (in preview)**.</span></span>

    <span data-ttu-id="00de9-149">选择“保存”保存设置并返回到“发布”对话框   。</span><span class="sxs-lookup"><span data-stu-id="00de9-149">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="“配置文件设置”对话框，其中突出显示了“部署模式”、“目标运行时”和“剪裁未使用的程序集”选项。":::

01. <span data-ttu-id="00de9-151">选择“发布”以发布剪裁过的应用  。</span><span class="sxs-lookup"><span data-stu-id="00de9-151">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="00de9-152">有关详细信息，请参阅[使用 Visual Studio 发布 .NET Core 应用](deploy-with-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="00de9-152">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="00de9-153">剪裁应用 - Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="00de9-153">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="00de9-154">Visual Studio for Mac 不提供在发布期间剪裁应用的选项。</span><span class="sxs-lookup"><span data-stu-id="00de9-154">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="00de9-155">你需要按照[剪裁应用 - CLI](#trim-your-app---cli) 部分的说明手动发布。</span><span class="sxs-lookup"><span data-stu-id="00de9-155">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="00de9-156">有关详细信息，请参阅[使用 .NET Core CLI 发布 .NET Core 应用](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="00de9-156">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="00de9-157">请参阅</span><span class="sxs-lookup"><span data-stu-id="00de9-157">See also</span></span>

- <span data-ttu-id="00de9-158">[.NET Core 应用程序部署](index.md)。</span><span class="sxs-lookup"><span data-stu-id="00de9-158">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="00de9-159">[使用 .NET Core CLI 发布 .NET Core 应用](deploy-with-cli.md)。</span><span class="sxs-lookup"><span data-stu-id="00de9-159">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="00de9-160">[使用 Visual Studio 发布 .NET Core 应用](deploy-with-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="00de9-160">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="00de9-161">[dotnet publish 命令](../tools/dotnet-publish.md)。</span><span class="sxs-lookup"><span data-stu-id="00de9-161">[dotnet publish command](../tools/dotnet-publish.md).</span></span>
