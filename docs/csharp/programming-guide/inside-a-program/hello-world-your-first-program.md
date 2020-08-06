---
title: Hello World - 你在 Windows 或 Mac 上使用 Visual Studio 的第一个程序 - C# 编程指南
description: Visual Studio 是一个专业的开发环境，具有适用于 .NET 开发的许多功能。 使用 Visual Studio 创建 C# 版本的 Hello World！
ms.date: 09/12/2019
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
ms.openlocfilehash: b78937b8ba1c7d4718bfb6252dac705945336d2a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301822"
---
# <a name="hello-world----your-first-program"></a><span data-ttu-id="d3d16-104">Hello World -- 你的第一个程序</span><span class="sxs-lookup"><span data-stu-id="d3d16-104">Hello World -- Your first program</span></span>

<span data-ttu-id="d3d16-105">在本文中，你将使用 Visual Studio 创建传统的“Hello World!”</span><span class="sxs-lookup"><span data-stu-id="d3d16-105">In this article, you'll use Visual Studio to create the traditional "Hello World!"</span></span> <span data-ttu-id="d3d16-106">版本。</span><span class="sxs-lookup"><span data-stu-id="d3d16-106">program.</span></span> <span data-ttu-id="d3d16-107">Visual Studio 是一个专业的集成开发环境 (IDE)，具有适用于 .NET 开发的许多功能。</span><span class="sxs-lookup"><span data-stu-id="d3d16-107">Visual Studio is a professional Integrated Development Environment (IDE) with many features designed for .NET development.</span></span> <span data-ttu-id="d3d16-108">只需使用 Visual Studio 中的几个功能即可创建此程序。</span><span class="sxs-lookup"><span data-stu-id="d3d16-108">You'll use only a few of the features in Visual Studio to create this program.</span></span> <span data-ttu-id="d3d16-109">如需了解有关 Visual Studio 的详细信息，请参阅 [Visual C# 入门](/visualstudio/ide/quickstart-csharp-console)。</span><span class="sxs-lookup"><span data-stu-id="d3d16-109">To learn more about Visual Studio, see [Getting Started with Visual C#](/visualstudio/ide/quickstart-csharp-console).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="create-a-new-application"></a><span data-ttu-id="d3d16-110">创建一个新的应用程序</span><span class="sxs-lookup"><span data-stu-id="d3d16-110">Create a new application</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="d3d16-111">Windows</span><span class="sxs-lookup"><span data-stu-id="d3d16-111">Windows</span></span>](#tab/windows)

<span data-ttu-id="d3d16-112">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="d3d16-112">Start Visual Studio.</span></span> <span data-ttu-id="d3d16-113">你将在 Windows 上看到以下图像：</span><span class="sxs-lookup"><span data-stu-id="d3d16-113">You'll see the following image on Windows:</span></span>

![Windows 上的 Visual Studio 欢迎屏幕](./media/hello-world-your-first-program/visual-studio-windows-start-screen.png)

<span data-ttu-id="d3d16-115">在图像右下角选择“创建新项目”。</span><span class="sxs-lookup"><span data-stu-id="d3d16-115">Select **Create a new project** in the lower right corner of the image.</span></span> <span data-ttu-id="d3d16-116">Visual Studio 会显示“新建项目”对话框：</span><span class="sxs-lookup"><span data-stu-id="d3d16-116">Visual Studio displays the **New Project** dialog:</span></span>

![Windows 上的 Visual Studio 新建项目屏幕](./media/hello-world-your-first-program/visual-studio-windows-new-project.png)

> [!NOTE]
> <span data-ttu-id="d3d16-118">如果这是首次启动 Visual Studio，则“最近使用的项目模板”列表为空。</span><span class="sxs-lookup"><span data-stu-id="d3d16-118">If this is the first time you've started Visual Studio, the **Recent project templates** list is empty.</span></span>

<span data-ttu-id="d3d16-119">在“新建项目”对话框中，选择“控制台应用(.NET Core)”，然后按“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d3d16-119">On the new project dialog, choose "Console App (.NET Core)" and then press **Next**.</span></span> <span data-ttu-id="d3d16-120">请为项目命名（例如“HelloWorld”），然后按“创建”。</span><span class="sxs-lookup"><span data-stu-id="d3d16-120">Give your project a name, such as "HelloWorld", then press **Create**.</span></span>

<span data-ttu-id="d3d16-121">Visual Studio 将打开你的项目。</span><span class="sxs-lookup"><span data-stu-id="d3d16-121">Visual Studio opens your project.</span></span> <span data-ttu-id="d3d16-122">一个基本的“Hello World!”已初见雏形</span><span class="sxs-lookup"><span data-stu-id="d3d16-122">It's already a basic "Hello World!"</span></span> <span data-ttu-id="d3d16-123">示例。</span><span class="sxs-lookup"><span data-stu-id="d3d16-123">example.</span></span> <span data-ttu-id="d3d16-124">按 `Ctrl` + `F5` 运行项目。</span><span class="sxs-lookup"><span data-stu-id="d3d16-124">Press `Ctrl` + `F5` to run your project.</span></span> <span data-ttu-id="d3d16-125">Visual Studio 生成项目，将源代码转换为可执行文件。</span><span class="sxs-lookup"><span data-stu-id="d3d16-125">Visual Studio builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="d3d16-126">然后，它会启动一个运行新应用程序的命令窗口。</span><span class="sxs-lookup"><span data-stu-id="d3d16-126">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="d3d16-127">你应在窗口中看到以下文本：</span><span class="sxs-lookup"><span data-stu-id="d3d16-127">You should see the following text in the window:</span></span>

```console
Hello World!

C:\Program Files\dotnet\dotnet.exe (process 11964) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="d3d16-128">按相关键关闭窗口。</span><span class="sxs-lookup"><span data-stu-id="d3d16-128">Press a key to close the window.</span></span>

# <a name="macos"></a>[<span data-ttu-id="d3d16-129">macOS</span><span class="sxs-lookup"><span data-stu-id="d3d16-129">macOS</span></span>](#tab/macos)

<span data-ttu-id="d3d16-130">启动 Visual Studio for Mac。</span><span class="sxs-lookup"><span data-stu-id="d3d16-130">Start Visual Studio for Mac.</span></span> <span data-ttu-id="d3d16-131">你将在 Mac 上看到以下图像：</span><span class="sxs-lookup"><span data-stu-id="d3d16-131">You'll see the following image on Mac:</span></span>

![Mac 上的 Visual Studio 欢迎屏幕](./media/hello-world-your-first-program/visual-studio-mac-start-screen.png)

> [!NOTE]
> <span data-ttu-id="d3d16-133">如果这是首次启动 Visual Studio for Mac，则“最近使用的项目模板”列表为空。</span><span class="sxs-lookup"><span data-stu-id="d3d16-133">If this is the first time you've started Visual Studio for Mac, the **Recent projects** list is empty.</span></span>

<span data-ttu-id="d3d16-134">在图像右上角选择“新建”。</span><span class="sxs-lookup"><span data-stu-id="d3d16-134">Select **New** in the upper right corner of the image.</span></span> <span data-ttu-id="d3d16-135">Visual Studio for Mac 会显示“新建项目”对话框：</span><span class="sxs-lookup"><span data-stu-id="d3d16-135">Visual Studio for Mac displays the **New Project** dialog:</span></span>

![Mac 上的 Visual Studio 新建项目屏幕](./media/hello-world-your-first-program/visual-studio-mac-new-project.png)

<span data-ttu-id="d3d16-137">在“新建项目”对话框中，选择“.NET Core”和“控制台应用”，然后按“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d3d16-137">On the new project dialog, choose ".NET Core", and "Console App" and then press **Next**.</span></span> <span data-ttu-id="d3d16-138">需要选择目标框架。</span><span class="sxs-lookup"><span data-stu-id="d3d16-138">You'll need to select the target framework.</span></span> <span data-ttu-id="d3d16-139">默认情况下，请按“下一步”。</span><span class="sxs-lookup"><span data-stu-id="d3d16-139">The default is fine, so press next.</span></span> <span data-ttu-id="d3d16-140">请为项目命名（例如“HelloWorld”），然后按“创建”。</span><span class="sxs-lookup"><span data-stu-id="d3d16-140">Give your project a name, such as "HelloWorld", then press **Create**.</span></span> <span data-ttu-id="d3d16-141">可以使用默认的项目位置。</span><span class="sxs-lookup"><span data-stu-id="d3d16-141">You can use the default project location.</span></span> <span data-ttu-id="d3d16-142">请勿将项目添加到源控件。</span><span class="sxs-lookup"><span data-stu-id="d3d16-142">Don't add this project to source control.</span></span>

<span data-ttu-id="d3d16-143">Visual Studio for Mac 打开你的项目。</span><span class="sxs-lookup"><span data-stu-id="d3d16-143">Visual Studio for Mac opens your project.</span></span> <span data-ttu-id="d3d16-144">一个基本的“Hello World!”已初见雏形</span><span class="sxs-lookup"><span data-stu-id="d3d16-144">It's already a basic "Hello World!"</span></span> <span data-ttu-id="d3d16-145">示例。</span><span class="sxs-lookup"><span data-stu-id="d3d16-145">example.</span></span> <span data-ttu-id="d3d16-146">按 `Ctrl` + `Fn` + `F5` 运行项目。</span><span class="sxs-lookup"><span data-stu-id="d3d16-146">Press `Ctrl` + `Fn` + `F5` to run your project.</span></span> <span data-ttu-id="d3d16-147">Visual Studio for Mac 生成项目，将源代码转换为可执行文件。</span><span class="sxs-lookup"><span data-stu-id="d3d16-147">Visual Studio for Mac builds your project, converting the source code into an executable.</span></span> <span data-ttu-id="d3d16-148">然后，它会启动一个运行新应用程序的命令窗口。</span><span class="sxs-lookup"><span data-stu-id="d3d16-148">Then, it launches a command window that runs your new application.</span></span> <span data-ttu-id="d3d16-149">你应在窗口中看到以下文本：</span><span class="sxs-lookup"><span data-stu-id="d3d16-149">You should see the following text in the window:</span></span>

```console
Hello World!

Press any key to close this window . . .
```

<span data-ttu-id="d3d16-150">按任意键结束会话。</span><span class="sxs-lookup"><span data-stu-id="d3d16-150">Press a key to end the session.</span></span>

---

## <a name="elements-of-a-c-program"></a><span data-ttu-id="d3d16-151">C# 程序的元素</span><span class="sxs-lookup"><span data-stu-id="d3d16-151">Elements of a C# program</span></span>

<span data-ttu-id="d3d16-152">我们来检查一下此程序的重要部分。</span><span class="sxs-lookup"><span data-stu-id="d3d16-152">Let's examine the important parts of this program.</span></span> <span data-ttu-id="d3d16-153">第一行包含一条注释。</span><span class="sxs-lookup"><span data-stu-id="d3d16-153">The first line contains a comment.</span></span> <span data-ttu-id="d3d16-154">字符 `//` 将该行的其余内容转换为一条注释。</span><span class="sxs-lookup"><span data-stu-id="d3d16-154">The characters `//` convert the rest of the line to a comment.</span></span>

[!code-csharp[csProgGuide#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#32)]

<span data-ttu-id="d3d16-155">还可以通过将文本块置于 `/*` 和 `*/` 字符之间，禁止对其的注释。</span><span class="sxs-lookup"><span data-stu-id="d3d16-155">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="d3d16-156">这在下面的示例中显示。</span><span class="sxs-lookup"><span data-stu-id="d3d16-156">This is shown in the following example.</span></span>

[!code-csharp[csProgGuide#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#33)]

<span data-ttu-id="d3d16-157">C# 控制台应用程序必须包含 `Main` 方法，控件在其中开始和结束。</span><span class="sxs-lookup"><span data-stu-id="d3d16-157">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="d3d16-158">在 `Main` 方法中，可以创建对象并执行其他方法。</span><span class="sxs-lookup"><span data-stu-id="d3d16-158">The `Main` method is where you create objects and execute other methods.</span></span>

<span data-ttu-id="d3d16-159">`Main` 方法是驻留在类或结构中的[静态](../../language-reference/keywords/static.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d3d16-159">The `Main` method is a [static](../../language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="d3d16-160">在上一个“Hello World!”</span><span class="sxs-lookup"><span data-stu-id="d3d16-160">In the previous "Hello World!"</span></span> <span data-ttu-id="d3d16-161">示例中，该方法驻留在名为 `Hello` 的类中。</span><span class="sxs-lookup"><span data-stu-id="d3d16-161">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="d3d16-162">可以通过以下方式之一来声明 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="d3d16-162">You can declare the `Main` method in one of the following ways:</span></span>

- <span data-ttu-id="d3d16-163">它可返回 `void`。</span><span class="sxs-lookup"><span data-stu-id="d3d16-163">It can return `void`.</span></span> <span data-ttu-id="d3d16-164">这表示程序不会返回值。</span><span class="sxs-lookup"><span data-stu-id="d3d16-164">That means your program doesn't return a value.</span></span>

[!code-csharp[csProgGuideMain#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#12)]

- <span data-ttu-id="d3d16-165">还可以返回一个整数。</span><span class="sxs-lookup"><span data-stu-id="d3d16-165">It can also return an integer.</span></span> <span data-ttu-id="d3d16-166">整数是应用程序的“退出代码”。</span><span class="sxs-lookup"><span data-stu-id="d3d16-166">The integer is the **exit code** for your application.</span></span>

[!code-csharp[csProgGuideMain#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#13)]

- <span data-ttu-id="d3d16-167">无论使用哪种返回类型，它都可以带有参数。</span><span class="sxs-lookup"><span data-stu-id="d3d16-167">With either of the return types, it can take arguments.</span></span>

[!code-csharp[csProgGuideMain#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#19)]

<span data-ttu-id="d3d16-168">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="d3d16-168">-or-</span></span>

[!code-csharp[csProgGuideMain#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#18)]

<span data-ttu-id="d3d16-169">`Main` 方法中定义的参数 `args` 是一个 `string` 类型的数组，该数组包含用于调用该程序的命令行自变量。</span><span class="sxs-lookup"><span data-stu-id="d3d16-169">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span>

<span data-ttu-id="d3d16-170">若要了解更多有关如何使用命令行参数的信息，请参阅 [Main() 和命令行参数](../main-and-command-args/index.md)中的示例。</span><span class="sxs-lookup"><span data-stu-id="d3d16-170">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../main-and-command-args/index.md).</span></span>

## <a name="input-and-output"></a><span data-ttu-id="d3d16-171">输入和输出</span><span class="sxs-lookup"><span data-stu-id="d3d16-171">Input and output</span></span>

<span data-ttu-id="d3d16-172">C# 程序通常使用由 .NET 的运行时库提供的输入/输出服务。</span><span class="sxs-lookup"><span data-stu-id="d3d16-172">C# programs generally use the input/output services provided by the run-time library of .NET.</span></span> <span data-ttu-id="d3d16-173">语句 `System.Console.WriteLine("Hello World!");` 使用 <xref:System.Console.WriteLine%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d3d16-173">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="d3d16-174">这是运行时库中 <xref:System.Console> 类的输出方法之一。</span><span class="sxs-lookup"><span data-stu-id="d3d16-174">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="d3d16-175">该方法将在标准输出流中显示其字符串参数，后接新行。</span><span class="sxs-lookup"><span data-stu-id="d3d16-175">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="d3d16-176">其他 <xref:System.Console> 方法可用于不同的输入和输出操作。</span><span class="sxs-lookup"><span data-stu-id="d3d16-176">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="d3d16-177">如果程序开头包含 `using System;` 指令，则可以直接使用 <xref:System> 类和方法，而不必进行完全限定。</span><span class="sxs-lookup"><span data-stu-id="d3d16-177">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="d3d16-178">例如，可以调用 `Console.WriteLine`，而非 `System.Console.WriteLine`：</span><span class="sxs-lookup"><span data-stu-id="d3d16-178">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>

[!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]

[!code-csharp[csProgGuide#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#23)]

<span data-ttu-id="d3d16-179">有关输入/输出方法的详细信息，请参阅 <xref:System.IO>。</span><span class="sxs-lookup"><span data-stu-id="d3d16-179">For more information about input/output methods, see <xref:System.IO>.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3d16-180">请参阅</span><span class="sxs-lookup"><span data-stu-id="d3d16-180">See also</span></span>

- [<span data-ttu-id="d3d16-181">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="d3d16-181">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d3d16-182">示例和教程</span><span class="sxs-lookup"><span data-stu-id="d3d16-182">Samples and tutorials</span></span>](../../../samples-and-tutorials/index.md)
- [<span data-ttu-id="d3d16-183">Main() 和命令行参数</span><span class="sxs-lookup"><span data-stu-id="d3d16-183">Main() and Command-Line Arguments</span></span>](../main-and-command-args/index.md)
- [<span data-ttu-id="d3d16-184">Visual C# 入门</span><span class="sxs-lookup"><span data-stu-id="d3d16-184">Getting Started with Visual C#</span></span>](/visualstudio/ide/quickstart-csharp-console)
