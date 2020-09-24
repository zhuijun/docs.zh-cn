---
title: 外部映射
ms.date: 03/30/2017
ms.assetid: 076606b8-d889-4ba0-b5da-ae577b146f23
ms.openlocfilehash: 79427cde0784746480e851cf1be56c8bce854919
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161381"
---
# <a name="external-mapping"></a><span data-ttu-id="84f76-102">外部映射</span><span class="sxs-lookup"><span data-stu-id="84f76-102">External Mapping</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="84f76-103">支持 *外部映射*，这是使用单独的 XML 文件指定数据库的数据模型和对象模型之间的映射的过程。</span><span class="sxs-lookup"><span data-stu-id="84f76-103">supports *external mapping*, a process by which you use a separate XML file to specify mapping between the data model of the database and your object model.</span></span> <span data-ttu-id="84f76-104">使用外部映射文件具有以下优点：</span><span class="sxs-lookup"><span data-stu-id="84f76-104">Advantages of using an external mapping file include the following:</span></span>  
  
- <span data-ttu-id="84f76-105">可以将映射代码放在应用程序代码外部。</span><span class="sxs-lookup"><span data-stu-id="84f76-105">You can keep your mapping code out of your application code.</span></span> <span data-ttu-id="84f76-106">此方法可以降低应用程序代码的混乱程度。</span><span class="sxs-lookup"><span data-stu-id="84f76-106">This approach reduces clutter in your application code.</span></span>  
  
- <span data-ttu-id="84f76-107">可以将外部映射文件视为类似于配置文件的某种东西。</span><span class="sxs-lookup"><span data-stu-id="84f76-107">You can treat an external mapping file something like a configuration file.</span></span> <span data-ttu-id="84f76-108">例如，在发布二进制文件后，只需交换出外部映射文件，就可以更新应用程序的工作方式。</span><span class="sxs-lookup"><span data-stu-id="84f76-108">For example, you can update how your application behaves after shipping the binaries by just swapping out the external mapping file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84f76-109">要求</span><span class="sxs-lookup"><span data-stu-id="84f76-109">Requirements</span></span>  

 <span data-ttu-id="84f76-110">映射文件必须为 XML 文件，并且该文件必须能够通过 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 架构定义 (.xsd) 文件的验证。</span><span class="sxs-lookup"><span data-stu-id="84f76-110">The mapping file must be an XML file, and the file must validate against a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] schema definition (.xsd) file.</span></span>  
  
 <span data-ttu-id="84f76-111">下列规则适用：</span><span class="sxs-lookup"><span data-stu-id="84f76-111">The following rules apply:</span></span>  
  
- <span data-ttu-id="84f76-112">映射文件必须为 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="84f76-112">The mapping file must be an XML file.</span></span>  
  
- <span data-ttu-id="84f76-113">XML 映射文件必须能够通过 XML 架构定义文件的验证。</span><span class="sxs-lookup"><span data-stu-id="84f76-113">The XML mapping file must be valid against the XML schema definition file.</span></span> <span data-ttu-id="84f76-114">有关详细信息，请参阅 [如何：验证 DBML 和外部映射文件](how-to-validate-dbml-and-external-mapping-files.md)。</span><span class="sxs-lookup"><span data-stu-id="84f76-114">For more information, see [How to: Validate DBML and External Mapping Files](how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
- <span data-ttu-id="84f76-115">外部映射会重写基于属性的映射。</span><span class="sxs-lookup"><span data-stu-id="84f76-115">External mapping overrides attribute-based mapping.</span></span> <span data-ttu-id="84f76-116">换句话说，在使用外部映射源创建 <xref:System.Data.Linq.DataContext> 时，<xref:System.Data.Linq.DataContext> 会忽略已在类上创建的所有映射属性。</span><span class="sxs-lookup"><span data-stu-id="84f76-116">In other words, when you use an external mapping source to create a <xref:System.Data.Linq.DataContext>, the <xref:System.Data.Linq.DataContext> ignores all mapping attributes you have created on classes.</span></span> <span data-ttu-id="84f76-117">无论类是否包含在外部映射文件中，都会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="84f76-117">This behavior is true whether the class is included in the external mapping file.</span></span>  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="84f76-118">不支持混合使用两种映射方式（基于属性的映射和外部映射）。</span><span class="sxs-lookup"><span data-stu-id="84f76-118">does not support the hybrid use of the two mapping approaches (attribute-based and external).</span></span>  
  
## <a name="xml-schema-definition-file"></a><span data-ttu-id="84f76-119">XML 架构定义文件</span><span class="sxs-lookup"><span data-stu-id="84f76-119">XML Schema Definition File</span></span>  

 <span data-ttu-id="84f76-120">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的外部映射必须能够通过以下 XML 架构定义的验证。</span><span class="sxs-lookup"><span data-stu-id="84f76-120">External mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be valid against the following XML schema definition.</span></span>  
  
 <span data-ttu-id="84f76-121">请将此架构定义文件与用于验证 DBML 文件的架构定义文件区分开来。</span><span class="sxs-lookup"><span data-stu-id="84f76-121">Distinguish this schema definition file from the schema definition file that is used to validate a DBML file.</span></span> <span data-ttu-id="84f76-122">有关详细信息，请参阅 [LINQ to SQL) 中的代码生成](code-generation-in-linq-to-sql.md) 。</span><span class="sxs-lookup"><span data-stu-id="84f76-122">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84f76-123">Visual Studio 用户还会在 "XML 架构" 对话框中找到此 XSD 文件，其形式为 "Linqtosqlmapping.xsd"。</span><span class="sxs-lookup"><span data-stu-id="84f76-123">Visual Studio users will also find this XSD file in the XML Schemas dialog box as "LinqToSqlMapping.xsd".</span></span> <span data-ttu-id="84f76-124">若要正确使用此文件来验证外部映射文件，请参阅 [如何：验证 DBML 和外部映射文件](how-to-validate-dbml-and-external-mapping-files.md)。</span><span class="sxs-lookup"><span data-stu-id="84f76-124">To use this file correctly for validating an external mapping file, see [How to: Validate DBML and External Mapping Files](how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://schemas.microsoft.com/linqtosql/mapping/2007" xmlns="http://schemas.microsoft.com/linqtosql/mapping/2007"  
