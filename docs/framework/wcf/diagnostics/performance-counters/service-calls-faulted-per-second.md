---
title: 服务：Calls Faulted Per Second（每秒出错的调用次数）
ms.date: 03/30/2017
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
ms.openlocfilehash: 211240d5bef7fe31a36f636313b48a2b9e15b239
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556006"
---
# <a name="service-calls-faulted-per-second"></a><span data-ttu-id="9ee50-102">服务：Calls Faulted Per Second（每秒出错的调用次数）</span><span class="sxs-lookup"><span data-stu-id="9ee50-102">Service: Calls Faulted Per Second</span></span>
<span data-ttu-id="9ee50-103">计数器名称：Calls Faulted Per Second（每秒出错的调用次数）。</span><span class="sxs-lookup"><span data-stu-id="9ee50-103">Counter Name: Calls Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9ee50-104">说明</span><span class="sxs-lookup"><span data-stu-id="9ee50-104">Description</span></span>  
 <span data-ttu-id="9ee50-105">一秒内向此服务返回了错误的调用的数目。</span><span class="sxs-lookup"><span data-stu-id="9ee50-105">Number of calls that have returned faults to this service in a second.</span></span>  
  
 <span data-ttu-id="9ee50-106">此计数器的性能计数器类型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值使用以下公式进行计算。</span><span class="sxs-lookup"><span data-stu-id="9ee50-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="9ee50-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="9ee50-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="9ee50-108">在 Windows Communication Foundation (WCF) 应用程序中，服务方法使用 SOAP 错误消息来传递处理错误信息。</span><span class="sxs-lookup"><span data-stu-id="9ee50-108">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="9ee50-109">SOAP 错误是包括在服务操作元数据中的消息类型，因此会创建一个错误协定，客户端可使用该协定来使执行更加可靠或更具交互性。</span><span class="sxs-lookup"><span data-stu-id="9ee50-109">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="9ee50-110">由于 SOAP 错误在客户端以 XML 格式表示，因此具有高度的互操作性。</span><span class="sxs-lookup"><span data-stu-id="9ee50-110">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ee50-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="9ee50-111">See also</span></span>

- [<span data-ttu-id="9ee50-112">在协定和服务中指定和处理错误</span><span class="sxs-lookup"><span data-stu-id="9ee50-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
