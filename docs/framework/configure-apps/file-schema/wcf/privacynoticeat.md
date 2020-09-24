---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 5e772e23b21c566c906be854e33b924698dcf3e0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158703"
---
# \<privacyNoticeAt>

<span data-ttu-id="56647-101">表示一个配置元素，该元素指定 `wsFederationHttp` 绑定中使用的隐私声明。</span><span class="sxs-lookup"><span data-stu-id="56647-101">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**  
  
## <a name="syntax"></a><span data-ttu-id="56647-102">语法</span><span class="sxs-lookup"><span data-stu-id="56647-102">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="56647-103">类型</span><span class="sxs-lookup"><span data-stu-id="56647-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56647-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="56647-104">Attributes and Elements</span></span>  

 <span data-ttu-id="56647-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="56647-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56647-106">特性</span><span class="sxs-lookup"><span data-stu-id="56647-106">Attributes</span></span>  
  
|<span data-ttu-id="56647-107">属性</span><span class="sxs-lookup"><span data-stu-id="56647-107">Attribute</span></span>|<span data-ttu-id="56647-108">描述</span><span class="sxs-lookup"><span data-stu-id="56647-108">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="56647-109">一个字符串，指定隐私声明位于的 URI。</span><span class="sxs-lookup"><span data-stu-id="56647-109">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="56647-110">一个整数，指定此隐私声明的版本。</span><span class="sxs-lookup"><span data-stu-id="56647-110">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56647-111">子元素</span><span class="sxs-lookup"><span data-stu-id="56647-111">Child Elements</span></span>  

 <span data-ttu-id="56647-112">无。</span><span class="sxs-lookup"><span data-stu-id="56647-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="56647-113">父元素</span><span class="sxs-lookup"><span data-stu-id="56647-113">Parent Elements</span></span>  
  
|<span data-ttu-id="56647-114">元素</span><span class="sxs-lookup"><span data-stu-id="56647-114">Element</span></span>|<span data-ttu-id="56647-115">描述</span><span class="sxs-lookup"><span data-stu-id="56647-115">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="56647-116">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="56647-116">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56647-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="56647-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="56647-118">绑定</span><span class="sxs-lookup"><span data-stu-id="56647-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="56647-119">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="56647-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="56647-120">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="56647-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
