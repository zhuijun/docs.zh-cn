---
title: 在绑定上配置超时值
description: 了解如何管理 WCF 绑定的超时设置，以提高服务的性能、可用性和安全性。
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: c41824a242d9b42290183cd70b9acf5b8ee59e6b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245110"
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="52c36-103">在绑定上配置超时值</span><span class="sxs-lookup"><span data-stu-id="52c36-103">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="52c36-104">WCF 绑定中提供了很多超时设置。</span><span class="sxs-lookup"><span data-stu-id="52c36-104">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="52c36-105">正确设置这些超时设置不仅可以提高您服务的性能，而且对发挥您服务的可用性和安全性起到重要作用。</span><span class="sxs-lookup"><span data-stu-id="52c36-105">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="52c36-106">WCF 绑定中提供了下列超时：</span><span class="sxs-lookup"><span data-stu-id="52c36-106">The following timeouts are available on WCF bindings:</span></span>  
  
1. <span data-ttu-id="52c36-107">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="52c36-107">OpenTimeout</span></span>  
  
2. <span data-ttu-id="52c36-108">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="52c36-108">CloseTimeout</span></span>  
  
3. <span data-ttu-id="52c36-109">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="52c36-109">SendTimeout</span></span>  
  
4. <span data-ttu-id="52c36-110">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="52c36-110">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="52c36-111">WCF 绑定超时</span><span class="sxs-lookup"><span data-stu-id="52c36-111">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="52c36-112">本主题中讨论的每个设置都是在绑定本身上设置的（无论是在代码还是在配置中）。</span><span class="sxs-lookup"><span data-stu-id="52c36-112">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="52c36-113">下面的代码演示如何对自承载服务的上下文中的 WCF 绑定以编程方式设置超时。</span><span class="sxs-lookup"><span data-stu-id="52c36-113">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
```csharp  
public static void Main()
{
    Uri baseAddress = new Uri("http://localhost/MyServer/MyService");

    try
    {
        ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService));

        WSHttpBinding binding = new WSHttpBinding();
        binding.OpenTimeout = new TimeSpan(0, 10, 0);
        binding.CloseTimeout = new TimeSpan(0, 10, 0);
        binding.SendTimeout = new TimeSpan(0, 10, 0);
        binding.ReceiveTimeout = new TimeSpan(0, 10, 0);

        serviceHost.AddServiceEndpoint("ICalculator", binding, baseAddress);
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();
    }
    catch (CommunicationException ex)
    {
        // Handle exception ...
    }
}
```  
  
 <span data-ttu-id="52c36-114">下面的示例演示如何在应用程序配置文件中配置绑定超时。</span><span class="sxs-lookup"><span data-stu-id="52c36-114">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding openTimeout="00:10:00"
                 closeTimeout="00:10:00"
                 sendTimeout="00:10:00"
                 receiveTimeout="00:10:00">
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
 <span data-ttu-id="52c36-115">有关这些设置的更多信息，可以在 <xref:System.ServiceModel.Channels.Binding> 类的参考文档中找到。</span><span class="sxs-lookup"><span data-stu-id="52c36-115">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="52c36-116">客户端超时</span><span class="sxs-lookup"><span data-stu-id="52c36-116">Client-side Timeouts</span></span>  
 <span data-ttu-id="52c36-117">在客户端：</span><span class="sxs-lookup"><span data-stu-id="52c36-117">On the client side:</span></span>  
  
1. <span data-ttu-id="52c36-118">SendTimeout — 用于初始化 OperationTimeout，此设置控制发送消息的整个过程，包括接收请求/答复服务操作的答复消息。</span><span class="sxs-lookup"><span data-stu-id="52c36-118">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="52c36-119">从回调协定方法发送答复消息时，此超时也适用。</span><span class="sxs-lookup"><span data-stu-id="52c36-119">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2. <span data-ttu-id="52c36-120">OpenTimeout –当未指定显式超时值时，在打开通道时使用。</span><span class="sxs-lookup"><span data-stu-id="52c36-120">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3. <span data-ttu-id="52c36-121">CloseTimeout –当未指定显式超时值时，在关闭通道时使用。</span><span class="sxs-lookup"><span data-stu-id="52c36-121">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4. <span data-ttu-id="52c36-122">ReceiveTimeout –未使用。</span><span class="sxs-lookup"><span data-stu-id="52c36-122">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="52c36-123">服务端超时</span><span class="sxs-lookup"><span data-stu-id="52c36-123">Service-side Timeouts</span></span>  
 <span data-ttu-id="52c36-124">在服务端：</span><span class="sxs-lookup"><span data-stu-id="52c36-124">On the service side:</span></span>  
  
1. <span data-ttu-id="52c36-125">SendTimeout、OpenTimeout、CloseTimeout 与客户端上的相同。</span><span class="sxs-lookup"><span data-stu-id="52c36-125">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2. <span data-ttu-id="52c36-126">ReceiveTimeout — 服务框架层用于初始化会话空闲超时，它控制一个会话在空闲多久之后发生超时。</span><span class="sxs-lookup"><span data-stu-id="52c36-126">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
