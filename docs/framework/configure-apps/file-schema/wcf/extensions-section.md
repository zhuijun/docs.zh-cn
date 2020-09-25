---
title: <extensions> 区
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: f3eb5d446291dfa6b7c8e0f1ee2b6a5cf53c2162
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185777"
---
# <a name="extensions-section"></a><span data-ttu-id="4a504-102">\<extensions> 区</span><span class="sxs-lookup"><span data-stu-id="4a504-102">\<extensions> section</span></span>

<span data-ttu-id="4a504-103">此配置节包含一个扩展集合，这些扩展使用户能够创建扩展的用户定义绑定、行为和其他方面。</span><span class="sxs-lookup"><span data-stu-id="4a504-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**  
  
## <a name="syntax"></a><span data-ttu-id="4a504-104">语法</span><span class="sxs-lookup"><span data-stu-id="4a504-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
    </bindingExtensions>
    <behaviorExtensions>
    </behaviorExtensions>
    <bindingElementExtensions>
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a504-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4a504-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4a504-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4a504-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a504-107">特性</span><span class="sxs-lookup"><span data-stu-id="4a504-107">Attributes</span></span>  

 <span data-ttu-id="4a504-108">无。</span><span class="sxs-lookup"><span data-stu-id="4a504-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4a504-109">子元素</span><span class="sxs-lookup"><span data-stu-id="4a504-109">Child Elements</span></span>  
  
|<span data-ttu-id="4a504-110">元素</span><span class="sxs-lookup"><span data-stu-id="4a504-110">Element</span></span>|<span data-ttu-id="4a504-111">描述</span><span class="sxs-lookup"><span data-stu-id="4a504-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviorExtensions>](behaviorextensions.md)|<span data-ttu-id="4a504-112">本节包含子元素，这些子元素指定使用户可以自定义服务或终结点行为的行为扩展。</span><span class="sxs-lookup"><span data-stu-id="4a504-112">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[\<bindingElementExtensions>](bindingelementextensions.md)|<span data-ttu-id="4a504-113">本节为使用计算机或应用程序配置文件中的自定义绑定元素提供支持。</span><span class="sxs-lookup"><span data-stu-id="4a504-113">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[\<bindingExtensions>](bindingextensions.md)|<span data-ttu-id="4a504-114">本节包含子元素，这些子元素指定使用户可以自定义绑定的绑定扩展。</span><span class="sxs-lookup"><span data-stu-id="4a504-114">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[\<endpointExtensions>](endpointextensions.md)|<span data-ttu-id="4a504-115">本节包含元注册标准终结点的子元素。</span><span class="sxs-lookup"><span data-stu-id="4a504-115">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a504-116">父元素</span><span class="sxs-lookup"><span data-stu-id="4a504-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4a504-117">元素</span><span class="sxs-lookup"><span data-stu-id="4a504-117">Element</span></span>|<span data-ttu-id="4a504-118">描述</span><span class="sxs-lookup"><span data-stu-id="4a504-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a504-119">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4a504-119">system.ServiceModel</span></span>|<span data-ttu-id="4a504-120">所有 WCF 配置元素的根元素。</span><span class="sxs-lookup"><span data-stu-id="4a504-120">The root element of all WCF configuration elements.</span></span>|
