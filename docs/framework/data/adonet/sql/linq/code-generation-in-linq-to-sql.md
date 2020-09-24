---
title: LINQ to SQL 中的代码生成
ms.date: 03/30/2017
ms.assetid: ddcbdaa1-e7fa-4d85-a379-313b49965c07
ms.openlocfilehash: f58448e0fc0c22795005b55a737b42374a750ec3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161524"
---
# <a name="code-generation-in-linq-to-sql"></a><span data-ttu-id="4b105-102">LINQ to SQL 中的代码生成</span><span class="sxs-lookup"><span data-stu-id="4b105-102">Code Generation in LINQ to SQL</span></span>

<span data-ttu-id="4b105-103">您可以使用对象关系设计器或 SQLMetal 命令行工具生成代码以表示数据库。</span><span class="sxs-lookup"><span data-stu-id="4b105-103">You can generate code to represent a database by using either the Object Relational Designer or the SQLMetal command-line tool.</span></span> <span data-ttu-id="4b105-104">在任一情况下，端到端代码生成都分成三个阶段：</span><span class="sxs-lookup"><span data-stu-id="4b105-104">In either case, end-to-end code generation occurs in three stages:</span></span>  
  
1. <span data-ttu-id="4b105-105">*DBML 提取*程序从数据库中提取架构信息，并将信息重新组合到 XML 格式的 DBML 文件中。</span><span class="sxs-lookup"><span data-stu-id="4b105-105">The *DBML Extractor* extracts schema information from the database and reassembles the information into an XML-formatted DBML file.</span></span>  
  
2. <span data-ttu-id="4b105-106">Dbml *验证* 器会扫描 dbml 文件以查找错误。</span><span class="sxs-lookup"><span data-stu-id="4b105-106">The DBML file is scanned by the *DBML Validator* for errors.</span></span>  
  
3. <span data-ttu-id="4b105-107">如果未显示验证错误，文件将传递到代码生成器。</span><span class="sxs-lookup"><span data-stu-id="4b105-107">If no validation errors appear, the file is passed to the Code Generator.</span></span>  
  
 <span data-ttu-id="4b105-108">有关详细信息，请参阅 [SqlMetal.exe（代码生成工具）](../../../../tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="4b105-108">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="4b105-109">使用 Visual Studio 的开发人员还可以使用对象关系设计器来生成代码。</span><span class="sxs-lookup"><span data-stu-id="4b105-109">Developers using Visual Studio can also use the Object Relational Designer to generate code.</span></span> <span data-ttu-id="4b105-110">请参阅 [Visual Studio 中的 LINQ to SQL 工具](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)。</span><span class="sxs-lookup"><span data-stu-id="4b105-110">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
## <a name="dbml-extractor"></a><span data-ttu-id="4b105-111">DBML 提取器</span><span class="sxs-lookup"><span data-stu-id="4b105-111">DBML Extractor</span></span>  

 <span data-ttu-id="4b105-112">DBML 提取器是一个 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 组件，它采用数据库元数据作为输入，生成 DBML 文件作为输出。</span><span class="sxs-lookup"><span data-stu-id="4b105-112">The DBML Extractor is a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] component that takes database metadata as input and produces a DBML file as output.</span></span>  
  
## <a name="code-generator"></a><span data-ttu-id="4b105-113">代码生成器</span><span class="sxs-lookup"><span data-stu-id="4b105-113">Code Generator</span></span>  

 <span data-ttu-id="4b105-114">代码生成器是一个 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 组件，它将 DBML 文件转换为 Visual Basic、c # 或 XML 映射文件。</span><span class="sxs-lookup"><span data-stu-id="4b105-114">The Code Generator is a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] component that translates DBML files to Visual Basic, C#, or XML mapping files.</span></span>  
  
