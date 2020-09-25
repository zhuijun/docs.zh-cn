---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 72778ce0070d853f8b081a4889ead9524bafd0e8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181344"
---
# \<policyImporter>

<span data-ttu-id="c14ef-101">指定一个策略导入程序，用于控制有关绑定的自定义策略断言的导入。</span><span class="sxs-lookup"><span data-stu-id="c14ef-101">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="c14ef-102">语法</span><span class="sxs-lookup"><span data-stu-id="c14ef-102">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c14ef-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c14ef-103">Attributes and Elements</span></span>  

 <span data-ttu-id="c14ef-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c14ef-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c14ef-105">特性</span><span class="sxs-lookup"><span data-stu-id="c14ef-105">Attributes</span></span>  
  
|<span data-ttu-id="c14ef-106">属性</span><span class="sxs-lookup"><span data-stu-id="c14ef-106">Attribute</span></span>|<span data-ttu-id="c14ef-107">描述</span><span class="sxs-lookup"><span data-stu-id="c14ef-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="c14ef-108">此元素的类型。</span><span class="sxs-lookup"><span data-stu-id="c14ef-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c14ef-109">子元素</span><span class="sxs-lookup"><span data-stu-id="c14ef-109">Child Elements</span></span>  

 <span data-ttu-id="c14ef-110">无</span><span class="sxs-lookup"><span data-stu-id="c14ef-110">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c14ef-111">父元素</span><span class="sxs-lookup"><span data-stu-id="c14ef-111">Parent Elements</span></span>  
  
|<span data-ttu-id="c14ef-112">元素</span><span class="sxs-lookup"><span data-stu-id="c14ef-112">Element</span></span>|<span data-ttu-id="c14ef-113">描述</span><span class="sxs-lookup"><span data-stu-id="c14ef-113">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="c14ef-114">指定用于控制有关绑定的自定义策略断言的导入的所有策略导入程序。</span><span class="sxs-lookup"><span data-stu-id="c14ef-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c14ef-115">备注</span><span class="sxs-lookup"><span data-stu-id="c14ef-115">Remarks</span></span>  

 <span data-ttu-id="c14ef-116">策略导入程序用于搜索有关绑定功能的自定义策略断言，并附加一个实现断言所需功能的自定义绑定元素。</span><span class="sxs-lookup"><span data-stu-id="c14ef-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c14ef-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="c14ef-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="c14ef-118">WCF 客户端配置</span><span class="sxs-lookup"><span data-stu-id="c14ef-118">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="c14ef-119">客户端</span><span class="sxs-lookup"><span data-stu-id="c14ef-119">Clients</span></span>](../../../wcf/feature-details/clients.md)
