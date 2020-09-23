---
title: Visual Basic 程序的结构
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: 90bc1fd62a05f670424e1fac368376401d1030c0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097769"
---
# <a name="structure-of-a-visual-basic-program"></a><span data-ttu-id="db353-102">Visual Basic 程序的结构</span><span class="sxs-lookup"><span data-stu-id="db353-102">Structure of a Visual Basic Program</span></span>

<span data-ttu-id="db353-103">Visual Basic 程序由标准构建基块构建。</span><span class="sxs-lookup"><span data-stu-id="db353-103">A Visual Basic program is built up from standard building blocks.</span></span> <span data-ttu-id="db353-104">*解决方案*由一个或多个项目组成。</span><span class="sxs-lookup"><span data-stu-id="db353-104">A *solution* comprises one or more projects.</span></span> <span data-ttu-id="db353-105">一个 *项目* 又可以包含一个或多个程序集。</span><span class="sxs-lookup"><span data-stu-id="db353-105">A *project* in turn can contain one or more assemblies.</span></span> <span data-ttu-id="db353-106">每个 *程序集* 都从一个或多个源文件进行编译。</span><span class="sxs-lookup"><span data-stu-id="db353-106">Each *assembly* is compiled from one or more source files.</span></span> <span data-ttu-id="db353-107">*源文件*提供类、结构、模块和接口的定义和实现，它们最终包含所有代码。</span><span class="sxs-lookup"><span data-stu-id="db353-107">A *source file* provides the definition and implementation of classes, structures, modules, and interfaces, which ultimately contain all your code.</span></span>  
  
 <span data-ttu-id="db353-108">有关 Visual Basic 程序的这些构建基块的详细信息，请参阅 .NET 中的 [解决方案和项目](/visualstudio/ide/solutions-and-projects-in-visual-studio) 和 [程序集](../../../standard/assembly/index.md)。</span><span class="sxs-lookup"><span data-stu-id="db353-108">For more information about these building blocks of a Visual Basic program, see [Solutions and Projects](/visualstudio/ide/solutions-and-projects-in-visual-studio) and [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
## <a name="file-level-programming-elements"></a><span data-ttu-id="db353-109">文件级编程元素</span><span class="sxs-lookup"><span data-stu-id="db353-109">File-Level Programming Elements</span></span>  

 <span data-ttu-id="db353-110">当您启动项目或文件并打开 "代码编辑器" 时，您将看到一些代码已存在并按正确的顺序排列。</span><span class="sxs-lookup"><span data-stu-id="db353-110">When you start a project or file and open the code editor, you see some code already in place and in the correct order.</span></span> <span data-ttu-id="db353-111">你编写的任何代码都应遵循以下顺序：</span><span class="sxs-lookup"><span data-stu-id="db353-111">Any code that you write should follow the following sequence:</span></span>  
  
1. <span data-ttu-id="db353-112">`Option` 前瞻性</span><span class="sxs-lookup"><span data-stu-id="db353-112">`Option` statements</span></span>  
  
2. <span data-ttu-id="db353-113">`Imports` 前瞻性</span><span class="sxs-lookup"><span data-stu-id="db353-113">`Imports` statements</span></span>  
  
3. <span data-ttu-id="db353-114">`Namespace` 语句和命名空间级别元素</span><span class="sxs-lookup"><span data-stu-id="db353-114">`Namespace` statements and namespace-level elements</span></span>  
  
 <span data-ttu-id="db353-115">如果按不同的顺序输入语句，则可能会导致编译错误。</span><span class="sxs-lookup"><span data-stu-id="db353-115">If you enter statements in a different order, compilation errors can result.</span></span>  
  
 <span data-ttu-id="db353-116">程序还可以包含条件编译语句。</span><span class="sxs-lookup"><span data-stu-id="db353-116">A program can also contain conditional compilation statements.</span></span> <span data-ttu-id="db353-117">可以在上述序列的语句之间点播这些文件。</span><span class="sxs-lookup"><span data-stu-id="db353-117">You can intersperse these in the source file among the statements of the preceding sequence.</span></span>  
  
### <a name="option-statements"></a><span data-ttu-id="db353-118">Option 语句</span><span class="sxs-lookup"><span data-stu-id="db353-118">Option Statements</span></span>  

 <span data-ttu-id="db353-119">`Option` 语句为后续代码建立基本规则，帮助防止语法和逻辑错误。</span><span class="sxs-lookup"><span data-stu-id="db353-119">`Option` statements establish ground rules for subsequent code, helping prevent syntax and logic errors.</span></span> <span data-ttu-id="db353-120">[Option Explicit 语句](../../language-reference/statements/option-explicit-statement.md)可确保所有变量都已正确声明和拼写，从而减少了调试时间。</span><span class="sxs-lookup"><span data-stu-id="db353-120">The [Option Explicit Statement](../../language-reference/statements/option-explicit-statement.md) ensures that all variables are declared and spelled correctly, which reduces debugging time.</span></span> <span data-ttu-id="db353-121">[Option Strict 语句](../../language-reference/statements/option-strict-statement.md)有助于最大程度减少在不同数据类型的变量之间工作时可能发生的逻辑错误和数据丢失。</span><span class="sxs-lookup"><span data-stu-id="db353-121">The [Option Strict Statement](../../language-reference/statements/option-strict-statement.md) helps to minimize logic errors and data loss that can occur when you work between variables of different data types.</span></span> <span data-ttu-id="db353-122">[Option Compare 语句](../../language-reference/statements/option-compare-statement.md)根据它们的或值来指定字符串的比较方式 `Binary` `Text` 。</span><span class="sxs-lookup"><span data-stu-id="db353-122">The [Option Compare Statement](../../language-reference/statements/option-compare-statement.md) specifies the way strings are compared to each other, based on either their `Binary` or `Text` values.</span></span>  
  
### <a name="imports-statements"></a><span data-ttu-id="db353-123">Imports 语句</span><span class="sxs-lookup"><span data-stu-id="db353-123">Imports Statements</span></span>  

 <span data-ttu-id="db353-124">可以在 [.Net 命名空间 ( 包含 Imports 语句，并键入) ](../../language-reference/statements/imports-statement-net-namespace-and-type.md) 导入项目外部定义的名称。</span><span class="sxs-lookup"><span data-stu-id="db353-124">You can include an [Imports Statement (.NET Namespace and Type)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) to import names defined outside your project.</span></span> <span data-ttu-id="db353-125">`Imports`通过语句，你的代码可以引用在导入的命名空间中定义的类和其他类型，而无需对它们进行限定。</span><span class="sxs-lookup"><span data-stu-id="db353-125">An `Imports` statement allows your code to refer to classes and other types defined within the imported namespace, without having to qualify them.</span></span> <span data-ttu-id="db353-126">您可以根据需要使用任意多个 `Imports` 语句。</span><span class="sxs-lookup"><span data-stu-id="db353-126">You can use as many `Imports` statements as appropriate.</span></span> <span data-ttu-id="db353-127">有关详细信息，请参阅 [引用和 Imports 语句](references-and-the-imports-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="db353-127">For more information, see [References and the Imports Statement](references-and-the-imports-statement.md).</span></span>  
  
### <a name="namespace-statements"></a><span data-ttu-id="db353-128">Namespace 语句</span><span class="sxs-lookup"><span data-stu-id="db353-128">Namespace Statements</span></span>  

 <span data-ttu-id="db353-129">命名空间可帮助你组织和分类编程元素以便于分组和访问。</span><span class="sxs-lookup"><span data-stu-id="db353-129">Namespaces help you organize and classify your programming elements for ease of grouping and accessing.</span></span> <span data-ttu-id="db353-130">使用 [Namespace 语句](../../language-reference/statements/namespace-statement.md) 将特定命名空间中的以下语句分类。</span><span class="sxs-lookup"><span data-stu-id="db353-130">You use the [Namespace Statement](../../language-reference/statements/namespace-statement.md) to classify the following statements within a particular namespace.</span></span> <span data-ttu-id="db353-131">有关详细信息，请参阅 [Visual Basic 中的命名空间](namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="db353-131">For more information, see [Namespaces in Visual Basic](namespaces.md).</span></span>  
  
### <a name="conditional-compilation-statements"></a><span data-ttu-id="db353-132">条件编译语句</span><span class="sxs-lookup"><span data-stu-id="db353-132">Conditional Compilation Statements</span></span>  

 <span data-ttu-id="db353-133">条件编译语句几乎可以出现在源文件中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="db353-133">Conditional compilation statements can appear almost anywhere in your source file.</span></span> <span data-ttu-id="db353-134">它们会在编译时包含或排除部分代码，具体取决于特定的条件。</span><span class="sxs-lookup"><span data-stu-id="db353-134">They cause parts of your code to be included or excluded at compile time depending on certain conditions.</span></span> <span data-ttu-id="db353-135">你还可以使用它们来调试应用程序，因为条件代码仅在调试模式下运行。</span><span class="sxs-lookup"><span data-stu-id="db353-135">You can also use them for debugging your application, because conditional code runs in debugging mode only.</span></span> <span data-ttu-id="db353-136">有关详细信息，请参阅 [条件编译](conditional-compilation.md)。</span><span class="sxs-lookup"><span data-stu-id="db353-136">For more information, see [Conditional Compilation](conditional-compilation.md).</span></span>  
  
## <a name="namespace-level-programming-elements"></a><span data-ttu-id="db353-137">命名空间级编程元素</span><span class="sxs-lookup"><span data-stu-id="db353-137">Namespace-Level Programming Elements</span></span>  

 <span data-ttu-id="db353-138">类、结构和模块包含源文件中的所有代码。</span><span class="sxs-lookup"><span data-stu-id="db353-138">Classes, structures, and modules contain all the code in your source file.</span></span> <span data-ttu-id="db353-139">它们是 *命名空间级别* 的元素，可出现在命名空间或源文件级别。</span><span class="sxs-lookup"><span data-stu-id="db353-139">They are *namespace-level* elements, which can appear within a namespace or at the source file level.</span></span> <span data-ttu-id="db353-140">它们保留所有其他编程元素的声明。</span><span class="sxs-lookup"><span data-stu-id="db353-140">They hold the declarations of all other programming elements.</span></span> <span data-ttu-id="db353-141">接口用于定义元素签名，但不提供实现，也显示在模块级别。</span><span class="sxs-lookup"><span data-stu-id="db353-141">Interfaces, which define element signatures but provide no implementation, also appear at module level.</span></span> <span data-ttu-id="db353-142">有关模块级元素的详细信息，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="db353-142">For more information on the module-level elements, see the following:</span></span>  
  
- [<span data-ttu-id="db353-143">Class 语句</span><span class="sxs-lookup"><span data-stu-id="db353-143">Class Statement</span></span>](../../language-reference/statements/class-statement.md)  
  
- [<span data-ttu-id="db353-144">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="db353-144">Structure Statement</span></span>](../../language-reference/statements/structure-statement.md)  
  
- [<span data-ttu-id="db353-145">Module 语句</span><span class="sxs-lookup"><span data-stu-id="db353-145">Module Statement</span></span>](../../language-reference/statements/module-statement.md)  
  
- [<span data-ttu-id="db353-146">Interface 语句</span><span class="sxs-lookup"><span data-stu-id="db353-146">Interface Statement</span></span>](../../language-reference/statements/interface-statement.md)  
  
 <span data-ttu-id="db353-147">命名空间级别的数据元素是枚举和委托。</span><span class="sxs-lookup"><span data-stu-id="db353-147">Data elements at namespace level are enumerations and delegates.</span></span>  
  
## <a name="module-level-programming-elements"></a><span data-ttu-id="db353-148">模块级编程元素</span><span class="sxs-lookup"><span data-stu-id="db353-148">Module-Level Programming Elements</span></span>  

 <span data-ttu-id="db353-149">过程、运算符、属性和事件是唯一的编程元素，这些元素可以保存可执行代码 (在运行时) 执行操作的语句。</span><span class="sxs-lookup"><span data-stu-id="db353-149">Procedures, operators, properties, and events are the only programming elements that can hold executable code (statements that perform actions at run time).</span></span> <span data-ttu-id="db353-150">它们是程序的 *模块级* 元素。</span><span class="sxs-lookup"><span data-stu-id="db353-150">They are the *module-level* elements of your program.</span></span> <span data-ttu-id="db353-151">有关过程级元素的详细信息，请参阅以下内容：</span><span class="sxs-lookup"><span data-stu-id="db353-151">For more information on the procedure-level elements, see the following:</span></span>  
  
- [<span data-ttu-id="db353-152">Function 语句</span><span class="sxs-lookup"><span data-stu-id="db353-152">Function Statement</span></span>](../../language-reference/statements/function-statement.md)  
  
- [<span data-ttu-id="db353-153">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="db353-153">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)  
  
- [<span data-ttu-id="db353-154">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="db353-154">Declare Statement</span></span>](../../language-reference/statements/declare-statement.md)  
  
- [<span data-ttu-id="db353-155">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="db353-155">Operator Statement</span></span>](../../language-reference/statements/operator-statement.md)  
  
- [<span data-ttu-id="db353-156">Property Statement</span><span class="sxs-lookup"><span data-stu-id="db353-156">Property Statement</span></span>](../../language-reference/statements/property-statement.md)  
  
- [<span data-ttu-id="db353-157">Event 语句</span><span class="sxs-lookup"><span data-stu-id="db353-157">Event Statement</span></span>](../../language-reference/statements/event-statement.md)  
  
 <span data-ttu-id="db353-158">模块级的数据元素包括变量、常量、枚举和委托。</span><span class="sxs-lookup"><span data-stu-id="db353-158">Data elements at module level are variables, constants, enumerations, and delegates.</span></span>  
  
## <a name="procedure-level-programming-elements"></a><span data-ttu-id="db353-159">过程级编程元素</span><span class="sxs-lookup"><span data-stu-id="db353-159">Procedure-Level Programming Elements</span></span>  

 <span data-ttu-id="db353-160">*过程级*元素的大部分内容是可执行语句，这些语句构成程序的运行时代码。</span><span class="sxs-lookup"><span data-stu-id="db353-160">Most of the contents of *procedure-level* elements are executable statements, which constitute the run-time code of your program.</span></span> <span data-ttu-id="db353-161">所有可执行代码都必须在 (`Function` 、 `Sub` 、、 `Operator` `Get` 、、、) `Set` `AddHandler` `RemoveHandler` `RaiseEvent` 的过程中。</span><span class="sxs-lookup"><span data-stu-id="db353-161">All executable code must be in some procedure (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`).</span></span> <span data-ttu-id="db353-162">有关详细信息，请参阅[语句](../language-features/statements.md)。</span><span class="sxs-lookup"><span data-stu-id="db353-162">For more information, see [Statements](../language-features/statements.md).</span></span>  
  
 <span data-ttu-id="db353-163">过程级别的数据元素仅限于局部变量和常量。</span><span class="sxs-lookup"><span data-stu-id="db353-163">Data elements at procedure level are limited to local variables and constants.</span></span>  
  
## <a name="the-main-procedure"></a><span data-ttu-id="db353-164">Main 过程</span><span class="sxs-lookup"><span data-stu-id="db353-164">The Main Procedure</span></span>  

 <span data-ttu-id="db353-165">此 `Main` 过程是加载应用程序时要运行的第一个代码。</span><span class="sxs-lookup"><span data-stu-id="db353-165">The `Main` procedure is the first code to run when your application has been loaded.</span></span> <span data-ttu-id="db353-166">`Main` 用作应用程序的起点和总体控制。</span><span class="sxs-lookup"><span data-stu-id="db353-166">`Main` serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="db353-167">有四种种类的 `Main` ：</span><span class="sxs-lookup"><span data-stu-id="db353-167">There are four varieties of `Main`:</span></span>  
  
- `Sub Main()`  
  
- `Sub Main(ByVal cmdArgs() As String)`  
  
- `Function Main() As Integer`  
  
- `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 <span data-ttu-id="db353-168">此过程最常见的方法是 `Sub Main()` 。</span><span class="sxs-lookup"><span data-stu-id="db353-168">The most common variety of this procedure is `Sub Main()`.</span></span> <span data-ttu-id="db353-169">有关详细信息，请参阅 [中的 Main 过程 Visual Basic](main-procedure.md)。</span><span class="sxs-lookup"><span data-stu-id="db353-169">For more information, see [Main Procedure in Visual Basic](main-procedure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db353-170">请参阅</span><span class="sxs-lookup"><span data-stu-id="db353-170">See also</span></span>

- [<span data-ttu-id="db353-171">Visual Basic 中的 Main 过程</span><span class="sxs-lookup"><span data-stu-id="db353-171">Main Procedure in Visual Basic</span></span>](main-procedure.md)
- [<span data-ttu-id="db353-172">Visual Basic 命名约定</span><span class="sxs-lookup"><span data-stu-id="db353-172">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
- [<span data-ttu-id="db353-173">Visual Basic 限制</span><span class="sxs-lookup"><span data-stu-id="db353-173">Visual Basic Limitations</span></span>](limitations.md)