## <a name="xml-schema-definition-file"></a><span data-ttu-id="4b105-115">XML 架构定义文件</span><span class="sxs-lookup"><span data-stu-id="4b105-115">XML Schema Definition File</span></span>  

 <span data-ttu-id="4b105-116">DBML 文件必须对下面的 XSD 架构定义文件有效。</span><span class="sxs-lookup"><span data-stu-id="4b105-116">The DBML file must be valid against the following schema definition as an XSD file.</span></span>  
  
 <span data-ttu-id="4b105-117">请将此架构定义文件与用于验证外部映射文件的架构定义文件区分开来。</span><span class="sxs-lookup"><span data-stu-id="4b105-117">Distinguish this schema definition file from the schema definition file that is used to validate an external mapping file.</span></span> <span data-ttu-id="4b105-118">有关详细信息，请参阅 [外部映射](external-mapping.md)) 。</span><span class="sxs-lookup"><span data-stu-id="4b105-118">For more information, see [External Mapping](external-mapping.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b105-119">Visual Studio 用户还会在 "XML 架构" 对话框中找到此 XSD 文件，其形式为 "Dbmlschema.xsd"。</span><span class="sxs-lookup"><span data-stu-id="4b105-119">Visual Studio users will also find this XSD file in the XML Schemas dialog box as "DbmlSchema.xsd".</span></span> <span data-ttu-id="4b105-120">若要正确使用 XSD 文件来验证 DBML 文件，请参阅 [如何：验证 dbml 和外部映射文件](how-to-validate-dbml-and-external-mapping-files.md)。</span><span class="sxs-lookup"><span data-stu-id="4b105-120">To use the XSD file correctly for validating a DBML file, see [How to: Validate DBML and External Mapping Files](how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://schemas.microsoft.com/linqtosql/dbml/2007" xmlns="http://schemas.microsoft.com/linqtosql/dbml/2007"  
elementFormDefault="qualified" >  
  <xs:element name="Database" type="Database" />  
  <xs:complexType name="Database">  
    <xs:sequence>  
      <xs:element name="Connection" type="Connection" minOccurs="0" maxOccurs="1" />  
      <xs:element name="Table" type="Table" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="Function" type="Function" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="EntityNamespace" type="xs:string" use="optional" />  
    <xs:attribute name="ContextNamespace" type="xs:string" use="optional" />  
    <xs:attribute name="Class" type="xs:string" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="ClassModifier" use="optional" />  
    <xs:attribute name="BaseType" type="xs:string" use="optional" />  
    <xs:attribute name="Provider" type="xs:string" use="optional" />  
    <xs:attribute name="ExternalMapping" type="xs:boolean" use="optional" />  
    <xs:attribute name="Serialization" type="SerializationMode" use="optional" />  
    <xs:attribute name="EntityBase" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Table">  
    <xs:all>  
      <xs:element name="Type" type="Type" minOccurs="1" maxOccurs="1" />  
      <xs:element name="InsertFunction" type="TableFunction" minOccurs="0" maxOccurs="1" />  
      <xs:element name="UpdateFunction" type="TableFunction" minOccurs="0" maxOccurs="1" />  
      <xs:element name="DeleteFunction" type="TableFunction" minOccurs="0" maxOccurs="1" />  
    </xs:all>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Member" type="xs:string" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="MemberModifier" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Type">  
    <xs:sequence>  
      <xs:choice minOccurs="0" maxOccurs="unbounded">  
        <xs:element name="Column" type="Column" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Association" type="Association" minOccurs="0" maxOccurs="unbounded" />  
      </xs:choice>  
      <xs:element name="Type" type="Type" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="IdRef" type="xs:IDREF" use="optional" />  
    <xs:attribute name="Id" type="xs:ID" use="optional" />  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="InheritanceCode" type="xs:string" use="optional" />  
    <xs:attribute name="IsInheritanceDefault" type="xs:boolean" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="ClassModifier" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Column">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="optional" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="MemberModifier" use="optional" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="IsReadOnly" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsPrimaryKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsDbGenerated" type="xs:boolean" use="optional" />  
    <xs:attribute name="CanBeNull" type="xs:boolean" use="optional" />  
    <xs:attribute name="UpdateCheck" type="UpdateCheck" use="optional" />  
    <xs:attribute name="IsDiscriminator" type="xs:boolean" use="optional" />  
    <xs:attribute name="Expression" type="xs:string" use="optional" />  
    <xs:attribute name="IsVersion" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsDelayLoaded" type="xs:boolean" use="optional" />  
    <xs:attribute name="AutoSync" type="AutoSync" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Association">  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="MemberModifier" use="optional" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attribute name="ThisKey" type="xs:string" use="optional" />  
    <xs:attribute name="OtherKey" type="xs:string" use="optional" />  
    <xs:attribute name="IsForeignKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="Cardinality" type="Cardinality" use="optional" />  
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
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Id" type="xs:ID" use="optional" />  
    <xs:attribute name="Method" type="xs:string" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="MemberModifier" use="optional" />  
    <xs:attribute name="HasMultipleResults" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsComposable" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="TableFunction">  
    <xs:sequence>  
      <xs:element name="Argument" type="TableFunctionParameter" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="Return" type="TableFunctionReturn" minOccurs="0" maxOccurs="1" />  
    </xs:sequence>  
    <xs:attribute name="FunctionId" type="xs:IDREF" use="required" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Parameter">  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Parameter" type="xs:string" use="optional" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="Direction" type="ParameterDirection" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Return">  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="TableFunctionParameter">  
    <xs:attribute name="Parameter" type="xs:string" use="required" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Version" type="Version" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="TableFunctionReturn">  
    <xs:attribute name="Member" type="xs:string" use="required" />  
  </xs:complexType>  
  <xs:complexType name="Connection">  
    <xs:attribute name="Provider" type="xs:string" use="required" />  
    <xs:attribute name="Mode" type="ConnectionMode" use="optional" />  
    <xs:attribute name="ConnectionString" type="xs:string" use="optional" />  
    <xs:attribute name="SettingsObjectName" type="xs:string" use="optional" />  
    <xs:attribute name="SettingsPropertyName" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:simpleType name="ConnectionMode">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="ConnectionString" />  
      <xs:enumeration value="AppSettings" />  
      <xs:enumeration value="WebSettings" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="AccessModifier">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Public" />  
      <xs:enumeration value="Internal" />  
      <xs:enumeration value="Protected" />  
      <xs:enumeration value="ProtectedInternal" />  
      <xs:enumeration value="Private" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="UpdateCheck">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="WhenChanged" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="SerializationMode">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="None" />  
      <xs:enumeration value="Unidirectional" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="ParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In" />  
      <xs:enumeration value="Out" />  
      <xs:enumeration value="InOut" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="Version">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Current" />  
      <xs:enumeration value="Original" />  
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
  <xs:simpleType name="ClassModifier">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Sealed" />  
      <xs:enumeration value="Abstract" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="MemberModifier">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Virtual" />  
      <xs:enumeration value="Override" />  
      <xs:enumeration value="New" />  
      <xs:enumeration value="NewVirtual" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="Cardinality">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="One" />  
      <xs:enumeration value="Many" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="sample-dbml-file"></a><span data-ttu-id="4b105-121">DBML 文件示例</span><span class="sxs-lookup"><span data-stu-id="4b105-121">Sample DBML File</span></span>  

 <span data-ttu-id="4b105-122">下面的代码摘自从 Northwind 示例数据库创建的 DBML 文件。</span><span class="sxs-lookup"><span data-stu-id="4b105-122">The following code is an excerpt from the DBML file created from the Northwind sample database.</span></span> <span data-ttu-id="4b105-123">可以通过使用带有 **/xml** 选项的 SQLMetal 生成整个文件。</span><span class="sxs-lookup"><span data-stu-id="4b105-123">You can generate the whole file by using SQLMetal with the **/xml** option.</span></span> <span data-ttu-id="4b105-124">有关详细信息，请参阅 [SqlMetal.exe（代码生成工具）](../../../../tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="4b105-124">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
<Database Name="northwnd" Class="Northwnd" xmlns="http://schemas.microsoft.com/dsltools/DLinqML">  
  
  <Table Name="Customers">  
    <Type Name="Customer">  
      <Column Name="CustomerID" Type="System.String" DbType="NChar(5) NOT NULL" IsPrimaryKey="True" CanBeNull="False" />  
      <Column Name="CompanyName" Type="System.String" DbType="NVarChar(40) NOT NULL" CanBeNull="False" />  
      <Column Name="ContactName" Type="System.String" DbType="NVarChar(30)" CanBeNull="True" />  
      <Column Name="ContactTitle" Type="System.String" DbType="NVarChar(30)" CanBeNull="True" />  
      <Column Name="Address" Type="System.String" DbType="NVarChar(60)" CanBeNull="True" />  
      <Column Name="City" Type="System.String" DbType="NVarChar(15)" CanBeNull="True" />  
      <Column Name="Region" Type="System.String" DbType="NVarChar(15)" CanBeNull="True" />  
      <Column Name="PostalCode" Type="System.String" DbType="NVarChar(10)" CanBeNull="True" />  
      <Column Name="Country" Type="System.String" DbType="NVarChar(15)" CanBeNull="True" />  
      <Column Name="Phone" Type="System.String" DbType="NVarChar(24)" CanBeNull="True" />  
      <Column Name="Fax" Type="System.String" DbType="NVarChar(24)" CanBeNull="True" />  
      <Association Name="FK_CustomerCustomerDemo_Customers" Member="CustomerCustomerDemos" ThisKey="CustomerID" OtherKey="CustomerID" OtherTable="CustomerCustomerDemo" DeleteRule="NO ACTION" />  
      <Association Name="FK_Orders_Customers" Member="Orders" ThisKey="CustomerID" OtherKey="CustomerID" OtherTable="Orders" DeleteRule="NO ACTION" />  
    </Type>  
  </Table>  
</Database>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b105-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="4b105-125">See also</span></span>

- [<span data-ttu-id="4b105-126">背景信息</span><span class="sxs-lookup"><span data-stu-id="4b105-126">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="4b105-127">外部映射</span><span class="sxs-lookup"><span data-stu-id="4b105-127">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="4b105-128">如何：将对象模型作为外部文件生成</span><span class="sxs-lookup"><span data-stu-id="4b105-128">How to: Generate the Object Model as an External File</span></span>](how-to-generate-the-object-model-as-an-external-file.md)
- [<span data-ttu-id="4b105-129">下载示例数据库</span><span class="sxs-lookup"><span data-stu-id="4b105-129">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="4b105-130">引用</span><span class="sxs-lookup"><span data-stu-id="4b105-130">Reference</span></span>](reference.md)
