---
title: 使用 Visual Studio Code 发布 .NET Core 控制台应用程序
description: 发布应用程序会创建运行 .NET Core 应用程序所需的一组文件。
ms.date: 07/04/2020
ms.openlocfilehash: 79c69546b79de3d702fb4bb6550e615d8d59fa74
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495520"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="46182-103">教程：使用 Visual Studio Code 发布 .NET Core 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="46182-103">Tutorial: Publish a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="46182-104">本教程演示如何发布控制台应用，以便其他用户可以运行它。</span><span class="sxs-lookup"><span data-stu-id="46182-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="46182-105">发布应用程序会创建运行应用程序所需的一组文件。</span><span class="sxs-lookup"><span data-stu-id="46182-105">Publishing creates the set of files that are needed to run an application.</span></span> <span data-ttu-id="46182-106">若要部署文件，请将文件复制到目标计算机。</span><span class="sxs-lookup"><span data-stu-id="46182-106">To deploy the files, copy them to the target machine.</span></span>

<span data-ttu-id="46182-107">.NET Core CLI 用于发布应用，因此可以根据需要使用 Visual Studio Code 以外的代码编辑器来学习本教程。</span><span class="sxs-lookup"><span data-stu-id="46182-107">The .NET Core CLI is used to publish the app, so you can follow this tutorial with a code editor other than Visual Studio Code if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="46182-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="46182-108">Prerequisites</span></span>

