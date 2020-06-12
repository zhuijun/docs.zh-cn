---
title: 在 Visual Studio Code 中创建 .NET Standard 类库
description: 了解如何使用 Visual Studio Code 创建 .NET Standard 类库。
ms.date: 05/29/2020
ms.openlocfilehash: 5720ac374d50ef27a07d463e57af1bd95a352d83
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446947"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio-code"></a><span data-ttu-id="2e0f2-103">教程：在 Visual Studio Code 中创建 .NET Standard 库</span><span class="sxs-lookup"><span data-stu-id="2e0f2-103">Tutorial: Create a .NET Standard library in Visual Studio Code</span></span>

<span data-ttu-id="2e0f2-104">类库定义的是可以由应用程序调用的类型和方法。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="2e0f2-105">借助面向 .NET Standard 2.0 的类库，任何支持相应 .NET Standard 版本的 .NET 实现都可以调用库。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="2e0f2-106">完成类库时，可以决定是要将其作为 NuGet 包进行分布，还是要将其作为与一个或多个应用程序捆绑在一起的组件进行添加。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-106">When you finish your class library, you can decide whether you want to distribute it as a NuGet package or include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="2e0f2-107">有关 .NET Standard 版本及其支持的平台列表，请参阅 [.NET Standard](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="2e0f2-108">在本教程中，将创建包含一个字符串处理方法的简单实用工具库。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-108">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="2e0f2-109">我们把它作为[扩展方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)进行实现，这样就可以把它作为 <xref:System.String> 类成员进行调用。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-109">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2e0f2-110">先决条件</span><span class="sxs-lookup"><span data-stu-id="2e0f2-110">Prerequisites</span></span>

