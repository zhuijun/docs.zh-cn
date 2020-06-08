---
title: 用于编译架构的 XmlSchemaSet
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
ms.openlocfilehash: 44850755c41b212e88e0b90dd3b016f96a0af96d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290222"
---
# <a name="xmlschemaset-for-schema-compilation"></a><span data-ttu-id="3d84a-102">用于编译架构的 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="3d84a-102">XmlSchemaSet for Schema Compilation</span></span>
<span data-ttu-id="3d84a-103">介绍 <xref:System.Xml.Schema.XmlSchemaSet>，一个可以存储和验证 XML 架构定义语言 (XSD) 架构的缓存。</span><span class="sxs-lookup"><span data-stu-id="3d84a-103">Describes the <xref:System.Xml.Schema.XmlSchemaSet>, a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
## <a name="the-xmlschemaset-class"></a><span data-ttu-id="3d84a-104">XmlSchemaSet 类</span><span class="sxs-lookup"><span data-stu-id="3d84a-104">The XmlSchemaSet Class</span></span>  
 <span data-ttu-id="3d84a-105"><xref:System.Xml.Schema.XmlSchemaSet> 是一个可以存储和验证 XML 架构定义语言 (XSD) 架构的缓存。</span><span class="sxs-lookup"><span data-stu-id="3d84a-105">The <xref:System.Xml.Schema.XmlSchemaSet> is a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
 <span data-ttu-id="3d84a-106">在 <xref:System.Xml?displayProperty=nameWithType> 1.0 版中，XML 架构作为架构库加载到 <xref:System.Xml.Schema.XmlSchemaCollection> 类中。</span><span class="sxs-lookup"><span data-stu-id="3d84a-106">In <xref:System.Xml?displayProperty=nameWithType> version 1.0, XML schemas were loaded into an <xref:System.Xml.Schema.XmlSchemaCollection> class as a library of schemas.</span></span> <span data-ttu-id="3d84a-107">在 <xref:System.Xml?displayProperty=nameWithType> 2.0 版中，<xref:System.Xml.XmlValidatingReader> 和 <xref:System.Xml.Schema.XmlSchemaCollection> 类已过时，分别由 <xref:System.Xml.XmlReader.Create%2A> 方法和 <xref:System.Xml.Schema.XmlSchemaSet> 类所取代。</span><span class="sxs-lookup"><span data-stu-id="3d84a-107">In <xref:System.Xml?displayProperty=nameWithType> version 2.0, the <xref:System.Xml.XmlValidatingReader> and the <xref:System.Xml.Schema.XmlSchemaCollection> classes are obsolete, and have been replaced by the <xref:System.Xml.XmlReader.Create%2A> methods, and the <xref:System.Xml.Schema.XmlSchemaSet> class respectively.</span></span>  
  
 <span data-ttu-id="3d84a-108">引入了 <xref:System.Xml.Schema.XmlSchemaSet> 来解决许多问题，包括标准兼容性、性能和过时的 Microsoft XML 数据简化 (XDR) 架构格式。</span><span class="sxs-lookup"><span data-stu-id="3d84a-108">The <xref:System.Xml.Schema.XmlSchemaSet> has been introduced to fix a number of issues including standards compatibility, performance, and the obsolete Microsoft XML-Data Reduced (XDR) schema format.</span></span>  
  
 <span data-ttu-id="3d84a-109">以下是 <xref:System.Xml.Schema.XmlSchemaCollection> 类和 <xref:System.Xml.Schema.XmlSchemaSet> 类之间的比较。</span><span class="sxs-lookup"><span data-stu-id="3d84a-109">The following is a comparison between the <xref:System.Xml.Schema.XmlSchemaCollection> class and the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span>  
  