- <span data-ttu-id="46182-109">本教程适用于在[使用 Visual Studio Code 创建 .NET Core 控制台应用程序](with-visual-studio-code.md)中创建的控制台应用。</span><span class="sxs-lookup"><span data-stu-id="46182-109">This tutorial works with the console app that you create in [Create a .NET Core console application using Visual Studio Code](with-visual-studio-code.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="46182-110">发布应用</span><span class="sxs-lookup"><span data-stu-id="46182-110">Publish the app</span></span>

1. <span data-ttu-id="46182-111">启动 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="46182-111">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="46182-112">打开在[使用 Visual Studio Code 创建 .NET Core 控制台应用程序](with-visual-studio-code.md)中创建的 HelloWorld 项目文件夹。</span><span class="sxs-lookup"><span data-stu-id="46182-112">Open the *HelloWorld* project folder that you created in [Create a .NET Core console application using Visual Studio Code](with-visual-studio-code.md).</span></span>

1. <span data-ttu-id="46182-113">从主菜单中选择“视图” > “终端” 。</span><span class="sxs-lookup"><span data-stu-id="46182-113">Choose **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="46182-114">终端在 HelloWorld 文件夹中打开。</span><span class="sxs-lookup"><span data-stu-id="46182-114">The terminal opens in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="46182-115">运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="46182-115">Run the following command:</span></span>

   ```dotnetcli
   dotnet publish --configuration Release
   ```

   <span data-ttu-id="46182-116">默认生成配置为“调试”，因此此命令指定“版本”生成配置 。</span><span class="sxs-lookup"><span data-stu-id="46182-116">The default build configuration is *Debug*, so this command specifies the *Release* build configuration.</span></span> <span data-ttu-id="46182-117">版本生成配置的输出进行了完全优化，且具有最低限度的符号调试信息。</span><span class="sxs-lookup"><span data-stu-id="46182-117">The output from the Release build configuration has minimal symbolic debug information and is fully optimized.</span></span>

   <span data-ttu-id="46182-118">该命令的输出类似于以下示例：</span><span class="sxs-lookup"><span data-stu-id="46182-118">The command output is similar to the following example:</span></span>

   ```output
   Microsoft (R) Build Engine version 16.7.0+b89cb5fde for .NET
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\HelloWorld.dll
     HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

## <a name="inspect-the-files"></a><span data-ttu-id="46182-119">检查文件</span><span class="sxs-lookup"><span data-stu-id="46182-119">Inspect the files</span></span>

<span data-ttu-id="46182-120">默认情况下，发布过程中会创建依赖于框架的部署，在此类部署中，已发布的应用程序在已安装 .NET Core 运行时的计算机上运行。</span><span class="sxs-lookup"><span data-stu-id="46182-120">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="46182-121">若要运行已发布的应用，可以使用可执行文件，或从命令提示符中运行 `dotnet HelloWorld.dll` 命令。</span><span class="sxs-lookup"><span data-stu-id="46182-121">To run the published app you can use the executable file or run the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="46182-122">在下面的步骤中，查看由发布过程创建的文件。</span><span class="sxs-lookup"><span data-stu-id="46182-122">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="46182-123">在左侧导航栏中选择“资源管理器”。</span><span class="sxs-lookup"><span data-stu-id="46182-123">Select the **Explorer** in the left navigation bar.</span></span>

1. <span data-ttu-id="46182-124">展开 bin/Release/netcoreapp3.1/publish。</span><span class="sxs-lookup"><span data-stu-id="46182-124">Expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-code/published-files-output.png" alt-text="显示已发布文件的资源管理器":::

   <span data-ttu-id="46182-126">如下图所示，已发布的输出包括以下文件：</span><span class="sxs-lookup"><span data-stu-id="46182-126">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="46182-127">HelloWorld.deps.json</span><span class="sxs-lookup"><span data-stu-id="46182-127">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="46182-128">这是应用程序的运行时依赖项文件。</span><span class="sxs-lookup"><span data-stu-id="46182-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="46182-129">它定义了运行应用程序所需的 .NET Core 组件和库（包括包含该应用程序的动态链接库）。</span><span class="sxs-lookup"><span data-stu-id="46182-129">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="46182-130">有关详细信息，请参阅[运行时配置文件](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="46182-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="46182-131">HelloWorld.dll</span><span class="sxs-lookup"><span data-stu-id="46182-131">*HelloWorld.dll*</span></span>

      <span data-ttu-id="46182-132">这是应用程序的[依赖于框架的部署](../deploying/deploy-with-cli.md#framework-dependent-deployment)版本。</span><span class="sxs-lookup"><span data-stu-id="46182-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="46182-133">若要执行此动态链接库，请在命令提示符处输入 `dotnet HelloWorld.dll`。</span><span class="sxs-lookup"><span data-stu-id="46182-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="46182-134">这种运行应用的方法适用于安装了 .NET Core 运行时的任何平台。</span><span class="sxs-lookup"><span data-stu-id="46182-134">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

   * <span data-ttu-id="46182-135">HelloWorld.exe（在 Linux 上而不是在 macOS 上创建的 HelloWorld） </span><span class="sxs-lookup"><span data-stu-id="46182-135">*HelloWorld.exe* (*HelloWorld* on Linux, not created on macOS.)</span></span>

      <span data-ttu-id="46182-136">这是应用程序的[依赖于框架的可执行文件](../deploying/deploy-with-cli.md#framework-dependent-executable)版本。</span><span class="sxs-lookup"><span data-stu-id="46182-136">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="46182-137">文件特定于操作系统。</span><span class="sxs-lookup"><span data-stu-id="46182-137">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="46182-138">HelloWorld.pdb（对于部署是可选的）</span><span class="sxs-lookup"><span data-stu-id="46182-138">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="46182-139">这是调试符号文件。</span><span class="sxs-lookup"><span data-stu-id="46182-139">This is the debug symbols file.</span></span> <span data-ttu-id="46182-140">尽管应在需要调试应用程序的已发布版本时保存此文件，但无需将此文件与应用程序一起部署。</span><span class="sxs-lookup"><span data-stu-id="46182-140">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="46182-141">HelloWorld.runtimeconfig.json</span><span class="sxs-lookup"><span data-stu-id="46182-141">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="46182-142">这是应用程序的运行时配置文件。</span><span class="sxs-lookup"><span data-stu-id="46182-142">This is the application's run-time configuration file.</span></span> <span data-ttu-id="46182-143">它标识用于运行应用程序的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="46182-143">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="46182-144">还可向其添加配置选项。</span><span class="sxs-lookup"><span data-stu-id="46182-144">You can also add configuration options to it.</span></span> <span data-ttu-id="46182-145">有关详细信息，请参阅 [.NET Core 运行时配置设置](../run-time-config/index.md#runtimeconfigjson)。</span><span class="sxs-lookup"><span data-stu-id="46182-145">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="46182-146">运行已发布的应用</span><span class="sxs-lookup"><span data-stu-id="46182-146">Run the published app</span></span>

1. <span data-ttu-id="46182-147">在“资源管理器”中，右键单击“发布”文件夹（在 macOS 上按住 <kbd>Ctrl</kbd> 单击），然后选择“在终端中打开”。</span><span class="sxs-lookup"><span data-stu-id="46182-147">In **Explorer**, right-click the *publish* folder (<kbd>Ctrl</kbd>-click on macOS), and select **Open in Terminal**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-code/open-in-terminal.png" alt-text="显示“在终端中打开”的上下文菜单":::

1. <span data-ttu-id="46182-149">在 Windows 或 Linux 上，使用可执行文件运行应用。</span><span class="sxs-lookup"><span data-stu-id="46182-149">On Windows or Linux, run the app by using the executable.</span></span>

   1. <span data-ttu-id="46182-150">在 Windows 上，输入 `.\HelloWorld.exe`，然后按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="46182-150">On Windows, enter `.\HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="46182-151">在 Linux 上，输入 `./HelloWorld`，然后按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="46182-151">On Linux, enter `./HelloWorld` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="46182-152">输入一个名字以响应提示，并按任意键退出。</span><span class="sxs-lookup"><span data-stu-id="46182-152">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="46182-153">在任何平台上，使用 [`dotnet`](../tools/dotnet.md) 命令运行应用：</span><span class="sxs-lookup"><span data-stu-id="46182-153">On any platform, run the app by using the  [`dotnet`](../tools/dotnet.md) command:</span></span>

   1. <span data-ttu-id="46182-154">输入 `dotnet HelloWorld.dll`，然后按 <kbd>Enter</kbd>。</span><span class="sxs-lookup"><span data-stu-id="46182-154">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="46182-155">输入一个名字以响应提示，并按任意键退出。</span><span class="sxs-lookup"><span data-stu-id="46182-155">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="46182-156">其他资源</span><span class="sxs-lookup"><span data-stu-id="46182-156">Additional resources</span></span>

- [<span data-ttu-id="46182-157">.NET Core 应用程序部署</span><span class="sxs-lookup"><span data-stu-id="46182-157">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="46182-158">后续步骤</span><span class="sxs-lookup"><span data-stu-id="46182-158">Next steps</span></span>

<span data-ttu-id="46182-159">在本教程中，你发布了一个控制台应用。</span><span class="sxs-lookup"><span data-stu-id="46182-159">In this tutorial, you published a console app.</span></span> <span data-ttu-id="46182-160">在下一教程中，你将创建类库。</span><span class="sxs-lookup"><span data-stu-id="46182-160">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="46182-161">使用 Visual Studio Code 创建 .NET Standard 库</span><span class="sxs-lookup"><span data-stu-id="46182-161">Create a .NET Standard library using Visual Studio Code</span></span>](library-with-visual-studio-code.md)
