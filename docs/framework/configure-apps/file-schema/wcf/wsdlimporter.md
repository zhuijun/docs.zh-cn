---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 82704aa40b508f1b1e2237c9768a7b7599c5c87e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158586"
---
# \<wsdlImporter>

<span data-ttu-id="7ce45-101">指定可导入带有 WS-Policy 附件的 Web 服务描述语言 (WSDL) 1.1 元数据的所有 WSDL 导入程序。</span><span class="sxs-lookup"><span data-stu-id="7ce45-101">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsdlImporters>**](wsdlimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsdlImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="7ce45-102">语法</span><span class="sxs-lookup"><span data-stu-id="7ce45-102">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ce45-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="7ce45-103">Attributes and Elements</span></span>  

 <span data-ttu-id="7ce45-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7ce45-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ce45-105">特性</span><span class="sxs-lookup"><span data-stu-id="7ce45-105">Attributes</span></span>  
  
|<span data-ttu-id="7ce45-106">属性</span><span class="sxs-lookup"><span data-stu-id="7ce45-106">Attribute</span></span>|<span data-ttu-id="7ce45-107">描述</span><span class="sxs-lookup"><span data-stu-id="7ce45-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="7ce45-108">此元素的类型。</span><span class="sxs-lookup"><span data-stu-id="7ce45-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ce45-109">子元素</span><span class="sxs-lookup"><span data-stu-id="7ce45-109">Child Elements</span></span>  

 <span data-ttu-id="7ce45-110">无。</span><span class="sxs-lookup"><span data-stu-id="7ce45-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ce45-111">父元素</span><span class="sxs-lookup"><span data-stu-id="7ce45-111">Parent Elements</span></span>  
  
|<span data-ttu-id="7ce45-112">元素</span><span class="sxs-lookup"><span data-stu-id="7ce45-112">Element</span></span>|<span data-ttu-id="7ce45-113">描述</span><span class="sxs-lookup"><span data-stu-id="7ce45-113">Description</span></span>|  
|-------------|-----------------|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="7ce45-114">指定可导入带有 WS-Policy 附件的 Web 服务描述语言 (WSDL) 1.1 元数据的所有 WSDL 导入程序。</span><span class="sxs-lookup"><span data-stu-id="7ce45-114">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ce45-115">备注</span><span class="sxs-lookup"><span data-stu-id="7ce45-115">Remarks</span></span>  

 <span data-ttu-id="7ce45-116">WSDL 导入程序可用于导入元数据并将这些信息转换为各种表示协定和终结点信息的类。</span><span class="sxs-lookup"><span data-stu-id="7ce45-116">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="7ce45-117">它可以有选择地导入协定和终结点信息以及公开任何导入错误的属性，并接受与导入和转换过程相关的类型信息。</span><span class="sxs-lookup"><span data-stu-id="7ce45-117">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="7ce45-118">它还支持导入某些绑定信息和属性，这些信息和属性提供了对任何策略文档、WSDL 文档、WSDL 扩展和 XML 架构文档的访问。</span><span class="sxs-lookup"><span data-stu-id="7ce45-118">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ce45-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="7ce45-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="7ce45-120">WCF 客户端配置</span><span class="sxs-lookup"><span data-stu-id="7ce45-120">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="7ce45-121">客户端</span><span class="sxs-lookup"><span data-stu-id="7ce45-121">Clients</span></span>](../../../wcf/feature-details/clients.md)
