---
title: 使用 Visual Studio for Mac 发布 .NET Core 控制台应用程序
description: 发布应用程序会创建运行 .NET Core 应用程序所需的一组文件。
ms.date: 06/08/2020
ms.openlocfilehash: ec6b867f145ffdea491187de3745149f2cebd8dd
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867537"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="c1373-103">教程：使用 Visual Studio for Mac 发布 .NET Core 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="c1373-103">Tutorial: Publish a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="c1373-104">本教程演示如何发布控制台应用，以便其他用户可以运行它。</span><span class="sxs-lookup"><span data-stu-id="c1373-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="c1373-105">发布应用程序会创建运行应用程序所需的一组文件。</span><span class="sxs-lookup"><span data-stu-id="c1373-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="c1373-106">若要部署文件，请将文件复制到目标计算机。</span><span class="sxs-lookup"><span data-stu-id="c1373-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c1373-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="c1373-107">Prerequisites</span></span>

- <span data-ttu-id="c1373-108">本教程适用于在[使用 Visual Studio for Mac 创建 .NET Core 控制台应用程序](with-visual-studio-mac.md)中创建的控制台应用。</span><span class="sxs-lookup"><span data-stu-id="c1373-108">This tutorial works with the console app that you create in [Create a .NET Core console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="c1373-109">发布应用</span><span class="sxs-lookup"><span data-stu-id="c1373-109">Publish the app</span></span>

1. <span data-ttu-id="c1373-110">启动 Visual Studio for Mac。</span><span class="sxs-lookup"><span data-stu-id="c1373-110">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="c1373-111">打开在[使用 Visual Studio for Mac 创建 .NET Core 控制台应用程序](with-visual-studio-mac.md)中创建的 HelloWorld 项目。</span><span class="sxs-lookup"><span data-stu-id="c1373-111">Open the HelloWorld project that you created in [Create a .NET Core console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="c1373-112">请确保 Visual Studio 生成的是应用程序的发布版本。</span><span class="sxs-lookup"><span data-stu-id="c1373-112">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="c1373-113">必要时，将工具栏上的生成配置设置从“调试”更改为“发布”。</span><span class="sxs-lookup"><span data-stu-id="c1373-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/toolbar-release.png" alt-text="选定发布版本的 Visual Studio 工具栏":::

1. <span data-ttu-id="c1373-115">从主菜单中，选择“生成” > “发布到文件夹...”。</span><span class="sxs-lookup"><span data-stu-id="c1373-115">From the main menu, choose **Build** > **Publish to Folder...**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-context-menu.png" alt-text="Visual Studio 发布上下文菜单":::

1. <span data-ttu-id="c1373-117">在“发布到文件夹”对话框中，选择“发布” 。</span><span class="sxs-lookup"><span data-stu-id="c1373-117">In the **Publish to Folder** dialog, select **Publish**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-to-folder-dialog.png" alt-text="Visual Studio“发布到文件夹”对话框":::

   <span data-ttu-id="c1373-119">此时会打开发布文件夹，其中显示已创建的文件。</span><span class="sxs-lookup"><span data-stu-id="c1373-119">The publish folder opens, showing the files that were created.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-folder.png" alt-text="发布文件夹":::

1. <span data-ttu-id="c1373-121">选择齿轮图标，并从上下文菜单中选择“将“发布”复制为路径名称”。</span><span class="sxs-lookup"><span data-stu-id="c1373-121">Select the gear icon, and select **Copy "publish" as Pathname** from the context menu.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/copy-path.png" alt-text="将路径复制到发布文件夹":::

## <a name="inspect-the-files"></a><span data-ttu-id="c1373-123">检查文件</span><span class="sxs-lookup"><span data-stu-id="c1373-123">Inspect the files</span></span>

<span data-ttu-id="c1373-124">发布过程中会创建依赖于框架的部署，在此类部署中，已发布的应用程序在已安装 .NET Core 运行时的计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="c1373-124">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="c1373-125">用户可以通过从命令提示符运行 `dotnet HelloWorld.dll` 命令来运行发布的应用。</span><span class="sxs-lookup"><span data-stu-id="c1373-125">Users can run the published app by running the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="c1373-126">如上图所示，已发布的输出包括以下文件：</span><span class="sxs-lookup"><span data-stu-id="c1373-126">As the preceding image shows, the published output includes the following files:</span></span>

* <span data-ttu-id="c1373-127">HelloWorld.deps.json</span><span class="sxs-lookup"><span data-stu-id="c1373-127">*HelloWorld.deps.json*</span></span>

  <span data-ttu-id="c1373-128">这是应用程序的运行时依赖项文件。</span><span class="sxs-lookup"><span data-stu-id="c1373-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="c1373-129">它定义了运行应用程序所需的 .NET Core 组件和库（包括包含该应用程序的动态链接库）。</span><span class="sxs-lookup"><span data-stu-id="c1373-129">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="c1373-130">有关详细信息，请参阅[运行时配置文件](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="c1373-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

* <span data-ttu-id="c1373-131">HelloWorld.dll</span><span class="sxs-lookup"><span data-stu-id="c1373-131">*HelloWorld.dll*</span></span>

   <span data-ttu-id="c1373-132">这是应用程序的[依赖于框架的部署](../deploying/deploy-with-cli.md#framework-dependent-deployment)版本。</span><span class="sxs-lookup"><span data-stu-id="c1373-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="c1373-133">若要执行此动态链接库，请在命令提示符处输入 `dotnet HelloWorld.dll`。</span><span class="sxs-lookup"><span data-stu-id="c1373-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="c1373-134">这种运行应用的方法适用于安装了 .NET Core 运行时的任何平台。</span><span class="sxs-lookup"><span data-stu-id="c1373-134">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

* <span data-ttu-id="c1373-135">HelloWorld.pdb（对于部署是可选的）</span><span class="sxs-lookup"><span data-stu-id="c1373-135">*HelloWorld.pdb* (optional for deployment)</span></span>

   <span data-ttu-id="c1373-136">这是调试符号文件。</span><span class="sxs-lookup"><span data-stu-id="c1373-136">This is the debug symbols file.</span></span> <span data-ttu-id="c1373-137">尽管应在需要调试应用程序的已发布版本时保存此文件，但无需将此文件与应用程序一起部署。</span><span class="sxs-lookup"><span data-stu-id="c1373-137">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

* <span data-ttu-id="c1373-138">HelloWorld.runtimeconfig.json</span><span class="sxs-lookup"><span data-stu-id="c1373-138">*HelloWorld.runtimeconfig.json*</span></span>

   <span data-ttu-id="c1373-139">这是应用程序的运行时配置文件。</span><span class="sxs-lookup"><span data-stu-id="c1373-139">This is the application's run-time configuration file.</span></span> <span data-ttu-id="c1373-140">它标识用于运行应用程序的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="c1373-140">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="c1373-141">还可向其添加配置选项。</span><span class="sxs-lookup"><span data-stu-id="c1373-141">You can also add configuration options to it.</span></span> <span data-ttu-id="c1373-142">有关详细信息，请参阅 [.NET Core 运行时配置设置](../run-time-config/index.md#runtimeconfigjson)。</span><span class="sxs-lookup"><span data-stu-id="c1373-142">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="c1373-143">运行已发布的应用</span><span class="sxs-lookup"><span data-stu-id="c1373-143">Run the published app</span></span>

1. <span data-ttu-id="c1373-144">打开终端并导航到发布文件夹。</span><span class="sxs-lookup"><span data-stu-id="c1373-144">Open a terminal and navigate to the *publish* folder.</span></span> <span data-ttu-id="c1373-145">为此，请输入 `cd`，然后粘贴前面复制的路径。</span><span class="sxs-lookup"><span data-stu-id="c1373-145">To do that, enter `cd` and then paste the path that you copied earlier.</span></span> <span data-ttu-id="c1373-146">例如：</span><span class="sxs-lookup"><span data-stu-id="c1373-146">For example:</span></span>

   ```console
   cd ~/Projects/HelloWorld/HelloWorld/bin/Release/netcoreapp3.1/publish/
   ```

1. <span data-ttu-id="c1373-147">使用 `dotnet` 命令运行应用：</span><span class="sxs-lookup"><span data-stu-id="c1373-147">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="c1373-148">输入 `dotnet HelloWorld.dll`，然后按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="c1373-148">Enter `dotnet HelloWorld.dll` and press <kbd>enter</kbd>.</span></span>

   1. <span data-ttu-id="c1373-149">输入一个名字以响应提示，并按任意键退出。</span><span class="sxs-lookup"><span data-stu-id="c1373-149">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c1373-150">其他资源</span><span class="sxs-lookup"><span data-stu-id="c1373-150">Additional resources</span></span>

- [<span data-ttu-id="c1373-151">.NET Core 应用程序部署</span><span class="sxs-lookup"><span data-stu-id="c1373-151">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="c1373-152">后续步骤</span><span class="sxs-lookup"><span data-stu-id="c1373-152">Next steps</span></span>

<span data-ttu-id="c1373-153">在本教程中，你发布了一个控制台应用。</span><span class="sxs-lookup"><span data-stu-id="c1373-153">In this tutorial, you published a console app.</span></span> <span data-ttu-id="c1373-154">在下一教程中，你将创建类库。</span><span class="sxs-lookup"><span data-stu-id="c1373-154">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1373-155">使用 Visual Studio for Mac 创建 .NET Standard 库</span><span class="sxs-lookup"><span data-stu-id="c1373-155">Create a .NET Standard library using Visual Studio for Mac</span></span>](library-with-visual-studio-mac.md)
