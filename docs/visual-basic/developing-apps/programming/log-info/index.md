---
title: 记录来自应用程序的信息
ms.date: 07/20/2015
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
ms.openlocfilehash: 43738b2d654435532a98654cbc40af134d43f02c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410018"
---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="72ef4-102">记录来自应用程序的信息 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72ef4-102">Logging Information from the Application (Visual Basic)</span></span>

<span data-ttu-id="72ef4-103">本节包含的主题介绍如何使用 `My.Application.Log` 或 `My.Log` 对象记录来自应用程序的信息，以及如何扩展应用程序的日志记录功能。</span><span class="sxs-lookup"><span data-stu-id="72ef4-103">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="72ef4-104">`Log` 对象提供用于将信息写入应用程序的日志侦听器的方法，而 `Log` 对象的高级 `TraceSource` 属性提供详细的配置信息。</span><span class="sxs-lookup"><span data-stu-id="72ef4-104">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="72ef4-105">`Log` 对象由应用程序的配置文件配置。</span><span class="sxs-lookup"><span data-stu-id="72ef4-105">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="72ef4-106">`My.Log` 对象仅适用于 ASP.NET 应用程序。</span><span class="sxs-lookup"><span data-stu-id="72ef4-106">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="72ef4-107">对于客户端应用程序，请使用 `My.Application.Log`。</span><span class="sxs-lookup"><span data-stu-id="72ef4-107">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="72ef4-108">有关详细信息，请参阅 <xref:Microsoft.VisualBasic.Logging.Log>。</span><span class="sxs-lookup"><span data-stu-id="72ef4-108">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="72ef4-109">任务</span><span class="sxs-lookup"><span data-stu-id="72ef4-109">Tasks</span></span>  
  
|<span data-ttu-id="72ef4-110">功能</span><span class="sxs-lookup"><span data-stu-id="72ef4-110">To</span></span>|<span data-ttu-id="72ef4-111">查看</span><span class="sxs-lookup"><span data-stu-id="72ef4-111">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="72ef4-112">将事件信息写入应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="72ef4-112">Write event information to the application's logs.</span></span>|[<span data-ttu-id="72ef4-113">如何：写入日志消息</span><span class="sxs-lookup"><span data-stu-id="72ef4-113">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)|  
|<span data-ttu-id="72ef4-114">将异常信息写入应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="72ef4-114">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="72ef4-115">如何：日志异常</span><span class="sxs-lookup"><span data-stu-id="72ef4-115">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)|  
|<span data-ttu-id="72ef4-116">在应用程序启动和关闭时，将跟踪信息写入应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="72ef4-116">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="72ef4-117">如何：在应用程序启动或关闭时记录消息</span><span class="sxs-lookup"><span data-stu-id="72ef4-117">How to: Log Messages When the Application Starts or Shuts Down</span></span>](how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="72ef4-118">配置 `My.Application.Log`，将信息写入文本文件。</span><span class="sxs-lookup"><span data-stu-id="72ef4-118">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="72ef4-119">如何：将事件信息写入文本文件</span><span class="sxs-lookup"><span data-stu-id="72ef4-119">How to: Write Event Information to a Text File</span></span>](how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="72ef4-120">配置 `My.Application.Log`，将信息写入事件日志。</span><span class="sxs-lookup"><span data-stu-id="72ef4-120">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="72ef4-121">如何：将信息写入应用程序事件日志</span><span class="sxs-lookup"><span data-stu-id="72ef4-121">How to: Write to an Application Event Log</span></span>](how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="72ef4-122">更改 `My.Application.Log` 写入信息的位置。</span><span class="sxs-lookup"><span data-stu-id="72ef4-122">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="72ef4-123">演练：更改 My.Application.Log 在哪里写入信息</span><span class="sxs-lookup"><span data-stu-id="72ef4-123">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="72ef4-124">确定 `My.Application.Log` 写入信息的位置。</span><span class="sxs-lookup"><span data-stu-id="72ef4-124">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="72ef4-125">演练：确定 My.Application.Log 在哪里写入信息</span><span class="sxs-lookup"><span data-stu-id="72ef4-125">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="72ef4-126">为 `My.Application.Log` 创建自定义日志侦听器。</span><span class="sxs-lookup"><span data-stu-id="72ef4-126">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="72ef4-127">演练：创建自定义日志侦听器</span><span class="sxs-lookup"><span data-stu-id="72ef4-127">Walkthrough: Creating Custom Log Listeners</span></span>](walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="72ef4-128">筛选 `My.Application.Log` 日志的输出。</span><span class="sxs-lookup"><span data-stu-id="72ef4-128">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="72ef4-129">演练：筛选 My.Application.Log 输出</span><span class="sxs-lookup"><span data-stu-id="72ef4-129">Walkthrough: Filtering My.Application.Log Output</span></span>](walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="72ef4-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="72ef4-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="72ef4-131">使用应用程序日志</span><span class="sxs-lookup"><span data-stu-id="72ef4-131">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="72ef4-132">排除故障：日志侦听器</span><span class="sxs-lookup"><span data-stu-id="72ef4-132">Troubleshooting: Log Listeners</span></span>](troubleshooting-log-listeners.md)
