---
title: 在 Visual Studio 中创建 .NET Standard 类库
description: 了解如何使用 Visual Studio 创建 .NET Standard 类库。
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: ef9c62b0378e1064d8cfd90a8c59aed74ea312b2
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701560"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio"></a><span data-ttu-id="be4dc-103">教程：在 Visual Studio 中创建 .NET Standard 库</span><span class="sxs-lookup"><span data-stu-id="be4dc-103">Tutorial: Create a .NET Standard library using Visual Studio</span></span>

<span data-ttu-id="be4dc-104">在本教程中，将创建包含一个字符串处理方法的简单实用工具库。</span><span class="sxs-lookup"><span data-stu-id="be4dc-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="be4dc-105">我们把它作为[扩展方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)进行实现，这样就可以把它作为 <xref:System.String> 类成员进行调用。</span><span class="sxs-lookup"><span data-stu-id="be4dc-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="be4dc-106">类库定义的是可以由应用程序调用的类型和方法。</span><span class="sxs-lookup"><span data-stu-id="be4dc-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="be4dc-107">借助面向 .NET Standard 2.0 的类库，任何支持相应 .NET Standard 版本的 .NET 实现都可以调用库。</span><span class="sxs-lookup"><span data-stu-id="be4dc-107">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="be4dc-108">完成类库后，可以将其作为第三方组件进行分发，也可以作为与一个或多个应用程序捆绑在一起的组件进行分发。</span><span class="sxs-lookup"><span data-stu-id="be4dc-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="be4dc-109">先决条件</span><span class="sxs-lookup"><span data-stu-id="be4dc-109">Prerequisites</span></span>

