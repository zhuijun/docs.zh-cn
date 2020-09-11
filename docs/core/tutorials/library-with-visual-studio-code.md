---
title: 在 Visual Studio Code 中创建 .NET Standard 类库
description: 了解如何使用 Visual Studio Code 创建 .NET Standard 类库。
ms.date: 06/08/2020
ms.openlocfilehash: 966b9b0b48f67809e82d9133c523995cd97b6015
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495507"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-code"></a><span data-ttu-id="a925b-103">教程：在 Visual Studio Code 中创建 .NET Standard 库</span><span class="sxs-lookup"><span data-stu-id="a925b-103">Tutorial: Create a .NET Standard library using Visual Studio Code</span></span>

<span data-ttu-id="a925b-104">在本教程中，将创建包含一个字符串处理方法的简单实用工具库。</span><span class="sxs-lookup"><span data-stu-id="a925b-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="a925b-105">我们把它作为[扩展方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)进行实现，这样就可以把它作为 <xref:System.String> 类成员进行调用。</span><span class="sxs-lookup"><span data-stu-id="a925b-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="a925b-106">类库定义的是可以由应用程序调用的类型和方法。</span><span class="sxs-lookup"><span data-stu-id="a925b-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="a925b-107">借助面向 .NET Standard 2.0 的类库，任何支持相应 .NET Standard 版本的 .NET 实现都可以调用库。</span><span class="sxs-lookup"><span data-stu-id="a925b-107">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="a925b-108">完成类库后，可以将其作为第三方组件进行分发，也可以作为与一个或多个应用程序捆绑在一起的组件进行分发。</span><span class="sxs-lookup"><span data-stu-id="a925b-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a925b-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="a925b-109">Prerequisites</span></span>

