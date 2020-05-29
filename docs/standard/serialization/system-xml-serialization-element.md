---
title: <system.xml.serialization> 元素
description: 本文介绍 <system.xml.serialization> 元素，该元素是用于控制 XML 序列化的顶级元素。
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 1e66220004d561f937d03c506e6f30db4ccc635b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380116"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="f8731-103">\<system.xml.serialization> 元素</span><span class="sxs-lookup"><span data-stu-id="f8731-103">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="f8731-104">用于控制 XML 序列化的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="f8731-104">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="f8731-105">有关配置文件的详细信息，请参阅[配置文件架构](../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f8731-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="f8731-106">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f8731-106">\<configuration></span></span>\
<span data-ttu-id="f8731-107">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="f8731-107">\<system.xml.serialization></span></span>

## <a name="syntax"></a><span data-ttu-id="f8731-108">语法</span><span class="sxs-lookup"><span data-stu-id="f8731-108">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f8731-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f8731-109">Attributes and Elements</span></span>

<span data-ttu-id="f8731-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f8731-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f8731-111">特性</span><span class="sxs-lookup"><span data-stu-id="f8731-111">Attributes</span></span>

<span data-ttu-id="f8731-112">无。</span><span class="sxs-lookup"><span data-stu-id="f8731-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f8731-113">子元素</span><span class="sxs-lookup"><span data-stu-id="f8731-113">Child Elements</span></span>

|<span data-ttu-id="f8731-114">元素</span><span class="sxs-lookup"><span data-stu-id="f8731-114">Element</span></span>|<span data-ttu-id="f8731-115">描述</span><span class="sxs-lookup"><span data-stu-id="f8731-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8731-116">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="f8731-116">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="f8731-117">确定 <xref:System.DateTime> 对象的序列化模式。</span><span class="sxs-lookup"><span data-stu-id="f8731-117">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="f8731-118">\<schemaImporterExtensions> 元素</span><span class="sxs-lookup"><span data-stu-id="f8731-118">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="f8731-119">包含将 XSD 类型映射到 .NET Framework 类型时 <xref:System.Xml.Serialization.XmlSchemaImporter> 所用的类型。</span><span class="sxs-lookup"><span data-stu-id="f8731-119">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f8731-120">父元素</span><span class="sxs-lookup"><span data-stu-id="f8731-120">Parent Elements</span></span>

|<span data-ttu-id="f8731-121">元素</span><span class="sxs-lookup"><span data-stu-id="f8731-121">Element</span></span>|<span data-ttu-id="f8731-122">描述</span><span class="sxs-lookup"><span data-stu-id="f8731-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f8731-123">\<configuration> 元素</span><span class="sxs-lookup"><span data-stu-id="f8731-123">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="f8731-124">公共语言运行库和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="f8731-124">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="f8731-125">示例</span><span class="sxs-lookup"><span data-stu-id="f8731-125">Example</span></span>

<span data-ttu-id="f8731-126">下面的代码示例演示如何指定 <xref:System.DateTime> 对象的序列化模式，以及将 XSD 类型映射到 .NET Framework 类型时 <xref:System.Xml.Serialization.XmlSchemaImporter> 所用的其他类型。</span><span class="sxs-lookup"><span data-stu-id="f8731-126">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

```xml
<system.xml.serialization>
    <xmlSerializer checkDeserializeAdvances="false" />
    <dateTimeSerialization mode = "Local" />
    <schemaImporterExtensions>
        <add
        name = "MobileCapabilities"
        type = "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f6f11d40a3a" />
    </schemaImporterExtensions>
</system.xml.serialization>
```

## <a name="see-also"></a><span data-ttu-id="f8731-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="f8731-127">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="f8731-128">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="f8731-128">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f8731-129">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="f8731-129">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="f8731-130">\<schemaImporterExtensions> 元素</span><span class="sxs-lookup"><span data-stu-id="f8731-130">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="f8731-131">\<schemaImporterExtensions> 的 \<add> 元素</span><span class="sxs-lookup"><span data-stu-id="f8731-131">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
