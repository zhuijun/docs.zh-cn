---
title: 在 Visual Studio 中创建 .NET Standard 类库
description: 了解如何使用 Visual Studio 创建 .NET Standard 类库。
ms.date: 08/07/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet,contperfq1
ms.openlocfilehash: 595e93d8d8d22478c6770ddd4f70a0214653f5b9
ms.sourcegitcommit: d337df55f83325918cbbd095eb573400bea49064
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2020
ms.locfileid: "88187947"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio"></a><span data-ttu-id="48231-103">教程：在 Visual Studio 中创建 .NET Standard 库</span><span class="sxs-lookup"><span data-stu-id="48231-103">Tutorial: Create a .NET Standard library using Visual Studio</span></span>

<span data-ttu-id="48231-104">在本教程中，将创建包含一个字符串处理方法的简单类库。</span><span class="sxs-lookup"><span data-stu-id="48231-104">In this tutorial, you create a simple class library that contains a single string-handling method.</span></span>

<span data-ttu-id="48231-105">类库定义的是可以由应用程序调用的类型和方法。</span><span class="sxs-lookup"><span data-stu-id="48231-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="48231-106">借助面向 .NET Standard 2.0 的类库，任何支持相应 .NET Standard 版本的 .NET 实现都可以调用库。</span><span class="sxs-lookup"><span data-stu-id="48231-106">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span>

<span data-ttu-id="48231-107">完成类库后，可将其作为 NuGet 包或作为与使用该类库的应用程序捆绑在一起的组件进行分发。</span><span class="sxs-lookup"><span data-stu-id="48231-107">When you finish your class library, you can distribute it as a NuGet package or as a component bundled with the application that uses it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="48231-108">先决条件</span><span class="sxs-lookup"><span data-stu-id="48231-108">Prerequisites</span></span>

