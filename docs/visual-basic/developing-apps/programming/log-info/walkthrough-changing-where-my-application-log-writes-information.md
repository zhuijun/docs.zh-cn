---
title: 更改 My.Application.Log 写入信息的位置
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: f9e45cdf4507840f62e32678f4c0a7be2c0be054
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398287"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="6f6e0-102">演练：更改 My.Application.Log 写入信息的位置 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f6e0-102">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="6f6e0-103">可以使用 `My.Application.Log` 和 `My.Log` 对象来记录有关应用程序中所发生事件的信息。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="6f6e0-104">本演练将演示如何重写默认设置，以及如何使 `Log` 对象将信息写入其他日志侦听器。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-104">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6f6e0-105">系统必备</span><span class="sxs-lookup"><span data-stu-id="6f6e0-105">Prerequisites</span></span>

<span data-ttu-id="6f6e0-106">`Log` 对象可以将信息写入多个日志侦听器。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-106">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="6f6e0-107">在更改配置之前，需要确定日志侦听器的当前配置。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-107">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="6f6e0-108">有关详细信息，请参阅[演练：确定 My.Application.Log 写入信息的位置](walkthrough-determining-where-my-application-log-writes-information.md)。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-108">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](walkthrough-determining-where-my-application-log-writes-information.md).</span></span>

<span data-ttu-id="6f6e0-109">建议查看[如何：将事件信息写入文本文件](how-to-write-event-information-to-a-text-file.md)或[如何：写入应用程序事件日志](how-to-write-to-an-application-event-log.md)。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-109">You may want to review [How to: Write Event Information to a Text File](how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](how-to-write-to-an-application-event-log.md).</span></span>

### <a name="to-add-listeners"></a><span data-ttu-id="6f6e0-110">添加侦听器</span><span class="sxs-lookup"><span data-stu-id="6f6e0-110">To add listeners</span></span>

1. <span data-ttu-id="6f6e0-111">在“解决方案资源管理器”  中右键单击 app.config，然后选择“打开”  。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="6f6e0-112">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="6f6e0-112">\- or -</span></span>

     <span data-ttu-id="6f6e0-113">如果其中没有 app.config 文件：</span><span class="sxs-lookup"><span data-stu-id="6f6e0-113">If there is no app.config file:</span></span>

    1. <span data-ttu-id="6f6e0-114">在 **“项目”** 菜单上选择 **“添加新项”** 。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-114">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="6f6e0-115">在“添加新项”  对话框中，选择“应用程序配置文件”  。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-115">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>

    3. <span data-ttu-id="6f6e0-116">单击 **添加**。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-116">Click **Add**.</span></span>

2. <span data-ttu-id="6f6e0-117">找到 `<listeners>` 部分，该部分位于 `<source>` 属性为“DefaultSource”的 `name` 部分当中，后者又位于 `<sources>` 部分之下。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-117">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="6f6e0-118">`<sources>` 部分位于 `<system.diagnostics>` 部分当中，后者又位于顶级 `<configuration>` 部分之下。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-118">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="6f6e0-119">将这些元素添加到该 `<listeners>` 部分。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-119">Add these elements to that `<listeners>` section.</span></span>

    ```xml
    <!-- Uncomment to connect the application file log. -->
    <!-- <add name="FileLog" /> -->
    <!-- Uncomment to connect the event log. -->
    <!-- <add name="EventLog" /> -->
    <!-- Uncomment to connect the event log. -->
    <!-- <add name="Delimited" /> -->
    <!-- Uncomment to connect the XML log. -->
    <!-- <add name="XmlWriter" /> -->
    <!-- Uncomment to connect the console log. -->
    <!-- <add name="Console" /> -->
    ```

4. <span data-ttu-id="6f6e0-120">取消注释希望接收 `Log` 消息的日志侦听器。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-120">Uncomment the log listeners that you want to receive `Log` messages.</span></span>

5. <span data-ttu-id="6f6e0-121">找到 `<sharedListeners>` 部分，该部分位于 `<system.diagnostics>` 部分当中，后者又位于顶级 `<configuration>` 部分之下。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-121">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

6. <span data-ttu-id="6f6e0-122">将这些元素添加到该 `<sharedListeners>` 部分。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-122">Add these elements to that `<sharedListeners>` section.</span></span>

    ```xml
    <add name="FileLog"
         type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
               Microsoft.VisualBasic, Version=8.0.0.0,
               Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
         initializeData="FileLogWriter" />
    <add name="EventLog"
         type="System.Diagnostics.EventLogTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="sample application"/>
    <add name="Delimited"
         type="System.Diagnostics.DelimitedListTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="c:\temp\sampleDelimitedFile.txt"
         traceOutputOptions="DateTime" />
    <add name="XmlWriter"
         type="System.Diagnostics.XmlWriterTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="c:\temp\sampleLogFile.xml" />
    <add name="Console"
         type="System.Diagnostics.ConsoleTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="true" />
    ```

