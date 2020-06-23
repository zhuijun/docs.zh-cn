---
title: 如何：使用 ChannelFactory
description: 了解如何创建通道工厂以创建多个通道，以便使用 WCF 客户端访问服务。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 7c87026ca4cf7c739f4615da9bc7f0272a382392
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246657"
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="0037d-103">如何：使用 ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="0037d-103">How to: Use the ChannelFactory</span></span>
<span data-ttu-id="0037d-104"><xref:System.ServiceModel.ChannelFactory%601> 泛型类用于某些高级方案中，这些方案要求创建可用于创建多个通道的通道工厂。</span><span class="sxs-lookup"><span data-stu-id="0037d-104">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="0037d-105">创建和使用 ChannelFactory 类</span><span class="sxs-lookup"><span data-stu-id="0037d-105">To create and use the ChannelFactory class</span></span>  
  
1. <span data-ttu-id="0037d-106">生成并运行 Windows Communication Foundation （WCF）服务。</span><span class="sxs-lookup"><span data-stu-id="0037d-106">Build and run an Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="0037d-107">有关详细信息，请参阅[设计和实现服务](../designing-and-implementing-services.md)、[配置服务](../configuring-services.md)和[托管服务](../hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="0037d-107">For more information, see [Designing and Implementing Services](../designing-and-implementing-services.md), [Configuring Services](../configuring-services.md), and [Hosting Services](../hosting-services.md).</span></span>  
  
2. <span data-ttu-id="0037d-108">使用 "工作的[元数据实用工具（Svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md) " 生成客户端的协定（接口）。</span><span class="sxs-lookup"><span data-stu-id="0037d-108">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3. <span data-ttu-id="0037d-109">在客户端代码中，使用 <xref:System.ServiceModel.ChannelFactory%601> 类创建多个终结点侦听器。</span><span class="sxs-lookup"><span data-stu-id="0037d-109">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0037d-110">示例</span><span class="sxs-lookup"><span data-stu-id="0037d-110">Example</span></span>  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
