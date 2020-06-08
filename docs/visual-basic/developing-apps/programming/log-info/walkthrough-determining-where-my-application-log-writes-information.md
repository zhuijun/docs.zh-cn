---
title: 确定 My.Application.Log 写入信息的位置
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, output location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: 00b543dbe96ca99446f6797a13b66ee62c422b93
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398274"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="dd8c8-102">演练：确定 My.Application.Log 写入信息的位置 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd8c8-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="dd8c8-103">`My.Application.Log` 对象可以将信息写入多个日志侦听器。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="dd8c8-104">日志侦听器由计算机的配置文件配置，并且可以通过应用程序的配置文件重写。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="dd8c8-105">本主题介绍默认设置以及如何确定应用程序的设置。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-105">This topic describes the default settings and how to determine the settings for your application.</span></span>

<span data-ttu-id="dd8c8-106">有关默认输出位置的详细信息，请参阅[使用应用程序日志](working-with-application-logs.md)。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-106">For more information about the default output locations, see [Working with Application Logs](working-with-application-logs.md).</span></span>

### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="dd8c8-107">确定 My.Application.Log 的侦听器</span><span class="sxs-lookup"><span data-stu-id="dd8c8-107">To determine the listeners for My.Application.Log</span></span>

1. <span data-ttu-id="dd8c8-108">找到程序集的配置文件。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="dd8c8-109">如果正在开发程序集，则可通过“解决方案资源管理器”访问 Visual Studio 中的 app.config  。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-109">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span></span> <span data-ttu-id="dd8c8-110">否则，配置文件名称即为程序集的名称附加“.config”，并且与程序集位于相同的目录中。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="dd8c8-111">不是每个程序集都有配置文件。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-111">Not every assembly has a configuration file.</span></span>

    <span data-ttu-id="dd8c8-112">配置文件是一个 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-112">The configuration file is an XML file.</span></span>

2. <span data-ttu-id="dd8c8-113">找到 `<listeners>` 部分，该部分位于 `<source>` 属性为“DefaultSource”的 `name` 部分当中，后者又位于 `<sources>` 部分之下。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="dd8c8-114">`<sources>` 部分位于 `<system.diagnostics>` 部分当中，后者又位于顶级 `<configuration>` 部分之下。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

    <span data-ttu-id="dd8c8-115">如果这些部分不存在，则计算机的配置文件可能会配置 `My.Application.Log` 日志侦听器。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="dd8c8-116">以下步骤介绍如何确定计算机配置文件定义的内容：</span><span class="sxs-lookup"><span data-stu-id="dd8c8-116">The following steps describe how to determine what the computer configuration file defines:</span></span>

    1. <span data-ttu-id="dd8c8-117">找到计算机的 machine.config 文件。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="dd8c8-118">通常情况下，该文件位于 *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* 目录，其中 `SystemRoot` 是操作系统目录，`frameworkVersion` 是 .NET Framework 的版本。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the .NET Framework.</span></span>

        <span data-ttu-id="dd8c8-119">machine.config 中的设置可以通过应用程序的配置文件重写。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>

        <span data-ttu-id="dd8c8-120">如果如下所列的可选元素不存在，可以创建它们。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-120">If the optional elements listed below do not exist, you can create them.</span></span>

    2. <span data-ttu-id="dd8c8-121">找到 `<listeners>` 部分，该部分位于 `<source>` 属性为“DefaultSource”的 `name` 部分当中，后者又位于 `<sources>` 部分当中，这部分位于 `<system.diagnostics>` 部分当中，位于顶级 `<configuration>` 部分之下。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

        <span data-ttu-id="dd8c8-122">如果这些部分不存在，则 `My.Application.Log` 将只有默认的日志侦听器。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>

3. <span data-ttu-id="dd8c8-123">在 <`listeners>` 部分找到 <`add>` 元素。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>

     <span data-ttu-id="dd8c8-124">这些元素会将命名的日志侦听器添加到 `My.Application.Log` 源。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>

4. <span data-ttu-id="dd8c8-125">在 `<add>` 部分找到具有日志侦听器名称的 `<sharedListeners>` 元素，该部分位于 `<system.diagnostics>` 部分当中，后者又位于顶级 `<configuration>` 部分之下。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="dd8c8-126">对于许多类型的共享侦听器，该侦听器的初始化数据说明了侦听器写入数据的位置：</span><span class="sxs-lookup"><span data-stu-id="dd8c8-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>

    - <span data-ttu-id="dd8c8-127"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> 侦听器将信息写入文件日志，如简介中所述。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>

    - <span data-ttu-id="dd8c8-128"><xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> 侦听器将信息写入 `initializeData` 参数指定的计算机事件日志。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="dd8c8-129">若要查看事件日志，可以使用“服务器资源管理器”  或“Windows 事件查看器”。  </span><span class="sxs-lookup"><span data-stu-id="dd8c8-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="dd8c8-130">有关详细信息，请参阅 [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md)。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-130">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

    - <span data-ttu-id="dd8c8-131"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> 和 <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> 侦听器将信息写入 `initializeData` 参数指定的文件。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="dd8c8-132"><xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> 侦听器将信息写入命令行控制台。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>

    - <span data-ttu-id="dd8c8-133">有关其他类型的日志侦听器写入信息的位置的信息，请参阅该类型的文档。</span><span class="sxs-lookup"><span data-stu-id="dd8c8-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd8c8-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd8c8-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [<span data-ttu-id="dd8c8-135">使用应用程序日志</span><span class="sxs-lookup"><span data-stu-id="dd8c8-135">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="dd8c8-136">如何：日志异常</span><span class="sxs-lookup"><span data-stu-id="dd8c8-136">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="dd8c8-137">如何：编写日志消息</span><span class="sxs-lookup"><span data-stu-id="dd8c8-137">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="dd8c8-138">演练：更改 My.Application.Log 写入信息的位置</span><span class="sxs-lookup"><span data-stu-id="dd8c8-138">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="dd8c8-139">.NET Framework 中的 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="dd8c8-139">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)
- [<span data-ttu-id="dd8c8-140">疑难解答：日志侦听器</span><span class="sxs-lookup"><span data-stu-id="dd8c8-140">Troubleshooting: Log Listeners</span></span>](troubleshooting-log-listeners.md)