7. <span data-ttu-id="6f6e0-123">app.config 文件的内容应类似于下面的 XML：</span><span class="sxs-lookup"><span data-stu-id="6f6e0-123">The content of the app.config file should be similar to the following XML:</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
              <!-- Uncomment to connect the application file log. -->
              <!-- <add name="FileLog" /> -->
              <!-- Uncomment to connect the event log. -->
              <!-- <add name="EventLog" /> -->
              <!-- Uncomment to connect the event log. -->
              <!-- <add name="Delimited" /> -->
              <!-- Uncomment to connect the XML log. -->
              <!-- <add name="XmlWriter" /> -->
              <!-- Uncomment to connect the console log. -->
              <!-- <add name="Console" /> -->
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="Information" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
               initializeData="FileLogWriter" />
          <add name="EventLog"
               type="System.Diagnostics.EventLogTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="sample application"/>
          <add name="Delimited"
               type="System.Diagnostics.DelimitedListTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="c:\temp\sampleDelimitedFile.txt"
               traceOutputOptions="DateTime" />
          <add name="XmlWriter"
               type="System.Diagnostics.XmlWriterTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="c:\temp\sampleLogFile.xml" />
          <add name="Console"
               type="System.Diagnostics.ConsoleTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="true" />
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="6f6e0-124">重新配置侦听器</span><span class="sxs-lookup"><span data-stu-id="6f6e0-124">To reconfigure a listener</span></span>

1. <span data-ttu-id="6f6e0-125">在 `<add>` 部分找到侦听器的 `<sharedListeners>` 元素。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-125">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>

2. <span data-ttu-id="6f6e0-126">`type` 特性提供了侦听器类型的名称。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-126">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="6f6e0-127">此类型必须继承自 <xref:System.Diagnostics.TraceListener> 类。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-127">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="6f6e0-128">请使用强名称类型名称以确保使用正确的类型。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-128">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="6f6e0-129">有关详细信息，请参阅下面的“引用强名称类型”部分。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-129">For more information, see the "To reference a strongly named type" section below.</span></span>

     <span data-ttu-id="6f6e0-130">可以使用的类型有：</span><span class="sxs-lookup"><span data-stu-id="6f6e0-130">Some types that you can use are:</span></span>

    - <span data-ttu-id="6f6e0-131"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> 侦听器，它将信息写入文件日志。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>

    - <span data-ttu-id="6f6e0-132"><xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> 侦听器，它将信息写入 `initializeData` 参数指定的计算机事件日志。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>

    - <span data-ttu-id="6f6e0-133"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> 和 <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> 侦听器，它们将信息写入 `initializeData` 参数指定的文件。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-133">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="6f6e0-134"><xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> 侦听器，它将信息写入命令行控制台。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>

     <span data-ttu-id="6f6e0-135">有关其他类型的日志侦听器写入信息的位置的信息，请参阅该类型的文档。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-135">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

3. <span data-ttu-id="6f6e0-136">当应用程序创建日志侦听器对象时，它将传递 `initializeData` 特性作为构造函数参数。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-136">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="6f6e0-137">`initializeData` 特性的含义取决于跟踪侦听器。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-137">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>

4. <span data-ttu-id="6f6e0-138">创建日志侦听器后，应用程序将设置该侦听器的属性。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-138">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="6f6e0-139">这些属性由 `<add>` 元素中的其他特性定义。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-139">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="6f6e0-140">有关特定侦听器的属性的详细信息，请参阅该侦听器类型的文档。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-140">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>

### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="6f6e0-141">引用强名称类型</span><span class="sxs-lookup"><span data-stu-id="6f6e0-141">To reference a strongly named type</span></span>

1. <span data-ttu-id="6f6e0-142">为确保日志侦听器使用正确的类型，请确保使用完全限定的类型名称和强名称程序集名称。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-142">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="6f6e0-143">强名称类型的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="6f6e0-143">The syntax of a strongly named type is as follows:</span></span>

     <span data-ttu-id="6f6e0-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span><span class="sxs-lookup"><span data-stu-id="6f6e0-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>

2. <span data-ttu-id="6f6e0-145">本代码示例将演示如何在这种情况下确定完全限定类型“System.Diagnostics.FileLogTraceListener”的强命名类型。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-145">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]

     <span data-ttu-id="6f6e0-146">它是输出类型，并且可用于唯一引用强名称类型，如上面的“添加侦听器”过程所示。</span><span class="sxs-lookup"><span data-stu-id="6f6e0-146">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>

     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

## <a name="see-also"></a><span data-ttu-id="6f6e0-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f6e0-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [<span data-ttu-id="6f6e0-148">如何：将事件信息写入文本文件</span><span class="sxs-lookup"><span data-stu-id="6f6e0-148">How to: Write Event Information to a Text File</span></span>](how-to-write-event-information-to-a-text-file.md)
- [<span data-ttu-id="6f6e0-149">如何：写入应用程序事件日志</span><span class="sxs-lookup"><span data-stu-id="6f6e0-149">How to: Write to an Application Event Log</span></span>](how-to-write-to-an-application-event-log.md)