|<span data-ttu-id="3d84a-110">XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="3d84a-110">XmlSchemaCollection</span></span>|<span data-ttu-id="3d84a-111">XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="3d84a-111">XmlSchemaSet</span></span>|  
|-------------------------|------------------|  
|<span data-ttu-id="3d84a-112">支持 Microsoft XDR 和 W3C XML 架构。</span><span class="sxs-lookup"><span data-stu-id="3d84a-112">Supports Microsoft XDR and W3C XML schemas.</span></span>|<span data-ttu-id="3d84a-113">只支持 W3C XML 架构。</span><span class="sxs-lookup"><span data-stu-id="3d84a-113">Only supports W3C XML schemas.</span></span>|  
|<span data-ttu-id="3d84a-114">架构在调用 <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> 方法时编译。</span><span class="sxs-lookup"><span data-stu-id="3d84a-114">Schemas are compiled when the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method is called.</span></span>|<span data-ttu-id="3d84a-115">架构在调用 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法时不编译。</span><span class="sxs-lookup"><span data-stu-id="3d84a-115">Schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span> <span data-ttu-id="3d84a-116">这样可以提高创建架构库时的性能。</span><span class="sxs-lookup"><span data-stu-id="3d84a-116">This provides a performance improvement during creation of the schema library.</span></span>|  
|<span data-ttu-id="3d84a-117">每个架构都会生成单独编译的版本，这就会产生各个“架构岛”。</span><span class="sxs-lookup"><span data-stu-id="3d84a-117">Each schema generates an individual compiled version that can result in "schema islands."</span></span> <span data-ttu-id="3d84a-118">因此，所有包含和导入仅在该架构中有效。</span><span class="sxs-lookup"><span data-stu-id="3d84a-118">As a result, all includes and imports are scoped only within that schema.</span></span>|<span data-ttu-id="3d84a-119">已编译的架构生成单个逻辑架构，即一个架构“集”。</span><span class="sxs-lookup"><span data-stu-id="3d84a-119">Compiled schemas generate a single logical schema, a "set" of schemas.</span></span> <span data-ttu-id="3d84a-120">添加到该架构集的架构内的任何导入架构将直接添加到架构集中。</span><span class="sxs-lookup"><span data-stu-id="3d84a-120">Any imported schemas within a schema that are added to the set are directly added to the set themselves.</span></span> <span data-ttu-id="3d84a-121">这意味着所有类型可以供所有架构使用。</span><span class="sxs-lookup"><span data-stu-id="3d84a-121">This means that all types are available to all schemas.</span></span>|  
|<span data-ttu-id="3d84a-122">特定目标命名空间在集合中只能存在一个架构。</span><span class="sxs-lookup"><span data-stu-id="3d84a-122">Only one schema for a particular target namespace can exist in the collection.</span></span>|<span data-ttu-id="3d84a-123">只要不存在类型冲突，就可以为同一目标命名空间添加多个架构。</span><span class="sxs-lookup"><span data-stu-id="3d84a-123">Multiple schemas for the same target namespace can be added as long as there are no type conflicts.</span></span>|  
  
## <a name="migrating-to-the-xmlschemaset"></a><span data-ttu-id="3d84a-124">迁移到 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="3d84a-124">Migrating to the XmlSchemaSet</span></span>  
 <span data-ttu-id="3d84a-125">以下代码示例提供从过时的 <xref:System.Xml.Schema.XmlSchemaSet> 类迁移到新的 <xref:System.Xml.Schema.XmlSchemaCollection> 类的指南。</span><span class="sxs-lookup"><span data-stu-id="3d84a-125">The following code example provides a guide to migrating to the new <xref:System.Xml.Schema.XmlSchemaSet> class from the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class.</span></span> <span data-ttu-id="3d84a-126">该代码示例说明两个类之间的下列主要区别。</span><span class="sxs-lookup"><span data-stu-id="3d84a-126">The code example illustrates the following major differences between the two classes.</span></span>  
  
- <span data-ttu-id="3d84a-127">与 <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> 类的 <xref:System.Xml.Schema.XmlSchemaCollection> 方法不同，在调用 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法时，不编译架构。</span><span class="sxs-lookup"><span data-stu-id="3d84a-127">Unlike the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when calling the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3d84a-128"><xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法在示例代码中显式调用。</span><span class="sxs-lookup"><span data-stu-id="3d84a-128">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is explicitly called in the example code.</span></span>  
  