- <span data-ttu-id="48231-109">安装了具有“.NET Core 跨平台开发”工作负载的 [Visual Studio 2019 版本 16.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="48231-109">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="48231-110">选择此工作负载时，将自动安装 .NET Core 3.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="48231-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="48231-111">创建解决方案</span><span class="sxs-lookup"><span data-stu-id="48231-111">Create a solution</span></span>

<span data-ttu-id="48231-112">首先，创建一个空白解决方案来放置类库项目。</span><span class="sxs-lookup"><span data-stu-id="48231-112">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="48231-113">Visual Studio 解决方案用作一个或多个项目的容器。</span><span class="sxs-lookup"><span data-stu-id="48231-113">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="48231-114">将其他相关项目添加到同一个解决方案中。</span><span class="sxs-lookup"><span data-stu-id="48231-114">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="48231-115">创建空白解决方案：</span><span class="sxs-lookup"><span data-stu-id="48231-115">To create the blank solution:</span></span>

1. <span data-ttu-id="48231-116">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="48231-116">Start Visual Studio.</span></span>

2. <span data-ttu-id="48231-117">在“开始”窗口上，选择“创建新项目”。</span><span class="sxs-lookup"><span data-stu-id="48231-117">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="48231-118">在“创建新项目”页面上，在搜索框中输入“解决方案”。</span><span class="sxs-lookup"><span data-stu-id="48231-118">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="48231-119">选择“空白解决方案”模板，然后选择“下一步”。</span><span class="sxs-lookup"><span data-stu-id="48231-119">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Visual Studio 中的空白解决方案模板](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="48231-121">在“配置新项目”页面上，在“项目名称”框中输入“ClassLibraryProjects”。</span><span class="sxs-lookup"><span data-stu-id="48231-121">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="48231-122">然后选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="48231-122">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="48231-123">创建类库项目</span><span class="sxs-lookup"><span data-stu-id="48231-123">Create a class library project</span></span>

1. <span data-ttu-id="48231-124">将名为“StringLibrary”的新 .NET Standard 类库项目添加到解决方案。</span><span class="sxs-lookup"><span data-stu-id="48231-124">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="48231-125">在“解决方案资源管理器”中，右键单击解决方案并选择“添加” > “新建项目”  。</span><span class="sxs-lookup"><span data-stu-id="48231-125">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="48231-126">在“创建新项目”页面上，在搜索框中输入“库”。</span><span class="sxs-lookup"><span data-stu-id="48231-126">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="48231-127">从“语言”列表中选择“C#”或“Visual Basic”，然后从“平台”列表中选择“所有平台”。</span><span class="sxs-lookup"><span data-stu-id="48231-127">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="48231-128">选择“类库 (.NET Standard)”模板，然后选择“下一步”。</span><span class="sxs-lookup"><span data-stu-id="48231-128">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="48231-129">在“配置新项目”页面，在“项目名称”框中输入“StringLibrary”。</span><span class="sxs-lookup"><span data-stu-id="48231-129">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="48231-130">然后，选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="48231-130">Then, choose **Create**.</span></span>

1. <span data-ttu-id="48231-131">请检查以确保库面向 .NET Standard 的正确版本。</span><span class="sxs-lookup"><span data-stu-id="48231-131">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="48231-132">右键单击“解决方案资源管理器”中的库项目，然后选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="48231-132">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="48231-133">“目标框架”文本框显示项目面向 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="48231-133">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![类库的项目属性](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="48231-135">如果使用 Visual Basic，请清除“根命名空间”文本框中的文本。</span><span class="sxs-lookup"><span data-stu-id="48231-135">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![类库的项目属性](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="48231-137">对于每个项目，Visual Basic 会自动创建一个与项目名称对应的命名空间。</span><span class="sxs-lookup"><span data-stu-id="48231-137">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="48231-138">在本教程中，通过使用代码文件中的 [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) 关键字定义顶级命名空间。</span><span class="sxs-lookup"><span data-stu-id="48231-138">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="48231-139">将 Class1.cs 或 Class1.vb 代码窗口中的代码替换为以下代码，并保存文件 。</span><span class="sxs-lookup"><span data-stu-id="48231-139">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="48231-140">如果未显示想要使用的语言，请更改页面顶部的语言选择器。</span><span class="sxs-lookup"><span data-stu-id="48231-140">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   <span data-ttu-id="48231-141">类库 `UtilityLibraries.StringLibrary`包含一个名为 `StartsWithUpper` 的方法。</span><span class="sxs-lookup"><span data-stu-id="48231-141">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="48231-142">此方法会返回 <xref:System.Boolean> 值，以指明当前字符串实例是否以大写字符开头。</span><span class="sxs-lookup"><span data-stu-id="48231-142">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="48231-143">Unicode 标准会区分大小写字符。</span><span class="sxs-lookup"><span data-stu-id="48231-143">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="48231-144">如果为大写字符，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="48231-144">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

   <span data-ttu-id="48231-145">`StartsWithUpper` 以[扩展方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)的形式进行实现，这样就可以将其作为 <xref:System.String> 类成员进行调用。</span><span class="sxs-lookup"><span data-stu-id="48231-145">`StartsWithUpper` is implemented as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

1. <span data-ttu-id="48231-146">在菜单栏上，选择“生成” > “生成解决方案”以验证项目是否正确编译 。</span><span class="sxs-lookup"><span data-stu-id="48231-146">On the menu bar, select **Build** > **Build Solution** to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="48231-147">向解决方案添加控制台应用</span><span class="sxs-lookup"><span data-stu-id="48231-147">Add a console app to the solution</span></span>

<span data-ttu-id="48231-148">添加使用类库的控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="48231-148">Add a console application that uses the class library.</span></span> <span data-ttu-id="48231-149">应用将提示用户输入字符串，并报告字符串是否以大写字符开头。</span><span class="sxs-lookup"><span data-stu-id="48231-149">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="48231-150">将名为“ShowCase”的新 .NET Core 控制台应用程序添加到解决方案。</span><span class="sxs-lookup"><span data-stu-id="48231-150">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="48231-151">在“解决方案资源管理器”中右键单击解决方案并选择“添加” > “新建项目”。</span><span class="sxs-lookup"><span data-stu-id="48231-151">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="48231-152">在“创建新项目”页面，在搜索框中输入“控制台”。</span><span class="sxs-lookup"><span data-stu-id="48231-152">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="48231-153">从“语言”列表中选择“C#”或“Visual Basic”，然后从“平台”列表中选择“所有平台”。</span><span class="sxs-lookup"><span data-stu-id="48231-153">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="48231-154">选择“控制台应用 (.NET Core)”模板，然后选择“下一步”。</span><span class="sxs-lookup"><span data-stu-id="48231-154">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="48231-155">在“配置新项目”页面，在“项目名称”框中输入“ShowCase”。</span><span class="sxs-lookup"><span data-stu-id="48231-155">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="48231-156">然后选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="48231-156">Then choose **Create**.</span></span>

1. <span data-ttu-id="48231-157">在“Program.cs”或“Program.vb”文件的代码窗口中，将所有代码替换为以下代码 。</span><span class="sxs-lookup"><span data-stu-id="48231-157">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   <span data-ttu-id="48231-158">该代码使用 `row` 变量来维护写入到控制台窗口的数据行数计数。</span><span class="sxs-lookup"><span data-stu-id="48231-158">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="48231-159">如果大于或等于 25，该代码将清除控制台窗口，并向用户显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="48231-159">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="48231-160">该程序会提示用户输入字符串。</span><span class="sxs-lookup"><span data-stu-id="48231-160">The program prompts the user to enter a string.</span></span> <span data-ttu-id="48231-161">它会指明字符串是否以大写字符开头。</span><span class="sxs-lookup"><span data-stu-id="48231-161">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="48231-162">如果用户没有输入字符串就按 <kbd>Enter</kbd> 键，那么应用程序会终止，控制台窗口会关闭。</span><span class="sxs-lookup"><span data-stu-id="48231-162">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="48231-163">添加项目引用</span><span class="sxs-lookup"><span data-stu-id="48231-163">Add a project reference</span></span>

<span data-ttu-id="48231-164">最初，新的控制台应用项目无权访问类库。</span><span class="sxs-lookup"><span data-stu-id="48231-164">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="48231-165">若要允许该项目调用类库中的方法，可以创建对类库项目的项目引用。</span><span class="sxs-lookup"><span data-stu-id="48231-165">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="48231-166">在“解决方案资源管理器”中，右键单击 `ShowCase` 项目的“依赖项”节点，并选择“添加项目引用”  。</span><span class="sxs-lookup"><span data-stu-id="48231-166">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![在 Visual Studio 中添加引用上下文菜单](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="48231-168">在“引用管理器”对话框中，选择“StringLibrary”项目，然后选择“确定”按钮  。</span><span class="sxs-lookup"><span data-stu-id="48231-168">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![选择了“StringLibrary”的“引用管理器”对话框](media/library-with-visual-studio/manage-project-references.png)

## <a name="run-the-app"></a><span data-ttu-id="48231-170">运行应用</span><span class="sxs-lookup"><span data-stu-id="48231-170">Run the app</span></span>

1. <span data-ttu-id="48231-171">在“**解决方案资源管理器**”中，右键单击“**ShowCase**”项目，在上下文菜单中选择“**设为启动项目**”。</span><span class="sxs-lookup"><span data-stu-id="48231-171">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Visual Studio 中用于设置启动项目的项目上下文菜单](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="48231-173">按 Ctrl+F5 编译并运行程序，而不进行调试<kbd></kbd><kbd></kbd>。</span><span class="sxs-lookup"><span data-stu-id="48231-173">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to compile and run the program without debugging.</span></span>

   ![Visual Studio 中显示“调试”按钮的项目工具栏](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="48231-175">输入字符串并按 Enter 以试用程序，然后按 Enter 退出<kbd></kbd><kbd></kbd>。</span><span class="sxs-lookup"><span data-stu-id="48231-175">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="运行展示的控制台窗口":::

## <a name="additional-resources"></a><span data-ttu-id="48231-177">其他资源</span><span class="sxs-lookup"><span data-stu-id="48231-177">Additional resources</span></span>

* [<span data-ttu-id="48231-178">使用 .NET Core CLI 开发库</span><span class="sxs-lookup"><span data-stu-id="48231-178">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="48231-179">[.NET Standard 版本及其支持的平台](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="48231-179">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="48231-180">后续步骤</span><span class="sxs-lookup"><span data-stu-id="48231-180">Next steps</span></span>

<span data-ttu-id="48231-181">在本教程中，你创建了一个类库。</span><span class="sxs-lookup"><span data-stu-id="48231-181">In this tutorial, you created a class library.</span></span> <span data-ttu-id="48231-182">在下一教程中，你将了解如何对类库进行单元测试。</span><span class="sxs-lookup"><span data-stu-id="48231-182">In the next tutorial, you learn how to unit test the class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="48231-183">使用 Visual Studio 对 .NET Standard 库进行单元测试</span><span class="sxs-lookup"><span data-stu-id="48231-183">Unit test a .NET Standard library using Visual Studio</span></span>](testing-library-with-visual-studio.md)

<span data-ttu-id="48231-184">或者，你可以跳过自动单元测试，并了解如何通过创建 NuGet 包来共享库：</span><span class="sxs-lookup"><span data-stu-id="48231-184">Or you can skip automated unit testing and learn how to share the library by creating a NuGet package:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="48231-185">使用 Visual Studio 创建和发布包</span><span class="sxs-lookup"><span data-stu-id="48231-185">Create and publish a package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)

<span data-ttu-id="48231-186">同时，还可以了解如何发布控制台应用。</span><span class="sxs-lookup"><span data-stu-id="48231-186">Or learn how to publish a console app.</span></span> <span data-ttu-id="48231-187">如果从本教程中创建的解决方案发布控制台应用，类库将以 .dll 文件的形式随附。</span><span class="sxs-lookup"><span data-stu-id="48231-187">If you publish the console app from the solution you created in this tutorial, the class library goes with it as a *.dll* file.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="48231-188">使用 Visual Studio 发布 .NET Core 控制台应用程序</span><span class="sxs-lookup"><span data-stu-id="48231-188">Publish a .NET Core console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
