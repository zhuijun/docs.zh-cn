---
title: 请求-答复服务
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: df42f3fa8f5a15572987b0d4859856c7f838e632
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586229"
---
# <a name="request-reply-services"></a><span data-ttu-id="863d9-102">请求-答复服务</span><span class="sxs-lookup"><span data-stu-id="863d9-102">Request-Reply Services</span></span>
<span data-ttu-id="863d9-103">请求-答复服务是 Windows Communication Foundation （WCF）中的默认操作协定类型。</span><span class="sxs-lookup"><span data-stu-id="863d9-103">Request-reply services are the default type of operation contract in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="863d9-104">客户端调用服务操作并等待服务的响应。</span><span class="sxs-lookup"><span data-stu-id="863d9-104">Clients make calls to service operations and wait for a response from the service.</span></span> <span data-ttu-id="863d9-105">你可以同步执行对服务操作的调用（客户端接收到服务的响应或调用超时前客户端将保持阻止状态），也可以异步执行对服务操作的调用（客户端调用服务操作，继续工作，并在其他线程上接收服务的响应）。</span><span class="sxs-lookup"><span data-stu-id="863d9-105">You can perform calls to a service operation either synchronously, where the client blocks until it receives a response from the service or the call times, or asynchronously, where the client makes a call to the service operation, continues working, and receives the response from the service on another thread.</span></span>  
  
 <span data-ttu-id="863d9-106">若要创建请求-答复服务协定，请定义服务协定，然后对每个操作应用 <xref:System.ServiceModel.OperationContractAttribute> 类，如下面的示例代码所示。</span><span class="sxs-lookup"><span data-stu-id="863d9-106">To create a request-reply service contract, define your service contract, and apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="863d9-107">您不必将 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 属性设置为 `false`，因为这是默认行为。</span><span class="sxs-lookup"><span data-stu-id="863d9-107">You do not have to set the  <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `false` because this is the default behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="863d9-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="863d9-108">See also</span></span>

- [<span data-ttu-id="863d9-109">单向服务</span><span class="sxs-lookup"><span data-stu-id="863d9-109">One-Way Services</span></span>](one-way-services.md)
- [<span data-ttu-id="863d9-110">双工服务</span><span class="sxs-lookup"><span data-stu-id="863d9-110">Duplex Services</span></span>](duplex-services.md)
