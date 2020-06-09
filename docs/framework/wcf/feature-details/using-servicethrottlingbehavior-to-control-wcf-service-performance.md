---
title: 使用 ServiceThrottlingBehavior 控制 WCF 服务性能
ms.date: 03/30/2017
helpviewer_keywords:
- behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
ms.openlocfilehash: 9cc5141805504bc46391105f475860b032f12d32
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600226"
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a><span data-ttu-id="9f101-102">使用 ServiceThrottlingBehavior 控制 WCF 服务性能</span><span class="sxs-lookup"><span data-stu-id="9f101-102">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>
<span data-ttu-id="9f101-103"><xref:System.ServiceModel.Description.ServiceThrottlingBehavior> 类公开的属性可用于限制在应用程序级别创建实例或会话的数量。</span><span class="sxs-lookup"><span data-stu-id="9f101-103">The <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> class exposes properties that you can use to limit how many instances or sessions are created at the application level.</span></span> <span data-ttu-id="9f101-104">使用此行为，可以微调 Windows Communication Foundation （WCF）应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="9f101-104">Using this behavior, you can fine-tune the performance of your Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a><span data-ttu-id="9f101-105">控制服务实例和并发调用</span><span class="sxs-lookup"><span data-stu-id="9f101-105">Controlling Service Instances and Concurrent Calls</span></span>  
 <span data-ttu-id="9f101-106">使用 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> 属性指定在 <xref:System.ServiceModel.ServiceHost> 类上主动处理的最大消息数，并使用 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> 属性指定服务中 <xref:System.ServiceModel.InstanceContext> 对象的最大数目。</span><span class="sxs-lookup"><span data-stu-id="9f101-106">Use the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> property to specify the maximum number of messages actively processing across a <xref:System.ServiceModel.ServiceHost> class, and the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> property to specify the maximum number of <xref:System.ServiceModel.InstanceContext> objects in the service.</span></span>  
  
 <span data-ttu-id="9f101-107">由于确定这些属性的设置通常是在实际经验针对负载运行应用程序之后发生的，因此， <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> 通常使用元素在应用程序配置文件中指定属性的设置 [\<serviceThrottling>](../../configure-apps/file-schema/wcf/servicethrottling.md) 。</span><span class="sxs-lookup"><span data-stu-id="9f101-107">Because determining the settings for these properties usually takes place after real-world experience running the application against loads, the settings for the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> properties is typically specified in an application configuration file using the [\<serviceThrottling>](../../configure-apps/file-schema/wcf/servicethrottling.md) element.</span></span>  
  
 <span data-ttu-id="9f101-108">下面的代码示例演示如何使用将 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>、<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A> 和 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> 属性设置为 1（作为最小示例）的应用程序配置文件中的 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> 类。</span><span class="sxs-lookup"><span data-stu-id="9f101-108">The following code example shows the use of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> class from an application configuration file that sets the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, and <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> properties to 1 as a trivial example.</span></span> <span data-ttu-id="9f101-109">实际体验确定任何特定应用程序的最佳设置。</span><span class="sxs-lookup"><span data-stu-id="9f101-109">Real-world experience determines the optimal settings for any particular application.</span></span>  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 <span data-ttu-id="9f101-110">确切的运行时行为取决于 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 和 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 属性的值，这两种属性分别控制操作一次可执行的消息数以及有关传入通道会话的服务 <xref:System.ServiceModel.InstanceContext> 的生存期。</span><span class="sxs-lookup"><span data-stu-id="9f101-110">The exact run-time behavior depends upon the values of the <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> and <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> properties, which control how many messages can execute inside an operation at once and the lifetimes of the service <xref:System.ServiceModel.InstanceContext> relative to incoming channel sessions, respectively.</span></span>  
  
 <span data-ttu-id="9f101-111">有关详细信息，请参见 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> 和 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>。</span><span class="sxs-lookup"><span data-stu-id="9f101-111">For details, see <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, and <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f101-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9f101-112">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
