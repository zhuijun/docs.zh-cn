---
title: 在 Visual Studio Code 中创建 .NET Standard 类库
description: 了解如何使用 Visual Studio Code 创建 .NET Standard 类库。
ms.date: 06/08/2020
ms.openlocfilehash: f7d2319bcea58f63ca40e43ba39745bdf1b394ce
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701794"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-code"></a><span data-ttu-id="001ad-103">教程：在 Visual Studio Code 中创建 .NET Standard 库</span><span class="sxs-lookup"><span data-stu-id="001ad-103">Tutorial: Create a .NET Standard library using Visual Studio Code</span></span>

<span data-ttu-id="001ad-104">在本教程中，将创建包含一个字符串处理方法的简单实用工具库。</span><span class="sxs-lookup"><span data-stu-id="001ad-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="001ad-105">我们把它作为[扩展方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)进行实现，这样就可以把它作为 <xref:System.String> 类成员进行调用。</span><span class="sxs-lookup"><span data-stu-id="001ad-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="001ad-106">类库定义的是可以由应用程序调用的类型和方法。</span><span class="sxs-lookup"><span data-stu-id="001ad-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="001ad-107">借助面向 .NET Standard 2.0 的类库，任何支持相应 .NET Standard 版本的 .NET 实现都可以调用库。</span><span class="sxs-lookup"><span data-stu-id="001ad-107">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="001ad-108">完成类库后，可以将其作为第三方组件进行分发，也可以作为与一个或多个应用程序捆绑在一起的组件进行分发。</span><span class="sxs-lookup"><span data-stu-id="001ad-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="001ad-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="001ad-109">Prerequisites</span></span>

