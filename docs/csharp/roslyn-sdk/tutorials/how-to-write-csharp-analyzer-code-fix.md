---
title: 教程：编写第一个分析器和代码修补程序
description: 本教程提供了有关使用 .NET 编译器 SDK (Roslyn API) 生成分析器和代码修补程序的分步说明。
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: e79907f364939462b7d0d5814c4752be23bcfdf3
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381588"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="00ac7-103">教程：编写第一个分析器和代码修补程序</span><span class="sxs-lookup"><span data-stu-id="00ac7-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="00ac7-104">.NET Compiler Platform SDK 提供创建面向 C# 或 Visual Basic 代码的自定义警告所需的工具。</span><span class="sxs-lookup"><span data-stu-id="00ac7-104">The .NET Compiler Platform SDK provides the tools you need to create custom warnings that target C# or Visual Basic code.</span></span> <span data-ttu-id="00ac7-105">分析器包含识别规则冲突的代码。</span><span class="sxs-lookup"><span data-stu-id="00ac7-105">Your **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="00ac7-106">代码修补程序包含修复冲突的代码。</span><span class="sxs-lookup"><span data-stu-id="00ac7-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="00ac7-107">实现的规则可以是从代码结构到编码样式再到命名约定之类的任何内容。</span><span class="sxs-lookup"><span data-stu-id="00ac7-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="00ac7-108">.NET Compiler Platform 在开发人员编写代码时提供运行分析的框架，以及用于修复代码的所有 Visual Studio UI 功能：显示编辑器中的波形曲线、填充 Visual Studio 错误列表、创建“灯泡”建议，并显示建议修补程序的丰富预览。</span><span class="sxs-lookup"><span data-stu-id="00ac7-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="00ac7-109">在本教程中，将探讨使用 Roslyn API 创建分析器以及随附的代码修补程序。</span><span class="sxs-lookup"><span data-stu-id="00ac7-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="00ac7-110">分析器是一种执行源代码分析并向用户报告问题的方法。</span><span class="sxs-lookup"><span data-stu-id="00ac7-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="00ac7-111">（可选）分析器还可以提供表示对用户源代码进行修改的代码修补程序。</span><span class="sxs-lookup"><span data-stu-id="00ac7-111">Optionally, an analyzer can also provide a code fix that represents a modification to the user's source code.</span></span> <span data-ttu-id="00ac7-112">本教程将创建一个分析器，用于查找可以使用 `const` 修饰符声明的但未执行此操作的局部变量声明。</span><span class="sxs-lookup"><span data-stu-id="00ac7-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="00ac7-113">随附的代码修补程序修改这些声明来添加 `const` 修饰符。</span><span class="sxs-lookup"><span data-stu-id="00ac7-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="00ac7-114">先决条件</span><span class="sxs-lookup"><span data-stu-id="00ac7-114">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="00ac7-115">当前 Visual Studio“随附代码修补程序的分析器(.NET Standard)”模板有一个已知 bug，应在 Visual Studio 2019 版本 16.7 中修复。</span><span class="sxs-lookup"><span data-stu-id="00ac7-115">The current Visual Studio **Analyzer with code fix (.NET Standard)** template has a known bug in it and should be fixed in Visual Studio 2019 version 16.7.</span></span> <span data-ttu-id="00ac7-116">除非进行了以下更改，否则模板中的项目将不会编译：</span><span class="sxs-lookup"><span data-stu-id="00ac7-116">The projects in the template will not compile unless the following changes are made:</span></span>
>
> 1. <span data-ttu-id="00ac7-117">选择“工具” > “选项” > “NuGet 包管理器” > “包源”</span><span class="sxs-lookup"><span data-stu-id="00ac7-117">Select **Tools** > **Options** > **NuGet Package Manager** > **Package Sources**</span></span>
>    - <span data-ttu-id="00ac7-118">选择加号按钮来添加新源：</span><span class="sxs-lookup"><span data-stu-id="00ac7-118">Select the plus button, to add a new source:</span></span>
>    - <span data-ttu-id="00ac7-119">将“源”设置为 `https://dotnet.myget.org/F/roslyn-analyzers/api/v3/index.json`，并选择“更新”</span><span class="sxs-lookup"><span data-stu-id="00ac7-119">Set the **Source** to `https://dotnet.myget.org/F/roslyn-analyzers/api/v3/index.json` and select **Update**</span></span>
> 1. <span data-ttu-id="00ac7-120">在“解决方案资源管理器”中，右键单击“MakeConst.Vsix”项目，然后选择“编辑项目文件”</span><span class="sxs-lookup"><span data-stu-id="00ac7-120">From the **Solution Explorer**, right-click on the **MakeConst.Vsix** project, and select **Edit Project File**</span></span>
>    - <span data-ttu-id="00ac7-121">更新 `<AssemblyName>` 节点以添加 `.Visx` 后缀：</span><span class="sxs-lookup"><span data-stu-id="00ac7-121">Update the `<AssemblyName>` node to add the `.Visx` suffix:</span></span>
>      - `<AssemblyName>MakeConst.Vsix</AssemblyName>`
>    - <span data-ttu-id="00ac7-122">更新第 41 行上的 `<ProjectReference>` 节点以更改 `TargetFramework` 值：</span><span class="sxs-lookup"><span data-stu-id="00ac7-122">Update the `<ProjectReference>` node on line 41 to alter the `TargetFramework` value:</span></span>
>      - `<ProjectReference Update="@(ProjectReference)" AdditionalProperties="TargetFramework=netstandard2.0" />`
> 1. <span data-ttu-id="00ac7-123">在“MakeConst.Test”项目中更新“MakeConstUnitTests.cs”文件 ：</span><span class="sxs-lookup"><span data-stu-id="00ac7-123">Update the *MakeConstUnitTests.cs* file, in the *MakeConst.Test* project:</span></span>
>    - <span data-ttu-id="00ac7-124">将第 9 行更改为以下内容，注意命名空间的改变：</span><span class="sxs-lookup"><span data-stu-id="00ac7-124">Change line 9 to the following, notice namespace alteration:</span></span>
>      - `using Verify = Microsoft.CodeAnalysis.CSharp.Testing.MSTest.CodeFixVerifier<`
>    - <span data-ttu-id="00ac7-125">将第 24 行更改为以下方法：</span><span class="sxs-lookup"><span data-stu-id="00ac7-125">Change line 24 to the following method:</span></span>
>      - `await Verify.VerifyAnalyzerAsync(test);`
>    - <span data-ttu-id="00ac7-126">将第 62 行更改为以下方法：</span><span class="sxs-lookup"><span data-stu-id="00ac7-126">Change line 62 to the following method:</span></span>
>      - `await Verify.VerifyCodeFixAsync(test, expected, fixtest);`

