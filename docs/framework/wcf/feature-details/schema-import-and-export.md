---
title: 架构导入和导出
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
ms.openlocfilehash: 942ade69d92d8a213f65a3a2e463b6924e2f986e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590210"
---
# <a name="schema-import-and-export"></a><span data-ttu-id="c7a21-102">架构导入和导出</span><span class="sxs-lookup"><span data-stu-id="c7a21-102">Schema Import and Export</span></span>
<span data-ttu-id="c7a21-103">Windows Communication Foundation （WCF）包含一个新的序列化引擎 <xref:System.Runtime.Serialization.DataContractSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="c7a21-103">Windows Communication Foundation (WCF) includes a new serialization engine, the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="c7a21-104">在 `DataContractSerializer` .NET Framework 对象和 XML （双向）之间进行转换。</span><span class="sxs-lookup"><span data-stu-id="c7a21-104">The `DataContractSerializer` translates between .NET Framework objects and XML (in both directions).</span></span> <span data-ttu-id="c7a21-105">除了序列化程序本身，WCF 还包括关联的架构导入和架构导出机制。</span><span class="sxs-lookup"><span data-stu-id="c7a21-105">In addition to the serializer itself, WCF includes associated schema import and schema export mechanisms.</span></span> <span data-ttu-id="c7a21-106">*架构*是序列化程序生成或反序列化程序可以访问的 XML 形状的正式、精确和计算机可读的说明。</span><span class="sxs-lookup"><span data-stu-id="c7a21-106">*Schema* is a formal, precise, and machine-readable description of the shape of XML that the serializer produces or that the deserializer can access.</span></span> <span data-ttu-id="c7a21-107">WCF 使用万维网联合会（W3C） XML 架构定义语言（XSD）作为其架构表示形式，这与许多第三方平台广泛互操作。</span><span class="sxs-lookup"><span data-stu-id="c7a21-107">WCF uses the World Wide Web Consortium (W3C) XML Schema definition language (XSD) as its schema representation, which is widely interoperable with numerous third-party platforms.</span></span>  
  
 <span data-ttu-id="c7a21-108">架构导入组件 <xref:System.Runtime.Serialization.XsdDataContractImporter> 使用 XSD 架构文档并生成 .NET Framework 类（通常是数据协定类），以便序列化的窗体与给定的架构相对应。</span><span class="sxs-lookup"><span data-stu-id="c7a21-108">The schema import component, <xref:System.Runtime.Serialization.XsdDataContractImporter>, takes an XSD schema document and generates .NET Framework classes (normally data contract classes) such that the serialized forms correspond to the given schema.</span></span>  
  
 <span data-ttu-id="c7a21-109">例如，以下架构片段：</span><span class="sxs-lookup"><span data-stu-id="c7a21-109">For example, the following schema fragment:</span></span>  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 <span data-ttu-id="c7a21-110">生成以下类型（略经简化以便于阅读）。</span><span class="sxs-lookup"><span data-stu-id="c7a21-110">generates the following type (simplified slightly for better readability).</span></span>  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 <span data-ttu-id="c7a21-111">请注意，生成的类型遵循几个数据协定最佳做法（请参阅[最佳做法：数据协定版本控制](../best-practices-data-contract-versioning.md)）：</span><span class="sxs-lookup"><span data-stu-id="c7a21-111">Note that the generated type follows several data contract best practices (found in [Best Practices: Data Contract Versioning](../best-practices-data-contract-versioning.md)):</span></span>  
  