elementFormDefault="qualified" >  
  <xs:element name="Database" type="Database" />  
  <xs:complexType name="Database">  
    <xs:sequence>  
      <xs:element name="Table" type="Table" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="Function" type="Function" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Provider" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Table">  
    <xs:sequence>  
      <xs:element name="Type" type="Type" minOccurs="1" maxOccurs="1" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Type">  
    <xs:sequence>  
      <xs:choice minOccurs="0" maxOccurs="unbounded">  
        <xs:element name="Column" type="Column" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Association" type="Association" minOccurs="0" maxOccurs="unbounded" />  
      </xs:choice>  
      <xs:element name="Type" type="Type" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="InheritanceCode" type="xs:string" use="optional" />  
    <xs:attribute name="IsInheritanceDefault" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Column">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="IsPrimaryKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsDbGenerated" type="xs:boolean" use="optional" />  
    <xs:attribute name="CanBeNull" type="xs:boolean" use="optional" />  
    <xs:attribute name="UpdateCheck" type="UpdateCheck" use="optional" />  
    <xs:attribute name="IsDiscriminator" type="xs:boolean" use="optional" />  
    <xs:attribute name="Expression" type="xs:string" use="optional" />  
    <xs:attribute name="IsVersion" type="xs:boolean" use="optional" />  
    <xs:attribute name="AutoSync" type="AutoSync" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Association">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="ThisKey" type="xs:string" use="optional" />  
    <xs:attribute name="OtherKey" type="xs:string" use="optional" />  
    <xs:attribute name="IsForeignKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsUnique" type="xs:boolean" use="optional" />  
    <xs:attribute name="DeleteRule" type="xs:string" use="optional" />  
    <xs:attribute name="DeleteOnNull" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Function">  
    <xs:sequence>  
      <xs:element name="Parameter" type="Parameter" minOccurs="0" maxOccurs="unbounded" />  
      <xs:choice>  
        <xs:element name="ElementType" type="Type" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Return" type="Return" minOccurs="0" maxOccurs="1" />  
      </xs:choice>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Method" type="xs:string" use="required" />  
    <xs:attribute name="IsComposable" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Parameter">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Parameter" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="Direction" type="ParameterDirection" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Return">  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:simpleType name="UpdateCheck">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="WhenChanged" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="ParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In" />  
      <xs:enumeration value="Out" />  
      <xs:enumeration value="InOut" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="AutoSync">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="OnInsert" />  
      <xs:enumeration value="OnUpdate" />  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Default" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="84f76-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="84f76-125">See also</span></span>

- [<span data-ttu-id="84f76-126">LINQ to SQL 中的代码生成</span><span class="sxs-lookup"><span data-stu-id="84f76-126">Code Generation in LINQ to SQL</span></span>](code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="84f76-127">引用</span><span class="sxs-lookup"><span data-stu-id="84f76-127">Reference</span></span>](reference.md)
- [<span data-ttu-id="84f76-128">如何：将对象模型作为外部文件生成</span><span class="sxs-lookup"><span data-stu-id="84f76-128">How to: Generate the Object Model as an External File</span></span>](how-to-generate-the-object-model-as-an-external-file.md)
