---
title: 使用 Visual Studio Code 通过 .NET Core 创建控制台应用程序
description: 了解如何使用 Visual Studio Code 和 .NET Core CLI 创建 .NET Core 控制台应用程序。
ms.date: 05/22/2020
ms.openlocfilehash: 673c4a639a2cab26261b7cdafd5d8e20acfafb94
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201706"
---
# <a name="tutorial-create-a-console-application-with-net-core-using-visual-studio-code"></a><span data-ttu-id="06f13-103">教程：使用 Visual Studio Code 通过 .NET Core 创建控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="06f13-103">Tutorial: Create a console application with .NET Core using Visual Studio Code</span></span>

<span data-ttu-id="06f13-104">本教程演示如何使用 Visual Studio Code 和 .NET Core CLI 创建并运行 .NET Core 控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="06f13-104">This tutorial shows how to create and run a .NET Core console application by using Visual Studio Code and the .NET Core CLI.</span></span> <span data-ttu-id="06f13-105">项目任务（如创建、编译和运行项目）是使用 CLI 完成的，因此，如果你愿意，可以使用其他代码编辑器来学习本教程并在终端中运行命令。</span><span class="sxs-lookup"><span data-stu-id="06f13-105">Project tasks, such as creating, compiling, and running a project are done by using the CLI, so you can follow this tutorial with a different code editor and run commands in a terminal if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="06f13-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="06f13-106">Prerequisites</span></span>

