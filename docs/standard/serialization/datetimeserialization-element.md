---
title: <dateTimeSerialization> 元素
description: 本文介绍 <dateTimeSerialization> 元素，该元素可确定 DateTime 对象的序列化模式。
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 652a88e25f59cd905e47ef71351e47e67f375286
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375828"
---
# <a name="datetimeserialization-element"></a><span data-ttu-id="8f306-103">\<dateTimeSerialization> 元素</span><span class="sxs-lookup"><span data-stu-id="8f306-103">\<dateTimeSerialization> Element</span></span>
<span data-ttu-id="8f306-104">确定 <xref:System.DateTime> 对象的序列化模式。</span><span class="sxs-lookup"><span data-stu-id="8f306-104">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="8f306-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8f306-105">\<configuration></span></span>  
<span data-ttu-id="8f306-106">\<dateTimeSerialization></span><span class="sxs-lookup"><span data-stu-id="8f306-106">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f306-107">语法</span><span class="sxs-lookup"><span data-stu-id="8f306-107">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f306-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="8f306-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8f306-109">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8f306-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f306-110">特性</span><span class="sxs-lookup"><span data-stu-id="8f306-110">Attributes</span></span>  
  
|<span data-ttu-id="8f306-111">特性</span><span class="sxs-lookup"><span data-stu-id="8f306-111">Attributes</span></span>|<span data-ttu-id="8f306-112">描述</span><span class="sxs-lookup"><span data-stu-id="8f306-112">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="8f306-113">可选。</span><span class="sxs-lookup"><span data-stu-id="8f306-113">Optional.</span></span> <span data-ttu-id="8f306-114">指定序列化模式。</span><span class="sxs-lookup"><span data-stu-id="8f306-114">Specifies the serialization mode.</span></span> <span data-ttu-id="8f306-115">设置为 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> 值之一。</span><span class="sxs-lookup"><span data-stu-id="8f306-115">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="8f306-116">默认值为 RoundTrip。</span><span class="sxs-lookup"><span data-stu-id="8f306-116">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f306-117">子元素</span><span class="sxs-lookup"><span data-stu-id="8f306-117">Child Elements</span></span>  
 <span data-ttu-id="8f306-118">无。</span><span class="sxs-lookup"><span data-stu-id="8f306-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f306-119">父元素</span><span class="sxs-lookup"><span data-stu-id="8f306-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8f306-120">元素</span><span class="sxs-lookup"><span data-stu-id="8f306-120">Element</span></span>|<span data-ttu-id="8f306-121">描述</span><span class="sxs-lookup"><span data-stu-id="8f306-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f306-122">system.xml.serialization</span><span class="sxs-lookup"><span data-stu-id="8f306-122">system.xml.serialization</span></span>|<span data-ttu-id="8f306-123">用于控制 XML 序列化的顶级元素。</span><span class="sxs-lookup"><span data-stu-id="8f306-123">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f306-124">备注</span><span class="sxs-lookup"><span data-stu-id="8f306-124">Remarks</span></span>  
 <span data-ttu-id="8f306-125">在 .NET Framework 1.0、1.1、2.0 以及更高版本中，将此属性设置为 Local 时，<xref:System.DateTime> 对象始终设置为本地时间格式。</span><span class="sxs-lookup"><span data-stu-id="8f306-125">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="8f306-126">即，序列化的数据中总是包含本地时区信息。</span><span class="sxs-lookup"><span data-stu-id="8f306-126">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="8f306-127">将此属性设置为 Local 可确保与较早版本的 .NET Framework 兼容。</span><span class="sxs-lookup"><span data-stu-id="8f306-127">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="8f306-128">在 .NET Framework 2.0 及更高版本中，将此属性设置为 Roundtrip 时，系统会检查 <xref:System.DateTime> 对象以确定这些对象位于本地时区、UTC 时区还是未指定的时区中。</span><span class="sxs-lookup"><span data-stu-id="8f306-128">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="8f306-129">随后会序列化 <xref:System.DateTime> 对象并保留该信息。</span><span class="sxs-lookup"><span data-stu-id="8f306-129">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="8f306-130">这是默认行为，建议为所有不与 Framework 的较早版本通信的新应用程序使用此行为。</span><span class="sxs-lookup"><span data-stu-id="8f306-130">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f306-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="8f306-131">See also</span></span>

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="8f306-132">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="8f306-132">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="8f306-133">\<schemaImporterExtensions> 元素</span><span class="sxs-lookup"><span data-stu-id="8f306-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="8f306-134">\<schemaImporterExtensions> 的 \<add> 元素</span><span class="sxs-lookup"><span data-stu-id="8f306-134">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [<span data-ttu-id="8f306-135">\<system.xml.serialization> 元素</span><span class="sxs-lookup"><span data-stu-id="8f306-135">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
