---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: f5bcd142fb2b032ea179bcbba68fee53b98d2d77
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736313"
---
# \<transactionFlow>
<span data-ttu-id="76c9f-101">指定自定义绑定的事务流支持。</span><span class="sxs-lookup"><span data-stu-id="76c9f-101">Specifies transaction flow support for the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**  
  
## <a name="syntax"></a><span data-ttu-id="76c9f-102">语法</span><span class="sxs-lookup"><span data-stu-id="76c9f-102">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76c9f-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="76c9f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="76c9f-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="76c9f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76c9f-105">特性</span><span class="sxs-lookup"><span data-stu-id="76c9f-105">Attributes</span></span>  
  
|<span data-ttu-id="76c9f-106">属性</span><span class="sxs-lookup"><span data-stu-id="76c9f-106">Attribute</span></span>|<span data-ttu-id="76c9f-107">说明</span><span class="sxs-lookup"><span data-stu-id="76c9f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76c9f-108">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="76c9f-108">transactionProtocol</span></span>|<span data-ttu-id="76c9f-109">指定要使用的事务处理协议。</span><span class="sxs-lookup"><span data-stu-id="76c9f-109">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="76c9f-110">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="76c9f-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="76c9f-111">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="76c9f-111">-   OleTransactions</span></span><br /><span data-ttu-id="76c9f-112">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="76c9f-112">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="76c9f-113">默认值为 OleTransactions。</span><span class="sxs-lookup"><span data-stu-id="76c9f-113">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="76c9f-114">此属性的类型为 <xref:System.ServiceModel.TransactionProtocol>。</span><span class="sxs-lookup"><span data-stu-id="76c9f-114">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76c9f-115">子元素</span><span class="sxs-lookup"><span data-stu-id="76c9f-115">Child Elements</span></span>  
 <span data-ttu-id="76c9f-116">无。</span><span class="sxs-lookup"><span data-stu-id="76c9f-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76c9f-117">父元素</span><span class="sxs-lookup"><span data-stu-id="76c9f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="76c9f-118">元素</span><span class="sxs-lookup"><span data-stu-id="76c9f-118">Element</span></span>|<span data-ttu-id="76c9f-119">描述</span><span class="sxs-lookup"><span data-stu-id="76c9f-119">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="76c9f-120">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="76c9f-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76c9f-121">注解</span><span class="sxs-lookup"><span data-stu-id="76c9f-121">Remarks</span></span>  
 <span data-ttu-id="76c9f-122">此元素允许你在终结点绑定设置中启用或禁用传入事务流，并允许指定传入事务所需的协议格式。</span><span class="sxs-lookup"><span data-stu-id="76c9f-122">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="76c9f-123">有关使用此配置元素的详细信息，请参阅配置[配置](../../../wcf/feature-details/servicemodel-transaction-configuration.md)和[启用事务流](../../../wcf/feature-details/enabling-transaction-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="76c9f-123">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="76c9f-124">使用 `OleTransactions` 协议在终结点之间对事务进行流处理时，如果目标终结点尝试使用任何 `OleTransactions` 之外的协议进行流处理，则可能丢失事务超时。</span><span class="sxs-lookup"><span data-stu-id="76c9f-124">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="76c9f-125">这可能导致 OleTransactions 跃点后面的所有下级节点的超时时间比预期延迟。</span><span class="sxs-lookup"><span data-stu-id="76c9f-125">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76c9f-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="76c9f-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="76c9f-127">ServiceModel 事务配置</span><span class="sxs-lookup"><span data-stu-id="76c9f-127">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="76c9f-128">启用事务流</span><span class="sxs-lookup"><span data-stu-id="76c9f-128">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="76c9f-129">绑定</span><span class="sxs-lookup"><span data-stu-id="76c9f-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="76c9f-130">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="76c9f-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="76c9f-131">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="76c9f-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
