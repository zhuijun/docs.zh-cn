---
title: 通过 CLI 开始使用 .NET Core
description: 一个分步教程，演示如何使用 .NET Core CLI 开始在 Windows、Linux 或 macOS 上使用 .NET Core。
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: 7658f2498b87a90b3925d83628f6ea9247a2fc15
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840866"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a><span data-ttu-id="d3404-103">使用 .NET Core CLI 实现 .NET Core 入门</span><span class="sxs-lookup"><span data-stu-id="d3404-103">Get started with .NET Core using the .NET Core CLI</span></span>

<span data-ttu-id="d3404-104">本文介绍如何开始使用 .NET Core CLI 开发在 Windows、Linux 和 macOS 上运行的 .NET Core 应用。</span><span class="sxs-lookup"><span data-stu-id="d3404-104">This article will show you how to start developing .NET Core apps that work on Windows, Linux, and macOS using the .NET Core CLI.</span></span>

<span data-ttu-id="d3404-105">如果不熟悉 .NET Core CLI，请参阅 [.NET Core 概述](../tools/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d3404-105">If you're unfamiliar with the .NET Core CLI, see the [.NET Core CLI overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d3404-106">系统必备</span><span class="sxs-lookup"><span data-stu-id="d3404-106">Prerequisites</span></span>

- <span data-ttu-id="d3404-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="d3404-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="d3404-108">按需选择的文本编辑器或代码编辑器。</span><span class="sxs-lookup"><span data-stu-id="d3404-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="d3404-109">Hello，控制台应用！</span><span class="sxs-lookup"><span data-stu-id="d3404-109">Hello, Console App!</span></span>

<span data-ttu-id="d3404-110">若要[查看或下载示例代码](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild)，可以访问 dotnet/samples GitHub 存储库。</span><span class="sxs-lookup"><span data-stu-id="d3404-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="d3404-111">有关下载说明，请参阅[示例和教程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="d3404-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="d3404-112">打开命令提示符，创建一个名为“Hello”  的文件夹。</span><span class="sxs-lookup"><span data-stu-id="d3404-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="d3404-113">导航到创建的文件夹，键入下列内容。</span><span class="sxs-lookup"><span data-stu-id="d3404-113">Navigate to the folder you created and type the following.</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="d3404-114">让我们进行快速演练：</span><span class="sxs-lookup"><span data-stu-id="d3404-114">Let's do a quick walkthrough:</span></span>

01. `dotnet new console`

    <span data-ttu-id="d3404-115">[dotnet new](../tools/dotnet-new.md) 会创建一个最新的 Hello.csproj 项目文件，其中包含生成控制台应用所必需的依赖项  。</span><span class="sxs-lookup"><span data-stu-id="d3404-115">[dotnet new](../tools/dotnet-new.md) creates an up-to-date *Hello.csproj* project file with the dependencies necessary to build a console app.</span></span> <span data-ttu-id="d3404-116">此外，它还会创建一个 Program.cs  ，这是包含应用程序入口点的基本文件。</span><span class="sxs-lookup"><span data-stu-id="d3404-116">It also creates a *Program.cs*, a basic file containing the entry point for the application.</span></span>

    <span data-ttu-id="d3404-117">Hello.csproj  ：</span><span class="sxs-lookup"><span data-stu-id="d3404-117">*Hello.csproj*:</span></span>

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    <span data-ttu-id="d3404-118">项目文件指定还原依赖项和生成程序所需的一切。</span><span class="sxs-lookup"><span data-stu-id="d3404-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

    - <span data-ttu-id="d3404-119">`<OutputType>` 元素指定我们要生成的可执行文件，即控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="d3404-119">The `<OutputType>` element specifies that we're building an executable, in other words a console application.</span></span>
    - <span data-ttu-id="d3404-120">`<TargetFramework>` 元素指定要定位的 .NET 实现代码。</span><span class="sxs-lookup"><span data-stu-id="d3404-120">The `<TargetFramework>` element specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="d3404-121">在高级方案中，可以指定多个目标框架，并在单个操作中生成所有目标框架。</span><span class="sxs-lookup"><span data-stu-id="d3404-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="d3404-122">在本教程中，我们将仅针对 .NET Core 3.1 进行生成。</span><span class="sxs-lookup"><span data-stu-id="d3404-122">In this tutorial, we'll stick to building only for .NET Core 3.1.</span></span>

    <span data-ttu-id="d3404-123">Program.cs  :</span><span class="sxs-lookup"><span data-stu-id="d3404-123">*Program.cs*:</span></span>

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    <span data-ttu-id="d3404-124">该程序从 `using System` 开始，这意味着“将 `System` 命名空间中的所有内容都纳入此文件的作用域”。</span><span class="sxs-lookup"><span data-stu-id="d3404-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="d3404-125">`System` 命名空间包括 `Console` 类。</span><span class="sxs-lookup"><span data-stu-id="d3404-125">The `System` namespace includes the `Console` class.</span></span>

    <span data-ttu-id="d3404-126">接着定义一个名为 `Hello` 的命名空间。</span><span class="sxs-lookup"><span data-stu-id="d3404-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="d3404-127">你可以将其更改为任何你喜欢的名称。</span><span class="sxs-lookup"><span data-stu-id="d3404-127">You can change this to anything you want.</span></span> <span data-ttu-id="d3404-128">在该命名空间中定义了一个名为 `Program` 的类，其中 `Main` 方法采用名为 `args` 的字符串数组。</span><span class="sxs-lookup"><span data-stu-id="d3404-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings named `args`.</span></span> <span data-ttu-id="d3404-129">此数组包含在运行程序时所传递的参数列表。</span><span class="sxs-lookup"><span data-stu-id="d3404-129">This array contains the list of arguments passed in when the program is run.</span></span> <span data-ttu-id="d3404-130">实际上，不使用此数组，程序只会写入文本“Hello World!”</span><span class="sxs-lookup"><span data-stu-id="d3404-130">As it is, this array is not used and the program simply writes the text "Hello World!"</span></span> <span data-ttu-id="d3404-131">“Hello World!”。</span><span class="sxs-lookup"><span data-stu-id="d3404-131">to the console.</span></span> <span data-ttu-id="d3404-132">稍后将对使用此参数的代码进行更改。</span><span class="sxs-lookup"><span data-stu-id="d3404-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

    <span data-ttu-id="d3404-133">`dotnet new` 隐式调用 [dotnet restore](../tools/dotnet-restore.md)。</span><span class="sxs-lookup"><span data-stu-id="d3404-133">`dotnet new` calls [dotnet restore](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="d3404-134">`dotnet restore` 调用到 [NuGet](https://www.nuget.org/)（.NET 包管理器）以还原依赖项树。</span><span class="sxs-lookup"><span data-stu-id="d3404-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="d3404-135">NuGet 分析 Hello.csproj  文件、下载文件中定义的依赖项（或从计算机缓存中获取）并编写 obj/project.assets.json  文件，在编译和运行示例时需要使用该文件。</span><span class="sxs-lookup"><span data-stu-id="d3404-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

02. `dotnet run`

    <span data-ttu-id="d3404-136">[dotnet run](../tools/dotnet-run.md) 调用 [dotnet build](../tools/dotnet-build.md) 来确保已生成要生成的目标，然后调用 `dotnet <assembly.dll>` 运行目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="d3404-136">[dotnet run](../tools/dotnet-run.md) calls [dotnet build](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="d3404-137">将获得以下输出。</span><span class="sxs-lookup"><span data-stu-id="d3404-137">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="d3404-138">或者，还可以运行 `dotnet build` 来编译代码，无需运行已生成的控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="d3404-138">Alternatively, you can also run `dotnet build` to compile the code without running the build console applications.</span></span> <span data-ttu-id="d3404-139">这会基于项目的名称将已编译的应用程序作为 DLL 文件生成。</span><span class="sxs-lookup"><span data-stu-id="d3404-139">This results in a compiled application, as a DLL file, based on the name of the project.</span></span> <span data-ttu-id="d3404-140">在这种情况下，创建的文件命名为 Hello.dll  。</span><span class="sxs-lookup"><span data-stu-id="d3404-140">In this case, the file created is named *Hello.dll*.</span></span> <span data-ttu-id="d3404-141">此应用可以使用 Windows 上的 `dotnet bin\Debug\netcoreapp3.1\Hello.dll` 运行（非 Windows 系统使用 `/`）。</span><span class="sxs-lookup"><span data-stu-id="d3404-141">This app can be run with `dotnet bin\Debug\netcoreapp3.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span>

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    <span data-ttu-id="d3404-142">将获得以下输出。</span><span class="sxs-lookup"><span data-stu-id="d3404-142">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="d3404-143">在编译应用时，会随 `Hello.dll` 一起创建特定于操作系统的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="d3404-143">When the app is compiled, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="d3404-144">在 Windows 上，这将是 `Hello.exe`；在 Linux 或 macOS 上，这将是 `hello`。</span><span class="sxs-lookup"><span data-stu-id="d3404-144">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="d3404-145">在上面的示例中，用 `Hello.exe` 或 `Hello` 命名该文件。</span><span class="sxs-lookup"><span data-stu-id="d3404-145">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="d3404-146">可以直接运行该可执行文件。</span><span class="sxs-lookup"><span data-stu-id="d3404-146">You can run that executable directly.</span></span>

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a><span data-ttu-id="d3404-147">修改程序</span><span class="sxs-lookup"><span data-stu-id="d3404-147">Modify the program</span></span>

<span data-ttu-id="d3404-148">让我们稍微更改一下程序。</span><span class="sxs-lookup"><span data-stu-id="d3404-148">Let's change the program a bit.</span></span> <span data-ttu-id="d3404-149">Fibonacci 数字很有意思，那么除了使用参数，让我们也来添加 Fibonacci 数字，让运行应用的用户开心一下。</span><span class="sxs-lookup"><span data-stu-id="d3404-149">Fibonacci numbers are fun, so let's add that and also to use the argument to greet the person running the app.</span></span>

01. <span data-ttu-id="d3404-150">将 *Program.cs* 文件的内容替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="d3404-150">Replace the contents of your *Program.cs*  file with the following code:</span></span>

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. <span data-ttu-id="d3404-151">运行 [dotnet build](../tools/dotnet-build.md) 以编译更改。</span><span class="sxs-lookup"><span data-stu-id="d3404-151">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

03. <span data-ttu-id="d3404-152">运行向应用传递参数的程序。</span><span class="sxs-lookup"><span data-stu-id="d3404-152">Run the program passing a parameter to the app.</span></span> <span data-ttu-id="d3404-153">使用 `dotnet` 命令运行应用时，将 `--` 添加到末尾。</span><span class="sxs-lookup"><span data-stu-id="d3404-153">When you use the `dotnet` command to run an app, add `--` to the end.</span></span> <span data-ttu-id="d3404-154">`--` 右侧的任何内容都将作为参数传递到应用。</span><span class="sxs-lookup"><span data-stu-id="d3404-154">Anything to the right of `--` will be passed as a parameter to the app.</span></span> <span data-ttu-id="d3404-155">在下面的示例中，值 `John` 传递到应用。</span><span class="sxs-lookup"><span data-stu-id="d3404-155">In the following example, the value `John` is passed to the app.</span></span>

    ```dotnetcli
    dotnet run -- John
    ```

    <span data-ttu-id="d3404-156">将获得以下输出。</span><span class="sxs-lookup"><span data-stu-id="d3404-156">You get the following output.</span></span>

    ```console
    Hello John!
    Fibonacci Numbers 1-15:
    1: 0
    2: 1
    3: 1
    4: 2
    5: 3
    6: 5
    7: 8
    8: 13
    9: 21
    10: 34
    11: 55
    12: 89
    13: 144
    14: 233
    15: 377
    ```

<span data-ttu-id="d3404-157">这就是所有的操作！</span><span class="sxs-lookup"><span data-stu-id="d3404-157">And that's it!</span></span> <span data-ttu-id="d3404-158">可以按任意喜欢的方式修改 Program.cs  。</span><span class="sxs-lookup"><span data-stu-id="d3404-158">You can modify *Program.cs* any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="d3404-159">使用多个文件</span><span class="sxs-lookup"><span data-stu-id="d3404-159">Working with multiple files</span></span>

<span data-ttu-id="d3404-160">单个文件适用于简单的一次性程序，但如果要构建较为复杂的应用，则项目中可能会有多个代码文件。</span><span class="sxs-lookup"><span data-stu-id="d3404-160">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple code files on your project.</span></span> <span data-ttu-id="d3404-161">我们通过缓存一些 Fibonacci 值并添加一些递归特性来基于之前的 Fibonacci 示例进行构建。</span><span class="sxs-lookup"><span data-stu-id="d3404-161">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

01. <span data-ttu-id="d3404-162">使用以下代码将新文件添加到名为 *FibonacciGenerator.cs* 的 *Hello* 目录：</span><span class="sxs-lookup"><span data-stu-id="d3404-162">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. <span data-ttu-id="d3404-163">更改 *Program.cs* 文件中的 `Main` 方法，以实例化新的类并调用其方法，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="d3404-163">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. <span data-ttu-id="d3404-164">运行 [dotnet build](../tools/dotnet-build.md) 以编译更改。</span><span class="sxs-lookup"><span data-stu-id="d3404-164">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

04. <span data-ttu-id="d3404-165">通过执行 [dotnet run](../tools/dotnet-run.md) 来运行应用。</span><span class="sxs-lookup"><span data-stu-id="d3404-165">Run your app by executing [dotnet run](../tools/dotnet-run.md).</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="d3404-166">将获得以下输出。</span><span class="sxs-lookup"><span data-stu-id="d3404-166">You get the following output.</span></span>

    ```console
    0
    1
    1
    2
    3
    5
    8
    13
    21
    34
    55
    89
    144
    233
    377
    ```

## <a name="publish-your-app"></a><span data-ttu-id="d3404-167">发布你的应用</span><span class="sxs-lookup"><span data-stu-id="d3404-167">Publish your app</span></span>

<span data-ttu-id="d3404-168">准备好分发应用后，使用 [dotnet publish](../tools/dotnet-publish.md) 命令在 bin\\debug\\netcoreapp3.1\\publish\\（非 Windows 系统使用 `/`）处生成 publish 文件夹。</span><span class="sxs-lookup"><span data-stu-id="d3404-168">Once you're ready to distribute your app, use the [dotnet publish](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp3.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="d3404-169">可以将 publish  文件夹的内容分发到其他平台，只要这些平台安装了 dotnet 运行时即可。</span><span class="sxs-lookup"><span data-stu-id="d3404-169">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

```dotnetcli
dotnet publish
```

<span data-ttu-id="d3404-170">将获得类似于下面的输出。</span><span class="sxs-lookup"><span data-stu-id="d3404-170">You get output similar to the following.</span></span>

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

<span data-ttu-id="d3404-171">上面的输出可能会因当前文件夹和操作系统而有所不同，但输出应类似。</span><span class="sxs-lookup"><span data-stu-id="d3404-171">The output above may differ based on your current folder and operating system, but the output should be similar.</span></span>

<span data-ttu-id="d3404-172">可以使用 [dotnet](../tools/dotnet.md) 命令运行已发布的应用：</span><span class="sxs-lookup"><span data-stu-id="d3404-172">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

<span data-ttu-id="d3404-173">将获得以下输出。</span><span class="sxs-lookup"><span data-stu-id="d3404-173">You get the following output.</span></span>

```console
0
1
1
2
3
5
8
13
21
34
55
89
144
233
377
```

<span data-ttu-id="d3404-174">如本文开头处所述，会随 `Hello.dll` 一起创建特定于操作系统的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="d3404-174">As mentioned at the start of this article, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="d3404-175">在 Windows 上，这将是 `Hello.exe`；在 Linux 或 macOS 上，这将是 `hello`。</span><span class="sxs-lookup"><span data-stu-id="d3404-175">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="d3404-176">在上面的示例中，用 `Hello.exe` 或 `Hello` 命名该文件。</span><span class="sxs-lookup"><span data-stu-id="d3404-176">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="d3404-177">可以直接运行已发布的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="d3404-177">You can run this published executable directly.</span></span>

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

0
1
1
2
3
5
8
13
21
34
55
89
144
233
377
```

## <a name="conclusion"></a><span data-ttu-id="d3404-178">结束语</span><span class="sxs-lookup"><span data-stu-id="d3404-178">Conclusion</span></span>

<span data-ttu-id="d3404-179">这就是所有的操作！</span><span class="sxs-lookup"><span data-stu-id="d3404-179">And that's it!</span></span> <span data-ttu-id="d3404-180">现在，可以开始使用此处学到的基本概念来创建自己的程序了。</span><span class="sxs-lookup"><span data-stu-id="d3404-180">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3404-181">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d3404-181">See also</span></span>

- [<span data-ttu-id="d3404-182">使用 .NET Core CLI 组织和测试项目</span><span class="sxs-lookup"><span data-stu-id="d3404-182">Organizing and testing projects with the .NET Core CLI</span></span>](testing-with-cli.md)
- [<span data-ttu-id="d3404-183">使用 .NET Core CLI 发布 .NET Core 应用</span><span class="sxs-lookup"><span data-stu-id="d3404-183">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="d3404-184">.NET Core 应用程序部署</span><span class="sxs-lookup"><span data-stu-id="d3404-184">.NET Core application deployment</span></span>](../deploying/index.md)
