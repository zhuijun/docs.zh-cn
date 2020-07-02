---
title: 跟踪侦听器
description: 探索跟踪侦听器，这些侦听器是用于收集和记录在 .NET 中发送的跟踪消息的机制。 侦听器将收集、存储和路由消息。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Listener object types
- listeners
- Trace class, listeners
- trace listeners, about trace listeners
- Listeners collection
- trace listeners
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 444b0d33-67ea-4c36-9e94-79c50f839025
ms.openlocfilehash: d08f86c782284a296090cf63e4b03c8d446a95fc
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803518"
---
# <a name="trace-listeners"></a><span data-ttu-id="a23a3-104">跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="a23a3-104">Trace Listeners</span></span>
<span data-ttu-id="a23a3-105">使用 Trace、Debug 和 <xref:System.Diagnostics.TraceSource> 时，必须具有用于收集和记录发送的消息的机制。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a23a3-105">When using **Trace**, **Debug** and <xref:System.Diagnostics.TraceSource>, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="a23a3-106">跟踪消息由*侦听器*接收。</span><span class="sxs-lookup"><span data-stu-id="a23a3-106">Trace messages are received by *listeners*.</span></span> <span data-ttu-id="a23a3-107">侦听器的用途是收集、存储和路由跟踪消息。</span><span class="sxs-lookup"><span data-stu-id="a23a3-107">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="a23a3-108">侦听器会将跟踪输出定向到适当的目标，如日志、窗口或文本文件。</span><span class="sxs-lookup"><span data-stu-id="a23a3-108">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="a23a3-109">侦听器可用于 Debug、Trace 和 <xref:System.Diagnostics.TraceSource> 类，其中每个类都可以将输出发送到多种侦听器对象。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a23a3-109">Listeners are available to the **Debug**, **Trace**, and <xref:System.Diagnostics.TraceSource> classes, each of which can send its output to a variety of listener objects.</span></span> <span data-ttu-id="a23a3-110">以下是常用的预定义侦听器：</span><span class="sxs-lookup"><span data-stu-id="a23a3-110">The following are the commonly used predefined listeners:</span></span>  
  
- <span data-ttu-id="a23a3-111"><xref:System.Diagnostics.TextWriterTraceListener> 将输出重定向到 <xref:System.IO.TextWriter> 类的实例或为 <xref:System.IO.Stream> 类的任何项。</span><span class="sxs-lookup"><span data-stu-id="a23a3-111">A <xref:System.Diagnostics.TextWriterTraceListener> redirects output to an instance of the <xref:System.IO.TextWriter> class or to anything that is a <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="a23a3-112">它也可以写入到控制台或文件，因为它们是 <xref:System.IO.Stream> 类。</span><span class="sxs-lookup"><span data-stu-id="a23a3-112">It can also write to the console or to a file, because these are <xref:System.IO.Stream> classes.</span></span>  
  
- <span data-ttu-id="a23a3-113"><xref:System.Diagnostics.EventLogTraceListener> 将输出重定向到事件日志。</span><span class="sxs-lookup"><span data-stu-id="a23a3-113">An <xref:System.Diagnostics.EventLogTraceListener> redirects output to an event log.</span></span>  
  
- <span data-ttu-id="a23a3-114"><xref:System.Diagnostics.DefaultTraceListener> 向 OutputDebugString 和 Debugger.Log 方法发出 Write 和 WriteLine 消息。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a23a3-114">A <xref:System.Diagnostics.DefaultTraceListener> emits **Write** and **WriteLine** messages to the **OutputDebugString** and to the **Debugger.Log** method.</span></span> <span data-ttu-id="a23a3-115">在 Visual Studio 中，这会导致“输出”窗口中显示调试消息。</span><span class="sxs-lookup"><span data-stu-id="a23a3-115">In Visual Studio, this causes the debugging messages to appear in the Output window.</span></span> <span data-ttu-id="a23a3-116">Fail 和失败的 Assert 消息也发到 OutputDebugString Windows API 和 Debugger.Log 方法，同样将显示消息框。\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a23a3-116">**Fail** and failed **Assert** messages also emit to the **OutputDebugString** Windows API and the **Debugger.Log** method, and also cause a message box to be displayed.</span></span> <span data-ttu-id="a23a3-117">此行为是 Debug 和 Trace 消息的默认行为，因为 DefaultTraceListener 自动包含在每个 `Listeners` 集合中，且是自动包含的唯一侦听器。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a23a3-117">This behavior is the default behavior for **Debug** and **Trace** messages, because **DefaultTraceListener** is automatically included in every `Listeners` collection and is the only listener automatically included.</span></span>  
  
- <span data-ttu-id="a23a3-118"><xref:System.Diagnostics.ConsoleTraceListener> 将跟踪或调试输出定向到标准输出或标准错误流。</span><span class="sxs-lookup"><span data-stu-id="a23a3-118">A <xref:System.Diagnostics.ConsoleTraceListener> directs tracing or debugging output to either the standard output or the standard error stream.</span></span>  
  
- <span data-ttu-id="a23a3-119"><xref:System.Diagnostics.DelimitedListTraceListener> 将跟踪或调试输出定向到文本编写器（如流编写器）或流（如文件流）。</span><span class="sxs-lookup"><span data-stu-id="a23a3-119">A <xref:System.Diagnostics.DelimitedListTraceListener> directs tracing or debugging output to a text writer, such as a stream writer, or to a stream, such as a file stream.</span></span> <span data-ttu-id="a23a3-120">跟踪输出采用带分隔符的文本格式，该格式使用属性指定的分隔符 <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> 。</span><span class="sxs-lookup"><span data-stu-id="a23a3-120">The trace output is in a delimited text format that uses the delimiter specified by the <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> property.</span></span>  
  
