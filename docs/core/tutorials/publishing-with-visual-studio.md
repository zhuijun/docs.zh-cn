---
title: 使用 Visual Studio 发布 .NET Core 控制台应用程序
description: 发布应用程序会创建运行 .NET Core 应用程序所需的一组文件。
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 44646a307d230db395b55b9dec5acfd168605940
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701279"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="15d4a-103">教程：使用 Visual Studio 发布 .NET Core 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="15d4a-103">Tutorial: Publish a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="15d4a-104">本教程演示如何发布控制台应用，以便其他用户可以运行它。</span><span class="sxs-lookup"><span data-stu-id="15d4a-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="15d4a-105">发布应用程序会创建运行应用程序所需的一组文件。</span><span class="sxs-lookup"><span data-stu-id="15d4a-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="15d4a-106">若要部署文件，请将文件复制到目标计算机。</span><span class="sxs-lookup"><span data-stu-id="15d4a-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="15d4a-107">先决条件</span><span class="sxs-lookup"><span data-stu-id="15d4a-107">Prerequisites</span></span>

- <span data-ttu-id="15d4a-108">本教程适用于[在 Visual Studio 2019 中创建 .NET Core 控制台应用程序](with-visual-studio.md)中创建的控制台应用。</span><span class="sxs-lookup"><span data-stu-id="15d4a-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="15d4a-109">发布应用</span><span class="sxs-lookup"><span data-stu-id="15d4a-109">Publish the app</span></span>

1. <span data-ttu-id="15d4a-110">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="15d4a-110">Start Visual Studio.</span></span>

1. <span data-ttu-id="15d4a-111">打开按照[在 Visual Studio 中创建 .NET Core 控制台应用程序](with-visual-studio.md)创建的 HelloWorld 项目。</span><span class="sxs-lookup"><span data-stu-id="15d4a-111">Open the *HelloWorld* project that you created in [Create a .NET Core console application in Visual Studio](with-visual-studio.md).</span></span>