- <span data-ttu-id="3d84a-129">要循环访问 <xref:System.Xml.Schema.XmlSchemaSet>，必须使用 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 属性。</span><span class="sxs-lookup"><span data-stu-id="3d84a-129">To iterate over an <xref:System.Xml.Schema.XmlSchemaSet>, you must use the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="3d84a-130">以下是过时的 <xref:System.Xml.Schema.XmlSchemaCollection> 代码示例。</span><span class="sxs-lookup"><span data-stu-id="3d84a-130">The following is the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> code example.</span></span>  
  
```vb  
Dim schemaCollection As XmlSchemaCollection = New XmlSchemaCollection()  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema in schemaCollection  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaCollection schemaCollection = new XmlSchemaCollection();  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
  
foreach(XmlSchema schema in schemaCollection)  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
 <span data-ttu-id="3d84a-131">以下是等效的 <xref:System.Xml.Schema.XmlSchemaSet> 代码示例。</span><span class="sxs-lookup"><span data-stu-id="3d84a-131">The following is the equivalent <xref:System.Xml.Schema.XmlSchemaSet> code example.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim schema As XmlSchema  
  
For Each schema in schemaSet.Schemas()  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
foreach(XmlSchema schema in schemaSet.Schemas())  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
## <a name="adding-and-retrieving-schemas"></a><span data-ttu-id="3d84a-132">添加和检索架构</span><span class="sxs-lookup"><span data-stu-id="3d84a-132">Adding and Retrieving Schemas</span></span>  
 <span data-ttu-id="3d84a-133">架构是使用 <xref:System.Xml.Schema.XmlSchemaSet> 的 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法添加到 <xref:System.Xml.Schema.XmlSchemaSet> 中的。</span><span class="sxs-lookup"><span data-stu-id="3d84a-133">Schemas are added to an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3d84a-134">架构添加到 <xref:System.Xml.Schema.XmlSchemaSet> 中后，将与目标命名空间 URI 关联。</span><span class="sxs-lookup"><span data-stu-id="3d84a-134">When a schema is added to an <xref:System.Xml.Schema.XmlSchemaSet>, it is associated with a target namespace URI.</span></span> <span data-ttu-id="3d84a-135">目标命名空间 URI 可以指定为 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法的参数，如果未指定目标命名空间，<xref:System.Xml.Schema.XmlSchemaSet> 将使用架构中定义的目标命名空间。</span><span class="sxs-lookup"><span data-stu-id="3d84a-135">The target namespace URI can either be specified as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method or if no target namespace is specified, the <xref:System.Xml.Schema.XmlSchemaSet> uses the target namespace defined in the schema.</span></span>  
  
 <span data-ttu-id="3d84a-136">架构是使用 <xref:System.Xml.Schema.XmlSchemaSet> 的 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 属性从 <xref:System.Xml.Schema.XmlSchemaSet> 检索的。</span><span class="sxs-lookup"><span data-stu-id="3d84a-136">Schemas are retrieved from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3d84a-137">通过 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 属性，可以循环访问 <xref:System.Xml.Schema.XmlSchema> 中包含的 <xref:System.Xml.Schema.XmlSchemaSet> 对象。</span><span class="sxs-lookup"><span data-stu-id="3d84a-137">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> allows you to iterate over the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3d84a-138"><xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 属性返回 <xref:System.Xml.Schema.XmlSchema> 中包含的所有 <xref:System.Xml.Schema.XmlSchemaSet> 对象，如果给定了目标命名空间参数，则返回属于该目标命名空间的所有 <xref:System.Xml.Schema.XmlSchema> 对象。</span><span class="sxs-lookup"><span data-stu-id="3d84a-138">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property either returns all the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>, or, given a target namespace parameter, returns all the <xref:System.Xml.Schema.XmlSchema> objects that belong to the target namespace.</span></span> <span data-ttu-id="3d84a-139">如果 `null` 指定为目标命名空间参数，<xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 属性将返回所有没有命名空间的架构。</span><span class="sxs-lookup"><span data-stu-id="3d84a-139">If `null` is specified as the target namespace parameter, the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property returns all schemas without a namespace.</span></span>  
  
 <span data-ttu-id="3d84a-140">以下示例将 `books.xsd` 命名空间中的 `http://www.contoso.com/books` 架构添加到 <xref:System.Xml.Schema.XmlSchemaSet>，从 `http://www.contoso.com/books` 检索所有属于 <xref:System.Xml.Schema.XmlSchemaSet> 命名空间的架构，然后将这些架构写入 <xref:System.Console>。</span><span class="sxs-lookup"><span data-stu-id="3d84a-140">The following example adds the `books.xsd` schema in the `http://www.contoso.com/books` namespace to an <xref:System.Xml.Schema.XmlSchemaSet>, retrieves all schemas that belong to the `http://www.contoso.com/books` namespace from the <xref:System.Xml.Schema.XmlSchemaSet>, and then writes those schemas to the <xref:System.Console>.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas("http://www.contoso.com/books")  
  
   schema.Write(Console.Out)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas("http://www.contoso.com/books"))  
{  
   schema.Write(Console.Out);  
}  
```  
  
 <span data-ttu-id="3d84a-141">有关在 <xref:System.Xml.Schema.XmlSchemaSet> 对象中添加和检索架构的更多信息，请参见 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法和 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 属性的参考文档。</span><span class="sxs-lookup"><span data-stu-id="3d84a-141">For more information about adding and retrieving schemas from an <xref:System.Xml.Schema.XmlSchemaSet> object, see the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method and the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property reference documentation.</span></span>  
  
## <a name="compiling-schemas"></a><span data-ttu-id="3d84a-142">编译架构</span><span class="sxs-lookup"><span data-stu-id="3d84a-142">Compiling Schemas</span></span>  
 <span data-ttu-id="3d84a-143"><xref:System.Xml.Schema.XmlSchemaSet> 中的架构通过 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法编译为一个逻辑架构。</span><span class="sxs-lookup"><span data-stu-id="3d84a-143">Schemas in an <xref:System.Xml.Schema.XmlSchemaSet> are compiled into one logical schema by the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d84a-144">与过时的 <xref:System.Xml.Schema.XmlSchemaCollection> 类不同，架构在调用 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法时不编译。</span><span class="sxs-lookup"><span data-stu-id="3d84a-144">Unlike the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span>  
  
 <span data-ttu-id="3d84a-145">如果 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法成功执行，<xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 属性将设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="3d84a-145">If the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method executes successfully, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d84a-146">如果架构在 <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 中编辑，<xref:System.Xml.Schema.XmlSchemaSet> 属性不受影响。</span><span class="sxs-lookup"><span data-stu-id="3d84a-146">The <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is not affected if schemas are edited while in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3d84a-147">不跟踪对 <xref:System.Xml.Schema.XmlSchemaSet> 中各个架构的更新。</span><span class="sxs-lookup"><span data-stu-id="3d84a-147">Updates of the individual schemas in the <xref:System.Xml.Schema.XmlSchemaSet> are not tracked.</span></span> <span data-ttu-id="3d84a-148">因此，只要 <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 中没有添加或移除任何架构，即使 `true` 中包含的一个架构已更改，<xref:System.Xml.Schema.XmlSchemaSet> 属性也可以为 <xref:System.Xml.Schema.XmlSchemaSet>。</span><span class="sxs-lookup"><span data-stu-id="3d84a-148">As a result, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property can be `true` even though one of the schemas contained in the <xref:System.Xml.Schema.XmlSchemaSet> has been altered, as long as no schemas were added or removed from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="3d84a-149">以下示例将 `books.xsd` 文件添加到 <xref:System.Xml.Schema.XmlSchemaSet> 中，然后调用 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="3d84a-149">The following example adds the `books.xsd` file to the <xref:System.Xml.Schema.XmlSchemaSet> and then calls the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
schemaSet.Compile()  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
schemaSet.Compile();  
```  
  
 <span data-ttu-id="3d84a-150">有关编译 <xref:System.Xml.Schema.XmlSchemaSet> 中的架构的更多信息，请参见 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 方法参考文档。</span><span class="sxs-lookup"><span data-stu-id="3d84a-150">For more information about compiling schemas in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method reference documentation.</span></span>  
  