1. <span data-ttu-id="001ad-110">已安装 [C# 扩展](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) 的 [Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="001ad-110">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="001ad-111">有关如何在 Visual Studio Code 上安装扩展的信息，请访问 [VS Code 扩展市场](https://code.visualstudio.com/docs/editor/extension-gallery)。</span><span class="sxs-lookup"><span data-stu-id="001ad-111">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="001ad-112">[.NET Core 3.1 SDK 或更高版本](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="001ad-112">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="001ad-113">创建解决方案</span><span class="sxs-lookup"><span data-stu-id="001ad-113">Create a solution</span></span>

<span data-ttu-id="001ad-114">首先，创建一个空白解决方案来放置类库项目。</span><span class="sxs-lookup"><span data-stu-id="001ad-114">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="001ad-115">解决方案用作一个或多个项目的容器。</span><span class="sxs-lookup"><span data-stu-id="001ad-115">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="001ad-116">将其他相关项目添加到同一个解决方案中。</span><span class="sxs-lookup"><span data-stu-id="001ad-116">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="001ad-117">启动 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="001ad-117">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="001ad-118">从主菜单中选择“文件” > “打开文件夹”（在 macOS 上为“打开...”）</span><span class="sxs-lookup"><span data-stu-id="001ad-118">Select **File** > **Open Folder** (**Open...** on macOS) from the main menu</span></span>

1. <span data-ttu-id="001ad-119">在“打开文件夹”对话框中，创建“ClassLibraryProjects”文件夹，然后单击“选择文件夹”（在 macOS 上为“打开”）。</span><span class="sxs-lookup"><span data-stu-id="001ad-119">In the **Open Folder** dialog, create a *ClassLibraryProjects* folder and click **Select Folder** (**Open** on macOS).</span></span>

1. <span data-ttu-id="001ad-120">在主菜单中选择“视图” > “终端”，从 Visual Studio Code 中打开“终端”  。</span><span class="sxs-lookup"><span data-stu-id="001ad-120">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="001ad-121">“终端”在“ClassLibraryProjects”文件夹中连同命令提示符一起打开。</span><span class="sxs-lookup"><span data-stu-id="001ad-121">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="001ad-122">在“终端”中输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="001ad-122">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="001ad-123">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="001ad-123">The terminal output looks like the following example:</span></span>

   ```
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="001ad-124">创建类库项目</span><span class="sxs-lookup"><span data-stu-id="001ad-124">Create a class library project</span></span>

<span data-ttu-id="001ad-125">将名为“StringLibrary”的新 .NET Standard 类库项目添加到解决方案。</span><span class="sxs-lookup"><span data-stu-id="001ad-125">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="001ad-126">在终端中，运行以下命令创建库项目：</span><span class="sxs-lookup"><span data-stu-id="001ad-126">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="001ad-127">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="001ad-127">The terminal output looks like the following example:</span></span>

   ```
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="001ad-128">运行以下命令，向解决方案添加库项目：</span><span class="sxs-lookup"><span data-stu-id="001ad-128">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="001ad-129">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="001ad-129">The terminal output looks like the following example:</span></span>

   ```
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="001ad-130">请检查以确保库面向 .NET Standard 的正确版本。</span><span class="sxs-lookup"><span data-stu-id="001ad-130">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="001ad-131">在资源管理器中，打开 StringLibrary/StringLibrary.csproj。</span><span class="sxs-lookup"><span data-stu-id="001ad-131">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="001ad-132">`TargetFramework` 元素表明项目面向 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="001ad-132">The `TargetFramework` element shows that the project targets .NET Standard 2.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="001ad-133">打开 Class1.cs 并将代码替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="001ad-133">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="001ad-134">类库 `UtilityLibraries.StringLibrary`包含一个名为 `StartsWithUpper` 的方法。</span><span class="sxs-lookup"><span data-stu-id="001ad-134">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="001ad-135">此方法会返回 <xref:System.Boolean> 值，以指明当前字符串实例是否以大写字符开头。</span><span class="sxs-lookup"><span data-stu-id="001ad-135">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="001ad-136">Unicode 标准会区分大小写字符。</span><span class="sxs-lookup"><span data-stu-id="001ad-136">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="001ad-137">如果为大写字符，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="001ad-137">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="001ad-138">保存该文件。</span><span class="sxs-lookup"><span data-stu-id="001ad-138">Save the file.</span></span>

1. <span data-ttu-id="001ad-139">运行以下命令以生成解决方案，并验证项目是否正确编译。</span><span class="sxs-lookup"><span data-stu-id="001ad-139">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="001ad-140">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="001ad-140">The terminal output looks like the following example:</span></span>

   ```
   Microsoft (R) Build Engine version 16.6.0 for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     You are using a preview version of .NET Core. See: https://aka.ms/dotnet-core-preview
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\netstandard2.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="001ad-141">向解决方案添加控制台应用</span><span class="sxs-lookup"><span data-stu-id="001ad-141">Add a console app to the solution</span></span>

<span data-ttu-id="001ad-142">添加使用类库的控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="001ad-142">Add a console application that uses the class library.</span></span> <span data-ttu-id="001ad-143">应用将提示用户输入字符串，并报告字符串是否以大写字符开头。</span><span class="sxs-lookup"><span data-stu-id="001ad-143">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="001ad-144">在终端中，运行以下命令创建控制台应用项目：</span><span class="sxs-lookup"><span data-stu-id="001ad-144">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="001ad-145">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="001ad-145">The terminal output looks like the following example:</span></span>

   ```
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="001ad-146">运行以下命令，向解决方案添加控制台应用项目：</span><span class="sxs-lookup"><span data-stu-id="001ad-146">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="001ad-147">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="001ad-147">The terminal output looks like the following example:</span></span>

   ```
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="001ad-148">打开 ShowCase/Program.cs 并将所有代码替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="001ad-148">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="001ad-149">该代码使用 `row` 变量来维护写入到控制台窗口的数据行数计数。</span><span class="sxs-lookup"><span data-stu-id="001ad-149">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="001ad-150">如果大于或等于 25，该代码将清除控制台窗口，并向用户显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="001ad-150">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="001ad-151">该程序会提示用户输入字符串。</span><span class="sxs-lookup"><span data-stu-id="001ad-151">The program prompts the user to enter a string.</span></span> <span data-ttu-id="001ad-152">它会指明字符串是否以大写字符开头。</span><span class="sxs-lookup"><span data-stu-id="001ad-152">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="001ad-153">如果用户没有输入字符串就按 <kbd>Enter</kbd> 键，那么应用程序会终止，控制台窗口会关闭。</span><span class="sxs-lookup"><span data-stu-id="001ad-153">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="001ad-154">保存更改。</span><span class="sxs-lookup"><span data-stu-id="001ad-154">Save your changes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="001ad-155">添加项目引用</span><span class="sxs-lookup"><span data-stu-id="001ad-155">Add a project reference</span></span>

<span data-ttu-id="001ad-156">最初，新的控制台应用项目无权访问类库。</span><span class="sxs-lookup"><span data-stu-id="001ad-156">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="001ad-157">若要允许该项目调用类库中的方法，可以创建对类库项目的项目引用。</span><span class="sxs-lookup"><span data-stu-id="001ad-157">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="001ad-158">运行下面的命令：</span><span class="sxs-lookup"><span data-stu-id="001ad-158">Run the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/Showcase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="001ad-159">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="001ad-159">The terminal output looks like the following example:</span></span>

   ```
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a><span data-ttu-id="001ad-160">运行应用</span><span class="sxs-lookup"><span data-stu-id="001ad-160">Run the app</span></span>

1. <span data-ttu-id="001ad-161">在终端中运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="001ad-161">Run the following command in the terminal:</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="001ad-162">输入字符串并按 Enter 以试用程序，然后按 Enter 退出<kbd></kbd><kbd></kbd>。</span><span class="sxs-lookup"><span data-stu-id="001ad-162">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="001ad-163">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="001ad-163">The terminal output looks like the following example:</span></span>

   ```
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   A string that starts with a lowercase letter
   Input: A string that starts with a lowercase letter
   Begins with uppercase? : Yes
   ```

## <a name="additional-resources"></a><span data-ttu-id="001ad-164">其他资源</span><span class="sxs-lookup"><span data-stu-id="001ad-164">Additional resources</span></span>

* [<span data-ttu-id="001ad-165">使用 .NET Core CLI 开发库</span><span class="sxs-lookup"><span data-stu-id="001ad-165">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="001ad-166">[.NET Standard 版本及其支持的平台](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="001ad-166">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="001ad-167">后续步骤</span><span class="sxs-lookup"><span data-stu-id="001ad-167">Next steps</span></span>

<span data-ttu-id="001ad-168">在本教程中，你创建了一个解决方案，添加了一个库项目，并添加了一个使用该库的控制台应用项目。</span><span class="sxs-lookup"><span data-stu-id="001ad-168">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="001ad-169">在下一教程中，将向解决方案中添加单元测试项目。</span><span class="sxs-lookup"><span data-stu-id="001ad-169">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="001ad-170">在 Visual Studio Code 中使用 .NET Core 测试 .NET Standard 库</span><span class="sxs-lookup"><span data-stu-id="001ad-170">Test a .NET Standard library with .NET Core using Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