- <span data-ttu-id="a23a3-121"><xref:System.Diagnostics.XmlWriterTraceListener> 将跟踪或调试输出以 XML 编码数据的形式定向到 <xref:System.IO.TextWriter> 或 <xref:System.IO.Stream>，例如 <xref:System.IO.FileStream>。</span><span class="sxs-lookup"><span data-stu-id="a23a3-121">An <xref:System.Diagnostics.XmlWriterTraceListener> directs tracing or debugging output as XML-encoded data to a <xref:System.IO.TextWriter> or to a <xref:System.IO.Stream>, such as a <xref:System.IO.FileStream>.</span></span>  
  
 <span data-ttu-id="a23a3-122">如果你希望 <xref:System.Diagnostics.DefaultTraceListener> 以外的任何侦听器接收 Debug、Trace 和 <xref:System.Diagnostics.TraceSource> 输出，则必须将其添加到 `Listeners` 集合。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a23a3-122">If you want any listener besides the <xref:System.Diagnostics.DefaultTraceListener> to receive **Debug**, **Trace** and <xref:System.Diagnostics.TraceSource> output, you must add it to the `Listeners` collection.</span></span> <span data-ttu-id="a23a3-123">有关详细信息，请参阅[如何：创建和初始化跟踪侦听器](how-to-create-and-initialize-trace-listeners.md)和[如何：将 TraceSource 和筛选器与跟踪侦听器一起使用](how-to-use-tracesource-and-filters-with-trace-listeners.md)。</span><span class="sxs-lookup"><span data-stu-id="a23a3-123">For more information, see [How to: Create and Initialize Trace Listeners](how-to-create-and-initialize-trace-listeners.md) and [How to: Use TraceSource and Filters with Trace Listeners](how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span> <span data-ttu-id="a23a3-124">侦听器集合中的任何侦听器均从跟踪输出方法获取相同消息。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a23a3-124">Any listener in the **Listeners** collection gets the same messages from the trace output methods.</span></span> <span data-ttu-id="a23a3-125">例如，假设你设置了两个侦听器：TextWriterTraceListener 和 EventLogTraceListener。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a23a3-125">For example, suppose you set up two listeners: a **TextWriterTraceListener** and an **EventLogTraceListener**.</span></span> <span data-ttu-id="a23a3-126">每个侦听器接收相同消息。</span><span class="sxs-lookup"><span data-stu-id="a23a3-126">Each listener receives the same message.</span></span> <span data-ttu-id="a23a3-127">TextWriterTraceListener 将输出定向到流，而 EventLogTraceListener 将输出定向到事件日志。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a23a3-127">The **TextWriterTraceListener** would direct its output to a stream, and the **EventLogTraceListener** would direct its output to an event log.</span></span>  
  
 <span data-ttu-id="a23a3-128">以下示例演示如何将输出发送到 Listeners 集合。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a23a3-128">The following example shows how to send output to the **Listeners** collection.</span></span>  
  
```vb  
' Use this example when debugging.  
Debug.WriteLine("Error in Widget 42")  
' Use this example when tracing.  
Trace.WriteLine("Error in Widget 42")  
```  
  
```csharp  
// Use this example when debugging.  
System.Diagnostics.Debug.WriteLine("Error in Widget 42");  
// Use this example when tracing.  
System.Diagnostics.Trace.WriteLine("Error in Widget 42");  
```  
  
 <span data-ttu-id="a23a3-129">调试和跟踪共享一个 Listeners 集合，因此，如果你在应用程序中将侦听器对象添加到 Debug.Listeners 集合，则它也将被添加到 Trace.Listeners 集合。\*\*\*\*\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a23a3-129">Debug and trace share the same **Listeners** collection, so if you add a listener object to a **Debug.Listeners** collection in your application, it gets added to the **Trace.Listeners** collection as well.</span></span>  
  
 <span data-ttu-id="a23a3-130">以下示例演示如何使用侦听器将跟踪信息发送到控制台：</span><span class="sxs-lookup"><span data-stu-id="a23a3-130">The following example shows how to use a listener to send tracing information to a console:</span></span>  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a><span data-ttu-id="a23a3-131">开发人员定义的侦听器</span><span class="sxs-lookup"><span data-stu-id="a23a3-131">Developer-Defined Listeners</span></span>  
 <span data-ttu-id="a23a3-132">可以通过从 TraceListener 基类继承并用自定义方法重写其方法来定义侦听器。\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a23a3-132">You can define your own listeners by inheriting from the **TraceListener** base class and overriding its methods with your customized methods.</span></span> <span data-ttu-id="a23a3-133">有关创建开发人员定义的侦听器的详细信息，请参阅 .NET Framework 参考中的 <xref:System.Diagnostics.TraceListener>。</span><span class="sxs-lookup"><span data-stu-id="a23a3-133">For more information on creating developer-defined listeners, see <xref:System.Diagnostics.TraceListener> in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a23a3-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="a23a3-134">See also</span></span>

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="a23a3-135">跟踪应用程序和在应用程序中插入检测点</span><span class="sxs-lookup"><span data-stu-id="a23a3-135">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="a23a3-136">跟踪开关</span><span class="sxs-lookup"><span data-stu-id="a23a3-136">Trace Switches</span></span>](trace-switches.md)
