---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: bb2989ed52a88d805510d65e1dc1740df7bb55eb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735941"
---
# \<useManagedPresentation>
<span data-ttu-id="d3e04-101">一个绑定元素，用于与支持 WS-Trust 的 CardSpace 配置文件的 CardSpace 安全令牌服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="d3e04-101">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="d3e04-102">此元素没有属性并且以空开关形式存在。</span><span class="sxs-lookup"><span data-stu-id="d3e04-102">This element has no attribute and is present as an empty switch.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**  
  
## <a name="syntax"></a><span data-ttu-id="d3e04-103">语法</span><span class="sxs-lookup"><span data-stu-id="d3e04-103">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3e04-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d3e04-104">Attributes and Elements</span></span>  
 <span data-ttu-id="d3e04-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d3e04-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3e04-106">特性</span><span class="sxs-lookup"><span data-stu-id="d3e04-106">Attributes</span></span>  
 <span data-ttu-id="d3e04-107">无。</span><span class="sxs-lookup"><span data-stu-id="d3e04-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d3e04-108">子元素</span><span class="sxs-lookup"><span data-stu-id="d3e04-108">Child Elements</span></span>  
 <span data-ttu-id="d3e04-109">无</span><span class="sxs-lookup"><span data-stu-id="d3e04-109">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3e04-110">父元素</span><span class="sxs-lookup"><span data-stu-id="d3e04-110">Parent Elements</span></span>  
  
|<span data-ttu-id="d3e04-111">元素</span><span class="sxs-lookup"><span data-stu-id="d3e04-111">Element</span></span>|<span data-ttu-id="d3e04-112">说明</span><span class="sxs-lookup"><span data-stu-id="d3e04-112">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d3e04-113">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="d3e04-113">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3e04-114">注解</span><span class="sxs-lookup"><span data-stu-id="d3e04-114">Remarks</span></span>  
 <span data-ttu-id="d3e04-115">标识提供程序使用此元素，用以在它的策略中表明它支持 WS-Trust 的 CardSpace 配置文件这一事实。</span><span class="sxs-lookup"><span data-stu-id="d3e04-115">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="d3e04-116">发布这种策略断言的标识提供程序应该能够基于该 CardSpace 配置文件颁发令牌。</span><span class="sxs-lookup"><span data-stu-id="d3e04-116">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e04-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d3e04-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d3e04-118">绑定</span><span class="sxs-lookup"><span data-stu-id="d3e04-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d3e04-119">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="d3e04-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d3e04-120">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="d3e04-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
