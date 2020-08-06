---
title: 使用异常 - C# 编程指南
description: 了解如何使用异常。 异常由遇到错误的代码引发，由更正错误的代码捕捉。
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: fb45381f1c6cfa2f27d036ead8e662b7a0d8d924
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303369"
---
# <a name="use-exceptions-c-programming-guide"></a><span data-ttu-id="2e935-104">使用异常（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="2e935-104">Use exceptions (C# programming guide)</span></span>

<span data-ttu-id="2e935-105">在 C# 中，程序中的运行时错误通过使用一种称为“异常”的机制在程序中传播。</span><span class="sxs-lookup"><span data-stu-id="2e935-105">In C#, errors in the program at run time are propagated through the program by using a mechanism called exceptions.</span></span> <span data-ttu-id="2e935-106">异常由遇到错误的代码引发，由能够更正错误的代码捕捉。</span><span class="sxs-lookup"><span data-stu-id="2e935-106">Exceptions are thrown by code that encounters an error and caught by code that can correct the error.</span></span> <span data-ttu-id="2e935-107">异常可由 .NET 运行时或由程序中的代码引发。</span><span class="sxs-lookup"><span data-stu-id="2e935-107">Exceptions can be thrown by the .NET runtime or by code in a program.</span></span> <span data-ttu-id="2e935-108">一旦引发了一个异常，此异常会在调用堆栈中传播，直到找到针对它的 `catch` 语句。</span><span class="sxs-lookup"><span data-stu-id="2e935-108">Once an exception is thrown, it propagates up the call stack until a `catch` statement for the exception is found.</span></span> <span data-ttu-id="2e935-109">未捕获的异常由系统提供的通用异常处理程序处理，该处理程序会显示一个对话框。</span><span class="sxs-lookup"><span data-stu-id="2e935-109">Uncaught exceptions are handled by a generic exception handler provided by the system that displays a dialog box.</span></span>  
  
 <span data-ttu-id="2e935-110">异常由从 <xref:System.Exception> 派生的类表示。</span><span class="sxs-lookup"><span data-stu-id="2e935-110">Exceptions are represented by classes derived from <xref:System.Exception>.</span></span> <span data-ttu-id="2e935-111">此类标识异常的类型，并包含详细描述异常的属性。</span><span class="sxs-lookup"><span data-stu-id="2e935-111">This class identifies the type of exception and contains properties that have details about the exception.</span></span> <span data-ttu-id="2e935-112">引发异常涉及创建异常派生类的实例，配置异常的属性（可选），然后使用 `throw` 关键字引发该对象。</span><span class="sxs-lookup"><span data-stu-id="2e935-112">Throwing an exception involves creating an instance of an exception-derived class, optionally configuring properties of the exception, and then throwing the object by using the `throw` keyword.</span></span> <span data-ttu-id="2e935-113">例如：</span><span class="sxs-lookup"><span data-stu-id="2e935-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 <span data-ttu-id="2e935-114">引发异常后，运行时将检查当前语句，以确定它是否在 `try` 块内。</span><span class="sxs-lookup"><span data-stu-id="2e935-114">After an exception is thrown, the runtime checks the current statement to see whether it is within a `try` block.</span></span> <span data-ttu-id="2e935-115">如果在，则将检查与 `try` 块关联的所有 `catch` 块，以确定它们是否可以捕获该异常。</span><span class="sxs-lookup"><span data-stu-id="2e935-115">If it is, any `catch` blocks associated with the `try` block are checked to see whether they can catch the exception.</span></span> <span data-ttu-id="2e935-116">`Catch` 块通常会指定异常类型；如果该 `catch` 块的类型与异常或异常的基类的类型相同，则该 `catch` 块可处理该方法。</span><span class="sxs-lookup"><span data-stu-id="2e935-116">`Catch` blocks typically specify exception types; if the type of the `catch` block is the same type as the exception, or a base class of the exception, the `catch` block can handle the method.</span></span> <span data-ttu-id="2e935-117">例如：</span><span class="sxs-lookup"><span data-stu-id="2e935-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 <span data-ttu-id="2e935-118">如果引发异常的语句不在 `try` 块内或者包含该语句的 `try` 块没有匹配的 `catch` 块，则运行时将检查调用方法中是否有 `try` 语句和 `catch` 块。</span><span class="sxs-lookup"><span data-stu-id="2e935-118">If the statement that throws an exception is not within a `try` block or if the `try` block that encloses it has no matching `catch` block, the runtime checks the calling method for a `try` statement and `catch` blocks.</span></span> <span data-ttu-id="2e935-119">运行时将继续调用堆栈，搜索兼容的 `catch` 块。</span><span class="sxs-lookup"><span data-stu-id="2e935-119">The runtime continues up the calling stack, searching for a compatible `catch` block.</span></span> <span data-ttu-id="2e935-120">在找到并执行 `catch` 块之后，控制权将传递给 `catch` 块之后的下一个语句。</span><span class="sxs-lookup"><span data-stu-id="2e935-120">After the `catch` block is found and executed, control is passed to the next statement after that `catch` block.</span></span>  
  
 <span data-ttu-id="2e935-121">一个 `try` 语句可包含多个 `catch` 块。</span><span class="sxs-lookup"><span data-stu-id="2e935-121">A `try` statement can contain more than one `catch` block.</span></span> <span data-ttu-id="2e935-122">将执行第一个能够处理该异常的 `catch` 语句；将忽略任何后续的 `catch` 语句，即使它们是兼容的也是如此。</span><span class="sxs-lookup"><span data-stu-id="2e935-122">The first `catch` statement that can handle the exception is executed; any following `catch` statements, even if they are compatible, are ignored.</span></span> <span data-ttu-id="2e935-123">因此，应始终按照从最具有针对性（或派生程序最高）到最不具有针对性的顺序来捕获块。</span><span class="sxs-lookup"><span data-stu-id="2e935-123">Therefore, catch blocks should always be ordered from most specific (or most-derived) to least specific.</span></span> <span data-ttu-id="2e935-124">例如：</span><span class="sxs-lookup"><span data-stu-id="2e935-124">For example:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 <span data-ttu-id="2e935-125">执行 `catch` 块之前，运行时会检查 `finally` 块。</span><span class="sxs-lookup"><span data-stu-id="2e935-125">Before the `catch` block is executed, the runtime checks for `finally` blocks.</span></span> <span data-ttu-id="2e935-126">`Finally` 块使程序员可以清除中止的 `try` 块可能遗留下的任何模糊状态，或者释放任何外部资源（例如图形句柄、数据库连接或文件流），而无需等待垃圾回收器在运行时完成这些对象。</span><span class="sxs-lookup"><span data-stu-id="2e935-126">`Finally` blocks enable the programmer to clean up any ambiguous state that could be left over from an aborted `try` block, or to release any external resources (such as graphics handles, database connections or file streams) without waiting for the garbage collector in the runtime to finalize the objects.</span></span> <span data-ttu-id="2e935-127">例如：</span><span class="sxs-lookup"><span data-stu-id="2e935-127">For example:</span></span>  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 <span data-ttu-id="2e935-128">如果 `WriteByte()` 引发了异常并且未调用 `file.Close()`，则第二个 `try` 块中尝试重新打开文件的代码将会失败，并且文件将保持锁定状态。</span><span class="sxs-lookup"><span data-stu-id="2e935-128">If `WriteByte()` threw an exception, the code in the second `try` block that tries to reopen the file would fail if `file.Close()` is not called, and the file would remain locked.</span></span> <span data-ttu-id="2e935-129">由于即使引发异常也会执行 `finally` 块，前一示例中的 `finally` 块可使文件正确关闭，从而有助于避免错误。</span><span class="sxs-lookup"><span data-stu-id="2e935-129">Because `finally` blocks are executed even if an exception is thrown, the `finally` block in the previous example allows for the file to be closed correctly and helps avoid an error.</span></span>  
  
 <span data-ttu-id="2e935-130">如果引发异常之后没有在调用堆栈上找到兼容的 `catch` 块，则会出现以下三种情况之一：</span><span class="sxs-lookup"><span data-stu-id="2e935-130">If no compatible `catch` block is found on the call stack after an exception is thrown, one of three things occurs:</span></span>  
  
- <span data-ttu-id="2e935-131">如果异常存在于终结器内，将中止终结器，并调用基类终结器（如果有）。</span><span class="sxs-lookup"><span data-stu-id="2e935-131">If the exception is within a finalizer, the finalizer is aborted and the base finalizer, if any, is called.</span></span>  
  
- <span data-ttu-id="2e935-132">如果调用堆栈包含静态构造函数或静态字段初始值设定项，将引发 <xref:System.TypeInitializationException>，同时将原始异常分配给新异常的 <xref:System.Exception.InnerException%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="2e935-132">If the call stack contains a static constructor, or a static field initializer, a <xref:System.TypeInitializationException> is thrown, with the original exception assigned to the <xref:System.Exception.InnerException%2A> property of the new exception.</span></span>  
  
- <span data-ttu-id="2e935-133">如果到达线程的开头，则终止线程。</span><span class="sxs-lookup"><span data-stu-id="2e935-133">If the start of the thread is reached, the thread is terminated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e935-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="2e935-134">See also</span></span>

- [<span data-ttu-id="2e935-135">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="2e935-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2e935-136">异常和异常处理</span><span class="sxs-lookup"><span data-stu-id="2e935-136">Exceptions and Exception Handling</span></span>](./index.md)
