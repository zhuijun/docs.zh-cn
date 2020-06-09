---
title: ServiceModel 事务配置
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 1d04a7bb756cccb33b436c1f57decc0249764828
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600330"
---
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="b7ba0-102">ServiceModel 事务配置</span><span class="sxs-lookup"><span data-stu-id="b7ba0-102">ServiceModel Transaction Configuration</span></span>
<span data-ttu-id="b7ba0-103">Windows Communication Foundation （WCF）提供了三个属性，用于为服务配置事务： `transactionFlow` 、 `transactionProtocol` 和 `transactionTimeout` 。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-103">Windows Communication Foundation (WCF) provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="b7ba0-104">配置 transactionFlow</span><span class="sxs-lookup"><span data-stu-id="b7ba0-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="b7ba0-105">WCF 提供的大多数预定义绑定都包含 `transactionFlow` 和 `transactionProtocol` 属性，以便您可以将绑定配置为使用特定的事务流协议为特定终结点接受传入事务。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-105">Most of the predefined bindings WCF provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="b7ba0-106">此外，你可以使用 `transactionFlow` 元素及其 `transactionProtocol` 特性生成你自己的自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="b7ba0-107">有关设置配置元素的详细信息，请参阅 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 和[WCF 配置架构](../../configure-apps/file-schema/wcf/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-107">For more information about setting the configuration elements, see [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) and [WCF Configuration Schema](../../configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="b7ba0-108">`transactionFlow` 属性指定是否为使用绑定的服务终结点启用事务流。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="b7ba0-109">配置 transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="b7ba0-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="b7ba0-110">`transactionProtocol` 属性指定要应用于使用绑定的服务终结点的事务协议。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="b7ba0-111">下面是一个配置节示例，该配置节将指定的绑定配置为支持事务流并且使用 WS-AtomicTransaction 协议。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding name="test"  
      closeTimeout="00:00:10"  
      openTimeout="00:00:20"
      receiveTimeout="00:00:30"  
      sendTimeout="00:00:40"  
      transactionFlow="true"  
      transactionProtocol="WSAtomicTransactionOctober2004"  
      hostNameComparisonMode="WeakWildcard"  
      maxBufferSize="1001"  
      maxConnections="123"
      maxReceivedMessageSize="1000">  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="b7ba0-112">配置 transactionTimeout</span><span class="sxs-lookup"><span data-stu-id="b7ba0-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="b7ba0-113">您可以 `transactionTimeout` 在配置文件的元素中配置您的 WCF 服务的属性 `behavior` 。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-113">You can configure the `transactionTimeout` attribute for your WCF service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="b7ba0-114">下面的代码演示如何执行此操作。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="b7ba0-115">`transactionTimeout` 属性指定了在该服务中创建的新事务必须在此期间完成的时间段。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="b7ba0-116">它被用作任何建立新事务的操作的 <xref:System.Transactions.TransactionScope> 超时，而且，如果应用了 <xref:System.ServiceModel.OperationBehaviorAttribute>，则 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 属性将设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="b7ba0-117">超时指定了从创建事务到完成两阶段提交协议的第 1 阶段之间的持续时间。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="b7ba0-118">如果在 `service` 配置节内设置了此属性，则应该通过 <xref:System.ServiceModel.OperationBehaviorAttribute> 应用相应服务的至少一个方法，其中 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="b7ba0-119">请注意，所使用的超时值是此 `transactionTimeout` 配置设置和任何 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 属性之间的较小值。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7ba0-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b7ba0-120">See also</span></span>

- [\<binding>](../../configure-apps/file-schema/wcf/bindings.md)
- [<span data-ttu-id="b7ba0-121">WCF 配置架构</span><span class="sxs-lookup"><span data-stu-id="b7ba0-121">WCF Configuration Schema</span></span>](../../configure-apps/file-schema/wcf/index.md)
