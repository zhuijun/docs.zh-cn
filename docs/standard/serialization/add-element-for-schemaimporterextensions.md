---
title: <schemaImporterExtensions> 的 <add> 元素
description: <add> 元素可添加 XmlSchemaImporter 在将 XSD 类型映射到 .NET Framework 类型时所用的类型。
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 401d1ba9cc2f97e93d7851f96f73b552e6ed6356
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378480"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="6b0d5-103">\<schemaImporterExtensions> 的 \<add> 元素</span><span class="sxs-lookup"><span data-stu-id="6b0d5-103">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="6b0d5-104">添加将 XSD 类型映射到 .NET Framework 类型时 <xref:System.Xml.Serialization.XmlSchemaImporter> 所用的类型。</span><span class="sxs-lookup"><span data-stu-id="6b0d5-104">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="6b0d5-105">有关配置文件的详细信息，请参阅[配置文件架构](../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="6b0d5-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="6b0d5-106">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6b0d5-106">\<configuration></span></span>  
<span data-ttu-id="6b0d5-107">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="6b0d5-107">\<system.xml.serialization></span></span>  
<span data-ttu-id="6b0d5-108">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="6b0d5-108">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="6b0d5-109">\<add></span><span class="sxs-lookup"><span data-stu-id="6b0d5-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b0d5-110">语法</span><span class="sxs-lookup"><span data-stu-id="6b0d5-110">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b0d5-111">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6b0d5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6b0d5-112">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6b0d5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b0d5-113">特性</span><span class="sxs-lookup"><span data-stu-id="6b0d5-113">Attributes</span></span>  
  
|<span data-ttu-id="6b0d5-114">特性</span><span class="sxs-lookup"><span data-stu-id="6b0d5-114">Attribute</span></span>|<span data-ttu-id="6b0d5-115">描述</span><span class="sxs-lookup"><span data-stu-id="6b0d5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b0d5-116">**name**</span><span class="sxs-lookup"><span data-stu-id="6b0d5-116">**name**</span></span>|<span data-ttu-id="6b0d5-117">用于查找实例的简单名称。</span><span class="sxs-lookup"><span data-stu-id="6b0d5-117">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="6b0d5-118">**type**</span><span class="sxs-lookup"><span data-stu-id="6b0d5-118">**type**</span></span>|<span data-ttu-id="6b0d5-119">必需。</span><span class="sxs-lookup"><span data-stu-id="6b0d5-119">Required.</span></span> <span data-ttu-id="6b0d5-120">指定要添加的架构扩展类。</span><span class="sxs-lookup"><span data-stu-id="6b0d5-120">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="6b0d5-121">type 特性值必须位于一行上，并且包含完全限定的类型名称。</span><span class="sxs-lookup"><span data-stu-id="6b0d5-121">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="6b0d5-122">当程序集放置在全局程序集缓存 (GAC) 中时，该特性值还必须包括已签名程序集的版本、区域性和公钥标记。</span><span class="sxs-lookup"><span data-stu-id="6b0d5-122">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b0d5-123">子元素</span><span class="sxs-lookup"><span data-stu-id="6b0d5-123">Child Elements</span></span>  
 <span data-ttu-id="6b0d5-124">无。</span><span class="sxs-lookup"><span data-stu-id="6b0d5-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b0d5-125">父元素</span><span class="sxs-lookup"><span data-stu-id="6b0d5-125">Parent Elements</span></span>  
  
|<span data-ttu-id="6b0d5-126">元素</span><span class="sxs-lookup"><span data-stu-id="6b0d5-126">Element</span></span>|<span data-ttu-id="6b0d5-127">描述</span><span class="sxs-lookup"><span data-stu-id="6b0d5-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b0d5-128">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="6b0d5-128">\<schemaImporterExtensions></span></span>|<span data-ttu-id="6b0d5-129">包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 所使用的类型。</span><span class="sxs-lookup"><span data-stu-id="6b0d5-129">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6b0d5-130">示例</span><span class="sxs-lookup"><span data-stu-id="6b0d5-130">Example</span></span>  
 <span data-ttu-id="6b0d5-131">下面的代码示例添加 XmlSchemaImporter 可以在映射类型时使用的扩展类型。</span><span class="sxs-lookup"><span data-stu-id="6b0d5-131">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <schemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a" />
    </schemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b0d5-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="6b0d5-132">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="6b0d5-133">\<system.xml.serialization> 元素</span><span class="sxs-lookup"><span data-stu-id="6b0d5-133">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="6b0d5-134">\<schemaImporterExtensions> 元素</span><span class="sxs-lookup"><span data-stu-id="6b0d5-134">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