1. <span data-ttu-id="15d4a-112">请确保 Visual Studio 正在使用“发布”生成配置。</span><span class="sxs-lookup"><span data-stu-id="15d4a-112">Make sure that Visual Studio is using the Release build configuration.</span></span> <span data-ttu-id="15d4a-113">必要时，将工具栏上的生成配置设置从“调试”更改为“发布”。</span><span class="sxs-lookup"><span data-stu-id="15d4a-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![选定发布版本的 Visual Studio 工具栏](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="15d4a-115">右键单击“HelloWorld”项目（而不是 HelloWorld 解决方案），然后选择菜单中的“发布”。</span><span class="sxs-lookup"><span data-stu-id="15d4a-115">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span>

   ![Visual Studio 发布上下文菜单](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="15d4a-117">在“发布”页的“目标”选项卡上，选择“文件夹”，然后选择“下一步”   。</span><span class="sxs-lookup"><span data-stu-id="15d4a-117">On the **Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   ![在 Visual Studio 中选择发布目标](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="15d4a-119">在“发布”页的“位置”选项卡上，选择“完成”  。</span><span class="sxs-lookup"><span data-stu-id="15d4a-119">On the **Location** tab of the **Publish** page, select **Finish**.</span></span>

   ![Visual Studio“发布”页的“位置”选项卡](media/publishing-with-visual-studio/publish-page-loc-tab.png)

1. <span data-ttu-id="15d4a-121">在“发布”窗口的“发布”选项卡上，选择“发布”  。</span><span class="sxs-lookup"><span data-stu-id="15d4a-121">On the **Publish** tab of the **Publish** window, select **Publish**.</span></span>

   ![Visual Studio 发布窗口](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="15d4a-123">检查文件</span><span class="sxs-lookup"><span data-stu-id="15d4a-123">Inspect the files</span></span>

<span data-ttu-id="15d4a-124">默认情况下，发布过程中会创建依赖于框架的部署，在此类部署中，已发布的应用程序在已安装 .NET Core 运行时的计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="15d4a-124">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="15d4a-125">用户可以通过双击可执行文件或从命令提示符发出 `dotnet HelloWorld.dll` 命令来运行发布的应用。</span><span class="sxs-lookup"><span data-stu-id="15d4a-125">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="15d4a-126">在下面的步骤中，查看由发布过程创建的文件。</span><span class="sxs-lookup"><span data-stu-id="15d4a-126">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="15d4a-127">在“解决方案资源管理器”中，选择“显示所有文件” 。</span><span class="sxs-lookup"><span data-stu-id="15d4a-127">In **Solution Explorer**, select **Show all files**.</span></span>

1. <span data-ttu-id="15d4a-128">在项目文件夹中，展开 bin/Release/netcoreapp3.1/publish。</span><span class="sxs-lookup"><span data-stu-id="15d4a-128">In the project folder, expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="显示已发布文件的解决方案资源管理器":::

   <span data-ttu-id="15d4a-130">如下图所示，已发布的输出包括以下文件：</span><span class="sxs-lookup"><span data-stu-id="15d4a-130">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="15d4a-131">HelloWorld.deps.json</span><span class="sxs-lookup"><span data-stu-id="15d4a-131">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="15d4a-132">这是应用程序的运行时依赖项文件。</span><span class="sxs-lookup"><span data-stu-id="15d4a-132">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="15d4a-133">它定义了运行应用程序所需的 .NET Core 组件和库（包括包含该应用程序的动态链接库）。</span><span class="sxs-lookup"><span data-stu-id="15d4a-133">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="15d4a-134">有关详细信息，请参阅[运行时配置文件](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="15d4a-134">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="15d4a-135">HelloWorld.dll</span><span class="sxs-lookup"><span data-stu-id="15d4a-135">*HelloWorld.dll*</span></span>

      <span data-ttu-id="15d4a-136">这是应用程序的[依赖于框架的部署](../deploying/deploy-with-cli.md#framework-dependent-deployment)版本。</span><span class="sxs-lookup"><span data-stu-id="15d4a-136">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="15d4a-137">若要执行此动态链接库，请在命令提示符处输入 `dotnet HelloWorld.dll`。</span><span class="sxs-lookup"><span data-stu-id="15d4a-137">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="15d4a-138">这种运行应用的方法适用于安装了 .NET Core 运行时的任何平台。</span><span class="sxs-lookup"><span data-stu-id="15d4a-138">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

   * <span data-ttu-id="15d4a-139">*HelloWorld.exe*</span><span class="sxs-lookup"><span data-stu-id="15d4a-139">*HelloWorld.exe*</span></span>

      <span data-ttu-id="15d4a-140">这是应用程序的[依赖于框架的可执行文件](../deploying/deploy-with-cli.md#framework-dependent-executable)版本。</span><span class="sxs-lookup"><span data-stu-id="15d4a-140">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="15d4a-141">若要运行该版本，请在命令提示符处输入 `HelloWorld.exe`。</span><span class="sxs-lookup"><span data-stu-id="15d4a-141">To run it, enter `HelloWorld.exe` at a command prompt.</span></span> <span data-ttu-id="15d4a-142">文件特定于操作系统。</span><span class="sxs-lookup"><span data-stu-id="15d4a-142">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="15d4a-143">HelloWorld.pdb（对于部署是可选的）</span><span class="sxs-lookup"><span data-stu-id="15d4a-143">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="15d4a-144">这是调试符号文件。</span><span class="sxs-lookup"><span data-stu-id="15d4a-144">This is the debug symbols file.</span></span> <span data-ttu-id="15d4a-145">尽管应在需要调试应用程序的已发布版本时保存此文件，但无需将此文件与应用程序一起部署。</span><span class="sxs-lookup"><span data-stu-id="15d4a-145">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="15d4a-146">HelloWorld.runtimeconfig.json</span><span class="sxs-lookup"><span data-stu-id="15d4a-146">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="15d4a-147">这是应用程序的运行时配置文件。</span><span class="sxs-lookup"><span data-stu-id="15d4a-147">This is the application's run-time configuration file.</span></span> <span data-ttu-id="15d4a-148">它标识用于运行应用程序的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="15d4a-148">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="15d4a-149">还可向其添加配置选项。</span><span class="sxs-lookup"><span data-stu-id="15d4a-149">You can also add configuration options to it.</span></span> <span data-ttu-id="15d4a-150">有关详细信息，请参阅 [.NET Core 运行时配置设置](../run-time-config/index.md#runtimeconfigjson)。</span><span class="sxs-lookup"><span data-stu-id="15d4a-150">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="15d4a-151">运行已发布的应用</span><span class="sxs-lookup"><span data-stu-id="15d4a-151">Run the published app</span></span>

1. <span data-ttu-id="15d4a-152">在“解决方案资源管理器”中，右键单击“模型”文件夹，然后选择“复制完整路径”。</span><span class="sxs-lookup"><span data-stu-id="15d4a-152">In **Solution Explorer**, right-click the *publish* folder, and select **Copy Full Path**.</span></span>

1. <span data-ttu-id="15d4a-153">打开命令提示符，然后导航到“发布”文件夹。</span><span class="sxs-lookup"><span data-stu-id="15d4a-153">Open a command prompt and navigate to the *publish* folder.</span></span> <span data-ttu-id="15d4a-154">为此，请输入 `cd`，然后粘贴完整路径。</span><span class="sxs-lookup"><span data-stu-id="15d4a-154">To do that, enter `cd` and then paste the full path.</span></span> <span data-ttu-id="15d4a-155">例如：</span><span class="sxs-lookup"><span data-stu-id="15d4a-155">For example:</span></span>

   ```
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. <span data-ttu-id="15d4a-156">使用可执行文件运行应用：</span><span class="sxs-lookup"><span data-stu-id="15d4a-156">Run the app by using the executable:</span></span>

   1. <span data-ttu-id="15d4a-157">输入 `HelloWorld.exe`，然后按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="15d4a-157">Enter `HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="15d4a-158">输入一个名字以响应提示，并按任意键退出。</span><span class="sxs-lookup"><span data-stu-id="15d4a-158">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="15d4a-159">使用 `dotnet` 命令运行应用：</span><span class="sxs-lookup"><span data-stu-id="15d4a-159">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="15d4a-160">输入 `dotnet HelloWorld.dll`，然后按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="15d4a-160">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="15d4a-161">输入一个名字以响应提示，并按任意键退出。</span><span class="sxs-lookup"><span data-stu-id="15d4a-161">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="15d4a-162">其他资源</span><span class="sxs-lookup"><span data-stu-id="15d4a-162">Additional resources</span></span>

- [<span data-ttu-id="15d4a-163">.NET Core 应用程序部署</span><span class="sxs-lookup"><span data-stu-id="15d4a-163">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="15d4a-164">后续步骤</span><span class="sxs-lookup"><span data-stu-id="15d4a-164">Next steps</span></span>

<span data-ttu-id="15d4a-165">在本教程中，你发布了一个控制台应用。</span><span class="sxs-lookup"><span data-stu-id="15d4a-165">In this tutorial, you published a console app.</span></span> <span data-ttu-id="15d4a-166">在下一教程中，你将创建类库。</span><span class="sxs-lookup"><span data-stu-id="15d4a-166">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="15d4a-167">在 Visual Studio 中创建 .NET Standard 库</span><span class="sxs-lookup"><span data-stu-id="15d4a-167">Create a .NET Standard library in Visual Studio</span></span>](library-with-visual-studio.md)
