---
title: 使用 Visual Studio 创建 .NET Core 控制台应用程序
description: 了解如何使用 Visual Studio 通过 C# 或 Visual Basic 创建 .NET Core 控制台应用程序。
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 7ef8e17b8a42defc0858123332976d30c83f20c8
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84700427"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="53697-103">教程：使用 Visual Studio 创建 .NET Core 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="53697-103">Tutorial: Create a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="53697-104">本教程演示如何在 Visual Studio 2019 中创建和运行 .NET Core 控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="53697-104">This tutorial shows how to create and run a .NET Core console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="53697-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="53697-105">Prerequisites</span></span>

- <span data-ttu-id="53697-106">安装了具有“.NET Core 跨平台开发”工作负载的 [Visual Studio 2019 版本 16.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="53697-106">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="53697-107">选择此工作负载时，将自动安装 .NET Core 3.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="53697-107">The .NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="53697-108">有关详细信息，请参阅[在 Visual Studio 中安装 .NET Core SDK](../install/sdk.md?pivots=os-windows#install-with-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="53697-108">For more information, see [Install the .NET Core SDK with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="53697-109">创建应用</span><span class="sxs-lookup"><span data-stu-id="53697-109">Create the app</span></span>

<span data-ttu-id="53697-110">创建一个名为“HelloWorld”的 .NET Core 控制台应用项目。</span><span class="sxs-lookup"><span data-stu-id="53697-110">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="53697-111">启动 Visual Studio 2019。</span><span class="sxs-lookup"><span data-stu-id="53697-111">Start Visual Studio 2019.</span></span>

1. <span data-ttu-id="53697-112">在“开始”页上，选择“创建新项目”。</span><span class="sxs-lookup"><span data-stu-id="53697-112">On the start page, choose **Create a new project**.</span></span>

   ![在 Visual Studio“开始”页选择“创建新项目”按钮](./media/with-visual-studio/start-window.png)

1. <span data-ttu-id="53697-114">在“创建新项目”页面，在搜索框中输入“控制台”。</span><span class="sxs-lookup"><span data-stu-id="53697-114">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="53697-115">接下来，从“语言”列表中选择“C#”或“Visual Basic”，然后从“平台”列表中选择“所有平台”  。</span><span class="sxs-lookup"><span data-stu-id="53697-115">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="53697-116">选择“控制台应用 (.NET Core)”模板，然后选择“下一步”。</span><span class="sxs-lookup"><span data-stu-id="53697-116">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   ![使用所选筛选器创建新项目窗口](./media/with-visual-studio/create-new-project.png)

   > [!TIP]
   > <span data-ttu-id="53697-118">如果看不到 .NET Core 模板，则可能缺少所需的工作负载。</span><span class="sxs-lookup"><span data-stu-id="53697-118">If you don't see the .NET Core templates, you're probably missing the required workload.</span></span> <span data-ttu-id="53697-119">在“找不到所需内容?”消息下，选择“安装更多工具和功能”链接。</span><span class="sxs-lookup"><span data-stu-id="53697-119">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="53697-120">Visual Studio 安装程序随即打开。</span><span class="sxs-lookup"><span data-stu-id="53697-120">The Visual Studio Installer opens.</span></span> <span data-ttu-id="53697-121">确保安装了“.NET Core 跨平台开发”工作负载。</span><span class="sxs-lookup"><span data-stu-id="53697-121">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

1. <span data-ttu-id="53697-122">在“配置新项目”对话框中，在“项目名称”框中输入“HelloWorld”。</span><span class="sxs-lookup"><span data-stu-id="53697-122">In the **Configure your new project** dialog,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="53697-123">然后选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="53697-123">Then choose **Create**.</span></span>

   ![为新项目窗口配置“项目名称”、“位置”和“解决方案名称”字段](./media/with-visual-studio/configure-new-project.png)

<span data-ttu-id="53697-125">用于创建简单的“Hello World”应用程序的模板。</span><span class="sxs-lookup"><span data-stu-id="53697-125">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="53697-126">它会调用 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法来显示“Hello World!”</span><span class="sxs-lookup"><span data-stu-id="53697-126">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="53697-127">显示文本字符串“Hello World!”。</span><span class="sxs-lookup"><span data-stu-id="53697-127">in the console window.</span></span>

<span data-ttu-id="53697-128">模板代码将定义类 `Program`，其中包含一个需要将 <xref:System.String> 数组用作参数的方法 `Main`：</span><span class="sxs-lookup"><span data-stu-id="53697-128">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="53697-129">`Main` 是应用程序入口点，同时也是在应用程序启动时由运行时自动调用的方法。</span><span class="sxs-lookup"><span data-stu-id="53697-129">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="53697-130">*args* 数组中包含在应用程序启动时提供的所有命令行自变量。</span><span class="sxs-lookup"><span data-stu-id="53697-130">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="53697-131">如果未显示想要使用的语言，请更改页面顶部的语言选择器。</span><span class="sxs-lookup"><span data-stu-id="53697-131">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="53697-132">运行应用</span><span class="sxs-lookup"><span data-stu-id="53697-132">Run the app</span></span>

1. <span data-ttu-id="53697-133">按 <kbd>Shift</kbd>+<kbd>F5</kbd> 运行程序而不进行调试。</span><span class="sxs-lookup"><span data-stu-id="53697-133">Press <kbd>Shift</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

   <span data-ttu-id="53697-134">此时将打开在屏幕上显示文本“Hello World!”</span><span class="sxs-lookup"><span data-stu-id="53697-134">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="53697-135">并附带一些 Visual Studio 调试信息的控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="53697-135">printed on the screen and some Visual Studio debug information.</span></span>

   ![控制台窗口，其中显示 Hello World Press any key to continue](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="53697-137">按任意键关闭控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="53697-137">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="53697-138">增强应用</span><span class="sxs-lookup"><span data-stu-id="53697-138">Enhance the app</span></span>

<span data-ttu-id="53697-139">改进应用程序，使其提示用户输入名字，并将其与日期和时间一同显示。</span><span class="sxs-lookup"><span data-stu-id="53697-139">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="53697-140">在 Program.cs 或 Program.vb 中，将 `Main` 方法的内容（当前只是调用 `Console.WriteLine` 的行）替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="53697-140">In *Program.cs* or *Program.vb*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-csharp[GettingStarted#1](./snippets/with-visual-studio/csharp/Program.cs#1)]
   [!code-vb[GettingStarted#1](./snippets/with-visual-studio/vb/Program.vb#1)]

   <span data-ttu-id="53697-141">此代码在控制台中显示“What is your name?”，</span><span class="sxs-lookup"><span data-stu-id="53697-141">This code displays "What is your name?"</span></span> <span data-ttu-id="53697-142">然后等待用户输入字符串并按 Enter<kbd></kbd>。</span><span class="sxs-lookup"><span data-stu-id="53697-142">in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="53697-143">它会将此字符串存储到名为 `name` 的变量中。</span><span class="sxs-lookup"><span data-stu-id="53697-143">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="53697-144">它还会检索 <xref:System.DateTime.Now?displayProperty=nameWithType> 属性的值（其中包含当前的本地时间），并将此值赋给 `date` 变量（Visual Basic 中为 `currentDate`）。</span><span class="sxs-lookup"><span data-stu-id="53697-144">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="53697-145">最后，它会在控制台窗口中显示这些值。</span><span class="sxs-lookup"><span data-stu-id="53697-145">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="53697-146">`\n`（Visual Basic 中为 `vbCrLf`）表示换行符。</span><span class="sxs-lookup"><span data-stu-id="53697-146">The `\n` (`vbCrLf` in Visual Basic) represents a newline character.</span></span>

   <span data-ttu-id="53697-147">字符串前面的美元符号 (`$`) 使你可以将表达式（如变量名称）放入字符串中的大括号内。</span><span class="sxs-lookup"><span data-stu-id="53697-147">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="53697-148">表达式值将代替表达式插入到字符串中。</span><span class="sxs-lookup"><span data-stu-id="53697-148">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="53697-149">此语法称为[内插字符串](../../csharp/language-reference/tokens/interpolated.md)。</span><span class="sxs-lookup"><span data-stu-id="53697-149">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="53697-150">按 <kbd>Shift</kbd>+<kbd>F5</kbd> 运行程序而不进行调试。</span><span class="sxs-lookup"><span data-stu-id="53697-150">Press <kbd>Shift</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

1. <span data-ttu-id="53697-151">出现提示时，输入名称并按 Enter<kbd></kbd> 键。</span><span class="sxs-lookup"><span data-stu-id="53697-151">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   ![控制台窗口，含已修改程序的输出](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="53697-153">按任意键关闭控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="53697-153">Press any key to close the console window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="53697-154">后续步骤</span><span class="sxs-lookup"><span data-stu-id="53697-154">Next steps</span></span>

<span data-ttu-id="53697-155">在本教程中，你创建了一个 .NET Core 控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="53697-155">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="53697-156">在下一教程中，你将调试该应用。</span><span class="sxs-lookup"><span data-stu-id="53697-156">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="53697-157">在 Visual Studio 中调试 .NET Core 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="53697-157">Debug a .NET Core console application in Visual Studio</span></span>](debugging-with-visual-studio.md)