- <span data-ttu-id="be4dc-110">安装了具有“.NET Core 跨平台开发”工作负载的 [Visual Studio 2019 版本 16.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="be4dc-110">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="be4dc-111">选择此工作负载时，将自动安装 .NET Core 3.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="be4dc-111">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="be4dc-112">有关详细信息，请参阅[安装 .NET Core SDK](../install/sdk.md?pivots=os-windows) 一文中的[在 Visual Studio 中安装](../install/sdk.md?pivots=os-windows#install-with-visual-studio)部分。</span><span class="sxs-lookup"><span data-stu-id="be4dc-112">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="be4dc-113">创建解决方案</span><span class="sxs-lookup"><span data-stu-id="be4dc-113">Create a solution</span></span>

<span data-ttu-id="be4dc-114">首先，创建一个空白解决方案来放置类库项目。</span><span class="sxs-lookup"><span data-stu-id="be4dc-114">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="be4dc-115">Visual Studio 解决方案用作一个或多个项目的容器。</span><span class="sxs-lookup"><span data-stu-id="be4dc-115">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="be4dc-116">将其他相关项目添加到同一个解决方案中。</span><span class="sxs-lookup"><span data-stu-id="be4dc-116">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="be4dc-117">创建空白解决方案：</span><span class="sxs-lookup"><span data-stu-id="be4dc-117">To create the blank solution:</span></span>

1. <span data-ttu-id="be4dc-118">启动 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="be4dc-118">Start Visual Studio.</span></span>

2. <span data-ttu-id="be4dc-119">在“开始”窗口上，选择“创建新项目”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-119">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="be4dc-120">在“创建新项目”页面上，在搜索框中输入“解决方案”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-120">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="be4dc-121">选择“空白解决方案”模板，然后选择“下一步”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-121">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Visual Studio 中的空白解决方案模板](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="be4dc-123">在“配置新项目”页面上，在“项目名称”框中输入“ClassLibraryProjects”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-123">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="be4dc-124">然后选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-124">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="be4dc-125">创建类库项目</span><span class="sxs-lookup"><span data-stu-id="be4dc-125">Create a class library project</span></span>

1. <span data-ttu-id="be4dc-126">将名为“StringLibrary”的新 .NET Standard 类库项目添加到解决方案。</span><span class="sxs-lookup"><span data-stu-id="be4dc-126">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="be4dc-127">在“解决方案资源管理器”中，右键单击解决方案并选择“添加” > “新建项目”  。</span><span class="sxs-lookup"><span data-stu-id="be4dc-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="be4dc-128">在“创建新项目”页面上，在搜索框中输入“库”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="be4dc-129">从“语言”列表中选择“C#”或“Visual Basic”，然后从“平台”列表中选择“所有平台”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-129">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="be4dc-130">选择“类库 (.NET Standard)”模板，然后选择“下一步”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="be4dc-131">在“配置新项目”页面，在“项目名称”框中输入“StringLibrary”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="be4dc-132">然后，选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="be4dc-133">请检查以确保库面向 .NET Standard 的正确版本。</span><span class="sxs-lookup"><span data-stu-id="be4dc-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="be4dc-134">右键单击“解决方案资源管理器”中的库项目，然后选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="be4dc-135">“目标框架”文本框显示项目面向 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="be4dc-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![类库的项目属性](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="be4dc-137">如果使用 Visual Basic，请清除“根命名空间”文本框中的文本。</span><span class="sxs-lookup"><span data-stu-id="be4dc-137">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![类库的项目属性](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="be4dc-139">对于每个项目，Visual Basic 会自动创建一个与项目名称对应的命名空间。</span><span class="sxs-lookup"><span data-stu-id="be4dc-139">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="be4dc-140">在本教程中，通过使用代码文件中的 [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) 关键字定义顶级命名空间。</span><span class="sxs-lookup"><span data-stu-id="be4dc-140">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="be4dc-141">将 Class1.cs 或 Class1.vb 代码窗口中的代码替换为以下代码，并保存文件 。</span><span class="sxs-lookup"><span data-stu-id="be4dc-141">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="be4dc-142">如果未显示想要使用的语言，请更改页面顶部的语言选择器。</span><span class="sxs-lookup"><span data-stu-id="be4dc-142">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   <span data-ttu-id="be4dc-143">类库 `UtilityLibraries.StringLibrary`包含一个名为 `StartsWithUpper` 的方法。</span><span class="sxs-lookup"><span data-stu-id="be4dc-143">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="be4dc-144">此方法会返回 <xref:System.Boolean> 值，以指明当前字符串实例是否以大写字符开头。</span><span class="sxs-lookup"><span data-stu-id="be4dc-144">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="be4dc-145">Unicode 标准会区分大小写字符。</span><span class="sxs-lookup"><span data-stu-id="be4dc-145">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="be4dc-146">如果为大写字符，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="be4dc-146">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="be4dc-147">在菜单栏上，选择“生成” > “生成解决方案”以验证项目是否正确编译 。</span><span class="sxs-lookup"><span data-stu-id="be4dc-147">On the menu bar, select **Build** > **Build Solution** to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="be4dc-148">向解决方案添加控制台应用</span><span class="sxs-lookup"><span data-stu-id="be4dc-148">Add a console app to the solution</span></span>

<span data-ttu-id="be4dc-149">添加使用类库的控制台应用程序。</span><span class="sxs-lookup"><span data-stu-id="be4dc-149">Add a console application that uses the class library.</span></span> <span data-ttu-id="be4dc-150">应用将提示用户输入字符串，并报告字符串是否以大写字符开头。</span><span class="sxs-lookup"><span data-stu-id="be4dc-150">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="be4dc-151">将名为“ShowCase”的新 .NET Core 控制台应用程序添加到解决方案。</span><span class="sxs-lookup"><span data-stu-id="be4dc-151">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="be4dc-152">在“解决方案资源管理器”中右键单击解决方案并选择“添加” > “新建项目”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-152">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="be4dc-153">在“创建新项目”页面，在搜索框中输入“控制台”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-153">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="be4dc-154">从“语言”列表中选择“C#”或“Visual Basic”，然后从“平台”列表中选择“所有平台”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-154">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="be4dc-155">选择“控制台应用 (.NET Core)”模板，然后选择“下一步”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-155">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="be4dc-156">在“配置新项目”页面，在“项目名称”框中输入“ShowCase”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-156">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="be4dc-157">然后选择“创建”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-157">Then choose **Create**.</span></span>

1. <span data-ttu-id="be4dc-158">在“Program.cs”或“Program.vb”文件的代码窗口中，将所有代码替换为以下代码 。</span><span class="sxs-lookup"><span data-stu-id="be4dc-158">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   <span data-ttu-id="be4dc-159">该代码使用 `row` 变量来维护写入到控制台窗口的数据行数计数。</span><span class="sxs-lookup"><span data-stu-id="be4dc-159">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="be4dc-160">如果大于或等于 25，该代码将清除控制台窗口，并向用户显示一条消息。</span><span class="sxs-lookup"><span data-stu-id="be4dc-160">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="be4dc-161">该程序会提示用户输入字符串。</span><span class="sxs-lookup"><span data-stu-id="be4dc-161">The program prompts the user to enter a string.</span></span> <span data-ttu-id="be4dc-162">它会指明字符串是否以大写字符开头。</span><span class="sxs-lookup"><span data-stu-id="be4dc-162">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="be4dc-163">如果用户没有输入字符串就按 <kbd>Enter</kbd> 键，那么应用程序会终止，控制台窗口会关闭。</span><span class="sxs-lookup"><span data-stu-id="be4dc-163">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="be4dc-164">添加项目引用</span><span class="sxs-lookup"><span data-stu-id="be4dc-164">Add a project reference</span></span>

<span data-ttu-id="be4dc-165">最初，新的控制台应用项目无权访问类库。</span><span class="sxs-lookup"><span data-stu-id="be4dc-165">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="be4dc-166">若要允许该项目调用类库中的方法，可以创建对类库项目的项目引用。</span><span class="sxs-lookup"><span data-stu-id="be4dc-166">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="be4dc-167">在“解决方案资源管理器”中，右键单击 `ShowCase` 项目的“依赖项”节点，并选择“添加项目引用”  。</span><span class="sxs-lookup"><span data-stu-id="be4dc-167">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![在 Visual Studio 中添加引用上下文菜单](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="be4dc-169">在“引用管理器”对话框中，选择“StringLibrary”项目，然后选择“确定”按钮  。</span><span class="sxs-lookup"><span data-stu-id="be4dc-169">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![选择了“StringLibrary”的“引用管理器”对话框](media/library-with-visual-studio/manage-project-references.png)

## <a name="run-the-app"></a><span data-ttu-id="be4dc-171">运行应用</span><span class="sxs-lookup"><span data-stu-id="be4dc-171">Run the app</span></span>

1. <span data-ttu-id="be4dc-172">在“**解决方案资源管理器**”中，右键单击“**ShowCase**”项目，在上下文菜单中选择“**设为启动项目**”。</span><span class="sxs-lookup"><span data-stu-id="be4dc-172">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Visual Studio 中用于设置启动项目的项目上下文菜单](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="be4dc-174">按 <kbd>Shift</kbd>+<kbd>F5</kbd> 编译并运行程序，而不进行调试。</span><span class="sxs-lookup"><span data-stu-id="be4dc-174">Press <kbd>Shift</kbd>+<kbd>F5</kbd> to compile and run the program without debugging.</span></span>

   ![Visual Studio 中显示“调试”按钮的项目工具栏](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="be4dc-176">输入字符串并按 Enter 以试用程序，然后按 Enter 退出<kbd></kbd><kbd></kbd>。</span><span class="sxs-lookup"><span data-stu-id="be4dc-176">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="运行展示的控制台窗口":::

## <a name="additional-resources"></a><span data-ttu-id="be4dc-178">其他资源</span><span class="sxs-lookup"><span data-stu-id="be4dc-178">Additional resources</span></span>

* [<span data-ttu-id="be4dc-179">使用 .NET Core CLI 开发库</span><span class="sxs-lookup"><span data-stu-id="be4dc-179">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="be4dc-180">[.NET Standard 版本及其支持的平台](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="be4dc-180">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="be4dc-181">后续步骤</span><span class="sxs-lookup"><span data-stu-id="be4dc-181">Next steps</span></span>

<span data-ttu-id="be4dc-182">在本教程中，你创建了一个解决方案，添加了一个库项目，并添加了一个使用该库的控制台应用项目。</span><span class="sxs-lookup"><span data-stu-id="be4dc-182">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="be4dc-183">在下一教程中，将向解决方案中添加单元测试项目。</span><span class="sxs-lookup"><span data-stu-id="be4dc-183">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="be4dc-184">在 Visual Studio 中使用 .NET Core 测试 .NET Standard 库</span><span class="sxs-lookup"><span data-stu-id="be4dc-184">Test a .NET Standard library with .NET Core using Visual Studio</span></span>](testing-library-with-visual-studio.md)
