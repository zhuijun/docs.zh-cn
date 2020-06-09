---
title: 如何：使用 ChannelFactory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 4bb2053fb50931756e79d5346a3f14d2acbe04f6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595305"
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="d4e08-102">如何：使用 ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="d4e08-102">How to: Use the ChannelFactory</span></span>
<span data-ttu-id="d4e08-103"><xref:System.ServiceModel.ChannelFactory%601> 泛型类用于某些高级方案中，这些方案要求创建可用于创建多个通道的通道工厂。</span><span class="sxs-lookup"><span data-stu-id="d4e08-103">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="d4e08-104">创建和使用 ChannelFactory 类</span><span class="sxs-lookup"><span data-stu-id="d4e08-104">To create and use the ChannelFactory class</span></span>  
  
1. <span data-ttu-id="d4e08-105">生成并运行 Windows Communication Foundation （WCF）服务。</span><span class="sxs-lookup"><span data-stu-id="d4e08-105">Build and run an Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="d4e08-106">有关详细信息，请参阅[设计和实现服务](../designing-and-implementing-services.md)、[配置服务](../configuring-services.md)和[托管服务](../hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d4e08-106">For more information, see [Designing and Implementing Services](../designing-and-implementing-services.md), [Configuring Services](../configuring-services.md), and [Hosting Services](../hosting-services.md).</span></span>  
  
2. <span data-ttu-id="d4e08-107">使用 " [svcutil.exe" 元数据实用工具（）](../servicemodel-metadata-utility-tool-svcutil-exe.md)为客户端生成协定（接口）。</span><span class="sxs-lookup"><span data-stu-id="d4e08-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3. <span data-ttu-id="d4e08-108">在客户端代码中，使用 <xref:System.ServiceModel.ChannelFactory%601> 类创建多个终结点侦听器。</span><span class="sxs-lookup"><span data-stu-id="d4e08-108">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4e08-109">示例</span><span class="sxs-lookup"><span data-stu-id="d4e08-109">Example</span></span>  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