## <a name="reprocessing-schemas"></a><span data-ttu-id="3d84a-151">重新处理架构</span><span class="sxs-lookup"><span data-stu-id="3d84a-151">Reprocessing Schemas</span></span>  
 <span data-ttu-id="3d84a-152">重新处理 <xref:System.Xml.Schema.XmlSchemaSet> 中的架构时，将执行调用 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法时对架构执行的所有预处理步骤。</span><span class="sxs-lookup"><span data-stu-id="3d84a-152">Reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet> performs all the preprocessing steps performed on a schema when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span> <span data-ttu-id="3d84a-153">如果调用 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 方法成功，<xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 属性将设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="3d84a-153">If the call to the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method is successful, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `false`.</span></span>  
  
 <span data-ttu-id="3d84a-154">如果 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 中的架构在 <xref:System.Xml.Schema.XmlSchemaSet> 执行编译之后已修改，应使用 <xref:System.Xml.Schema.XmlSchemaSet> 方法。</span><span class="sxs-lookup"><span data-stu-id="3d84a-154">The <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method should be used when a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified after the <xref:System.Xml.Schema.XmlSchemaSet> has performed compilation.</span></span>  
  
 <span data-ttu-id="3d84a-155">以下示例说明如何使用 <xref:System.Xml.Schema.XmlSchemaSet> 方法重新处理添加到 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 中的架构。</span><span class="sxs-lookup"><span data-stu-id="3d84a-155">The following example illustrates reprocessing a schema added to the <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method.</span></span> <span data-ttu-id="3d84a-156">在使用 <xref:System.Xml.Schema.XmlSchemaSet> 方法编译了 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> 后，并且修改了添加到 <xref:System.Xml.Schema.XmlSchemaSet> 中的架构，即使 <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 中的架构已修改，`true` 属性仍将设置为 <xref:System.Xml.Schema.XmlSchemaSet>。</span><span class="sxs-lookup"><span data-stu-id="3d84a-156">After the <xref:System.Xml.Schema.XmlSchemaSet> is compiled using the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method, and the schema added to the <xref:System.Xml.Schema.XmlSchemaSet> is modified, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is set to `true` even though a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified.</span></span> <span data-ttu-id="3d84a-157">调用 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 方法将执行通过 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> 方法执行的所有预处理步骤，并将 <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> 属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="3d84a-157">Calling the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method performs all the preprocessing performed by the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method, and sets the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property to `false`.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
