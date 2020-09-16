---
title: 服务：Calls Failed Per Second（每秒失败的调用次数）
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 5629c55cba6f21de24a1de7e8d38a9c08fcf4fb1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559104"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="5980f-102">服务：Calls Failed Per Second（每秒失败的调用次数）</span><span class="sxs-lookup"><span data-stu-id="5980f-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="5980f-103">计数器名称：Calls Failed Per Second（每秒失败的调用次数）。</span><span class="sxs-lookup"><span data-stu-id="5980f-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5980f-104">说明</span><span class="sxs-lookup"><span data-stu-id="5980f-104">Description</span></span>  
 <span data-ttu-id="5980f-105">一秒钟内由此服务收到且具有未处理异常的调用次数。</span><span class="sxs-lookup"><span data-stu-id="5980f-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="5980f-106">此计数器的性能计数器类型 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))，其值使用以下公式进行计算。</span><span class="sxs-lookup"><span data-stu-id="5980f-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5980f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="5980f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="5980f-108">在托管代码中，出现错误条件时引发异常。</span><span class="sxs-lookup"><span data-stu-id="5980f-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="5980f-109">在托管代码中，出现错误条件时引发异常。</span><span class="sxs-lookup"><span data-stu-id="5980f-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="5980f-110">此服务中每出现一个未处理异常，此计数器就会递增。</span><span class="sxs-lookup"><span data-stu-id="5980f-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5980f-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="5980f-111">See also</span></span>

- [<span data-ttu-id="5980f-112">在协定和服务中指定和处理错误</span><span class="sxs-lookup"><span data-stu-id="5980f-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
