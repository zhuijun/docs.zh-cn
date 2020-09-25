---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: aad0bbde964644448fbafc6c628c00c9faaad497
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204757"
---
# \<metadata>

<span data-ttu-id="99899-101">指定可以处理服务元数据的方式。</span><span class="sxs-lookup"><span data-stu-id="99899-101">Specifies how service metadata can be processed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**  
  
## <a name="syntax"></a><span data-ttu-id="99899-102">语法</span><span class="sxs-lookup"><span data-stu-id="99899-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <client>
    <metadata>
      <policyImporters>
        <policyImporter type="string" />
      </policyImporters>
      <wsdlImporters>
        <wsdlImporter type="string" />
      </wsdlImporters>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99899-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="99899-103">Attributes and Elements</span></span>  

 <span data-ttu-id="99899-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="99899-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99899-105">特性</span><span class="sxs-lookup"><span data-stu-id="99899-105">Attributes</span></span>  

 <span data-ttu-id="99899-106">无。</span><span class="sxs-lookup"><span data-stu-id="99899-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="99899-107">子元素</span><span class="sxs-lookup"><span data-stu-id="99899-107">Child Elements</span></span>  
  
|<span data-ttu-id="99899-108">元素</span><span class="sxs-lookup"><span data-stu-id="99899-108">Element</span></span>|<span data-ttu-id="99899-109">描述</span><span class="sxs-lookup"><span data-stu-id="99899-109">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="99899-110">指定用于控制有关绑定的自定义策略断言的导入的所有策略导入程序。</span><span class="sxs-lookup"><span data-stu-id="99899-110">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="99899-111">策略导入程序用于搜索有关绑定功能的自定义策略断言，并附加一个实现断言所需功能的自定义绑定元素。</span><span class="sxs-lookup"><span data-stu-id="99899-111">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="99899-112">指定可导入带有 WS-Policy 附件的 Web 服务描述语言 (WSDL) 1.1 元数据的所有 WSDL 导入程序。</span><span class="sxs-lookup"><span data-stu-id="99899-112">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="99899-113">WSDL 导入程序可用于导入元数据并将这些信息转换为各种表示协定和终结点信息的类。</span><span class="sxs-lookup"><span data-stu-id="99899-113">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="99899-114">它可以有选择地导入协定和终结点信息以及公开任何导入错误的属性，并接受与导入和转换过程相关的类型信息。</span><span class="sxs-lookup"><span data-stu-id="99899-114">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="99899-115">它还支持导入某些绑定信息和属性，这些信息和属性提供了对任何策略文档、WSDL 文档、WSDL 扩展和 XML 架构文档的访问。</span><span class="sxs-lookup"><span data-stu-id="99899-115">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99899-116">父元素</span><span class="sxs-lookup"><span data-stu-id="99899-116">Parent Elements</span></span>  
  
|<span data-ttu-id="99899-117">元素</span><span class="sxs-lookup"><span data-stu-id="99899-117">Element</span></span>|<span data-ttu-id="99899-118">描述</span><span class="sxs-lookup"><span data-stu-id="99899-118">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="99899-119">client 节定义客户端可以连接的终结点的列表。</span><span class="sxs-lookup"><span data-stu-id="99899-119">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99899-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="99899-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="99899-121">WCF 客户端配置</span><span class="sxs-lookup"><span data-stu-id="99899-121">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="99899-122">客户端</span><span class="sxs-lookup"><span data-stu-id="99899-122">Clients</span></span>](../../../wcf/feature-details/clients.md)
