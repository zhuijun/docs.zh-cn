---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2ff70d3a8636970434582e417e4549ab6b433fc1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738760"
---
# \<privacyNoticeAt>
<span data-ttu-id="1f26d-101">表示一个配置元素，该元素指定 `wsFederationHttp` 绑定中使用的隐私声明。</span><span class="sxs-lookup"><span data-stu-id="1f26d-101">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**  
  
## <a name="syntax"></a><span data-ttu-id="1f26d-102">语法</span><span class="sxs-lookup"><span data-stu-id="1f26d-102">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="1f26d-103">类型</span><span class="sxs-lookup"><span data-stu-id="1f26d-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f26d-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1f26d-104">Attributes and Elements</span></span>  
 <span data-ttu-id="1f26d-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1f26d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f26d-106">特性</span><span class="sxs-lookup"><span data-stu-id="1f26d-106">Attributes</span></span>  
  
|<span data-ttu-id="1f26d-107">属性</span><span class="sxs-lookup"><span data-stu-id="1f26d-107">Attribute</span></span>|<span data-ttu-id="1f26d-108">说明</span><span class="sxs-lookup"><span data-stu-id="1f26d-108">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="1f26d-109">一个字符串，指定隐私声明位于的 URI。</span><span class="sxs-lookup"><span data-stu-id="1f26d-109">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="1f26d-110">一个整数，指定此隐私声明的版本。</span><span class="sxs-lookup"><span data-stu-id="1f26d-110">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f26d-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1f26d-111">Child Elements</span></span>  
 <span data-ttu-id="1f26d-112">无。</span><span class="sxs-lookup"><span data-stu-id="1f26d-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f26d-113">父元素</span><span class="sxs-lookup"><span data-stu-id="1f26d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="1f26d-114">元素</span><span class="sxs-lookup"><span data-stu-id="1f26d-114">Element</span></span>|<span data-ttu-id="1f26d-115">描述</span><span class="sxs-lookup"><span data-stu-id="1f26d-115">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="1f26d-116">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="1f26d-116">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f26d-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1f26d-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1f26d-118">绑定</span><span class="sxs-lookup"><span data-stu-id="1f26d-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1f26d-119">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="1f26d-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1f26d-120">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="1f26d-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