1. <span data-ttu-id="a925b-110">已安装 [C# 扩展](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) 的 [Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="a925b-110">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="a925b-111">有关如何在 Visual Studio Code 上安装扩展的信息，请访问 [VS Code 扩展市场](https://code.visualstudio.com/docs/editor/extension-gallery)。</span><span class="sxs-lookup"><span data-stu-id="a925b-111">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="a925b-112">[.NET Core 3.1 SDK 或更高版本](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="a925b-112">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="a925b-113">创建解决方案</span><span class="sxs-lookup"><span data-stu-id="a925b-113">Create a solution</span></span>

<span data-ttu-id="a925b-114">首先，创建一个空白解决方案来放置类库项目。</span><span class="sxs-lookup"><span data-stu-id="a925b-114">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="a925b-115">解决方案用作一个或多个项目的容器。</span><span class="sxs-lookup"><span data-stu-id="a925b-115">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="a925b-116">将其他相关项目添加到同一个解决方案中。</span><span class="sxs-lookup"><span data-stu-id="a925b-116">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="a925b-117">启动 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="a925b-117">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="a925b-118">从主菜单中选择“文件” > “打开文件夹”（在 macOS 上为“打开...”）</span><span class="sxs-lookup"><span data-stu-id="a925b-118">Select **File** > **Open Folder** (**Open...** on macOS) from the main menu</span></span>

1. <span data-ttu-id="a925b-119">在“打开文件夹”对话框中，创建“ClassLibraryProjects”文件夹，然后单击“选择文件夹”（在 macOS 上为“打开”）。</span><span class="sxs-lookup"><span data-stu-id="a925b-119">In the **Open Folder** dialog, create a *ClassLibraryProjects* folder and click **Select Folder** (**Open** on macOS).</span></span>

1. <span data-ttu-id="a925b-120">在主菜单中选择“视图” > “终端”，从 Visual Studio Code 中打开“终端”  。</span><span class="sxs-lookup"><span data-stu-id="a925b-120">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="a925b-121">“终端”在“ClassLibraryProjects”文件夹中连同命令提示符一起打开。</span><span class="sxs-lookup"><span data-stu-id="a925b-121">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="a925b-122">在“终端”中输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="a925b-122">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="a925b-123">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="a925b-123">The terminal output looks like the following example:</span></span>

   ```output
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="a925b-124">创建类库项目</span><span class="sxs-lookup"><span data-stu-id="a925b-124">Create a class library project</span></span>

<span data-ttu-id="a925b-125">将名为“StringLibrary”的新 .NET Standard 类库项目添加到解决方案。</span><span class="sxs-lookup"><span data-stu-id="a925b-125">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="a925b-126">在终端中，运行以下命令创建库项目：</span><span class="sxs-lookup"><span data-stu-id="a925b-126">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="a925b-127">`-o` 或 `--output` 命令指定用于放置生成的输出的位置。</span><span class="sxs-lookup"><span data-stu-id="a925b-127">The `-o` or `--output` command specifies the location to place the generated output.</span></span>

   <span data-ttu-id="a925b-128">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="a925b-128">The terminal output looks like the following example:</span></span>

   ```output
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj (in 328 ms).
   Restore succeeded.
   ```

1. <span data-ttu-id="a925b-129">运行以下命令，向解决方案添加库项目：</span><span class="sxs-lookup"><span data-stu-id="a925b-129">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="a925b-130">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="a925b-130">The terminal output looks like the following example:</span></span>

   ```output
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="a925b-131">请检查以确保库面向 .NET Standard 的正确版本。</span><span class="sxs-lookup"><span data-stu-id="a925b-131">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="a925b-132">在资源管理器中，打开 StringLibrary/StringLibrary.csproj。</span><span class="sxs-lookup"><span data-stu-id="a925b-132">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="a925b-133">`TargetFramework` 元素表明项目面向 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="a925b-133">The `TargetFramework` element shows that the project targets .NET Standard 2.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="a925b-134">打开 Class1.cs 并将代码替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="a925b-134">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="a925b-135">类库 `UtilityLibraries.StringLibrary`包含一个名为 `StartsWithUpper` 的方法。</span><span class="sxs-lookup"><span data-stu-id="a925b-135">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="a925b-136">此方法会返回 <xref:System.Boolean> 值，以指明当前字符串实例是否以大写字符开头。</span><span class="sxs-lookup"><span data-stu-id="a925b-136">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="a925b-137">Unicode 标准会区分大小写字符。</span><span class="sxs-lookup"><span data-stu-id="a925b-137">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="a925b-138">如果为大写字符，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="a925b-138">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="a925b-139">保存该文件。</span><span class="sxs-lookup"><span data-stu-id="a925b-139">Save the file.</span></span>

1. <span data-ttu-id="a925b-140">运行以下命令以生成解决方案，并验证项目是否正确编译。</span><span class="sxs-lookup"><span data-stu-id="a925b-140">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="a925b-141">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="a925b-141">The terminal output looks like the following example:</span></span>

   ```output
   Microsoft (R) Build Engine version 16.7.0+b89cb5fde for .NET
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\netstandard2.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="a925b-142">向解决方案添加控制台应用</span><span class="sxs-lookup"><span data-stu-id="a925b-142">Add a console app to the solution</span></span>

<span data-ttu-id="a925b-143">添加使用类库的控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="a925b-143">Add a console application that uses the class library.</span></span> <span data-ttu-id="a925b-144">应用将提示用户输入字符串，并报告字符串是否以大写字符开头。</span><span class="sxs-lookup"><span data-stu-id="a925b-144">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="a925b-145">在终端中，运行以下命令创建控制台应用项目：</span><span class="sxs-lookup"><span data-stu-id="a925b-145">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="a925b-146">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="a925b-146">The terminal output looks like the following example:</span></span>

   ```output
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj (in 210 ms).
   Restore succeeded.
   ```

1. <span data-ttu-id="a925b-147">运行以下命令，向解决方案添加控制台应用项目：</span><span class="sxs-lookup"><span data-stu-id="a925b-147">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="a925b-148">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="a925b-148">The terminal output looks like the following example:</span></span>

   ```output
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="a925b-149">打开 ShowCase/Program.cs 并将所有代码替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="a925b-149">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="a925b-150">该代码使用 `row` 变量来维护写入到控制台窗口的数据行数计数。</span><span class="sxs-lookup"><span data-stu-id="a925b-150">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="a925b-151">如果大于或等于 25，该代码将清除控制台窗口，并向用户显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="a925b-151">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="a925b-152">该程序会提示用户输入字符串。</span><span class="sxs-lookup"><span data-stu-id="a925b-152">The program prompts the user to enter a string.</span></span> <span data-ttu-id="a925b-153">它会指明字符串是否以大写字符开头。</span><span class="sxs-lookup"><span data-stu-id="a925b-153">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="a925b-154">如果用户没有输入字符串就按 <kbd>Enter</kbd> 键，那么应用程序会终止，控制台窗口会关闭。</span><span class="sxs-lookup"><span data-stu-id="a925b-154">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="a925b-155">保存更改。</span><span class="sxs-lookup"><span data-stu-id="a925b-155">Save your changes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="a925b-156">添加项目引用</span><span class="sxs-lookup"><span data-stu-id="a925b-156">Add a project reference</span></span>

<span data-ttu-id="a925b-157">最初，新的控制台应用项目无权访问类库。</span><span class="sxs-lookup"><span data-stu-id="a925b-157">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="a925b-158">若要允许该项目调用类库中的方法，可以创建对类库项目的项目引用。</span><span class="sxs-lookup"><span data-stu-id="a925b-158">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="a925b-159">运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="a925b-159">Run the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/ShowCase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="a925b-160">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="a925b-160">The terminal output looks like the following example:</span></span>

   ```output
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a><span data-ttu-id="a925b-161">运行应用</span><span class="sxs-lookup"><span data-stu-id="a925b-161">Run the app</span></span>

1. <span data-ttu-id="a925b-162">在终端中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a925b-162">Run the following command in the terminal:</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="a925b-163">输入字符串并按 Enter 以试用程序，然后按 Enter 退出<kbd></kbd><kbd></kbd>。</span><span class="sxs-lookup"><span data-stu-id="a925b-163">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="a925b-164">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="a925b-164">The terminal output looks like the following example:</span></span>

   ```output
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   a string that starts with a lowercase letter
   Input: a string that starts with a lowercase letter
   Begins with uppercase? : No
   ```

## <a name="additional-resources"></a><span data-ttu-id="a925b-165">其他资源</span><span class="sxs-lookup"><span data-stu-id="a925b-165">Additional resources</span></span>

* [<span data-ttu-id="a925b-166">使用 .NET Core CLI 开发库</span><span class="sxs-lookup"><span data-stu-id="a925b-166">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="a925b-167">[.NET Standard 版本及其支持的平台](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="a925b-167">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a925b-168">后续步骤</span><span class="sxs-lookup"><span data-stu-id="a925b-168">Next steps</span></span>

<span data-ttu-id="a925b-169">在本教程中，你创建了一个解决方案，添加了一个库项目，并添加了一个使用该库的控制台应用项目。</span><span class="sxs-lookup"><span data-stu-id="a925b-169">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="a925b-170">在下一教程中，将向解决方案中添加单元测试项目。</span><span class="sxs-lookup"><span data-stu-id="a925b-170">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a925b-171">在 Visual Studio Code 中使用 .NET Core 测试 .NET Standard 库</span><span class="sxs-lookup"><span data-stu-id="a925b-171">Test a .NET Standard library with .NET Core using Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
