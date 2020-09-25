---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 347a08a35ff898ab7037c11d3c87fda73c3ab2ab
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178094"
---
# \<headers>

<span data-ttu-id="f2066-101">除了其基本 URI 外，终结点可以按一个或多个 SOAP 标头寻址。</span><span class="sxs-lookup"><span data-stu-id="f2066-101">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="f2066-102">这一点在其中很有用的一组方案是一组 SOAP 媒介方案，其中终结点要求该终结点的客户端包括以媒介为目标的 SOAP 头。</span><span class="sxs-lookup"><span data-stu-id="f2066-102">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="f2066-103">此配置元素可用于定义此类自定义地址标头。</span><span class="sxs-lookup"><span data-stu-id="f2066-103">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="f2066-104">终结点标头集合中的项是用户定义的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="f2066-104">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="f2066-105">每个元素必须是格式良好的 XML。</span><span class="sxs-lookup"><span data-stu-id="f2066-105">Each element has to be well-formed XML.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<headers>**  
  
## <a name="syntax"></a><span data-ttu-id="f2066-106">语法</span><span class="sxs-lookup"><span data-stu-id="f2066-106">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2066-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f2066-107">Attributes and Elements</span></span>  

 <span data-ttu-id="f2066-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f2066-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2066-109">特性</span><span class="sxs-lookup"><span data-stu-id="f2066-109">Attributes</span></span>  

 <span data-ttu-id="f2066-110">无。</span><span class="sxs-lookup"><span data-stu-id="f2066-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f2066-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f2066-111">Child Elements</span></span>  

 <span data-ttu-id="f2066-112">用户定义的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="f2066-112">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f2066-113">父元素</span><span class="sxs-lookup"><span data-stu-id="f2066-113">Parent Elements</span></span>  
  
|<span data-ttu-id="f2066-114">元素</span><span class="sxs-lookup"><span data-stu-id="f2066-114">Element</span></span>|<span data-ttu-id="f2066-115">描述</span><span class="sxs-lookup"><span data-stu-id="f2066-115">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="f2066-116">配置不同类型的终结点。</span><span class="sxs-lookup"><span data-stu-id="f2066-116">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2066-117">备注</span><span class="sxs-lookup"><span data-stu-id="f2066-117">Remarks</span></span>  

 <span data-ttu-id="f2066-118">可选标头提供用于标识终结点或与终结点交互的更多详细寻址信息。</span><span class="sxs-lookup"><span data-stu-id="f2066-118">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="f2066-119">例如，标头可指示如何处理传入消息，终结点应发送答复消息的位置，或在多个实例可用时应使用哪个服务实例处理来自特定用户的传入消息。</span><span class="sxs-lookup"><span data-stu-id="f2066-119">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2066-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="f2066-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="f2066-121">终结点：地址、绑定和协定</span><span class="sxs-lookup"><span data-stu-id="f2066-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
