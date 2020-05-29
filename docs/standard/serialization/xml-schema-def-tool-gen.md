---
title: 如何：使用 XML 架构定义工具生成类和 XML 架构文档
description: 了解如何使用 XML 架构定义工具来生成描述类的 XML 架构，或生成 XML 架构定义的类。
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 21ce4ad846e21a328ba199f6253bd259be9d932b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379523"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="a608d-103">如何：使用 XML 架构定义工具生成类和 XML 架构文档</span><span class="sxs-lookup"><span data-stu-id="a608d-103">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>
<span data-ttu-id="a608d-104">使用 XML 架构定义工具 (Xsd.exe) 可以生成描述类的 XML 架构，也可以生成 XML 架构定义的类。</span><span class="sxs-lookup"><span data-stu-id="a608d-104">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="a608d-105">下面的过程说明如何执行这两种操作。</span><span class="sxs-lookup"><span data-stu-id="a608d-105">The following procedures show how to perform these operations.</span></span>

<span data-ttu-id="a608d-106">XML 架构定义工具 (Xsd.exe) 通常可在以下路径中找到：</span><span class="sxs-lookup"><span data-stu-id="a608d-106">The XML Schema Definition tool (Xsd.exe) usually can be found in the following path:</span></span>\
<span data-ttu-id="a608d-107">C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{版本}\\bin\\NETFX {版本} Tools\\</span><span class="sxs-lookup"><span data-stu-id="a608d-107">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span></span>

### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="a608d-108">生成符合特定架构的类</span><span class="sxs-lookup"><span data-stu-id="a608d-108">To generate classes that conform to a specific schema</span></span>  
  
1. <span data-ttu-id="a608d-109">打开命令提示。</span><span class="sxs-lookup"><span data-stu-id="a608d-109">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="a608d-110">将 XML 架构作为参数传递给 XML 架构定义工具，该工具将创建与 XML 架构精确匹配的一组类，例如：</span><span class="sxs-lookup"><span data-stu-id="a608d-110">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="a608d-111">该工具只能处理引用万维网联合会 2001 年 3 月 16 日的 XML 规范的架构。</span><span class="sxs-lookup"><span data-stu-id="a608d-111">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="a608d-112">换句话说，XML 架构命名空间必须是“http://www.w3.org/2001/XMLSchema”，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="a608d-112">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema" />  
    ```  
  
3. <span data-ttu-id="a608d-113">必要时用方法、属性或字段修改类。</span><span class="sxs-lookup"><span data-stu-id="a608d-113">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="a608d-114">有关利用特性修改类的详细信息，请参阅[使用特性控制 XML 序列化](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)和[控制编码的 SOAP 序列化的特性](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="a608d-114">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="a608d-115">当序列化一个或多个类的实例后，检查生成的 XML 流的架构通常非常有用。</span><span class="sxs-lookup"><span data-stu-id="a608d-115">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="a608d-116">例如，您可能发布架构以供其他人使用，或者可能将其与想达成一致的架构进行比较。</span><span class="sxs-lookup"><span data-stu-id="a608d-116">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="a608d-117">从一组类生成 XML 架构文档</span><span class="sxs-lookup"><span data-stu-id="a608d-117">To generate an XML Schema document from a set of classes</span></span>  
  
1. <span data-ttu-id="a608d-118">将一个或多个类编译成 DLL。</span><span class="sxs-lookup"><span data-stu-id="a608d-118">Compile the class or classes into a DLL.</span></span>  
  
2. <span data-ttu-id="a608d-119">打开命令提示。</span><span class="sxs-lookup"><span data-stu-id="a608d-119">Open a command prompt.</span></span>  
  
3. <span data-ttu-id="a608d-120">将 DLL 作为参数传递给 Xsd.exe，例如：</span><span class="sxs-lookup"><span data-stu-id="a608d-120">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="a608d-121">架构将被写入，以名称“schema0.xsd”开头。</span><span class="sxs-lookup"><span data-stu-id="a608d-121">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a608d-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="a608d-122">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="a608d-123">XML 架构定义工具和 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="a608d-123">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="a608d-124">XML 序列化简介</span><span class="sxs-lookup"><span data-stu-id="a608d-124">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="a608d-125">XML 架构定义工具 (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="a608d-125">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="a608d-126">如何：序列化对象</span><span class="sxs-lookup"><span data-stu-id="a608d-126">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="a608d-127">如何：反序列化对象</span><span class="sxs-lookup"><span data-stu-id="a608d-127">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
