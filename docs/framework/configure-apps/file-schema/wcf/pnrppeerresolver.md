---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: 0a8cc60226b13552d47faec3a156ed1f59acacb9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181396"
---
# \<pnrpPeerResolver>

<span data-ttu-id="f5e53-101">指定要将 PNRP（对等名称解析协议）解析程序用作解析程序。</span><span class="sxs-lookup"><span data-stu-id="f5e53-101">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="f5e53-102">此元素是可选的，因为 PNRP 是默认解析程序。</span><span class="sxs-lookup"><span data-stu-id="f5e53-102">This element is optional because PNRP is the default resolver.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="f5e53-103">语法</span><span class="sxs-lookup"><span data-stu-id="f5e53-103">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5e53-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f5e53-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f5e53-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f5e53-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5e53-106">特性</span><span class="sxs-lookup"><span data-stu-id="f5e53-106">Attributes</span></span>  
  
|<span data-ttu-id="f5e53-107">属性</span><span class="sxs-lookup"><span data-stu-id="f5e53-107">Attribute</span></span>|<span data-ttu-id="f5e53-108">描述</span><span class="sxs-lookup"><span data-stu-id="f5e53-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f5e53-109">resolverType</span><span class="sxs-lookup"><span data-stu-id="f5e53-109">resolverType</span></span>|<span data-ttu-id="f5e53-110">一个字符串，指定要使用的解析程序。</span><span class="sxs-lookup"><span data-stu-id="f5e53-110">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="f5e53-111">此属性是可选的。</span><span class="sxs-lookup"><span data-stu-id="f5e53-111">This attribute is optional.</span></span> <span data-ttu-id="f5e53-112">如果不设置，或者将其设置为空字符串，则使用 PNRP。</span><span class="sxs-lookup"><span data-stu-id="f5e53-112">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5e53-113">子元素</span><span class="sxs-lookup"><span data-stu-id="f5e53-113">Child Elements</span></span>  

 <span data-ttu-id="f5e53-114">无</span><span class="sxs-lookup"><span data-stu-id="f5e53-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f5e53-115">父元素</span><span class="sxs-lookup"><span data-stu-id="f5e53-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f5e53-116">元素</span><span class="sxs-lookup"><span data-stu-id="f5e53-116">Element</span></span>|<span data-ttu-id="f5e53-117">描述</span><span class="sxs-lookup"><span data-stu-id="f5e53-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f5e53-118">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="f5e53-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f5e53-119">示例</span><span class="sxs-lookup"><span data-stu-id="f5e53-119">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="f5e53-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="f5e53-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f5e53-121">绑定</span><span class="sxs-lookup"><span data-stu-id="f5e53-121">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f5e53-122">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="f5e53-122">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f5e53-123">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="f5e53-123">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="f5e53-124">对等解析程序</span><span class="sxs-lookup"><span data-stu-id="f5e53-124">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
