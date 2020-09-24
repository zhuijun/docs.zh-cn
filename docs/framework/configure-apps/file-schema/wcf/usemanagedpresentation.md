---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: 86a6f975b05133d5f9f21fcfb82ef4c23d2ffaba
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148807"
---
# \<useManagedPresentation>

<span data-ttu-id="e1e66-101">一个绑定元素，用于与支持 WS-Trust 的 CardSpace 配置文件的 CardSpace 安全令牌服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="e1e66-101">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="e1e66-102">此元素没有属性并且以空开关形式存在。</span><span class="sxs-lookup"><span data-stu-id="e1e66-102">This element has no attribute and is present as an empty switch.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**  
  
## <a name="syntax"></a><span data-ttu-id="e1e66-103">语法</span><span class="sxs-lookup"><span data-stu-id="e1e66-103">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1e66-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e1e66-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e1e66-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e1e66-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1e66-106">特性</span><span class="sxs-lookup"><span data-stu-id="e1e66-106">Attributes</span></span>  

 <span data-ttu-id="e1e66-107">无。</span><span class="sxs-lookup"><span data-stu-id="e1e66-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e1e66-108">子元素</span><span class="sxs-lookup"><span data-stu-id="e1e66-108">Child Elements</span></span>  

 <span data-ttu-id="e1e66-109">无</span><span class="sxs-lookup"><span data-stu-id="e1e66-109">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1e66-110">父元素</span><span class="sxs-lookup"><span data-stu-id="e1e66-110">Parent Elements</span></span>  
  
|<span data-ttu-id="e1e66-111">元素</span><span class="sxs-lookup"><span data-stu-id="e1e66-111">Element</span></span>|<span data-ttu-id="e1e66-112">描述</span><span class="sxs-lookup"><span data-stu-id="e1e66-112">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="e1e66-113">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="e1e66-113">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1e66-114">备注</span><span class="sxs-lookup"><span data-stu-id="e1e66-114">Remarks</span></span>  

 <span data-ttu-id="e1e66-115">标识提供程序使用此元素，用以在它的策略中表明它支持 WS-Trust 的 CardSpace 配置文件这一事实。</span><span class="sxs-lookup"><span data-stu-id="e1e66-115">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="e1e66-116">发布这种策略断言的标识提供程序应该能够基于该 CardSpace 配置文件颁发令牌。</span><span class="sxs-lookup"><span data-stu-id="e1e66-116">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1e66-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="e1e66-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e1e66-118">绑定</span><span class="sxs-lookup"><span data-stu-id="e1e66-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e1e66-119">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="e1e66-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e1e66-120">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="e1e66-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