- <span data-ttu-id="c7a21-112">此类型实现 <xref:System.Runtime.Serialization.IExtensibleDataObject> 接口。</span><span class="sxs-lookup"><span data-stu-id="c7a21-112">The type implements the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span> <span data-ttu-id="c7a21-113">有关详细信息，请参阅[向前兼容的数据协定](forward-compatible-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="c7a21-113">For more information, see [Forward-Compatible Data Contracts](forward-compatible-data-contracts.md).</span></span>  
  
- <span data-ttu-id="c7a21-114">数据成员作为封装私有字段的公共属性来实现。</span><span class="sxs-lookup"><span data-stu-id="c7a21-114">Data members are implemented as public properties that wrap private fields.</span></span>  
  
- <span data-ttu-id="c7a21-115">此类是一个分部类，不修改生成的代码就可以添加内容。</span><span class="sxs-lookup"><span data-stu-id="c7a21-115">The class is a partial class, and additions can be made without modifying generated code.</span></span>  
  
 <span data-ttu-id="c7a21-116"><xref:System.Runtime.Serialization.XsdDataContractExporter> 使您能够进行反向操作，使用可用 `DataContractSerializer` 进行序列化的类型并生成 XSD 架构文档。</span><span class="sxs-lookup"><span data-stu-id="c7a21-116">The <xref:System.Runtime.Serialization.XsdDataContractExporter> enables you to do the reverse—take types that are serializable with the `DataContractSerializer` and generate an XSD Schema document.</span></span>  
  
## <a name="fidelity-is-not-guaranteed"></a><span data-ttu-id="c7a21-117">不保证保真</span><span class="sxs-lookup"><span data-stu-id="c7a21-117">Fidelity Is Not Guaranteed</span></span>  
 <span data-ttu-id="c7a21-118">不保证进行往返行程的架构或类型完全保真。</span><span class="sxs-lookup"><span data-stu-id="c7a21-118">It is not guaranteed that schema or types make a round trip with total fidelity.</span></span> <span data-ttu-id="c7a21-119">（*往返*过程表示导入架构以创建一组类，并将结果导出为再次创建一个架构。）不能返回相同的架构。</span><span class="sxs-lookup"><span data-stu-id="c7a21-119">(A *round trip* means to import a schema to create a set of classes, and export the result to create a schema again.) The same schema may not be returned.</span></span> <span data-ttu-id="c7a21-120">反向过程也不保证保真。</span><span class="sxs-lookup"><span data-stu-id="c7a21-120">Reversing the process is also not guaranteed to preserve fidelity.</span></span> <span data-ttu-id="c7a21-121">（导出类型以生成其架构，然后重新导入此类型。</span><span class="sxs-lookup"><span data-stu-id="c7a21-121">(Export a type to generate its schema, and then import the type back.</span></span> <span data-ttu-id="c7a21-122">不太可能返回相同的类型。）</span><span class="sxs-lookup"><span data-stu-id="c7a21-122">It is unlikely the same type is returned.)</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="c7a21-123">支持的类型</span><span class="sxs-lookup"><span data-stu-id="c7a21-123">Supported Types</span></span>  
 <span data-ttu-id="c7a21-124">数据协定模型只支持有限的 WC3 架构子集。</span><span class="sxs-lookup"><span data-stu-id="c7a21-124">The data contract model supports only a limited subset of the WC3 schema.</span></span> <span data-ttu-id="c7a21-125">导入过程中任何不符合此子集的架构都将导致异常。</span><span class="sxs-lookup"><span data-stu-id="c7a21-125">Any schema that does not conform to this subset will cause an exception during the import process.</span></span> <span data-ttu-id="c7a21-126">例如，没有办法可以指定数据协定的数据成员应该作为 XML 属性进行序列化。</span><span class="sxs-lookup"><span data-stu-id="c7a21-126">For example, there is no way to specify that a data member of a data contract should be serialized as an XML attribute.</span></span> <span data-ttu-id="c7a21-127">这样，由于不能用正确的 XML 投影生成数据协定，需要使用 XML 属性的架构将不受支持，并且将在导入过程中导致异常。</span><span class="sxs-lookup"><span data-stu-id="c7a21-127">Thus, schemas that require the use of XML attributes are not supported and will cause exceptions during import, because it is impossible to generate a data contract with the correct XML projection.</span></span>  
  
 <span data-ttu-id="c7a21-128">例如，不能使用默认导入设置导入以下架构片段。</span><span class="sxs-lookup"><span data-stu-id="c7a21-128">For example, the following schema fragment cannot be imported using the default import settings.</span></span>  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 <span data-ttu-id="c7a21-129">有关详细信息，请参阅[数据协定架构参考](data-contract-schema-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="c7a21-129">For more information, see [Data Contract Schema Reference](data-contract-schema-reference.md).</span></span> <span data-ttu-id="c7a21-130">如果架构不符合数据协定规则，请使用另一个序列化引擎。</span><span class="sxs-lookup"><span data-stu-id="c7a21-130">If a schema does not conform to the data contract rules, use a different serialization engine.</span></span> <span data-ttu-id="c7a21-131">例如，<xref:System.Xml.Serialization.XmlSerializer> 使用自己的独立架构导入机制。</span><span class="sxs-lookup"><span data-stu-id="c7a21-131">For example, the <xref:System.Xml.Serialization.XmlSerializer> uses its own separate schema import mechanism.</span></span> <span data-ttu-id="c7a21-132">另有一种特殊的导入模式，可在其中扩展所支持架构的范围。</span><span class="sxs-lookup"><span data-stu-id="c7a21-132">Also, there is a special import mode in which the range of supported schema is expanded.</span></span> <span data-ttu-id="c7a21-133">有关详细信息，请参阅 <xref:System.Xml.Serialization.IXmlSerializable> 导入架构中的生成类型[以生成类](importing-schema-to-generate-classes.md)部分。</span><span class="sxs-lookup"><span data-stu-id="c7a21-133">For more information, see the section about generating <xref:System.Xml.Serialization.IXmlSerializable> types in [Importing Schema to Generate Classes](importing-schema-to-generate-classes.md).</span></span>  
  
 <span data-ttu-id="c7a21-134">`XsdDataContractExporter`支持可通过序列化的任何 .NET Framework 类型 `DataContractSerializer` 。</span><span class="sxs-lookup"><span data-stu-id="c7a21-134">The `XsdDataContractExporter` supports any .NET Framework types that can be serialized with the `DataContractSerializer`.</span></span> <span data-ttu-id="c7a21-135">有关详细信息，请参阅[数据协定序列化程序支持的类型](types-supported-by-the-data-contract-serializer.md)。</span><span class="sxs-lookup"><span data-stu-id="c7a21-135">For more information, see [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md).</span></span> <span data-ttu-id="c7a21-136">请注意，使用 `XsdDataContractExporter` 生成的架构通常是 `XsdDataContractImporter` 可以使用的有效数据（除非 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 用于对架构进行自定义）。</span><span class="sxs-lookup"><span data-stu-id="c7a21-136">Note that schema generated using the `XsdDataContractExporter` is normally valid data that the `XsdDataContractImporter` can use (unless the <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> is used to customize the schema).</span></span>  
  
 <span data-ttu-id="c7a21-137">有关使用的详细信息 <xref:System.Runtime.Serialization.XsdDataContractImporter> ，请参阅[导入架构以生成类](importing-schema-to-generate-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="c7a21-137">For more information about using the <xref:System.Runtime.Serialization.XsdDataContractImporter>, see [Importing Schema to Generate Classes](importing-schema-to-generate-classes.md).</span></span>  
  
 <span data-ttu-id="c7a21-138">有关使用的详细信息 <xref:System.Runtime.Serialization.XsdDataContractExporter> ，请参阅[从类导出架构](exporting-schemas-from-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="c7a21-138">For more information about using the <xref:System.Runtime.Serialization.XsdDataContractExporter>, see [Exporting Schemas from Classes](exporting-schemas-from-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7a21-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c7a21-139">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [<span data-ttu-id="c7a21-140">导入架构以生成类</span><span class="sxs-lookup"><span data-stu-id="c7a21-140">Importing Schema to Generate Classes</span></span>](importing-schema-to-generate-classes.md)
- [<span data-ttu-id="c7a21-141">从类导出架构</span><span class="sxs-lookup"><span data-stu-id="c7a21-141">Exporting Schemas from Classes</span></span>](exporting-schemas-from-classes.md)
