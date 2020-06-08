---
title: 在 Visual Studio 中使用 .NET Core 创建控制台应用程序
description: 了解如何使用 Visual Studio 通过 C# 或 Visual Basic 创建 .NET Core 控制台应用程序。
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 144d7bb087034839ad2cde2fa28a4961cff4321f
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306989"
---
# <a name="tutorial-create-a-net-core-console-application-in-visual-studio-2019"></a><span data-ttu-id="79b9e-103">教程：在 Visual Studio 2019 中创建 .NET Core 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="79b9e-103">Tutorial: Create a .NET Core console application in Visual Studio 2019</span></span>

<span data-ttu-id="79b9e-104">本教程演示如何在 Visual Studio 2019 中创建和运行 .NET Core 控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="79b9e-104">This tutorial shows how to create and run a .NET Core console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="79b9e-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="79b9e-105">Prerequisites</span></span>

- <span data-ttu-id="79b9e-106">安装了具有“.NET Core 跨平台开发”工作负载的 [Visual Studio 2019 版本 16.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="79b9e-106">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="79b9e-107">选择此工作负载时，将自动安装 .NET Core 3.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="79b9e-107">The .NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="79b9e-108">有关详细信息，请参阅[安装 .NET Core SDK](../install/sdk.md?pivots=os-windows) 一文中的[在 Visual Studio 中安装](../install/sdk.md?pivots=os-windows#install-with-visual-studio)部分。</span><span class="sxs-lookup"><span data-stu-id="79b9e-108">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="79b9e-109">创建应用</span><span class="sxs-lookup"><span data-stu-id="79b9e-109">Create the app</span></span>

<!-- markdownlint-disable MD025 -->

1. <span data-ttu-id="79b9e-110">打开 Visual Studio 2019。</span><span class="sxs-lookup"><span data-stu-id="79b9e-110">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="79b9e-111">创建一个名为“HelloWorld”的新 .NET Core 控制台应用项目。</span><span class="sxs-lookup"><span data-stu-id="79b9e-111">Create a new .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="79b9e-112">在“开始”页上，选择“创建新项目”。</span><span class="sxs-lookup"><span data-stu-id="79b9e-112">On the start page, choose **Create a new project**.</span></span>

      ![在 Visual Studio“开始”页选择“创建新项目”按钮](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="79b9e-114">在“创建新项目”页面，在搜索框中输入“控制台”。</span><span class="sxs-lookup"><span data-stu-id="79b9e-114">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="79b9e-115">接下来，从“语言”列表中选择“C#”或“Visual Basic”，然后从“平台”列表中选择“所有平台”  。</span><span class="sxs-lookup"><span data-stu-id="79b9e-115">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="79b9e-116">选择“控制台应用 (.NET Core)”模板，然后选择“下一步”。</span><span class="sxs-lookup"><span data-stu-id="79b9e-116">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![使用所选筛选器创建新项目窗口](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="79b9e-118">如果看不到 .NET Core 模板，则可能缺少所需的工作负载。</span><span class="sxs-lookup"><span data-stu-id="79b9e-118">If you don't see the .NET Core templates, you're probably missing the required workload.</span></span> <span data-ttu-id="79b9e-119">在“找不到所需内容?”消息下，选择“安装更多工具和功能”链接。</span><span class="sxs-lookup"><span data-stu-id="79b9e-119">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="79b9e-120">Visual Studio 安装程序随即打开。</span><span class="sxs-lookup"><span data-stu-id="79b9e-120">The Visual Studio Installer opens.</span></span> <span data-ttu-id="79b9e-121">确保安装了“.NET Core 跨平台开发”工作负载。</span><span class="sxs-lookup"><span data-stu-id="79b9e-121">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="79b9e-122">在“配置新项目”页面，在“项目名称”框中输入“HelloWorld”。</span><span class="sxs-lookup"><span data-stu-id="79b9e-122">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="79b9e-123">然后选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="79b9e-123">Then choose **Create**.</span></span>

      ![为新项目窗口配置“项目名称”、“位置”和“解决方案名称”字段](./media/with-visual-studio/configure-new-project.png)

   <span data-ttu-id="79b9e-125">.NET Core 控制台应用程序模板将定义类 `Program`，其中包含一个需要将 <xref:System.String> 数组用作参数的方法 `Main`。</span><span class="sxs-lookup"><span data-stu-id="79b9e-125">The Console Application template for .NET Core defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="79b9e-126">`Main` 是应用程序入口点，同时也是在应用程序启动时由运行时自动调用的方法。</span><span class="sxs-lookup"><span data-stu-id="79b9e-126">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="79b9e-127">*args* 数组中包含在应用程序启动时提供的所有命令行自变量。</span><span class="sxs-lookup"><span data-stu-id="79b9e-127">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   <span data-ttu-id="79b9e-128">如果未显示想要使用的语言，请更改页面顶部的语言选择器。</span><span class="sxs-lookup"><span data-stu-id="79b9e-128">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

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

   ```vb
   Imports System

   Module Program
       Sub Main(args As String())
           Console.WriteLine("Hello World!")
       End Sub
   End Module
   ```

   <span data-ttu-id="79b9e-129">用于创建简单的“Hello World”应用程序的模板。</span><span class="sxs-lookup"><span data-stu-id="79b9e-129">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="79b9e-130">它会调用 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法来显示“Hello World!”</span><span class="sxs-lookup"><span data-stu-id="79b9e-130">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="79b9e-131">显示文本字符串“Hello World!”。</span><span class="sxs-lookup"><span data-stu-id="79b9e-131">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="79b9e-132">运行应用</span><span class="sxs-lookup"><span data-stu-id="79b9e-132">Run the app</span></span>

1. <span data-ttu-id="79b9e-133">若要运行程序，请在工具栏上选择“HelloWorld”，或按 F5。</span><span class="sxs-lookup"><span data-stu-id="79b9e-133">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

   ![已选择“HelloWorld 运行”按钮的 Visual Studio 工具栏](./media/with-visual-studio/run-program.png)

   <span data-ttu-id="79b9e-135">此时将打开在屏幕上显示文本“Hello World!”</span><span class="sxs-lookup"><span data-stu-id="79b9e-135">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="79b9e-136">并附带一些 Visual Studio 调试信息的控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="79b9e-136">printed on the screen and some Visual Studio debug information.</span></span>

   ![控制台窗口，其中显示 Hello World Press any key to continue](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="79b9e-138">按任意键关闭控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="79b9e-138">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="79b9e-139">增强应用</span><span class="sxs-lookup"><span data-stu-id="79b9e-139">Enhance the app</span></span>

<span data-ttu-id="79b9e-140">改进应用程序，使其提示用户输入名字，并将其与日期和时间一同显示。</span><span class="sxs-lookup"><span data-stu-id="79b9e-140">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="79b9e-141">以下指令可修改应用并再次运行应用：</span><span class="sxs-lookup"><span data-stu-id="79b9e-141">The following instructions modify the app and run it again:</span></span>

1. <span data-ttu-id="79b9e-142">将 `Main` 方法的内容（当前只是调用 `Console.WriteLine` 的行）替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="79b9e-142">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-csharp[GettingStarted#1](./snippets/with-visual-studio/csharp/Program.cs#1)]
   [!code-vb[GettingStarted#1](./snippets/with-visual-studio/vb/Program.vb#1)]

   <span data-ttu-id="79b9e-143">此代码在控制台中显示“What is your name?”，</span><span class="sxs-lookup"><span data-stu-id="79b9e-143">This code displays "What is your name?"</span></span> <span data-ttu-id="79b9e-144">然后等待用户输入字符串并按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="79b9e-144">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="79b9e-145">它会将此字符串存储到名为 `name` 的变量中。</span><span class="sxs-lookup"><span data-stu-id="79b9e-145">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="79b9e-146">它还会检索 <xref:System.DateTime.Now?displayProperty=nameWithType> 属性的值（其中包含当前的本地时间），并将此值赋给 `date` 变量（Visual Basic 中为 `currentDate`）。</span><span class="sxs-lookup"><span data-stu-id="79b9e-146">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="79b9e-147">最后，它会在控制台窗口中显示这些值。</span><span class="sxs-lookup"><span data-stu-id="79b9e-147">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="79b9e-148">`\n`（Visual Basic 中为 `vbCrLf`）表示换行符。</span><span class="sxs-lookup"><span data-stu-id="79b9e-148">The `\n` (`vbCrLf` in Visual Basic) represents a newline character.</span></span>

   <span data-ttu-id="79b9e-149">字符串前面的美元符号 (`$`) 使你可以将表达式（如变量名称）放入字符串中的大括号内。</span><span class="sxs-lookup"><span data-stu-id="79b9e-149">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="79b9e-150">表达式值将代替表达式插入到字符串中。</span><span class="sxs-lookup"><span data-stu-id="79b9e-150">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="79b9e-151">此语法称为[内插字符串](../../csharp/language-reference/tokens/interpolated.md)。</span><span class="sxs-lookup"><span data-stu-id="79b9e-151">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="79b9e-152">若要运行程序，请在工具栏上选择“HelloWorld”，或按 F5。</span><span class="sxs-lookup"><span data-stu-id="79b9e-152">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="79b9e-153">出现提示时，输入名称并按 Enter 键。</span><span class="sxs-lookup"><span data-stu-id="79b9e-153">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![控制台窗口，含已修改程序的输出](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="79b9e-155">按任意键关闭控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="79b9e-155">Press any key to close the console window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="79b9e-156">后续步骤</span><span class="sxs-lookup"><span data-stu-id="79b9e-156">Next steps</span></span>

<span data-ttu-id="79b9e-157">在本教程中，你创建了一个 .NET Core 应用程序。</span><span class="sxs-lookup"><span data-stu-id="79b9e-157">In this tutorial, you created a .NET Core application.</span></span> <span data-ttu-id="79b9e-158">在下一教程中，你将调试该应用。</span><span class="sxs-lookup"><span data-stu-id="79b9e-158">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="79b9e-159">在 Visual Studio 中调试 .NET Core 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="79b9e-159">Debug a .NET Core console application in Visual Studio</span></span>](debugging-with-visual-studio.md)