1. <span data-ttu-id="2e0f2-111">已安装 [C# 扩展](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) 的 [Visual Studio Code](https://code.visualstudio.com/)。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-111">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="2e0f2-112">有关如何在 Visual Studio Code 上安装扩展的信息，请访问 [VS Code 扩展市场](https://code.visualstudio.com/docs/editor/extension-gallery)。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-112">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="2e0f2-113">[.NET Core 3.1 SDK 或更高版本](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="2e0f2-113">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="2e0f2-114">创建解决方案</span><span class="sxs-lookup"><span data-stu-id="2e0f2-114">Create a solution</span></span>

<span data-ttu-id="2e0f2-115">首先，创建一个空白解决方案来放置类库项目。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="2e0f2-116">解决方案用作一个或多个项目的容器。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-116">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="2e0f2-117">将其他相关项目添加到同一个解决方案中。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-117">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="2e0f2-118">打开 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-118">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="2e0f2-119">在主菜单中选择“文件” > “打开文件夹”/“打开…”，创建“ClassLibraryProjects”文件夹，然后单击“选择文件夹”/“打开”   。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-119">Select **File** > **Open Folder**/**Open...** from the main menu, create a *ClassLibraryProjects* folder, and click **Select Folder**/**Open**.</span></span>

1. <span data-ttu-id="2e0f2-120">在主菜单中选择“视图” > “终端”，从 Visual Studio Code 中打开“终端”  。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-120">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="2e0f2-121">“终端”在“ClassLibraryProjects”文件夹中连同命令提示符一起打开。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-121">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="2e0f2-122">在“终端”中输入以下命令：</span><span class="sxs-lookup"><span data-stu-id="2e0f2-122">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="2e0f2-123">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="2e0f2-123">The terminal output looks like the following example:</span></span>

   ```
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="2e0f2-124">创建类库项目</span><span class="sxs-lookup"><span data-stu-id="2e0f2-124">Create a class library project</span></span>

<span data-ttu-id="2e0f2-125">将名为“StringLibrary”的新 .NET Standard 类库项目添加到解决方案。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-125">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="2e0f2-126">在终端中，运行以下命令创建库项目：</span><span class="sxs-lookup"><span data-stu-id="2e0f2-126">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="2e0f2-127">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="2e0f2-127">The terminal output looks like the following example:</span></span>

   ```
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="2e0f2-128">运行以下命令，向解决方案添加库项目：</span><span class="sxs-lookup"><span data-stu-id="2e0f2-128">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="2e0f2-129">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="2e0f2-129">The terminal output looks like the following example:</span></span>

   ```
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="2e0f2-130">请检查以确保库面向 .NET Standard 的正确版本。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-130">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="2e0f2-131">在资源管理器中，打开 StringLibrary/StringLibrary.csproj。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-131">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="2e0f2-132">`TargetFramework` 元素表明项目面向 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-132">The `TargetFramework` element shows that the project targets .NET Standard 2.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="2e0f2-133">打开 Class1.cs 并将代码替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-133">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="2e0f2-134">类库 `UtilityLibraries.StringLibrary`包含一个名为 `StartsWithUpper` 的方法。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-134">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="2e0f2-135">此方法会返回 <xref:System.Boolean> 值，以指明当前字符串实例是否以大写字符开头。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-135">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="2e0f2-136">Unicode 标准会区分大小写字符。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-136">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="2e0f2-137">如果为大写字符，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-137">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="2e0f2-138">保存该文件。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-138">Save the file.</span></span>

1. <span data-ttu-id="2e0f2-139">运行以下命令以生成解决方案，并验证项目是否正确编译。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-139">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="2e0f2-140">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="2e0f2-140">The terminal output looks like the following example:</span></span>

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

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="2e0f2-141">向解决方案添加控制台应用</span><span class="sxs-lookup"><span data-stu-id="2e0f2-141">Add a console app to the solution</span></span>

<span data-ttu-id="2e0f2-142">添加使用类库的控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-142">Add a console application that uses the class library.</span></span> <span data-ttu-id="2e0f2-143">应用将提示用户输入字符串，并报告字符串是否以大写字符开头。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-143">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="2e0f2-144">在终端中，运行以下命令创建控制台应用项目：</span><span class="sxs-lookup"><span data-stu-id="2e0f2-144">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="2e0f2-145">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="2e0f2-145">The terminal output looks like the following example:</span></span>

   ```
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="2e0f2-146">运行以下命令，向解决方案添加控制台应用项目：</span><span class="sxs-lookup"><span data-stu-id="2e0f2-146">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="2e0f2-147">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="2e0f2-147">The terminal output looks like the following example:</span></span>

   ```
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="2e0f2-148">最初，新的控制台应用项目无权访问类库。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-148">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="2e0f2-149">若要允许该项目调用类库中的方法，请通过运行以下命令创建对类库项目的项目引用：</span><span class="sxs-lookup"><span data-stu-id="2e0f2-149">To allow it to call methods in the class library, create a project reference to the class library project by running the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/Showcase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="2e0f2-150">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="2e0f2-150">The terminal output looks like the following example:</span></span>

   ```
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

1. <span data-ttu-id="2e0f2-151">打开 ShowCase/Program.cs 并将所有代码替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-151">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="2e0f2-152">该代码使用 `row` 变量来维护写入到控制台窗口的数据行数计数。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-152">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="2e0f2-153">如果大于或等于 25，该代码将清除控制台窗口，并向用户显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-153">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="2e0f2-154">该程序会提示用户输入字符串。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-154">The program prompts the user to enter a string.</span></span> <span data-ttu-id="2e0f2-155">它会指明字符串是否以大写字符开头。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-155">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="2e0f2-156">如果用户没有输入字符串就按 Enter 键，那么应用程序会终止，控制台窗口会关闭。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-156">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="2e0f2-157">保存更改。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-157">Save your changes.</span></span>

1. <span data-ttu-id="2e0f2-158">运行该程序。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-158">Run the program.</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="2e0f2-159">输入字符串并按 Enter 以试用程序，然后按 Enter 退出<kbd></kbd><kbd></kbd>。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-159">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="2e0f2-160">终端输出如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="2e0f2-160">The terminal output looks like the following example:</span></span>

   ```
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   A string that starts with a lowercase letter
   Input: A string that starts with a lowercase letter
   Begins with uppercase? : Yes
   ```

## <a name="additional-resources"></a><span data-ttu-id="2e0f2-161">其他资源</span><span class="sxs-lookup"><span data-stu-id="2e0f2-161">Additional resources</span></span>

* [<span data-ttu-id="2e0f2-162">使用 .NET Core CLI 开发库</span><span class="sxs-lookup"><span data-stu-id="2e0f2-162">Develop libraries with the .NET Core CLI</span></span>](libraries.md)

## <a name="next-steps"></a><span data-ttu-id="2e0f2-163">后续步骤</span><span class="sxs-lookup"><span data-stu-id="2e0f2-163">Next steps</span></span>

<span data-ttu-id="2e0f2-164">在本教程中，你创建了一个解决方案，添加了一个库项目，并添加了一个使用该库的控制台应用项目。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-164">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="2e0f2-165">在下一教程中，将向解决方案中添加单元测试项目。</span><span class="sxs-lookup"><span data-stu-id="2e0f2-165">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2e0f2-166">在 Visual Studio Code 中使用 .NET Core 测试 .NET Standard 库</span><span class="sxs-lookup"><span data-stu-id="2e0f2-166">Test a .NET Standard library with .NET Core in Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