1. <span data-ttu-id="06f13-107">已安装 [C# 扩展](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) 的 [Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="06f13-107">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="06f13-108">有关如何在 Visual Studio Code 上安装扩展的信息，请访问 [VS Code 扩展市场](https://code.visualstudio.com/docs/editor/extension-gallery)。</span><span class="sxs-lookup"><span data-stu-id="06f13-108">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="06f13-109">[.NET Core 3.1 SDK 或更高版本](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="06f13-109">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-the-app"></a><span data-ttu-id="06f13-110">创建应用</span><span class="sxs-lookup"><span data-stu-id="06f13-110">Create the app</span></span>

1. <span data-ttu-id="06f13-111">打开 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="06f13-111">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="06f13-112">创建项目。</span><span class="sxs-lookup"><span data-stu-id="06f13-112">Create a project.</span></span>

   1. <span data-ttu-id="06f13-113">在主菜单中选择“文件” > “打开文件夹”/“打开…”，创建“HelloWorld”文件夹，然后单击“选择文件夹”/“打开”   。</span><span class="sxs-lookup"><span data-stu-id="06f13-113">Select **File** > **Open Folder**/**Open...** from the main menu, create a *HelloWorld* folder, and click **Select Folder**/**Open**.</span></span>

      <span data-ttu-id="06f13-114">默认情况下，文件夹名称将是项目名称和命名空间名称。</span><span class="sxs-lookup"><span data-stu-id="06f13-114">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="06f13-115">稍后将在本教程中添加代码，假定项目命名空间为 `HelloWorld`。</span><span class="sxs-lookup"><span data-stu-id="06f13-115">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

   1. <span data-ttu-id="06f13-116">在主菜单中选择“视图” > “终端”，从 Visual Studio Code 中打开“终端”  。</span><span class="sxs-lookup"><span data-stu-id="06f13-116">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

      <span data-ttu-id="06f13-117">“终端”在“HelloWorld”文件夹中连同命令提示符一起打开。</span><span class="sxs-lookup"><span data-stu-id="06f13-117">The **Terminal** opens with the command prompt in the *HelloWorld* folder.</span></span>

   1. <span data-ttu-id="06f13-118">在“终端”中输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="06f13-118">In the **Terminal**, enter the following command:</span></span>

      ```dotnetcli
      dotnet new console
      ```

<span data-ttu-id="06f13-119">.NET Core 控制台应用程序模板将定义类 `Program`，其中包含一个需要将 <xref:System.String> 数组用作参数的方法 `Main`。</span><span class="sxs-lookup"><span data-stu-id="06f13-119">The Console Application template for .NET Core defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="06f13-120">Program.cs 文件具有以下代码：</span><span class="sxs-lookup"><span data-stu-id="06f13-120">The *Program.cs* file has the following code:</span></span>

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="06f13-121">`Main` 是应用程序入口点，同时也是在应用程序启动时由运行时自动调用的方法。</span><span class="sxs-lookup"><span data-stu-id="06f13-121">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="06f13-122">*args* 数组中包含在应用程序启动时提供的所有命令行自变量。</span><span class="sxs-lookup"><span data-stu-id="06f13-122">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="06f13-123">该模板创建一个简单的应用程序，以调用 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法来显示“Hello World!”</span><span class="sxs-lookup"><span data-stu-id="06f13-123">The template creates a simple application that calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="06f13-124">显示文本字符串“Hello World!”。</span><span class="sxs-lookup"><span data-stu-id="06f13-124">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="06f13-125">运行应用</span><span class="sxs-lookup"><span data-stu-id="06f13-125">Run the app</span></span>

<span data-ttu-id="06f13-126">在“终端”中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="06f13-126">Run the following command in the **Terminal**:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="06f13-127">程序显示“Hello World!”</span><span class="sxs-lookup"><span data-stu-id="06f13-127">The program displays "Hello World!"</span></span> <span data-ttu-id="06f13-128">然后结束。</span><span class="sxs-lookup"><span data-stu-id="06f13-128">and ends.</span></span>

![dotnet run 命令](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a><span data-ttu-id="06f13-130">增强应用</span><span class="sxs-lookup"><span data-stu-id="06f13-130">Enhance the app</span></span>

<span data-ttu-id="06f13-131">改进应用程序，使其提示用户输入名字，并将其与日期和时间一同显示。</span><span class="sxs-lookup"><span data-stu-id="06f13-131">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="06f13-132">单击打开 *Program.cs*。</span><span class="sxs-lookup"><span data-stu-id="06f13-132">Open *Program.cs* by clicking on it.</span></span>

   <span data-ttu-id="06f13-133">在 Visual Studio Code 中首次打开 C# 文件时，会在编辑器中加载 [OmniSharp](https://www.omnisharp.net/)。</span><span class="sxs-lookup"><span data-stu-id="06f13-133">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

   ![打开 Program.cs 文件](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="06f13-135">Visual Studio Code 提示添加缺少的资产时选择“是”，以生成和调试应用。</span><span class="sxs-lookup"><span data-stu-id="06f13-135">Select **Yes** when Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span>

   ![提示添加缺少的资产](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="06f13-137">将 Program.cs 中 `Main` 方法的内容（当前只是调用 `Console.WriteLine` 的行）替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="06f13-137">Replace the contents of the `Main` method in *Program.cs*, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   <span data-ttu-id="06f13-138">此代码在控制台中显示“What is your name?”，</span><span class="sxs-lookup"><span data-stu-id="06f13-138">This code displays "What is your name?"</span></span> <span data-ttu-id="06f13-139">然后等待用户输入字符串并按 Enter。</span><span class="sxs-lookup"><span data-stu-id="06f13-139">in the console window and waits until the user enters a string followed by the **Enter** key.</span></span> <span data-ttu-id="06f13-140">它会将此字符串存储到名为 `name` 的变量中。</span><span class="sxs-lookup"><span data-stu-id="06f13-140">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="06f13-141">它还会检索 <xref:System.DateTime.Now?displayProperty=nameWithType> 属性的值（其中包含当前的本地时间），并将此值赋给 `date` 变量。</span><span class="sxs-lookup"><span data-stu-id="06f13-141">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="06f13-142">最后，它会在控制台窗口中显示这些值。</span><span class="sxs-lookup"><span data-stu-id="06f13-142">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="06f13-143">`\n` 表示一个换行符。</span><span class="sxs-lookup"><span data-stu-id="06f13-143">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="06f13-144">字符串前面的美元符号 (`$`) 使你可以将表达式（如变量名称）放入字符串中的大括号内。</span><span class="sxs-lookup"><span data-stu-id="06f13-144">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="06f13-145">表达式值将代替表达式插入到字符串中。</span><span class="sxs-lookup"><span data-stu-id="06f13-145">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="06f13-146">此语法称为[内插字符串](../../csharp/language-reference/tokens/interpolated.md)。</span><span class="sxs-lookup"><span data-stu-id="06f13-146">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="06f13-147">保存更改。</span><span class="sxs-lookup"><span data-stu-id="06f13-147">Save your changes.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="06f13-148">在 Visual Studio Code 中，必须显式保存更改。</span><span class="sxs-lookup"><span data-stu-id="06f13-148">In Visual Studio Code, you have to explicitly save changes.</span></span> <span data-ttu-id="06f13-149">与 Visual Studio 不同，生成和运行应用时不会自动保存文件更改。</span><span class="sxs-lookup"><span data-stu-id="06f13-149">Unlike Visual Studio, file changes are not automatically saved when you build and run an app.</span></span>

1. <span data-ttu-id="06f13-150">再次运行程序：</span><span class="sxs-lookup"><span data-stu-id="06f13-150">Run the program again:</span></span>

   ```dotnetcli
   dotnet run
   ```

1. <span data-ttu-id="06f13-151">出现提示时，输入名称并按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="06f13-151">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="包含经过修改的程序输出的“终端”窗口":::

1. <span data-ttu-id="06f13-153">按任意键退出程序。</span><span class="sxs-lookup"><span data-stu-id="06f13-153">Press any key to exit the program.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="06f13-154">其他资源</span><span class="sxs-lookup"><span data-stu-id="06f13-154">Additional resources</span></span>

- [<span data-ttu-id="06f13-155">设置 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="06f13-155">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a><span data-ttu-id="06f13-156">后续步骤</span><span class="sxs-lookup"><span data-stu-id="06f13-156">Next steps</span></span>

<span data-ttu-id="06f13-157">在本教程中，你创建了一个 .NET Core 应用程序。</span><span class="sxs-lookup"><span data-stu-id="06f13-157">In this tutorial, you created a .NET Core application.</span></span> <span data-ttu-id="06f13-158">在下一教程中，你将调试该应用。</span><span class="sxs-lookup"><span data-stu-id="06f13-158">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="06f13-159">使用 Visual Studio Code 调试 .NET Core 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="06f13-159">Debug a .NET Core console application using Visual Studio Code</span></span>](debugging-with-visual-studio-code.md)
