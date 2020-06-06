---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4ef5890d52c3f2af42322f023b9a2a23cb583035
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855064"
---
# \<policyImporter>
<span data-ttu-id="d4bf2-101">指定一个策略导入程序，用于控制有关绑定的自定义策略断言的导入。</span><span class="sxs-lookup"><span data-stu-id="d4bf2-101">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="d4bf2-102">语法</span><span class="sxs-lookup"><span data-stu-id="d4bf2-102">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4bf2-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d4bf2-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d4bf2-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d4bf2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4bf2-105">特性</span><span class="sxs-lookup"><span data-stu-id="d4bf2-105">Attributes</span></span>  
  
|<span data-ttu-id="d4bf2-106">属性</span><span class="sxs-lookup"><span data-stu-id="d4bf2-106">Attribute</span></span>|<span data-ttu-id="d4bf2-107">说明</span><span class="sxs-lookup"><span data-stu-id="d4bf2-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="d4bf2-108">此元素的类型。</span><span class="sxs-lookup"><span data-stu-id="d4bf2-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4bf2-109">子元素</span><span class="sxs-lookup"><span data-stu-id="d4bf2-109">Child Elements</span></span>  
 <span data-ttu-id="d4bf2-110">无</span><span class="sxs-lookup"><span data-stu-id="d4bf2-110">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4bf2-111">父元素</span><span class="sxs-lookup"><span data-stu-id="d4bf2-111">Parent Elements</span></span>  
  
|<span data-ttu-id="d4bf2-112">元素</span><span class="sxs-lookup"><span data-stu-id="d4bf2-112">Element</span></span>|<span data-ttu-id="d4bf2-113">描述</span><span class="sxs-lookup"><span data-stu-id="d4bf2-113">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="d4bf2-114">指定用于控制有关绑定的自定义策略断言的导入的所有策略导入程序。</span><span class="sxs-lookup"><span data-stu-id="d4bf2-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4bf2-115">注解</span><span class="sxs-lookup"><span data-stu-id="d4bf2-115">Remarks</span></span>  
 <span data-ttu-id="d4bf2-116">策略导入程序用于搜索有关绑定功能的自定义策略断言，并附加一个实现断言所需功能的自定义绑定元素。</span><span class="sxs-lookup"><span data-stu-id="d4bf2-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4bf2-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d4bf2-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="d4bf2-118">WCF 客户端配置</span><span class="sxs-lookup"><span data-stu-id="d4bf2-118">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="d4bf2-119">客户端</span><span class="sxs-lookup"><span data-stu-id="d4bf2-119">Clients</span></span>](../../../wcf/feature-details/clients.md)
