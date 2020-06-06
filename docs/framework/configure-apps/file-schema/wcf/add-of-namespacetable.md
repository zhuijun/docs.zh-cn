---
title: <add> 的 <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 3b3b4a1584b37601269368ee0e4e973626ddf9cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850393"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="32a38-102">\<add> 的 \<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="32a38-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="32a38-103">表示一个配置元素，此元素包含随后可在 XPath 筛选器中用于路由的前缀映射的命名空间。</span><span class="sxs-lookup"><span data-stu-id="32a38-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namespaceTable>**](namespacetable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="32a38-104">语法</span><span class="sxs-lookup"><span data-stu-id="32a38-104">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32a38-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="32a38-105">Attributes and Elements</span></span>  
 <span data-ttu-id="32a38-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="32a38-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32a38-107">特性</span><span class="sxs-lookup"><span data-stu-id="32a38-107">Attributes</span></span>  
  
|<span data-ttu-id="32a38-108">属性</span><span class="sxs-lookup"><span data-stu-id="32a38-108">Attribute</span></span>|<span data-ttu-id="32a38-109">说明</span><span class="sxs-lookup"><span data-stu-id="32a38-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32a38-110">namespace</span><span class="sxs-lookup"><span data-stu-id="32a38-110">namespace</span></span>|<span data-ttu-id="32a38-111">一个包含命名空间的字符串。</span><span class="sxs-lookup"><span data-stu-id="32a38-111">A string containing the namespace.</span></span>|  
|<span data-ttu-id="32a38-112">前缀</span><span class="sxs-lookup"><span data-stu-id="32a38-112">prefix</span></span>|<span data-ttu-id="32a38-113">一个包含此命名空间的前缀的字符串。</span><span class="sxs-lookup"><span data-stu-id="32a38-113">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32a38-114">子元素</span><span class="sxs-lookup"><span data-stu-id="32a38-114">Child Elements</span></span>  
 <span data-ttu-id="32a38-115">无。</span><span class="sxs-lookup"><span data-stu-id="32a38-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32a38-116">父元素</span><span class="sxs-lookup"><span data-stu-id="32a38-116">Parent Elements</span></span>  
  
|<span data-ttu-id="32a38-117">元素</span><span class="sxs-lookup"><span data-stu-id="32a38-117">Element</span></span>|<span data-ttu-id="32a38-118">描述</span><span class="sxs-lookup"><span data-stu-id="32a38-118">Description</span></span>|  
|-------------|-----------------|  
|[\<namespaceTable>](namespacetable.md)|<span data-ttu-id="32a38-119">表示用于定义一组元素的配置节，这些元素包含随后可在 XPath 筛选器中用于路由的前缀映射的命名空间。</span><span class="sxs-lookup"><span data-stu-id="32a38-119">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32a38-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32a38-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