Dim schema As XmlSchema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim element As XmlSchemaElement = New XmlSchemaElement()  
schema.Items.Add(element)  
element.Name = "book"  
element.SchemaTypeName = New XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema")  
  
schemaSet.Reprocess(schema)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
XmlSchema schema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
XmlSchemaElement element = new XmlSchemaElement();  
schema.Items.Add(element);  
element.Name = "book";  
element.SchemaTypeName = new XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema");  
  
schemaSet.Reprocess(schema);  
```  
  
 <span data-ttu-id="3d84a-158">有关重新处理 <xref:System.Xml.Schema.XmlSchemaSet> 中的架构的更多信息，请参见 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> 方法参考文档。</span><span class="sxs-lookup"><span data-stu-id="3d84a-158">For more information about reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method reference documentation.</span></span>  
  
## <a name="checking-for-a-schema"></a><span data-ttu-id="3d84a-159">检查架构</span><span class="sxs-lookup"><span data-stu-id="3d84a-159">Checking for a Schema</span></span>  
 <span data-ttu-id="3d84a-160">可以使用 <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> 的 <xref:System.Xml.Schema.XmlSchemaSet> 方法检查架构是否包含在 <xref:System.Xml.Schema.XmlSchemaSet> 中。</span><span class="sxs-lookup"><span data-stu-id="3d84a-160">You can use the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> to check if a schema is contained within an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3d84a-161"><xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> 方法使用目标命名空间或要检查的 <xref:System.Xml.Schema.XmlSchema> 对象。</span><span class="sxs-lookup"><span data-stu-id="3d84a-161">The <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method takes either a target namespace or an <xref:System.Xml.Schema.XmlSchema> object to check for.</span></span> <span data-ttu-id="3d84a-162">在任何一种情况下，如果架构包含在 <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> 中，`true` 方法将返回 <xref:System.Xml.Schema.XmlSchemaSet>；否则，将返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="3d84a-162">In either case, the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method returns `true` if the schema is contained within the <xref:System.Xml.Schema.XmlSchemaSet>; otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="3d84a-163">有关检查架构的更多信息，请参见 <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> 方法参考文档。</span><span class="sxs-lookup"><span data-stu-id="3d84a-163">For more information about checking for a schema, see the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method reference documentation.</span></span>  
  
## <a name="removing-schemas"></a><span data-ttu-id="3d84a-164">移除架构</span><span class="sxs-lookup"><span data-stu-id="3d84a-164">Removing Schemas</span></span>  
 <span data-ttu-id="3d84a-165">架构使用 <xref:System.Xml.Schema.XmlSchemaSet> 的 <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> 和 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> 方法从 <xref:System.Xml.Schema.XmlSchemaSet> 中移除。</span><span class="sxs-lookup"><span data-stu-id="3d84a-165">Schemas are removed from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3d84a-166"><xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> 方法将指定架构从 <xref:System.Xml.Schema.XmlSchemaSet> 中移除，而 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> 方法将指定架构及其导入的所有架构从 <xref:System.Xml.Schema.XmlSchemaSet> 中移除。</span><span class="sxs-lookup"><span data-stu-id="3d84a-166">The <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> method removes the specified schema from the <xref:System.Xml.Schema.XmlSchemaSet>, while the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method removes the specified schema and all the schemas it imports from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="3d84a-167">以下示例说明如何将多个架构添加到 <xref:System.Xml.Schema.XmlSchemaSet> 中，然后使用 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> 方法移除其中一个架构及其导入的所有架构。</span><span class="sxs-lookup"><span data-stu-id="3d84a-167">The following example illustrates adding multiple schemas to an <xref:System.Xml.Schema.XmlSchemaSet>, then using the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method to remove one of the schemas and all the schemas it imports.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas()  
  
   If schema.TargetNamespace = "http://www.contoso.com/music" Then  
      schemaSet.RemoveRecursive(schema)  
   End If  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas())  
{  
   if (schema.TargetNamespace == "http://www.contoso.com/music")  
   {  
      schemaSet.RemoveRecursive(schema);  
   }  
}  
```  
  
 <span data-ttu-id="3d84a-168">有关移除 <xref:System.Xml.Schema.XmlSchemaSet> 中的架构的更多信息，请参见 <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> 和 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> 方法的参考文档。</span><span class="sxs-lookup"><span data-stu-id="3d84a-168">For more information about removing schemas from an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods reference documentation.</span></span>  
  
