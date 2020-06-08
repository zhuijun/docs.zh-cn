---
title: 使用 IAsyncResult 调用异步方法
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 88ca1b5bfbb8bfbdfef01dea8af07c5d56784c5c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289910"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="c8be4-102">使用 IAsyncResult 调用异步方法</span><span class="sxs-lookup"><span data-stu-id="c8be4-102">Calling Asynchronous Methods Using IAsyncResult</span></span>
<span data-ttu-id="c8be4-103">.NET Framework 和第三方类库中的类型可以提供方法，以便应用能够继续执行，同时在除主应用线程外的线程中执行异步操作。</span><span class="sxs-lookup"><span data-stu-id="c8be4-103">Types in the .NET Framework and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="c8be4-104">下面各部分介绍并提供了代码示例，展示了可以调用使用 <xref:System.IAsyncResult> 设计模式的异步方法的不同方式。</span><span class="sxs-lookup"><span data-stu-id="c8be4-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
- <span data-ttu-id="c8be4-105">[通过结束异步操作阻止应用执行](blocking-application-execution-by-ending-an-async-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="c8be4-105">[Blocking Application Execution by Ending an Async Operation](blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
- <span data-ttu-id="c8be4-106">[使用 AsyncWaitHandle 阻止应用执行](blocking-application-execution-using-an-asyncwaithandle.md)。</span><span class="sxs-lookup"><span data-stu-id="c8be4-106">[Blocking Application Execution Using an AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
- <span data-ttu-id="c8be4-107">[轮询异步操作状态](polling-for-the-status-of-an-asynchronous-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="c8be4-107">[Polling for the Status of an Asynchronous Operation](polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
- <span data-ttu-id="c8be4-108">[使用 AsyncCallback 委托结束异步操作](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="c8be4-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8be4-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c8be4-109">See also</span></span>

- [<span data-ttu-id="c8be4-110">基于事件的异步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="c8be4-110">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="c8be4-111">基于事件的异步模式概述</span><span class="sxs-lookup"><span data-stu-id="c8be4-111">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
