---
title: 另一个事件日志已使用该名称注册了一个源
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: 333c28036e2d1b7514c7370b98ff70a6d195a9dd
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058386"
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="b7a94-102">另一个事件日志已使用该名称注册了一个源</span><span class="sxs-lookup"><span data-stu-id="b7a94-102">Another event log has already registered a source with this name</span></span>

<span data-ttu-id="b7a94-103">已尝试向事件日志写入条目，其中指定的源使用其他事件日志进行注册。</span><span class="sxs-lookup"><span data-stu-id="b7a94-103">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="b7a94-104">在组件将条目写入日志前，必须设置 <xref:System.Diagnostics.EventLog.Source%2A> 组件实例的 <xref:System.Diagnostics.EventLog> 属性。</span><span class="sxs-lookup"><span data-stu-id="b7a94-104">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="b7a94-105">发生此情况时，系统将检查所指定的源是否使用写入该组件的事件日志进行注册，并在需要时调用 <xref:System.Diagnostics.EventLog.CreateEventSource%2A> 。</span><span class="sxs-lookup"><span data-stu-id="b7a94-105">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b7a94-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="b7a94-106">To correct this error</span></span>  
  
1. <span data-ttu-id="b7a94-107">使用 <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> 或 <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> 方法删除源与第一个日志之间的关联。</span><span class="sxs-lookup"><span data-stu-id="b7a94-107">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2. <span data-ttu-id="b7a94-108">使用新的日志注册源。</span><span class="sxs-lookup"><span data-stu-id="b7a94-108">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7a94-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="b7a94-109">See also</span></span>

- [<span data-ttu-id="b7a94-110">My. .Log</span><span class="sxs-lookup"><span data-stu-id="b7a94-110">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