## <a name="schema-resolution-and-xsimport"></a><span data-ttu-id="3d84a-169">架构解析和 xs:import</span><span class="sxs-lookup"><span data-stu-id="3d84a-169">Schema Resolution and xs:import</span></span>  
 <span data-ttu-id="3d84a-170">下列示例说明 <xref:System.Xml.Schema.XmlSchemaSet> 中存在给定命名空间的多个架构时，用于导入架构的 <xref:System.Xml.Schema.XmlSchemaSet> 行为。</span><span class="sxs-lookup"><span data-stu-id="3d84a-170">The following examples describe the <xref:System.Xml.Schema.XmlSchemaSet> behavior for importing schemas when multiple schemas for a given namespace exist in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="3d84a-171">例如，考虑包含 <xref:System.Xml.Schema.XmlSchemaSet> 命名空间的多个架构的 `http://www.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="3d84a-171">For example, consider an <xref:System.Xml.Schema.XmlSchemaSet> that contains multiple schemas for the `http://www.contoso.com` namespace.</span></span> <span data-ttu-id="3d84a-172">具有以下 `xs:import` 指令的架构添加到 <xref:System.Xml.Schema.XmlSchemaSet> 中。</span><span class="sxs-lookup"><span data-stu-id="3d84a-172">A schema with the following `xs:import` directive is added to the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <span data-ttu-id="3d84a-173"><xref:System.Xml.Schema.XmlSchemaSet> 尝试导入 `http://www.contoso.com` 命名空间的架构，方法是从 `http://www.contoso.com/schema.xsd` URL 加载该架构。</span><span class="sxs-lookup"><span data-stu-id="3d84a-173">The <xref:System.Xml.Schema.XmlSchemaSet> attempts to import a schema for the `http://www.contoso.com` namespace by loading it from the `http://www.contoso.com/schema.xsd` URL.</span></span> <span data-ttu-id="3d84a-174">只有架构文档中声明的架构声明和类型可以在导入架构中使用，即使 `http://www.contoso.com` 中存在 <xref:System.Xml.Schema.XmlSchemaSet> 命名空间的其他架构文档。</span><span class="sxs-lookup"><span data-stu-id="3d84a-174">Only the schema declaration and types declared in the schema document are available in the importing schema, even though there are other schema documents for the `http://www.contoso.com` namespace in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3d84a-175">如果 `schema.xsd` 文件不能位于 `http://www.contoso.com/schema.xsd` URL，则不会有任何 `http://www.contoso.com` 命名空间的架构导入到导入架构中。</span><span class="sxs-lookup"><span data-stu-id="3d84a-175">If the `schema.xsd` file cannot be located at the `http://www.contoso.com/schema.xsd` URL, no schema for the `http://www.contoso.com` namespace is imported into the importing schema.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="3d84a-176">验证 XML 文档</span><span class="sxs-lookup"><span data-stu-id="3d84a-176">Validating XML Documents</span></span>  
 <span data-ttu-id="3d84a-177">XML 文档可以针对 <xref:System.Xml.Schema.XmlSchemaSet> 中的架构进行验证。</span><span class="sxs-lookup"><span data-stu-id="3d84a-177">XML documents can be validated against schemas in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="3d84a-178">若要验证 XML 文档，可以将架构添加到 <xref:System.Xml.XmlReaderSettings> 对象的 <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> 属性中，也可以将 <xref:System.Xml.Schema.XmlSchemaSet> 添加到 <xref:System.Xml.XmlReaderSettings> 对象的 <xref:System.Xml.XmlReaderSettings.Schemas%2A> 属性中。</span><span class="sxs-lookup"><span data-stu-id="3d84a-178">You validate an XML document by adding a schema to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object, or by adding an <xref:System.Xml.Schema.XmlSchemaSet> to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="3d84a-179">然后，<xref:System.Xml.XmlReaderSettings> 类的 <xref:System.Xml.XmlReader.Create%2A> 方法使用 <xref:System.Xml.XmlReader> 对象创建一个 <xref:System.Xml.XmlReader> 对象并验证该 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="3d84a-179">The <xref:System.Xml.XmlReaderSettings> object is then used by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to create an <xref:System.Xml.XmlReader> object and validate the XML document.</span></span>  
  
 <span data-ttu-id="3d84a-180">若要详细了解如何使用 <xref:System.Xml.Schema.XmlSchemaSet> 验证 XML 文档，请参阅[使用 XmlSchemaSet 进行 XML 架构 (XSD) 验证](xml-schema-xsd-validation-with-xmlschemaset.md)。</span><span class="sxs-lookup"><span data-stu-id="3d84a-180">For more information about validating XML documents using an <xref:System.Xml.Schema.XmlSchemaSet>, see [XML Schema (XSD) Validation with XmlSchemaSet](xml-schema-xsd-validation-with-xmlschemaset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d84a-181">请参阅</span><span class="sxs-lookup"><span data-stu-id="3d84a-181">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [<span data-ttu-id="3d84a-182">XmlSchemaSet 作为架构缓存</span><span class="sxs-lookup"><span data-stu-id="3d84a-182">XmlSchemaSet as a Schema Cache</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="3d84a-183">使用 XmlSchemaSet 进行 XML 架构 (XSD) 验证</span><span class="sxs-lookup"><span data-stu-id="3d84a-183">XML Schema (XSD) Validation with XmlSchemaSet</span></span>](xml-schema-xsd-validation-with-xmlschemaset.md)