- [<span data-ttu-id="00ac7-127">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="00ac7-127">Visual Studio 2017</span></span>](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [<span data-ttu-id="00ac7-128">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="00ac7-128">Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads)

<span data-ttu-id="00ac7-129">必须通过 Visual Studio 安装程序安装 .NET 编译器平台 SDK：</span><span class="sxs-lookup"><span data-stu-id="00ac7-129">You'll need to install the **.NET Compiler Platform SDK** via the Visual Studio Installer:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="00ac7-130">可以通过几个步骤创建和验证分析器：</span><span class="sxs-lookup"><span data-stu-id="00ac7-130">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="00ac7-131">创建解决方案。</span><span class="sxs-lookup"><span data-stu-id="00ac7-131">Create the solution.</span></span>
1. <span data-ttu-id="00ac7-132">注册分析器名称和描述。</span><span class="sxs-lookup"><span data-stu-id="00ac7-132">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="00ac7-133">报告分析器警告和建议。</span><span class="sxs-lookup"><span data-stu-id="00ac7-133">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="00ac7-134">实现代码修复以接受建议。</span><span class="sxs-lookup"><span data-stu-id="00ac7-134">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="00ac7-135">通过单元测试改进分析。</span><span class="sxs-lookup"><span data-stu-id="00ac7-135">Improve the analysis through unit tests.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="00ac7-136">探索分析器模板</span><span class="sxs-lookup"><span data-stu-id="00ac7-136">Explore the analyzer template</span></span>

<span data-ttu-id="00ac7-137">分析器向用户报告可以转换为局部常量的任何局部变量声明。</span><span class="sxs-lookup"><span data-stu-id="00ac7-137">Your analyzer reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="00ac7-138">例如，考虑以下代码：</span><span class="sxs-lookup"><span data-stu-id="00ac7-138">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="00ac7-139">在上面的代码中，会向 `x` 分配常量值，并且永远不会被修改。</span><span class="sxs-lookup"><span data-stu-id="00ac7-139">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="00ac7-140">可以使用 `const` 修饰符声明：</span><span class="sxs-lookup"><span data-stu-id="00ac7-140">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="00ac7-141">涉及到确定变量是否可以保持不变的分析，需要进行句法分析、初始值设定项的常量分析和数据流分析，以确保永远不会写入该变量。</span><span class="sxs-lookup"><span data-stu-id="00ac7-141">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="00ac7-142">.NET Compiler Platform 提供了 API，以便更轻松地执行此分析。</span><span class="sxs-lookup"><span data-stu-id="00ac7-142">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span> <span data-ttu-id="00ac7-143">第一步是创建一个新的 C#“随附代码修补程序的分析器”项目。</span><span class="sxs-lookup"><span data-stu-id="00ac7-143">The first step is to create a new C# **Analyzer with code fix** project.</span></span>

- <span data-ttu-id="00ac7-144">在 Visual Studio 中，选择“文件”>“新建”>“项目...”，显示“新建项目”对话框。</span><span class="sxs-lookup"><span data-stu-id="00ac7-144">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
- <span data-ttu-id="00ac7-145">在“Visual C#”>“扩展性”下，选择“随附代码修补程序的分析器 (.NET Standard)”。</span><span class="sxs-lookup"><span data-stu-id="00ac7-145">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
- <span data-ttu-id="00ac7-146">给项目“MakeConst”命名，然后单击“确定”。</span><span class="sxs-lookup"><span data-stu-id="00ac7-146">Name your project "**MakeConst**" and click OK.</span></span>

<span data-ttu-id="00ac7-147">使用代码修复模板的分析器将创建三个项目：一个包含分析器和代码修补程序，第二个是单元测试项目，第三个是 VSIX 项目。</span><span class="sxs-lookup"><span data-stu-id="00ac7-147">The analyzer with code fix template creates three projects: one contains the analyzer and code fix, the second is a unit test project, and the third is the VSIX project.</span></span> <span data-ttu-id="00ac7-148">默认启动项目是 VSIX 项目。</span><span class="sxs-lookup"><span data-stu-id="00ac7-148">The default startup project is the VSIX project.</span></span> <span data-ttu-id="00ac7-149">按 F5<kbd></kbd> 启动 VSIX 项目。</span><span class="sxs-lookup"><span data-stu-id="00ac7-149">Press <kbd>F5</kbd> to start the VSIX project.</span></span> <span data-ttu-id="00ac7-150">这将启动已加载新分析器的第二个 Visual Studio 实例。</span><span class="sxs-lookup"><span data-stu-id="00ac7-150">This starts a second instance of Visual Studio that has loaded your new analyzer.</span></span>

> [!TIP]
> <span data-ttu-id="00ac7-151">在运行分析器时，请启动 Visual Studio 的第二个副本。</span><span class="sxs-lookup"><span data-stu-id="00ac7-151">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="00ac7-152">此第二个副本使用不同的注册表配置单元来存储设置。</span><span class="sxs-lookup"><span data-stu-id="00ac7-152">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="00ac7-153">这样便可以将 Visual Studio 两个副本中的可视化设置区分开来。</span><span class="sxs-lookup"><span data-stu-id="00ac7-153">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="00ac7-154">可以选择 Visual Studio 实验性运行的不同主题。</span><span class="sxs-lookup"><span data-stu-id="00ac7-154">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="00ac7-155">此外，不要在设置中漫游，也不要使用 Visual Studio 的实验性运行登录到 Visual Studio 帐户。</span><span class="sxs-lookup"><span data-stu-id="00ac7-155">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="00ac7-156">这样可以使设置保持不同。</span><span class="sxs-lookup"><span data-stu-id="00ac7-156">That keeps the settings different.</span></span>

<span data-ttu-id="00ac7-157">在刚刚启动的第二个 Visual Studio 实例中，创建一个新的 C# 控制台应用程序项目（.NET Core 或.NET Framework 项目将起作用 -- 分析器在源级别工作。）悬停在带波浪下划线的标记上，将显示分析器提供的警告文本。</span><span class="sxs-lookup"><span data-stu-id="00ac7-157">In the second Visual Studio instance that you just started, create a new C# Console Application project (either .NET Core or .NET Framework project will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="00ac7-158">该模板创建一个分析器，它报告有关类型名称包含小写字母的每种类型声明的警告，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="00ac7-158">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![分析器报告警告](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="00ac7-160">该模板还提供了一种代码修补程序，它可以将包含小写字符的任何类型名称更改为大写字母。</span><span class="sxs-lookup"><span data-stu-id="00ac7-160">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="00ac7-161">可以单击显示警告的灯泡，以查看建议的更改。</span><span class="sxs-lookup"><span data-stu-id="00ac7-161">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="00ac7-162">接受建议的更改会更新解决方案中的类型名称和所有对该类型的引用。</span><span class="sxs-lookup"><span data-stu-id="00ac7-162">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="00ac7-163">现在你已了解初始分析器的操作，关闭第二个 Visual Studio 实例，并返回到分析器项目。</span><span class="sxs-lookup"><span data-stu-id="00ac7-163">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="00ac7-164">无需启动 Visual Studio 的第二个副本和创建新代码来测试分析器中的每一项更改。</span><span class="sxs-lookup"><span data-stu-id="00ac7-164">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="00ac7-165">该模板还为你创建了单元测试项目。</span><span class="sxs-lookup"><span data-stu-id="00ac7-165">The template also creates a unit test project for you.</span></span> <span data-ttu-id="00ac7-166">该项目包含两个测试。</span><span class="sxs-lookup"><span data-stu-id="00ac7-166">That project contains two tests.</span></span> <span data-ttu-id="00ac7-167">`TestMethod1` 显示了在不触发诊断的情况下分析代码的典型测试格式。</span><span class="sxs-lookup"><span data-stu-id="00ac7-167">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="00ac7-168">`TestMethod2` 显示了先触发诊断然后应用建议的代码修补程序的测试格式。</span><span class="sxs-lookup"><span data-stu-id="00ac7-168">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="00ac7-169">在构建分析器和代码修补程序时，为不同的代码结构编写测试，以验证你的工作。</span><span class="sxs-lookup"><span data-stu-id="00ac7-169">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="00ac7-170">分析器的单元测试比使用 Visual Studio 以交互方式进行测试的速度更快。</span><span class="sxs-lookup"><span data-stu-id="00ac7-170">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="00ac7-171">当你知道哪些代码构造应触发和不应触发分析器时，分析器单元测试是一个很好的工具。</span><span class="sxs-lookup"><span data-stu-id="00ac7-171">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="00ac7-172">在 Visual Studio 的另一个副本加载分析器是用于浏览并找到你可能未曾想到的构造的绝佳工具。</span><span class="sxs-lookup"><span data-stu-id="00ac7-172">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="00ac7-173">创建分析器注册</span><span class="sxs-lookup"><span data-stu-id="00ac7-173">Create analyzer registrations</span></span>

<span data-ttu-id="00ac7-174">该模板将在 MakeConstAnalyzer.cs 文件中创建初始 `DiagnosticAnalyzer` 类。</span><span class="sxs-lookup"><span data-stu-id="00ac7-174">The template creates the initial `DiagnosticAnalyzer` class, in the **MakeConstAnalyzer.cs** file.</span></span> <span data-ttu-id="00ac7-175">此初始分析器显示每个分析器的两个重要属性。</span><span class="sxs-lookup"><span data-stu-id="00ac7-175">This initial analyzer shows two important properties of every analyzer.</span></span>

- <span data-ttu-id="00ac7-176">每个诊断分析器必须提供 `[DiagnosticAnalyzer]` 属性，用于描述其操作所用的语言。</span><span class="sxs-lookup"><span data-stu-id="00ac7-176">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
- <span data-ttu-id="00ac7-177">每个诊断分析器必须派生自 <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> 类。</span><span class="sxs-lookup"><span data-stu-id="00ac7-177">Every diagnostic analyzer must derive from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="00ac7-178">该模板还显示属于任何分析器的基本功能：</span><span class="sxs-lookup"><span data-stu-id="00ac7-178">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="00ac7-179">注册操作。</span><span class="sxs-lookup"><span data-stu-id="00ac7-179">Register actions.</span></span> <span data-ttu-id="00ac7-180">此操作表示应触发分析器以检查存在冲突的代码的代码更改。</span><span class="sxs-lookup"><span data-stu-id="00ac7-180">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="00ac7-181">当 Visual Studio 检测到匹配注册操作的代码编辑时，它调用分析器的注册方法。</span><span class="sxs-lookup"><span data-stu-id="00ac7-181">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="00ac7-182">创建诊断。</span><span class="sxs-lookup"><span data-stu-id="00ac7-182">Create diagnostics.</span></span> <span data-ttu-id="00ac7-183">当分析器检测到冲突，它会创建一个诊断对象，Visual Studio 使用该对象来通知用户有关冲突的信息。</span><span class="sxs-lookup"><span data-stu-id="00ac7-183">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="00ac7-184">在重写的 <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> 方法中注册操作。</span><span class="sxs-lookup"><span data-stu-id="00ac7-184">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="00ac7-185">在本教程中，你将访问“语法节点”寻找局部声明，并查看哪些具有常量值。</span><span class="sxs-lookup"><span data-stu-id="00ac7-185">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="00ac7-186">如果声明可以是常量，分析器将创建并报告诊断。</span><span class="sxs-lookup"><span data-stu-id="00ac7-186">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="00ac7-187">第一步是更新注册常量和 `Initialize` 方法，以便这些常量指示“Make Const”分析器。</span><span class="sxs-lookup"><span data-stu-id="00ac7-187">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="00ac7-188">大多数字符串常量在字符串资源文件中定义。</span><span class="sxs-lookup"><span data-stu-id="00ac7-188">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="00ac7-189">应遵循此做法，以便更轻松地实现本地化。</span><span class="sxs-lookup"><span data-stu-id="00ac7-189">You should follow that practice for easier localization.</span></span> <span data-ttu-id="00ac7-190">打开“MakeConst”分析器项目的“Resources.resx”。</span><span class="sxs-lookup"><span data-stu-id="00ac7-190">Open the **Resources.resx** file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="00ac7-191">将显示资源编辑器。</span><span class="sxs-lookup"><span data-stu-id="00ac7-191">This displays the resource editor.</span></span> <span data-ttu-id="00ac7-192">更新字符串资源，如下所示：</span><span class="sxs-lookup"><span data-stu-id="00ac7-192">Update the string resources as follows:</span></span>

- <span data-ttu-id="00ac7-193">将 `AnalyzerTitle` 更改为“变量可以保持不变”。</span><span class="sxs-lookup"><span data-stu-id="00ac7-193">Change `AnalyzerTitle` to "Variable can be made constant".</span></span>
- <span data-ttu-id="00ac7-194">将 `AnalyzerMessageFormat` 更改为“可以保持不变”。</span><span class="sxs-lookup"><span data-stu-id="00ac7-194">Change `AnalyzerMessageFormat` to "Can be made constant".</span></span>
- <span data-ttu-id="00ac7-195">将 `AnalyzerDescription` 更改为“保持不变”。</span><span class="sxs-lookup"><span data-stu-id="00ac7-195">Change `AnalyzerDescription` to "Make Constant".</span></span>

<span data-ttu-id="00ac7-196">此外，将“访问修饰符”下拉列表更改为 `public`。</span><span class="sxs-lookup"><span data-stu-id="00ac7-196">Also, change the **Access Modifier** drop-down to `public`.</span></span> <span data-ttu-id="00ac7-197">这样可以更轻松地在单元测试中使用这些常量。</span><span class="sxs-lookup"><span data-stu-id="00ac7-197">That makes it easier to use these constants in unit tests.</span></span> <span data-ttu-id="00ac7-198">完成后，资源编辑器应如下图所示：</span><span class="sxs-lookup"><span data-stu-id="00ac7-198">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![更新字符串资源](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="00ac7-200">剩余的更改在分析器文件中。</span><span class="sxs-lookup"><span data-stu-id="00ac7-200">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="00ac7-201">在 Visual Studio 中打开“MakeConstAnalyzer.cs”。</span><span class="sxs-lookup"><span data-stu-id="00ac7-201">Open **MakeConstAnalyzer.cs** in Visual Studio.</span></span> <span data-ttu-id="00ac7-202">将注册操作从作用于符号的操作更改为作用于语法的操作。</span><span class="sxs-lookup"><span data-stu-id="00ac7-202">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="00ac7-203">在 `MakeConstAnalyzerAnalyzer.Initialize` 方法中，找到在符号上注册操作的行：</span><span class="sxs-lookup"><span data-stu-id="00ac7-203">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="00ac7-204">使用下面的行替换它：</span><span class="sxs-lookup"><span data-stu-id="00ac7-204">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="00ac7-205">完成此更改后，可以删除 `AnalyzeSymbol` 方法。</span><span class="sxs-lookup"><span data-stu-id="00ac7-205">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="00ac7-206">此分析器检查 <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>，而不是 <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> 语句。</span><span class="sxs-lookup"><span data-stu-id="00ac7-206">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="00ac7-207">请注意，`AnalyzeNode` 下面有红色波浪线。</span><span class="sxs-lookup"><span data-stu-id="00ac7-207">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="00ac7-208">刚添加的代码引用未声明的 `AnalyzeNode` 方法。</span><span class="sxs-lookup"><span data-stu-id="00ac7-208">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="00ac7-209">使用以下代码声明该方法：</span><span class="sxs-lookup"><span data-stu-id="00ac7-209">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="00ac7-210">将 `Category` 更改为 MakeConstAnalyzer.cs 中的“Usage”，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="00ac7-210">Change the `Category` to "Usage" in **MakeConstAnalyzer.cs** as shown in the following code:</span></span>

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="00ac7-211">查找可以是常量的局部声明</span><span class="sxs-lookup"><span data-stu-id="00ac7-211">Find local declarations that could be const</span></span>

<span data-ttu-id="00ac7-212">可以开始编写 `AnalyzeNode` 方法的第一个版本了。</span><span class="sxs-lookup"><span data-stu-id="00ac7-212">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="00ac7-213">应查找可以是 `const` 但实际不是的单个局部声明，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="00ac7-213">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="00ac7-214">第一步是查找局部声明。</span><span class="sxs-lookup"><span data-stu-id="00ac7-214">The first step is to find local declarations.</span></span> <span data-ttu-id="00ac7-215">将以下代码添加到 MakeConstAnalyzer.cs 中的 `AnalyzeNode`：</span><span class="sxs-lookup"><span data-stu-id="00ac7-215">Add the following code to `AnalyzeNode` in **MakeConstAnalyzer.cs**:</span></span>

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

<span data-ttu-id="00ac7-216">此强制转换始终会成功，因为分析器注册了对局部声明的更改，并且只注册了局部声明。</span><span class="sxs-lookup"><span data-stu-id="00ac7-216">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="00ac7-217">没有其他节点类型会触发对 `AnalyzeNode` 方法的调用。</span><span class="sxs-lookup"><span data-stu-id="00ac7-217">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="00ac7-218">接下来，检查任何 `const` 修饰符的声明。</span><span class="sxs-lookup"><span data-stu-id="00ac7-218">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="00ac7-219">一旦找到，请立即返回。</span><span class="sxs-lookup"><span data-stu-id="00ac7-219">If you find them, return immediately.</span></span> <span data-ttu-id="00ac7-220">以下代码用于查找局部声明上的任何 `const` 修饰符：</span><span class="sxs-lookup"><span data-stu-id="00ac7-220">The following code looks for any `const` modifiers on the local declaration:</span></span>

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

<span data-ttu-id="00ac7-221">最后，需要检查变量是否可能是 `const`。</span><span class="sxs-lookup"><span data-stu-id="00ac7-221">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="00ac7-222">这意味着确保在其初始化后永远不会对其赋值。</span><span class="sxs-lookup"><span data-stu-id="00ac7-222">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="00ac7-223">将使用 <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext> 执行一些语义分析。</span><span class="sxs-lookup"><span data-stu-id="00ac7-223">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="00ac7-224">使用 `context` 参数确定局部变量声明是否可为 `const`。</span><span class="sxs-lookup"><span data-stu-id="00ac7-224">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="00ac7-225"><xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> 表示单个源文件中的所有语义信息。</span><span class="sxs-lookup"><span data-stu-id="00ac7-225">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents all of semantic information in a single source file.</span></span> <span data-ttu-id="00ac7-226">可参阅涵盖了[语义模型](../work-with-semantics.md)的文章了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="00ac7-226">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="00ac7-227">将使用 <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> 在局部声明语句上执行数据流分析。</span><span class="sxs-lookup"><span data-stu-id="00ac7-227">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="00ac7-228">然后，使用此数据流分析的结果确保局部变量不会在任何其他位置用新值来编写。</span><span class="sxs-lookup"><span data-stu-id="00ac7-228">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="00ac7-229">调用 <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> 扩展方法来检索变量的 <xref:Microsoft.CodeAnalysis.ILocalSymbol>，并检查确认它不包含在数据流分析的 <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> 集中。</span><span class="sxs-lookup"><span data-stu-id="00ac7-229">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="00ac7-230">在 `AnalyzeNode` 方法的末尾添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="00ac7-230">Add the following code to the end of the `AnalyzeNode` method:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="00ac7-231">刚添加的代码可确保变量不会修改，并因此可以进行 `const` 操作。</span><span class="sxs-lookup"><span data-stu-id="00ac7-231">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="00ac7-232">现在可以引发诊断了。</span><span class="sxs-lookup"><span data-stu-id="00ac7-232">It's time to raise the diagnostic.</span></span> <span data-ttu-id="00ac7-233">将以下代码添加为 `AnalyzeNode` 的最后一行：</span><span class="sxs-lookup"><span data-stu-id="00ac7-233">Add the following code as the last line in `AnalyzeNode`:</span></span>

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<span data-ttu-id="00ac7-234">可以通过按 F5<kbd></kbd> 运行分析器来检查进度。</span><span class="sxs-lookup"><span data-stu-id="00ac7-234">You can check your progress by pressing <kbd>F5</kbd> to run your analyzer.</span></span> <span data-ttu-id="00ac7-235">可以加载前面创建的控制台应用程序，然后添加以下测试代码：</span><span class="sxs-lookup"><span data-stu-id="00ac7-235">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="00ac7-236">应显示灯泡，且分析器应报告诊断。</span><span class="sxs-lookup"><span data-stu-id="00ac7-236">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="00ac7-237">但是，灯泡仍使用模板生成的代码修补程序，并告知你可以用大写。</span><span class="sxs-lookup"><span data-stu-id="00ac7-237">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="00ac7-238">下一部分将说明如何编写代码修补程序。</span><span class="sxs-lookup"><span data-stu-id="00ac7-238">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="00ac7-239">编写代码修补程序</span><span class="sxs-lookup"><span data-stu-id="00ac7-239">Write the code fix</span></span>

<span data-ttu-id="00ac7-240">分析器可以提供一个或多个代码修补程序。</span><span class="sxs-lookup"><span data-stu-id="00ac7-240">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="00ac7-241">代码修补程序定义解决报告问题的编辑。</span><span class="sxs-lookup"><span data-stu-id="00ac7-241">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="00ac7-242">对于你创建的分析器，可以提供将插入 const 关键字的代码修补程序：</span><span class="sxs-lookup"><span data-stu-id="00ac7-242">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="00ac7-243">用户从编辑器的灯泡 UI 中选择它，Visual Studio 更改代码。</span><span class="sxs-lookup"><span data-stu-id="00ac7-243">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="00ac7-244">打开由模板添加的“MakeConstCodeFixProvider.cs”文件。</span><span class="sxs-lookup"><span data-stu-id="00ac7-244">Open the **MakeConstCodeFixProvider.cs** file added by the template.</span></span>  <span data-ttu-id="00ac7-245">此代码修补程序已绑定到由诊断分析器生成的诊断 ID，但它尚没有实施正确的代码转换。</span><span class="sxs-lookup"><span data-stu-id="00ac7-245">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span> <span data-ttu-id="00ac7-246">首先应删除一些模板代码。</span><span class="sxs-lookup"><span data-stu-id="00ac7-246">First you should remove some of the template code.</span></span> <span data-ttu-id="00ac7-247">将标题字符串更改为“保持不变”：</span><span class="sxs-lookup"><span data-stu-id="00ac7-247">Change the title string to "Make constant":</span></span>

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

<span data-ttu-id="00ac7-248">接下来，删除 `MakeUppercaseAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="00ac7-248">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="00ac7-249">它不再适用。</span><span class="sxs-lookup"><span data-stu-id="00ac7-249">It no longer applies.</span></span>

<span data-ttu-id="00ac7-250">所有代码修复提供程序都派生自 <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>。</span><span class="sxs-lookup"><span data-stu-id="00ac7-250">All code fix providers derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="00ac7-251">它们都重写 <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> 以报告可用的代码修补程序。</span><span class="sxs-lookup"><span data-stu-id="00ac7-251">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="00ac7-252">在 `RegisterCodeFixesAsync` 中，将正在搜索的上级节点类型更改为 <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> 以匹配诊断：</span><span class="sxs-lookup"><span data-stu-id="00ac7-252">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="00ac7-253">接下来，更改用于注册代码修补程序的最后一行。</span><span class="sxs-lookup"><span data-stu-id="00ac7-253">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="00ac7-254">修补程序将创建新的文档，该文档通过将 `const` 修饰符添加到现有声明生成：</span><span class="sxs-lookup"><span data-stu-id="00ac7-254">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="00ac7-255">你会注意到刚在符号 `MakeConstAsync` 上添加的代码中的红色波浪线。</span><span class="sxs-lookup"><span data-stu-id="00ac7-255">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="00ac7-256">添加的 `MakeConstAsync` 声明如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="00ac7-256">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="00ac7-257">新的 `MakeConstAsync` 方法会将表示用户源文件的 <xref:Microsoft.CodeAnalysis.Document> 转换到现包含 `const` 声明的新 <xref:Microsoft.CodeAnalysis.Document>。</span><span class="sxs-lookup"><span data-stu-id="00ac7-257">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="00ac7-258">创建一个新的 `const` 关键字标记，以在声明语句的开头处插入。</span><span class="sxs-lookup"><span data-stu-id="00ac7-258">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="00ac7-259">请注意，首先从声明语句的第一个标记中删除任何前导琐碎内容，然后将其附加到 `const` 标记。</span><span class="sxs-lookup"><span data-stu-id="00ac7-259">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="00ac7-260">将以下代码添加到 `MakeConstAsync` 方法中：</span><span class="sxs-lookup"><span data-stu-id="00ac7-260">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="00ac7-261">接下来，使用以下代码向声明添加 `const` 标记：</span><span class="sxs-lookup"><span data-stu-id="00ac7-261">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="00ac7-262">接下来，设置要匹配 C# 格式设置规则的新声明的格式。</span><span class="sxs-lookup"><span data-stu-id="00ac7-262">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="00ac7-263">对所做的更改进行格式设置以匹配现有代码，这可创建更好的体验。</span><span class="sxs-lookup"><span data-stu-id="00ac7-263">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="00ac7-264">紧接着在现有代码后面添加以下语句：</span><span class="sxs-lookup"><span data-stu-id="00ac7-264">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="00ac7-265">此代码需要新命名空间。</span><span class="sxs-lookup"><span data-stu-id="00ac7-265">A new namespace is required for this code.</span></span> <span data-ttu-id="00ac7-266">将下面的 `using` 指令添加到文件的顶部：</span><span class="sxs-lookup"><span data-stu-id="00ac7-266">Add the following `using` directive to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="00ac7-267">最后一步是进行编辑。</span><span class="sxs-lookup"><span data-stu-id="00ac7-267">The final step is to make your edit.</span></span> <span data-ttu-id="00ac7-268">此过程包括三个步骤：</span><span class="sxs-lookup"><span data-stu-id="00ac7-268">There are three steps to this process:</span></span>

1. <span data-ttu-id="00ac7-269">获取现有文档的句柄。</span><span class="sxs-lookup"><span data-stu-id="00ac7-269">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="00ac7-270">通过将现有声明替换为新声明来创建一个新文档。</span><span class="sxs-lookup"><span data-stu-id="00ac7-270">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="00ac7-271">返回新文档。</span><span class="sxs-lookup"><span data-stu-id="00ac7-271">Return the new document.</span></span>

<span data-ttu-id="00ac7-272">在 `MakeConstAsync` 方法的末尾添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="00ac7-272">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="00ac7-273">代码修补程序已准备就绪。</span><span class="sxs-lookup"><span data-stu-id="00ac7-273">Your code fix is ready to try.</span></span>  <span data-ttu-id="00ac7-274">按 <kbd> F5 </kbd> 在第二个 Visual Studio 实例中运行分析器项目。</span><span class="sxs-lookup"><span data-stu-id="00ac7-274">Press <kbd>F5</kbd> to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="00ac7-275">在第二个 Visual Studio 实例中，创建一个新的 C# 控制台应用程序项目并向 Main 方法添加使用常量值初始化的几个局部变量声明。</span><span class="sxs-lookup"><span data-stu-id="00ac7-275">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="00ac7-276">你将看到它们被报告为警告，如下所示。</span><span class="sxs-lookup"><span data-stu-id="00ac7-276">You'll see that they are reported as warnings as below.</span></span>

![可以发出 const 警告](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="00ac7-278">现在已经有了很大的进展。</span><span class="sxs-lookup"><span data-stu-id="00ac7-278">You've made a lot of progress.</span></span> <span data-ttu-id="00ac7-279">可以进行 `const` 操作的声明下具有波浪线。</span><span class="sxs-lookup"><span data-stu-id="00ac7-279">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="00ac7-280">但仍有工作要做。</span><span class="sxs-lookup"><span data-stu-id="00ac7-280">But there is still work to do.</span></span> <span data-ttu-id="00ac7-281">如果将 `const` 添加到依次以 `i`、`j` 和 `k` 开头的声明，该过程会很有效。</span><span class="sxs-lookup"><span data-stu-id="00ac7-281">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="00ac7-282">不过，如果以从 `k` 开始的不同顺序添加 `const` 修饰符，分析器会生成错误：`k` 无法声明为 `const`，除非 `i` 和 `j` 均已进行 `const` 处理。</span><span class="sxs-lookup"><span data-stu-id="00ac7-282">But, if you add the `const` modifier in a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="00ac7-283">必须执行详细分析，以确保处理可以声明和初始化变量的不同方式。</span><span class="sxs-lookup"><span data-stu-id="00ac7-283">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-data-driven-tests"></a><span data-ttu-id="00ac7-284">构建数据驱动测试</span><span class="sxs-lookup"><span data-stu-id="00ac7-284">Build data driven tests</span></span>

<span data-ttu-id="00ac7-285">分析器和代码修补程序在简单的单个声明情况下工作，可以对其进行 const 处理。</span><span class="sxs-lookup"><span data-stu-id="00ac7-285">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="00ac7-286">在许多可能的声明语句中，该实现会出错。</span><span class="sxs-lookup"><span data-stu-id="00ac7-286">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="00ac7-287">可以通过使用模板编写的单元测试库来处理这种情况。</span><span class="sxs-lookup"><span data-stu-id="00ac7-287">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="00ac7-288">它要比反复打开 Visual Studio 的第二个副本快得多。</span><span class="sxs-lookup"><span data-stu-id="00ac7-288">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="00ac7-289">打开单元测试项目中的“MakeConstUnitTests.cs”文件。</span><span class="sxs-lookup"><span data-stu-id="00ac7-289">Open the **MakeConstUnitTests.cs** file in the unit test project.</span></span> <span data-ttu-id="00ac7-290">该模板会创建两个测试，这些测试遵循分析器和代码修补程序单元测试的两种常见模式。</span><span class="sxs-lookup"><span data-stu-id="00ac7-290">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="00ac7-291">`TestMethod1` 显示测试模式，确保分析器在不应报告诊断的情况下不会执行此操作。</span><span class="sxs-lookup"><span data-stu-id="00ac7-291">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="00ac7-292">`TestMethod2` 演示用于报告诊断和运行代码修补程序的模式。</span><span class="sxs-lookup"><span data-stu-id="00ac7-292">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="00ac7-293">适用于分析器几乎每个测试的代码遵循这两种模式之一。</span><span class="sxs-lookup"><span data-stu-id="00ac7-293">The code for almost every test for your analyzer follows one of these two patterns.</span></span> <span data-ttu-id="00ac7-294">对于第一步，可以将这些测试作为数据驱动测试重新进行。</span><span class="sxs-lookup"><span data-stu-id="00ac7-294">For the first step, you can rework these tests as data driven tests.</span></span> <span data-ttu-id="00ac7-295">然后，可以轻松通过添加新字符串常量来表示不同的测试输入创建新的测试。</span><span class="sxs-lookup"><span data-stu-id="00ac7-295">Then, it will be easy to create new tests by adding new string constants to represent different test inputs.</span></span>

<span data-ttu-id="00ac7-296">为提高效率，第一步是将两个测试重构为数据驱动测试。</span><span class="sxs-lookup"><span data-stu-id="00ac7-296">For efficiency, the first step is to refactor the two tests into data driven tests.</span></span> <span data-ttu-id="00ac7-297">然后，只需每个新测试定义几个字符串常量。</span><span class="sxs-lookup"><span data-stu-id="00ac7-297">Then, you only need to define a couple string constants for each new test.</span></span> <span data-ttu-id="00ac7-298">重构时，将这两种方法重命名为更有意义的名称。</span><span class="sxs-lookup"><span data-stu-id="00ac7-298">While you are refactoring, rename both methods to better names.</span></span> <span data-ttu-id="00ac7-299">将 `TestMethod1` 替换为此测试，以确保不会引发诊断：</span><span class="sxs-lookup"><span data-stu-id="00ac7-299">Replace `TestMethod1` with this test that ensures no diagnostic is raised:</span></span>

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

<span data-ttu-id="00ac7-300">可以通过定义不应导致诊断触发警告的任何代码片段来针对此测试创建新的数据行。</span><span class="sxs-lookup"><span data-stu-id="00ac7-300">You can create a new data row for this test by defining any code fragment that should not cause your diagnostic to trigger a warning.</span></span> <span data-ttu-id="00ac7-301">当没有为源代码片段触发任何诊断，此 `VerifyCSharpDiagnostic` 重载将通过。</span><span class="sxs-lookup"><span data-stu-id="00ac7-301">This overload of `VerifyCSharpDiagnostic` passes when there are no diagnostics triggered for the source code fragment.</span></span>

<span data-ttu-id="00ac7-302">接下来，将 `TestMethod2` 替换为此测试，以确保引发诊断且代码修补程序应用于源代码片段：</span><span class="sxs-lookup"><span data-stu-id="00ac7-302">Next, replace `TestMethod2` with this test that ensures a diagnostic is raised and a code fix applied for the source code fragment:</span></span>

```csharp
[DataTestMethod]
[DataRow(LocalIntCouldBeConstant, LocalIntCouldBeConstantFixed, 10, 13)]
public void WhenDiagnosticIsRaisedFixUpdatesCode(
    string test,
    string fixTest,
    int line,
    int column)
{
    var expected = new DiagnosticResult
    {
        Id = MakeConstAnalyzer.DiagnosticId,
        Message = new LocalizableResourceString(nameof(MakeConst.Resources.AnalyzerMessageFormat), MakeConst.Resources.ResourceManager, typeof(MakeConst.Resources)).ToString(),
        Severity = DiagnosticSeverity.Warning,
        Locations =
            new[] {
                    new DiagnosticResultLocation("Test0.cs", line, column)
                }
    };

    VerifyCSharpDiagnostic(test, expected);

    VerifyCSharpFix(test, fixTest);
}
```

<span data-ttu-id="00ac7-303">前面的代码还对生成预期诊断结果的代码进行一些更改。</span><span class="sxs-lookup"><span data-stu-id="00ac7-303">The preceding code also made a couple changes to the code that builds the expected diagnostic result.</span></span> <span data-ttu-id="00ac7-304">它使用在 `MakeConst` 分析器中注册的公共常量。</span><span class="sxs-lookup"><span data-stu-id="00ac7-304">It uses the public constants registered in the `MakeConst` analyzer.</span></span> <span data-ttu-id="00ac7-305">此外，它使用两个输入和固定源字符串常量。</span><span class="sxs-lookup"><span data-stu-id="00ac7-305">In addition, it uses two string constants for the input and fixed source.</span></span> <span data-ttu-id="00ac7-306">将以下字符串约束添加到 `UnitTest` 类：</span><span class="sxs-lookup"><span data-stu-id="00ac7-306">Add the following string constants to the `UnitTest` class:</span></span>

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

<span data-ttu-id="00ac7-307">运行这两个测试，以确保其通过。</span><span class="sxs-lookup"><span data-stu-id="00ac7-307">Run these two tests to make sure they pass.</span></span> <span data-ttu-id="00ac7-308">在 Visual Studio 中，通过选择“测试” > “Windows” > “测试资源管理器”来打开“测试资源管理器”。</span><span class="sxs-lookup"><span data-stu-id="00ac7-308">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span> <span data-ttu-id="00ac7-309">然后选择“全部运行”链接。</span><span class="sxs-lookup"><span data-stu-id="00ac7-309">Then select the **Run All** link.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="00ac7-310">为有效声明创建测试</span><span class="sxs-lookup"><span data-stu-id="00ac7-310">Create tests for valid declarations</span></span>

<span data-ttu-id="00ac7-311">作为一般规则，分析器应尽可能使工作量最小化以快速退出。</span><span class="sxs-lookup"><span data-stu-id="00ac7-311">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="00ac7-312">Visual Studio 调用注册分析器作为用户编辑代码。</span><span class="sxs-lookup"><span data-stu-id="00ac7-312">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="00ac7-313">响应能力是一项关键要求。</span><span class="sxs-lookup"><span data-stu-id="00ac7-313">Responsiveness is a key requirement.</span></span> <span data-ttu-id="00ac7-314">有多个代码测试用例，不应引发诊断。</span><span class="sxs-lookup"><span data-stu-id="00ac7-314">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="00ac7-315">分析器已处理这些测试中的一个，其中变量在初始化后进行了分配。</span><span class="sxs-lookup"><span data-stu-id="00ac7-315">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="00ac7-316">将以下字符串常量添加到测试来表示这种情况：</span><span class="sxs-lookup"><span data-stu-id="00ac7-316">Add the following string constant to your tests to represent that case:</span></span>

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="00ac7-317">然后，为此测试添加数据行，如下面的代码段所示：</span><span class="sxs-lookup"><span data-stu-id="00ac7-317">Then, add a data row for this test as shown in the snippet below:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="00ac7-318">此测试也通过了。</span><span class="sxs-lookup"><span data-stu-id="00ac7-318">This test passes as well.</span></span> <span data-ttu-id="00ac7-319">接下来，为尚未处理的情况添加常量：</span><span class="sxs-lookup"><span data-stu-id="00ac7-319">Next, add constants for conditions you haven't handled yet:</span></span>

- <span data-ttu-id="00ac7-320">已经是 `const` 的声明，因为它们已为 const 类型：</span><span class="sxs-lookup"><span data-stu-id="00ac7-320">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- <span data-ttu-id="00ac7-321">没有初始值设定项的声明，因为没有要使用的值：</span><span class="sxs-lookup"><span data-stu-id="00ac7-321">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- <span data-ttu-id="00ac7-322">初始值设定项不是常量的声明，因为它们不能是编译时常量：</span><span class="sxs-lookup"><span data-stu-id="00ac7-322">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="00ac7-323">甚至可能更加复杂，因为 C# 允许多个声明作为一条语句。</span><span class="sxs-lookup"><span data-stu-id="00ac7-323">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="00ac7-324">请考虑以下测试用例字符串常量：</span><span class="sxs-lookup"><span data-stu-id="00ac7-324">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="00ac7-325">变量 `i` 可以常量化，但变量 `j` 不能。</span><span class="sxs-lookup"><span data-stu-id="00ac7-325">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="00ac7-326">因此，此语句不能成为 const 声明。</span><span class="sxs-lookup"><span data-stu-id="00ac7-326">Therefore, this statement cannot be made a const declaration.</span></span> <span data-ttu-id="00ac7-327">为所有这些测试添加 `DataRow` 声明：</span><span class="sxs-lookup"><span data-stu-id="00ac7-327">Add the `DataRow` declarations for all these tests:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
    DataRow(VariableAssigned),
    DataRow(AlreadyConst),
    DataRow(NoInitializer),
    DataRow(InitializerNotConstant),
    DataRow(MultipleInitializers)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="00ac7-328">再次运行测试，将看到这些新测试用例失败。</span><span class="sxs-lookup"><span data-stu-id="00ac7-328">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="00ac7-329">更新分析器以忽略正确声明</span><span class="sxs-lookup"><span data-stu-id="00ac7-329">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="00ac7-330">需要对分析器的 `AnalyzeNode` 方法进行一些增强，以筛选出匹配这些条件的代码。</span><span class="sxs-lookup"><span data-stu-id="00ac7-330">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="00ac7-331">它们是所有相关条件，因此类似的更改将解决所有这些条件。</span><span class="sxs-lookup"><span data-stu-id="00ac7-331">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="00ac7-332">对 `AnalyzeNode` 进行以下更改：</span><span class="sxs-lookup"><span data-stu-id="00ac7-332">Make the following changes to `AnalyzeNode`:</span></span>

- <span data-ttu-id="00ac7-333">语义分析检查单个变量声明。</span><span class="sxs-lookup"><span data-stu-id="00ac7-333">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="00ac7-334">此代码必须位于 `foreach` 循环中，以检查同一语句中声明的所有变量。</span><span class="sxs-lookup"><span data-stu-id="00ac7-334">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
- <span data-ttu-id="00ac7-335">每个声明变量需要有初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="00ac7-335">Each declared variable needs to have an initializer.</span></span>
- <span data-ttu-id="00ac7-336">每个声明的变量的初始值设定项必须是编译时常量。</span><span class="sxs-lookup"><span data-stu-id="00ac7-336">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="00ac7-337">在 `AnalyzeNode` 方法中，替换原始语义分析：</span><span class="sxs-lookup"><span data-stu-id="00ac7-337">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="00ac7-338">使用以下代码片段：</span><span class="sxs-lookup"><span data-stu-id="00ac7-338">with the following code snippet:</span></span>

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (var variable in localDeclaration.Declaration.Variables)
{
    var initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    var constantValue = context.SemanticModel.GetConstantValue(initializer.Value);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (var variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

<span data-ttu-id="00ac7-339">第一个 `foreach` 循环将使用语法分析检查每个变量声明。</span><span class="sxs-lookup"><span data-stu-id="00ac7-339">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="00ac7-340">第一次检查可保证该变量具有初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="00ac7-340">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="00ac7-341">第二次检查可保证初始值设定项是一个常量。</span><span class="sxs-lookup"><span data-stu-id="00ac7-341">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="00ac7-342">第二个循环具有原始语义分析。</span><span class="sxs-lookup"><span data-stu-id="00ac7-342">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="00ac7-343">语义检查是在一个单独循环中，因为它对性能具有更大的影响。</span><span class="sxs-lookup"><span data-stu-id="00ac7-343">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="00ac7-344">再次运行测试，应看到它们全部通过。</span><span class="sxs-lookup"><span data-stu-id="00ac7-344">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="00ac7-345">添加最后的润饰</span><span class="sxs-lookup"><span data-stu-id="00ac7-345">Add the final polish</span></span>

<span data-ttu-id="00ac7-346">即将完成。</span><span class="sxs-lookup"><span data-stu-id="00ac7-346">You're almost done.</span></span> <span data-ttu-id="00ac7-347">分析器还要处理一些其他条件。</span><span class="sxs-lookup"><span data-stu-id="00ac7-347">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="00ac7-348">用户编写代码时，Visual Studio 将调用分析器。</span><span class="sxs-lookup"><span data-stu-id="00ac7-348">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="00ac7-349">通常情况下，分析器将针对无法进行编译的代码进行调用。</span><span class="sxs-lookup"><span data-stu-id="00ac7-349">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="00ac7-350">诊断分析器的 `AnalyzeNode` 方法不会检查以查看常量值是否可转换为变量类型。</span><span class="sxs-lookup"><span data-stu-id="00ac7-350">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="00ac7-351">因此，当前实现会不假思索地将不正确的声明（如 int i = “abc”）转换为局部常量。</span><span class="sxs-lookup"><span data-stu-id="00ac7-351">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="00ac7-352">为以下条件添加源字符串常量：</span><span class="sxs-lookup"><span data-stu-id="00ac7-352">Add a source string constant for that condition:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="00ac7-353">此外，无法正确处理引用类型。</span><span class="sxs-lookup"><span data-stu-id="00ac7-353">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="00ac7-354">允许用于引用类型的唯一常量值为 `null`， <xref:System.String?displayProperty=nameWithType> 这种情况除外，后者允许字符串。</span><span class="sxs-lookup"><span data-stu-id="00ac7-354">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayProperty=nameWithType>, which allows string literals.</span></span> <span data-ttu-id="00ac7-355">换而言之，`const string s = "abc"` 是合法的，但 `const object s = "abc"` 不是。</span><span class="sxs-lookup"><span data-stu-id="00ac7-355">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="00ac7-356">此代码片段验证以下条件：</span><span class="sxs-lookup"><span data-stu-id="00ac7-356">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="00ac7-357">为全面起见，需要添加另一个测试以确保你可以为字符串创建常量声明。</span><span class="sxs-lookup"><span data-stu-id="00ac7-357">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="00ac7-358">以下代码片段定义引发诊断的代码和在应用修补程序后的代码：</span><span class="sxs-lookup"><span data-stu-id="00ac7-358">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="00ac7-359">最后，如使用关键字 `var` 声明变量，代码修补程序将执行错误操作，并生成 `const var` 声明，C# 语言不支持该声明。</span><span class="sxs-lookup"><span data-stu-id="00ac7-359">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="00ac7-360">若要修复此 bug，代码修补程序必须将 `var` 关键字替换为推断类型的名称：</span><span class="sxs-lookup"><span data-stu-id="00ac7-360">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="00ac7-361">这些更改将更新这两个测试的数据行声明。</span><span class="sxs-lookup"><span data-stu-id="00ac7-361">These changes update the data row declarations for both tests.</span></span> <span data-ttu-id="00ac7-362">下面的代码显示这些具有所有数据行属性的测试：</span><span class="sxs-lookup"><span data-stu-id="00ac7-362">The following code shows these tests with all data row attributes:</span></span>

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

<span data-ttu-id="00ac7-363">幸运的是，所有上述 bug 可以使用你刚刚了解的相同技术解决。</span><span class="sxs-lookup"><span data-stu-id="00ac7-363">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="00ac7-364">若要修复第一个 bug，请先打开“DiagnosticAnalyzer.cs”并找到 foreach 循环，将检查其中每个局部声明的初始值设定项以确保向其分配常量值。</span><span class="sxs-lookup"><span data-stu-id="00ac7-364">To fix the first bug, first open **DiagnosticAnalyzer.cs** and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="00ac7-365">在第一个 foreach 循环之前，立即调用 `context.SemanticModel.GetTypeInfo()` 来检索有关局部声明的声明类型的详细信息：</span><span class="sxs-lookup"><span data-stu-id="00ac7-365">Immediately _before_ the first foreach loop, call `context.SemanticModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

<span data-ttu-id="00ac7-366">然后，在 `foreach` 循环中，检查每个初始值设定项，以确保它可以转换为变量类型。</span><span class="sxs-lookup"><span data-stu-id="00ac7-366">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="00ac7-367">确保初始值设定项为常量后，添加以下检查：</span><span class="sxs-lookup"><span data-stu-id="00ac7-367">Add the following check after ensuring that the initializer is a constant:</span></span>

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

<span data-ttu-id="00ac7-368">下一次更改建立在最后一次更改之上。</span><span class="sxs-lookup"><span data-stu-id="00ac7-368">The next change builds upon the last one.</span></span> <span data-ttu-id="00ac7-369">在第一个 foreach 循环的右大括号前，添加以下代码以检查当常量为字符串或 NULL 时局部声明的类型。</span><span class="sxs-lookup"><span data-stu-id="00ac7-369">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

```csharp
// Special cases:
//  * If the constant value is a string, the type of the local declaration
//    must be System.String.
//  * If the constant value is null, the type of the local declaration must
//    be a reference type.
if (constantValue.Value is string)
{
    if (variableType.SpecialType != SpecialType.System_String)
    {
        return;
    }
}
else if (variableType.IsReferenceType && constantValue.Value != null)
{
    return;
}
```

<span data-ttu-id="00ac7-370">必须在代码修复提供程序中编写更多代码以将 `var` 关键字替换为正确类型名称。</span><span class="sxs-lookup"><span data-stu-id="00ac7-370">You must write a bit more code in your code fix provider to replace the `var` keyword with the correct type name.</span></span> <span data-ttu-id="00ac7-371">返回到 CodeFixProvider.cs。</span><span class="sxs-lookup"><span data-stu-id="00ac7-371">Return to **CodeFixProvider.cs**.</span></span> <span data-ttu-id="00ac7-372">要添加的代码将执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="00ac7-372">The code you'll add does the following steps:</span></span>

- <span data-ttu-id="00ac7-373">检查声明是否为 `var` 声明，如果它是：</span><span class="sxs-lookup"><span data-stu-id="00ac7-373">Check if the declaration is a `var` declaration, and if it is:</span></span>
- <span data-ttu-id="00ac7-374">创建新类型的推断类型。</span><span class="sxs-lookup"><span data-stu-id="00ac7-374">Create a new type for the inferred type.</span></span>
- <span data-ttu-id="00ac7-375">确保类型声明不是别名。</span><span class="sxs-lookup"><span data-stu-id="00ac7-375">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="00ac7-376">如果是这样，则声明 `const var` 是合法的。</span><span class="sxs-lookup"><span data-stu-id="00ac7-376">If so, it is legal to declare `const var`.</span></span>
- <span data-ttu-id="00ac7-377">确保 `var` 不是此程序中的类型名称。</span><span class="sxs-lookup"><span data-stu-id="00ac7-377">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="00ac7-378">（如果是这样，则 `const var` 是合法的）。</span><span class="sxs-lookup"><span data-stu-id="00ac7-378">(If so, `const var` is legal).</span></span>
- <span data-ttu-id="00ac7-379">简化完整类型名称</span><span class="sxs-lookup"><span data-stu-id="00ac7-379">Simplify the full type name</span></span>

<span data-ttu-id="00ac7-380">这听起来好像有很多代码。</span><span class="sxs-lookup"><span data-stu-id="00ac7-380">That sounds like a lot of code.</span></span> <span data-ttu-id="00ac7-381">其实不然。</span><span class="sxs-lookup"><span data-stu-id="00ac7-381">It's not.</span></span> <span data-ttu-id="00ac7-382">将声明和初始化 `newLocal` 的行替换为以下代码。</span><span class="sxs-lookup"><span data-stu-id="00ac7-382">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="00ac7-383">在初始化 `newModifiers` 之后立即进行：</span><span class="sxs-lookup"><span data-stu-id="00ac7-383">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="00ac7-384">需要添加一个 `using` 指令才能使用 <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> 类型：</span><span class="sxs-lookup"><span data-stu-id="00ac7-384">You'll need to add one `using` directive to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="00ac7-385">运行测试，它们应全部通过。</span><span class="sxs-lookup"><span data-stu-id="00ac7-385">Run your tests, and they should all pass.</span></span> <span data-ttu-id="00ac7-386">通过运行已完成的分析器自行庆祝。</span><span class="sxs-lookup"><span data-stu-id="00ac7-386">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="00ac7-387">按 <kbd>Ctrl</kbd>+<kbd>F5</kbd> 在加载了 Roslyn Preview 扩展的第二个 Visual Studio 实例中运行分析器项目。</span><span class="sxs-lookup"><span data-stu-id="00ac7-387">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

- <span data-ttu-id="00ac7-388">在第二个 Visual Studio 实例，创建一个新的 C# 控制台应用程序项目并将 `int x = "abc";` 添加到 Main 方法。</span><span class="sxs-lookup"><span data-stu-id="00ac7-388">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="00ac7-389">由于第一个 bug 已修复，应不会报告针对此局部变量声明的警告（尽管像预期那样出现了编译器错误）。</span><span class="sxs-lookup"><span data-stu-id="00ac7-389">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
- <span data-ttu-id="00ac7-390">接下来，将 `object s = "abc";` 添加到 Main 方法。</span><span class="sxs-lookup"><span data-stu-id="00ac7-390">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="00ac7-391">由于第二个 bug 已修复，应不会报告任何警告。</span><span class="sxs-lookup"><span data-stu-id="00ac7-391">Because of the second bug fix, no warning should be reported.</span></span>
- <span data-ttu-id="00ac7-392">最后，添加另一个使用 `var` 关键字的局部变量。</span><span class="sxs-lookup"><span data-stu-id="00ac7-392">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="00ac7-393">你将看到一个警告和显示在左下方的一个建议。</span><span class="sxs-lookup"><span data-stu-id="00ac7-393">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
- <span data-ttu-id="00ac7-394">将编辑器插入点移到波浪下划线，然后按 <kbd>Ctrl</kbd>+<kbd>。</kbd></span><span class="sxs-lookup"><span data-stu-id="00ac7-394">Move the editor caret over the squiggly underline and press <kbd>Ctrl</kbd>+<kbd>.</kbd>.</span></span> <span data-ttu-id="00ac7-395">显示建议的代码修补程序。</span><span class="sxs-lookup"><span data-stu-id="00ac7-395">to display the suggested code fix.</span></span> <span data-ttu-id="00ac7-396">选择代码修补程序，请注意，`var` 关键字现已正确处理。</span><span class="sxs-lookup"><span data-stu-id="00ac7-396">Upon selecting your code fix, note that the `var` keyword is now handled correctly.</span></span>

<span data-ttu-id="00ac7-397">最后，添加以下代码：</span><span class="sxs-lookup"><span data-stu-id="00ac7-397">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="00ac7-398">完成这些更改后，仅在前两个变量上有红色波浪线。</span><span class="sxs-lookup"><span data-stu-id="00ac7-398">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="00ac7-399">将 `const` 同时添加到 `i` 和 `j`，你将获得一个有关 `k` 的新警告，因为它现在可以是 `const`。</span><span class="sxs-lookup"><span data-stu-id="00ac7-399">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="00ac7-400">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="00ac7-400">Congratulations!</span></span> <span data-ttu-id="00ac7-401">你已创建第一个 .NET Compiler Platform 扩展来执行即时代码分析，以便检测问题，并提供了用于快速更正的修补程序。</span><span class="sxs-lookup"><span data-stu-id="00ac7-401">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="00ac7-402">在此过程中，你已了解很多代码 API 是 .NET Compiler Platform SDK (Roslyn API) 的一部分。</span><span class="sxs-lookup"><span data-stu-id="00ac7-402">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="00ac7-403">可以在我们的示例 GitHub 存储库中根据[完成的示例](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst)来检查工作。</span><span class="sxs-lookup"><span data-stu-id="00ac7-403">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span>

## <a name="other-resources"></a><span data-ttu-id="00ac7-404">其他资源</span><span class="sxs-lookup"><span data-stu-id="00ac7-404">Other resources</span></span>

- [<span data-ttu-id="00ac7-405">语法分析入门</span><span class="sxs-lookup"><span data-stu-id="00ac7-405">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="00ac7-406">语义分析入门</span><span class="sxs-lookup"><span data-stu-id="00ac7-406">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)
