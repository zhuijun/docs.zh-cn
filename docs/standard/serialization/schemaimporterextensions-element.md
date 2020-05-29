---
title: <schemaImporterExtensions> 元素
description: <schemaImporterExtensions> 元素包含将 XSD 类型映射到 .NET Framework 类型时 XmlSchemaImporter 所用的类型。
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 5b9820ccdf2c75bed9beda72358c4c4d82ff9ff7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379792"
---
# <a name="schemaimporterextensions-element"></a><span data-ttu-id="4ef00-103">\<schemaImporterExtensions> 元素</span><span class="sxs-lookup"><span data-stu-id="4ef00-103">\<schemaImporterExtensions> Element</span></span>
<span data-ttu-id="4ef00-104">包含将 XSD 类型映射到 .NET Framework 类型时 <xref:System.Xml.Serialization.XmlSchemaImporter> 所用的类型。</span><span class="sxs-lookup"><span data-stu-id="4ef00-104">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span> <span data-ttu-id="4ef00-105">有关配置文件的详细信息，请参阅[配置文件架构](../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4ef00-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ef00-106">语法</span><span class="sxs-lookup"><span data-stu-id="4ef00-106">Syntax</span></span>  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a><span data-ttu-id="4ef00-107">子元素</span><span class="sxs-lookup"><span data-stu-id="4ef00-107">Child Elements</span></span>  
  
|<span data-ttu-id="4ef00-108">元素</span><span class="sxs-lookup"><span data-stu-id="4ef00-108">Element</span></span>|<span data-ttu-id="4ef00-109">描述</span><span class="sxs-lookup"><span data-stu-id="4ef00-109">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ef00-110">\<schemaImporterExtensions> 的 \<add> 元素</span><span class="sxs-lookup"><span data-stu-id="4ef00-110">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|<span data-ttu-id="4ef00-111">添加 <xref:System.Xml.Serialization.XmlSchemaImporter> 用来创建映射的类型。</span><span class="sxs-lookup"><span data-stu-id="4ef00-111">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> to create mappings.</span></span>|  
  
## <a name="parent-elements"></a><span data-ttu-id="4ef00-112">父元素</span><span class="sxs-lookup"><span data-stu-id="4ef00-112">Parent Elements</span></span>  
  
|<span data-ttu-id="4ef00-113">元素</span><span class="sxs-lookup"><span data-stu-id="4ef00-113">Element</span></span>|<span data-ttu-id="4ef00-114">描述</span><span class="sxs-lookup"><span data-stu-id="4ef00-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ef00-115">\<system.xml.serialization> 元素</span><span class="sxs-lookup"><span data-stu-id="4ef00-115">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="4ef00-116">用于控制 XML 序列化的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="4ef00-116">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4ef00-117">示例</span><span class="sxs-lookup"><span data-stu-id="4ef00-117">Example</span></span>  
 <span data-ttu-id="4ef00-118">下面的代码示例演示如何添加将 XSD 类型映射到 .NET Framework 类型时 <xref:System.Xml.Serialization.XmlSchemaImporter> 所用的类型。</span><span class="sxs-lookup"><span data-stu-id="4ef00-118">The following code example illustrates how to add types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =
        "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.xml.serialization>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ef00-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="4ef00-119">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="4ef00-120">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="4ef00-120">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="4ef00-121">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="4ef00-121">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="4ef00-122">\<schemaImporterExtensions> 的 \<add> 元素</span><span class="sxs-lookup"><span data-stu-id="4ef00-122">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="4ef00-123">\<system.xml.serialization> 元素</span><span class="sxs-lookup"><span data-stu-id="4ef00-123">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
