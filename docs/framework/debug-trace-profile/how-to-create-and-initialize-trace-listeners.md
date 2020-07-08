---
title: 如何：创建和初始化跟踪侦听器
description: 了解如何在 .NET 中使用类（如 DefaultTraceListener）创建和初始化跟踪侦听器。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- initializing trace listeners
- trace listeners, creating
- trace listeners, initializing
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 21726de1-61ee-4fdc-9dd0-3be49324d066
ms.openlocfilehash: 752306124e41a7fb7458daccc8c2891631eb9616
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051202"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a><span data-ttu-id="e22df-103">如何：创建和初始化跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="e22df-103">How to: Create and Initialize Trace Listeners</span></span>

<span data-ttu-id="e22df-104"><xref:System.Diagnostics.Debug?displayProperty=nameWithType> 和 <xref:System.Diagnostics.Trace?displayProperty=nameWithType> 类向接收和处理消息的对象（成为侦听器）中发送消息。</span><span class="sxs-lookup"><span data-stu-id="e22df-104">The <xref:System.Diagnostics.Debug?displayProperty=nameWithType> and <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes send messages to objects called listeners that receive and process these messages.</span></span> <span data-ttu-id="e22df-105">在启用跟踪或调试后将自动创建并初始化一个如上所述的侦听器 <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e22df-105">One such listener, the <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, is automatically created and initialized when tracing or debugging is enabled.</span></span> <span data-ttu-id="e22df-106">如果要将 <xref:System.Diagnostics.Trace> 或 <xref:System.Diagnostics.Debug> 输出定向到任何其他源，则必须创建并初始化其他跟踪侦听器。</span><span class="sxs-lookup"><span data-stu-id="e22df-106">If you want <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.Debug> output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span>

<span data-ttu-id="e22df-107">所创建的侦听器应反映应用程序的需要。</span><span class="sxs-lookup"><span data-stu-id="e22df-107">The listeners you create should reflect your application's needs.</span></span> <span data-ttu-id="e22df-108">例如，如果想要获取所有跟踪输出的文本记录，则创建 <xref:System.Diagnostics.TextWriterTraceListener> 侦听器；启用后，它会将所有输出都写入新的文本文件中。</span><span class="sxs-lookup"><span data-stu-id="e22df-108">For example, if you want a text record of all trace output, create a <xref:System.Diagnostics.TextWriterTraceListener> listener, which writes all output to a new text file when it is enabled.</span></span> <span data-ttu-id="e22df-109">另一方面，如果想要仅在应用程序执行过程中查看输出，则创建 <xref:System.Diagnostics.ConsoleTraceListener> 侦听器，以便将所有输出定向到控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="e22df-109">On the other hand, if you want to view output only during application execution, create a <xref:System.Diagnostics.ConsoleTraceListener> listener, which directs all output to a console window.</span></span> <span data-ttu-id="e22df-110"><xref:System.Diagnostics.EventLogTraceListener> 可以将跟踪输出定向到事件日志。</span><span class="sxs-lookup"><span data-stu-id="e22df-110">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log.</span></span> <span data-ttu-id="e22df-111">有关详细信息，请参阅[跟踪侦听器](trace-listeners.md)。</span><span class="sxs-lookup"><span data-stu-id="e22df-111">For more information, see [Trace Listeners](trace-listeners.md).</span></span>

<span data-ttu-id="e22df-112">可以在[应用程序配置文件](../configure-apps/index.md)或代码中创建跟踪侦听器。</span><span class="sxs-lookup"><span data-stu-id="e22df-112">You can create trace listeners in an [application configuration file](../configure-apps/index.md) or in your code.</span></span> <span data-ttu-id="e22df-113">我们建议使用应用程序配置文件，因为它们可在不更改代码的情况下添加、修改或删除跟踪侦听器。</span><span class="sxs-lookup"><span data-stu-id="e22df-113">We recommend the use of application configuration files, because they let you add, modify, or remove trace listeners without having to change your code.</span></span>

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a><span data-ttu-id="e22df-114">若要使用配置文件创建和初始化跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="e22df-114">To create and use a trace listener by using a configuration file</span></span>

