---
title: 错误消息
ms.date: 07/20/2015
helpviewer_keywords:
- errors [Visual Basic]
- error messages
- trappable errors
- errors [Visual Basic], trappable
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: 8c3ae80df58e00076692d91881534704d8278ff1
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873982"
---
# <a name="error-messages-visual-basic"></a><span data-ttu-id="a7095-102">错误消息 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7095-102">Error Messages (Visual Basic)</span></span>

<span data-ttu-id="a7095-103">编写、编译或运行 Visual Basic 应用程序时，可能会生成以下类型的错误：</span><span class="sxs-lookup"><span data-stu-id="a7095-103">When you write, compile, or run a Visual Basic application, the following types of errors can occur:</span></span>  
  
1. <span data-ttu-id="a7095-104">在 Visual Studio 中编写应用程序时发生的设计时错误。</span><span class="sxs-lookup"><span data-stu-id="a7095-104">Design-time errors, which occur when you write an application in Visual Studio.</span></span>  
  
2. <span data-ttu-id="a7095-105">在 Visual Studio 或命令提示符中编译应用程序时发生的编译时错误。</span><span class="sxs-lookup"><span data-stu-id="a7095-105">Compile-time errors, which occur when you compile an application in Visual Studio or at a command prompt.</span></span>  
  
3. <span data-ttu-id="a7095-106">在 Visual Studio 中运行应用程序或作为独立可执行文件运行时发生的运行时错误。</span><span class="sxs-lookup"><span data-stu-id="a7095-106">Run-time errors, which occur when you run an application in Visual Studio or as a stand-alone executable file.</span></span>  
  
 <span data-ttu-id="a7095-107">若要了解如何排查特定错误，请参阅[为 Visual Basic 程序员提供的附加资源](../../getting-started/additional-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="a7095-107">For information about how to troubleshoot a specific error, see [Additional Resources for Visual Basic Programmers](../../getting-started/additional-resources.md).</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="a7095-108">运行时错误</span><span class="sxs-lookup"><span data-stu-id="a7095-108">Run Time Errors</span></span>  

 <span data-ttu-id="a7095-109">如果 Visual Basic 应用程序尝试执行系统无法执行的操作，则会发生运行时错误，并且 Visual Basic 会引发 `Exception` 对象。</span><span class="sxs-lookup"><span data-stu-id="a7095-109">If a Visual Basic application tries to perform an action that the system can't execute, a run-time error occurs, and Visual Basic throws an `Exception` object.</span></span> <span data-ttu-id="a7095-110">Visual Basic 可以通过使用语句，生成任何数据类型（包括对象）的自定义错误 `Exception` `Throw` 。</span><span class="sxs-lookup"><span data-stu-id="a7095-110">Visual Basic can generate custom errors of any data type, including `Exception` objects, by using the `Throw` statement.</span></span> <span data-ttu-id="a7095-111">应用程序可以通过显示捕获到的异常的错误号和消息来识别错误。</span><span class="sxs-lookup"><span data-stu-id="a7095-111">An application can identify the error by displaying the error number and message of a caught exception.</span></span> <span data-ttu-id="a7095-112">如果未捕获到错误，应用程序会结束。</span><span class="sxs-lookup"><span data-stu-id="a7095-112">If an error isn't caught, the application ends.</span></span>  
  
 <span data-ttu-id="a7095-113">代码可用于捕获和检查运行时错误。</span><span class="sxs-lookup"><span data-stu-id="a7095-113">The code can trap and examine run-time errors.</span></span> <span data-ttu-id="a7095-114">如果将生成错误的代码封闭在 `Try` 代码块中，则可以在匹配的 `Catch` 代码块中捕获抛出的任何错误。</span><span class="sxs-lookup"><span data-stu-id="a7095-114">If you enclose the code that produces the error in a `Try` block, you can catch any thrown error within a matching `Catch` block.</span></span> <span data-ttu-id="a7095-115">若要了解如何在运行时捕获错误并在代码中响应错误，请参阅 [Try...Catch...Finally 语句](../statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="a7095-115">For information about how to trap errors at run time and respond to them in your code, see [Try...Catch...Finally Statement](../statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="compile-time-errors"></a><span data-ttu-id="a7095-116">编译时错误</span><span class="sxs-lookup"><span data-stu-id="a7095-116">Compile Time Errors</span></span>  

 <span data-ttu-id="a7095-117">如果 Visual Basic 编译器遇到代码问题，则会发生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="a7095-117">If the Visual Basic compiler encounters a problem in the code, a compile-time error occurs.</span></span> <span data-ttu-id="a7095-118">在代码编辑器中，可以轻松确定哪行代码导致错误发生，因为其下方会显示一条波形线。</span><span class="sxs-lookup"><span data-stu-id="a7095-118">In the Code Editor, you can easily identify which line of code caused the error because a wavy line appears under that line of code.</span></span> <span data-ttu-id="a7095-119">指向波形下划线或打开“错误列表”\*\*\*\*，即可看到错误消息（还可以查看其他消息）。</span><span class="sxs-lookup"><span data-stu-id="a7095-119">The error message appears if you either point to the wavy underline or open the **Error List**, which also shows other messages.</span></span>  
  
 <span data-ttu-id="a7095-120">如果标识符有波形下划线，且最右边的字符下面有短下划线，可以为类、构造函数、方法、属性、字段或枚举生成存根。</span><span class="sxs-lookup"><span data-stu-id="a7095-120">If an identifier has a wavy underline and a short underline appears under the rightmost character, you can generate a stub for the class, constructor, method, property, field or enum.</span></span> <span data-ttu-id="a7095-121">有关详细信息，请参阅[根据使用情况生成](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage)。</span><span class="sxs-lookup"><span data-stu-id="a7095-121">For more information, see [Generate From Usage](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).</span></span>
  
 <span data-ttu-id="a7095-122">通过解决 Visual Basic 编译器警告提示的问题，可以编写运行速度更快、bug 更少的代码。</span><span class="sxs-lookup"><span data-stu-id="a7095-122">By resolving warnings from the Visual Basic compiler, you might be able to write code that runs faster and has fewer bugs.</span></span> <span data-ttu-id="a7095-123">这些警告可以识别可能会在应用程序运行时生成错误的代码。</span><span class="sxs-lookup"><span data-stu-id="a7095-123">These warnings identify code that may cause errors when the application is run.</span></span> <span data-ttu-id="a7095-124">例如，如果尝试调用未赋值的对象变量的成员、让未设置返回值的函数返回值或执行有逻辑错误的 `Try` 代码块来捕获异常，编译器都会生成警告。</span><span class="sxs-lookup"><span data-stu-id="a7095-124">For example, the compiler warns you if you try to invoke a member of an unassigned object variable, return from a function without setting the return value, or execute a `Try` block with errors in the logic to catch exceptions.</span></span> <span data-ttu-id="a7095-125">若要详细了解警告（包括如何启用和禁用警告），请参阅[在 Visual Basic 中配置警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="a7095-125">For more information about warnings, including how to turn them on and off, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>
