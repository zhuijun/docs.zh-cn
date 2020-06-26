---
title: 如何：向应用程序代码添加跟踪语句
description: 了解如何在 .NET 中将跟踪语句添加到应用程序代码。 跟踪使用最常用的方法是将输出写入侦听器的方法。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], conditional writes based on switches
- trace statements
- WriteLineIf method
- tracing [.NET Framework], adding trace statements
- Assert method, tracing code
- trace switches, conditional writes based on switches
- WriteIf method
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
ms.openlocfilehash: 0c75a8775649aabe73b02187c4604d2eb3a8435b
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415883"
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="9cf5d-104">如何：向应用程序代码添加跟踪语句</span><span class="sxs-lookup"><span data-stu-id="9cf5d-104">How to: Add Trace Statements to Application Code</span></span>
<span data-ttu-id="9cf5d-105">最常用于跟踪的方法是用于将输出写入侦听器的以下方法：Write、WriteIf、WriteLine、WriteLineIf、Assert 和 Fail\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9cf5d-105">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="9cf5d-106">这些方法可以分为两类：Write、WriteLine 和 Fail 都无条件地发出输出，而 WriteIf、WriteLineIf 和 Assert 则测试 Boolean 条件并根据条件的值来写入或不写入\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9cf5d-106">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="9cf5d-107">WriteIf 和 WriteLineIf 在条件为 `true` 时发出输出，而 Assert 在条件为 `false` 时发出输出\*\*\*\*\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9cf5d-107">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="9cf5d-108">当设计跟踪和调试策略时，应考虑所需的输出形式。</span><span class="sxs-lookup"><span data-stu-id="9cf5d-108">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="9cf5d-109">填充不相关信息的多个 Write 语句将创建难以读取的日志\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9cf5d-109">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="9cf5d-110">另一方面，如果使用 WriteLine 将相关语句放置在单独的行上，可能会难以区分哪些信息应该在一起\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9cf5d-110">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="9cf5d-111">通常，当需要将来自多个源的信息组合起来创建单个信息性消息时，使用多个 Write；当需要创建单个完整消息时，则使用 WriteLine 语句\*\*\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9cf5d-111">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="9cf5d-112">写入完整的行</span><span class="sxs-lookup"><span data-stu-id="9cf5d-112">To write a complete line</span></span>  
  
1. <span data-ttu-id="9cf5d-113">调用 <xref:System.Diagnostics.Trace.WriteLine%2A> 或 <xref:System.Diagnostics.Trace.WriteLineIf%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9cf5d-113">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="9cf5d-114">一个回车符会被追加到此方法返回的消息末尾，使 Write、WriteIf、WriteLine 或 WriteLineIf 返回的下一条消息将从以下行开始：\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="9cf5d-114">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteLine("Error in AppendData procedure.")  
    Trace.WriteLineIf(errorFlag, "Error in AppendData procedure.")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteLine ("Error in AppendData procedure.");  
    System.Diagnostics.Trace.WriteLineIf(errorFlag,
       "Error in AppendData procedure.");  
    ```  
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="9cf5d-115">写入部分行</span><span class="sxs-lookup"><span data-stu-id="9cf5d-115">To write a partial line</span></span>  
  
1. <span data-ttu-id="9cf5d-116">调用 <xref:System.Diagnostics.Trace.Write%2A> 或 <xref:System.Diagnostics.Trace.WriteIf%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9cf5d-116">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="9cf5d-117">由 Write、WriteIf、WriteLine 或 WriteLineIf 生成的下一条消息将从由 Write 或 WriteIf 语句生成的消息所在的同一行上开始：\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="9cf5d-117">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteIf(errorFlag, "Error in AppendData procedure.")  
    Debug.WriteIf(errorFlag, "Transaction abandoned.")  
    Trace.Write("Invalid value for data request")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteIf(errorFlag,
       "Error in AppendData procedure.");  
    System.Diagnostics.Debug.WriteIf(errorFlag, "Transaction abandoned.");  
    Trace.Write("Invalid value for data request");  
    ```  
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="9cf5d-118">验证特定条件在执行方法之前或之后存在</span><span class="sxs-lookup"><span data-stu-id="9cf5d-118">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1. <span data-ttu-id="9cf5d-119">调用 <xref:System.Diagnostics.Trace.Assert%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9cf5d-119">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="9cf5d-120">可以将 Assert 用于跟踪和调试\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9cf5d-120">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="9cf5d-121">此示例将调用堆栈输出到 Listeners 集合中的任意侦听器\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="9cf5d-121">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="9cf5d-122">有关详细信息，请参阅[托管代码中的断言<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>和 ](/visualstudio/debugger/assertions-in-managed-code)。</span><span class="sxs-lookup"><span data-stu-id="9cf5d-122">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf5d-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="9cf5d-123">See also</span></span>

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9cf5d-124">跟踪应用程序和在应用程序中插入检测点</span><span class="sxs-lookup"><span data-stu-id="9cf5d-124">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="9cf5d-125">如何：创建、初始化和配置跟踪开关</span><span class="sxs-lookup"><span data-stu-id="9cf5d-125">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="9cf5d-126">跟踪开关</span><span class="sxs-lookup"><span data-stu-id="9cf5d-126">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="9cf5d-127">跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="9cf5d-127">Trace Listeners</span></span>](trace-listeners.md)