1. <span data-ttu-id="e22df-115">请声明应用程序配置文件中的跟踪侦听器。</span><span class="sxs-lookup"><span data-stu-id="e22df-115">Declare your trace listener in your application configuration file.</span></span> <span data-ttu-id="e22df-116">如果创建的侦听器需要的任何其他对象，请同时对它们进行声明。</span><span class="sxs-lookup"><span data-stu-id="e22df-116">If the listener you are creating requires any other objects, declare them as well.</span></span> <span data-ttu-id="e22df-117">下面的示例演示如何创建名为 `myListener` 的侦听器，它将写入到文本文件 `TextWriterOutput.log` 中。</span><span class="sxs-lookup"><span data-stu-id="e22df-117">The following example shows how to create a listener called `myListener` that writes to the text file `TextWriterOutput.log`.</span></span>

    ```xml
    <configuration>
      <system.diagnostics>
        <trace autoflush="false" indentsize="4">
          <listeners>
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="TextWriterOutput.log" />
            <remove name="Default" />
          </listeners>
        </trace>
      </system.diagnostics>
    </configuration>
    ```

2. <span data-ttu-id="e22df-118">在代码中使用 <xref:System.Diagnostics.Trace> 类以将消息写入到跟踪侦听器中。</span><span class="sxs-lookup"><span data-stu-id="e22df-118">Use the <xref:System.Diagnostics.Trace> class in your code to write a message to the trace listeners.</span></span>

    ```vb
    Trace.TraceInformation("Test message.")
    ' You must close or flush the trace to empty the output buffer.
    Trace.Flush()
    ```

    ```csharp
    Trace.TraceInformation("Test message.");
    // You must close or flush the trace to empty the output buffer.
    Trace.Flush();
    ```

### <a name="to-create-and-use-a-trace-listener-in-code"></a><span data-ttu-id="e22df-119">若要在代码中创建和使用跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="e22df-119">To create and use a trace listener in code</span></span>

- <span data-ttu-id="e22df-120">请将跟踪侦听器添加到 <xref:System.Diagnostics.Trace.Listeners%2A> 集合并将跟踪信息发送到侦听器。</span><span class="sxs-lookup"><span data-stu-id="e22df-120">Add the trace listener to the <xref:System.Diagnostics.Trace.Listeners%2A> collection and send trace information to the listeners.</span></span>

    ```vb
    Trace.Listeners.Add(New TextWriterTraceListener("TextWriterOutput.log", "myListener"))
    Trace.TraceInformation("Test message.")
    ' You must close or flush the trace to empty the output buffer.
    Trace.Flush()
    ```

    ```csharp
    Trace.Listeners.Add(new TextWriterTraceListener("TextWriterOutput.log", "myListener"));
    Trace.TraceInformation("Test message.");
    // You must close or flush the trace to empty the output buffer.
    Trace.Flush();
    ```

    <span data-ttu-id="e22df-121">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="e22df-121">\- or -</span></span>

- <span data-ttu-id="e22df-122">如果不希望侦听器接收跟踪输出，则不要将其添加到 <xref:System.Diagnostics.Trace.Listeners%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="e22df-122">If you do not want your listener to receive trace output, do not add it to the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span> <span data-ttu-id="e22df-123">可以通过调用侦听器自己的输出方法由独立于 <xref:System.Diagnostics.Trace.Listeners%2A> 集合的侦听器发出输出。</span><span class="sxs-lookup"><span data-stu-id="e22df-123">You can emit output through a listener independent of the <xref:System.Diagnostics.Trace.Listeners%2A> collection by calling the listener's own output methods.</span></span> <span data-ttu-id="e22df-124">下面的示例演示如何向不在 <xref:System.Diagnostics.Trace.Listeners%2A> 集合中的侦听器写入代码行。</span><span class="sxs-lookup"><span data-stu-id="e22df-124">The following example shows how to write a line to a listener that is not in the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span>

    ```vb
    Dim myListener As New TextWriterTraceListener("TextWriterOutput.log", "myListener")
    myListener.WriteLine("Test message.")
    ' You must close or flush the trace listener to empty the output buffer.
    myListener.Flush()
    ```

    ```csharp
    TextWriterTraceListener myListener = new TextWriterTraceListener("TextWriterOutput.log", "myListener");
    myListener.WriteLine("Test message.");
    // You must close or flush the trace listener to empty the output buffer.
    myListener.Flush();
    ```

## <a name="see-also"></a><span data-ttu-id="e22df-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="e22df-125">See also</span></span>

- [<span data-ttu-id="e22df-126">跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="e22df-126">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="e22df-127">跟踪开关</span><span class="sxs-lookup"><span data-stu-id="e22df-127">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="e22df-128">如何：向应用程序代码添加跟踪语句</span><span class="sxs-lookup"><span data-stu-id="e22df-128">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="e22df-129">跟踪应用程序和在应用程序中插入检测点</span><span class="sxs-lookup"><span data-stu-id="e22df-129">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
