---
title: <extensions>区
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 35621acaf96a80ffa3ffe4a3c6605143c48995a5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855355"
---
# <a name="extensions-section"></a><span data-ttu-id="d9e0d-102">\<extensions>区</span><span class="sxs-lookup"><span data-stu-id="d9e0d-102">\<extensions> section</span></span>
<span data-ttu-id="d9e0d-103">此配置节包含一个扩展集合，这些扩展使用户能够创建扩展的用户定义绑定、行为和其他方面。</span><span class="sxs-lookup"><span data-stu-id="d9e0d-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<extensions>**  
  
## <a name="syntax"></a><span data-ttu-id="d9e0d-104">语法</span><span class="sxs-lookup"><span data-stu-id="d9e0d-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9e0d-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d9e0d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d9e0d-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d9e0d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9e0d-107">特性</span><span class="sxs-lookup"><span data-stu-id="d9e0d-107">Attributes</span></span>  
 <span data-ttu-id="d9e0d-108">无。</span><span class="sxs-lookup"><span data-stu-id="d9e0d-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d9e0d-109">子元素</span><span class="sxs-lookup"><span data-stu-id="d9e0d-109">Child Elements</span></span>  
  
|<span data-ttu-id="d9e0d-110">元素</span><span class="sxs-lookup"><span data-stu-id="d9e0d-110">Element</span></span>|<span data-ttu-id="d9e0d-111">说明</span><span class="sxs-lookup"><span data-stu-id="d9e0d-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviorExtensions>](behaviorextensions.md)|<span data-ttu-id="d9e0d-112">本节包含子元素，这些子元素指定使用户可以自定义服务或终结点行为的行为扩展。</span><span class="sxs-lookup"><span data-stu-id="d9e0d-112">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[\<bindingElementExtensions>](bindingelementextensions.md)|<span data-ttu-id="d9e0d-113">本节为使用计算机或应用程序配置文件中的自定义绑定元素提供支持。</span><span class="sxs-lookup"><span data-stu-id="d9e0d-113">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[\<bindingExtensions>](bindingextensions.md)|<span data-ttu-id="d9e0d-114">本节包含子元素，这些子元素指定使用户可以自定义绑定的绑定扩展。</span><span class="sxs-lookup"><span data-stu-id="d9e0d-114">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[\<endpointExtensions>](endpointextensions.md)|<span data-ttu-id="d9e0d-115">本节包含元注册标准终结点的子元素。</span><span class="sxs-lookup"><span data-stu-id="d9e0d-115">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9e0d-116">父元素</span><span class="sxs-lookup"><span data-stu-id="d9e0d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d9e0d-117">元素</span><span class="sxs-lookup"><span data-stu-id="d9e0d-117">Element</span></span>|<span data-ttu-id="d9e0d-118">说明</span><span class="sxs-lookup"><span data-stu-id="d9e0d-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9e0d-119">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d9e0d-119">system.ServiceModel</span></span>|<span data-ttu-id="d9e0d-120">所有 WCF 配置元素的根元素。</span><span class="sxs-lookup"><span data-stu-id="d9e0d-120">The root element of all WCF configuration elements.</span></span>|
