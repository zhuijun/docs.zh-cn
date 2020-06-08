---
title: 如何：写入应用程序事件日志
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 298d6d85f8b21176b72db8e676617577eb03fada
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410031"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="198ce-102">如何：写入应用程序事件日志 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="198ce-102">How to: Write to an Application Event Log (Visual Basic)</span></span>

<span data-ttu-id="198ce-103">可以使用 `My.Application.Log` 和 `My.Log` 对象来写入有关应用程序中所发生事件的信息。</span><span class="sxs-lookup"><span data-stu-id="198ce-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="198ce-104">本示例将演示如何配置事件日志侦听器，以便 `My.Application.Log` 将跟踪信息写入应用程序事件日志。</span><span class="sxs-lookup"><span data-stu-id="198ce-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>

<span data-ttu-id="198ce-105">不能将信息写入安全日志。</span><span class="sxs-lookup"><span data-stu-id="198ce-105">You cannot write to the Security log.</span></span> <span data-ttu-id="198ce-106">只有 LocalSystem 或 Administrator 帐户的成员可以将信息写入系统日志。</span><span class="sxs-lookup"><span data-stu-id="198ce-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>

<span data-ttu-id="198ce-107">若要查看事件日志，可以使用“服务器资源管理器”  或“Windows 事件查看器”。  </span><span class="sxs-lookup"><span data-stu-id="198ce-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="198ce-108">有关详细信息，请参阅 [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md)。</span><span class="sxs-lookup"><span data-stu-id="198ce-108">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

## <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="198ce-109">添加和配置事件日志侦听器</span><span class="sxs-lookup"><span data-stu-id="198ce-109">To add and configure the event log listener</span></span>

1. <span data-ttu-id="198ce-110">在“解决方案资源管理器”  中右键单击 app.config，然后选择“打开”  。</span><span class="sxs-lookup"><span data-stu-id="198ce-110">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

    <span data-ttu-id="198ce-111">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="198ce-111">\- or -</span></span>

    <span data-ttu-id="198ce-112">如果其中没有 app.config 文件，</span><span class="sxs-lookup"><span data-stu-id="198ce-112">If there is no app.config file,</span></span>

    1. <span data-ttu-id="198ce-113">在 **“项目”** 菜单上选择 **“添加新项”** 。</span><span class="sxs-lookup"><span data-stu-id="198ce-113">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="198ce-114">在“添加新项”  对话框中，选择“应用程序配置文件”  。</span><span class="sxs-lookup"><span data-stu-id="198ce-114">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="198ce-115">单击 **添加**。</span><span class="sxs-lookup"><span data-stu-id="198ce-115">Click **Add**.</span></span>

2. <span data-ttu-id="198ce-116">在应用程序配置文件中找到 `<listeners>` 部分。</span><span class="sxs-lookup"><span data-stu-id="198ce-116">Locate the `<listeners>` section in the application configuration file.</span></span>

    <span data-ttu-id="198ce-117">`<listeners>` 部分位于 name 属性为“DefaultSource”的 `<source>` 部分当中，后者又嵌套在 `<system.diagnostics>` 部分当中，位于顶级 `<configuration>` 部分之下。</span><span class="sxs-lookup"><span data-stu-id="198ce-117">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="198ce-118">将此元素添加到该 `<listeners>` 部分：</span><span class="sxs-lookup"><span data-stu-id="198ce-118">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="EventLog"/>
    ```

4. <span data-ttu-id="198ce-119">找到 `<sharedListeners>` 部分，该部分位于 `<system.diagnostics>` 部分当中，后者又位于顶级 `<configuration>` 部分之下。</span><span class="sxs-lookup"><span data-stu-id="198ce-119">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="198ce-120">将此元素添加到该 `<sharedListeners>` 部分：</span><span class="sxs-lookup"><span data-stu-id="198ce-120">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    <span data-ttu-id="198ce-121">将 `APPLICATION_NAME` 替换为应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="198ce-121">Replace `APPLICATION_NAME` with the name of your application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="198ce-122">通常情况下，应用程序只将错误信息写入事件日志。</span><span class="sxs-lookup"><span data-stu-id="198ce-122">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="198ce-123">有关筛选日志输出的信息，请参阅 [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md)。</span><span class="sxs-lookup"><span data-stu-id="198ce-123">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md).</span></span>

## <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="198ce-124">将事件信息写入事件日志</span><span class="sxs-lookup"><span data-stu-id="198ce-124">To write event information to the event log</span></span>

<span data-ttu-id="198ce-125">使用 `My.Application.Log.WriteEntry` 或 `My.Application.Log.WriteException` 方法可以将信息写入事件日志。</span><span class="sxs-lookup"><span data-stu-id="198ce-125">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="198ce-126">有关详细信息，请参阅[如何：编写日志消息](how-to-write-log-messages.md)和[如何：记录异常](how-to-log-exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="198ce-126">For more information, see [How to: Write Log Messages](how-to-write-log-messages.md) and [How to: Log Exceptions](how-to-log-exceptions.md).</span></span>

<span data-ttu-id="198ce-127">为程序集配置事件日志侦听器后，它将接收该程序集写入 `My.Application.Log` 的所有消息。</span><span class="sxs-lookup"><span data-stu-id="198ce-127">After you configure the event log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="198ce-128">另请参阅</span><span class="sxs-lookup"><span data-stu-id="198ce-128">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="198ce-129">使用应用程序日志</span><span class="sxs-lookup"><span data-stu-id="198ce-129">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="198ce-130">如何：日志异常</span><span class="sxs-lookup"><span data-stu-id="198ce-130">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="198ce-131">演练：确定 My.Application.Log 写入信息的位置</span><span class="sxs-lookup"><span data-stu-id="198ce-131">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
