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
# <a name="schemaimporterextensions-element"></a>\<schemaImporterExtensions> 元素
包含将 XSD 类型映射到 .NET Framework 类型时 <xref:System.Xml.Serialization.XmlSchemaImporter> 所用的类型。 有关配置文件的详细信息，请参阅[配置文件架构](../../../docs/framework/configure-apps/file-schema/index.md)。  
  
## <a name="syntax"></a>语法  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<schemaImporterExtensions> 的 \<add> 元素](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|添加 <xref:System.Xml.Serialization.XmlSchemaImporter> 用来创建映射的类型。|  
  
## <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<system.xml.serialization> 元素](../../../docs/standard/serialization/system-xml-serialization-element.md)|用于控制 XML 序列化的顶级元素。|  
  
## <a name="example"></a>示例  
 下面的代码示例演示如何添加将 XSD 类型映射到 .NET Framework 类型时 <xref:System.Xml.Serialization.XmlSchemaImporter> 所用的类型。  
  
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
  
## <a name="see-also"></a>请参阅

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [配置文件架构](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization> 元素](../../../docs/standard/serialization/datetimeserialization-element.md)
- [\<schemaImporterExtensions> 的 \<add> 元素](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [\<system.xml.serialization> 元素](../../../docs/standard/serialization/system-xml-serialization-element.md)
