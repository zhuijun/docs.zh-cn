---
title: 管理 XML 文档中的命名空间
description: 了解如何管理 XML 文档中的命名空间。 XML 命名空间将 XML 文档中的元素和属性名称与自定义和预定义的 URI 关联起来。
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
ms.openlocfilehash: 3a3abd2e932b1afecab85e285b0e2c42eb1eb20f
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769257"
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="68fa3-104">管理 XML 文档中的命名空间</span><span class="sxs-lookup"><span data-stu-id="68fa3-104">Managing Namespaces in an XML Document</span></span>
<span data-ttu-id="68fa3-105">XML 命名空间将 XML 文档中的元素和属性名称与自定义和预定义的 URI 关联起来。</span><span class="sxs-lookup"><span data-stu-id="68fa3-105">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="68fa3-106">要创建这些关联，您应为命名空间 URI 定义前缀，并使用这些前缀来限定 XML 数据中的元素和属性名称。</span><span class="sxs-lookup"><span data-stu-id="68fa3-106">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="68fa3-107">命名空间可防止元素和属性名称冲突，并允许以不同方式处理和验证同名的元素和属性。</span><span class="sxs-lookup"><span data-stu-id="68fa3-107">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>
## <a name="declaring-namespaces"></a><span data-ttu-id="68fa3-108">声明命名空间</span><span class="sxs-lookup"><span data-stu-id="68fa3-108">Declaring namespaces</span></span>  
 <span data-ttu-id="68fa3-109">若要对某个元素声明命名空间，请使用 `xmlns:` 属性：</span><span class="sxs-lookup"><span data-stu-id="68fa3-109">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="68fa3-110">其中，`<name>` 是命名空间前缀，`<"uri">` 是用于标识命名空间的 URI。</span><span class="sxs-lookup"><span data-stu-id="68fa3-110">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="68fa3-111">在声明前缀后，可使用该前缀来限定 XML 文档中的元素和属性，并将它们与命名空间 URI 相关联。</span><span class="sxs-lookup"><span data-stu-id="68fa3-111">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="68fa3-112">因为命名空间前缀在整个文档中使用，所以它的长度应较短。</span><span class="sxs-lookup"><span data-stu-id="68fa3-112">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="68fa3-113">本示例定义两个 `BOOK` 元素。</span><span class="sxs-lookup"><span data-stu-id="68fa3-113">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="68fa3-114">第一个元素由前缀 `mybook` 限定，第二个元素由前缀 `bb` 限定。</span><span class="sxs-lookup"><span data-stu-id="68fa3-114">The first element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="68fa3-115">每个前缀都与不同的命名空间 URI 相关联：</span><span class="sxs-lookup"><span data-stu-id="68fa3-115">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines" />
</mybook>
```  
  
 <span data-ttu-id="68fa3-116">若要指示某个元素是特定命名空间的一部分，请向其添加命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="68fa3-116">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="68fa3-117">例如，如果 `Author` 元素属于 `mybook` 命名空间，则将其声明为 `<mybook:Author>`。</span><span class="sxs-lookup"><span data-stu-id="68fa3-117">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>
## <a name="declaration-scope"></a><span data-ttu-id="68fa3-118">声明范围</span><span class="sxs-lookup"><span data-stu-id="68fa3-118">Declaration scope</span></span>  
 <span data-ttu-id="68fa3-119">命名空间在从声明点开始直至声明它的元素结束这一范围内有效。</span><span class="sxs-lookup"><span data-stu-id="68fa3-119">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="68fa3-120">在此示例中，在 `BOOK` 元素中定义的命名空间不适用于 `BOOK` 元素外部的元素（例如，`Publisher` 元素）：</span><span class="sxs-lookup"><span data-stu-id="68fa3-120">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
```xml  
<Author>Joe Smith</Author>  
<BOOK xmlns:book="http://www.contoso.com">  
    <title>My Wonderful Day</title>  
      <price>$3.95</price>  
</BOOK>  
<Publisher>  
    <Name>MSPress</Name>  
</Publisher>  
```  
  
 <span data-ttu-id="68fa3-121">必须先声明命名空间，然后才可以使用它，但命名空间不一定出现在 XML 文档的顶部。</span><span class="sxs-lookup"><span data-stu-id="68fa3-121">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="68fa3-122">当您在 XML 文档中使用多个命名空间时，可以将一个命名空间定义为默认命名空间以产生外观更整洁的文档。</span><span class="sxs-lookup"><span data-stu-id="68fa3-122">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="68fa3-123">默认命名空间是在根元素中声明的，它适用于文档中的所有非限定元素。</span><span class="sxs-lookup"><span data-stu-id="68fa3-123">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="68fa3-124">默认命名空间只适用于元素，不适用于属性。</span><span class="sxs-lookup"><span data-stu-id="68fa3-124">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="68fa3-125">若要使用默认命名空间，请在该元素的声明中省略前缀和冒号：</span><span class="sxs-lookup"><span data-stu-id="68fa3-125">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
...
</BOOK>
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="68fa3-126">管理命名空间</span><span class="sxs-lookup"><span data-stu-id="68fa3-126">Managing namespaces</span></span>  
 <span data-ttu-id="68fa3-127"><xref:System.Xml.XmlNamespaceManager> 类存储命名空间 URI 及其前缀的集合，您可在此集合中查找、添加和删除命名空间。</span><span class="sxs-lookup"><span data-stu-id="68fa3-127">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="68fa3-128">在某些上下文中，需要使用此类以获得更佳 XML 处理性能。</span><span class="sxs-lookup"><span data-stu-id="68fa3-128">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="68fa3-129">例如，<xref:System.Xml.Xsl.XsltContext> 类使用 <xref:System.Xml.XmlNamespaceManager> 以获得 XPath 支持。</span><span class="sxs-lookup"><span data-stu-id="68fa3-129">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="68fa3-130">命名空间管理器对命名空间不执行任何验证，而是假定前缀和命名空间已经过验证并符合 [W3C 命名空间](https://www.w3.org/TR/REC-xml-names/)规范。</span><span class="sxs-lookup"><span data-stu-id="68fa3-130">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](https://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68fa3-131">[C#](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) 和 [Visual Basic](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) 中的 LINQ TO XML 不使用 <xref:System.Xml.XmlNamespaceManager> 来管理命名空间。</span><span class="sxs-lookup"><span data-stu-id="68fa3-131">LINQ TO XML in [C#](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [Visual Basic](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) don't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="68fa3-132">若要了解如何在使用 LINQ to XML 时管理命名空间，请参阅 LINQ 文档中的[使用 XML 命名空间 (C#)](../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md) 和[使用 XML 命名空间 (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="68fa3-132">See [Working with XML Namespaces (C#)](../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md) and [Working with XML Namespaces (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="68fa3-133">下面是可使用 <xref:System.Xml.XmlNamespaceManager> 类执行的一些管理和查找任务。</span><span class="sxs-lookup"><span data-stu-id="68fa3-133">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="68fa3-134">有关更多信息和示例，请遵循指向每个方法或属性的引用页的链接。</span><span class="sxs-lookup"><span data-stu-id="68fa3-134">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="68fa3-135">功能</span><span class="sxs-lookup"><span data-stu-id="68fa3-135">To</span></span>|<span data-ttu-id="68fa3-136">使用</span><span class="sxs-lookup"><span data-stu-id="68fa3-136">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="68fa3-137">添加命名空间</span><span class="sxs-lookup"><span data-stu-id="68fa3-137">Add a namespace</span></span>|<span data-ttu-id="68fa3-138"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="68fa3-138"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="68fa3-139">移除命名空间</span><span class="sxs-lookup"><span data-stu-id="68fa3-139">Remove a namespace</span></span>|<span data-ttu-id="68fa3-140"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="68fa3-140"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="68fa3-141">查找默认命名空间的 URI</span><span class="sxs-lookup"><span data-stu-id="68fa3-141">Find the URI for the default namespace</span></span>|<span data-ttu-id="68fa3-142"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> 属性</span><span class="sxs-lookup"><span data-stu-id="68fa3-142"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="68fa3-143">查找命名空间前缀的 URI</span><span class="sxs-lookup"><span data-stu-id="68fa3-143">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="68fa3-144"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="68fa3-144"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="68fa3-145">查找命名空间 URI 的前缀</span><span class="sxs-lookup"><span data-stu-id="68fa3-145">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="68fa3-146"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="68fa3-146"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="68fa3-147">获取当前节点中命名空间的列表</span><span class="sxs-lookup"><span data-stu-id="68fa3-147">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="68fa3-148"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="68fa3-148"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="68fa3-149">限定命名空间的范围</span><span class="sxs-lookup"><span data-stu-id="68fa3-149">Scope a namespace</span></span>|<span data-ttu-id="68fa3-150"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> 和 <xref:System.Xml.XmlNamespaceManager.PopScope%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="68fa3-150"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="68fa3-151">检查是否在当前范围内定义了前缀</span><span class="sxs-lookup"><span data-stu-id="68fa3-151">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="68fa3-152"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> 方法</span><span class="sxs-lookup"><span data-stu-id="68fa3-152"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="68fa3-153">获取用于查找前缀和 URI 的名称表</span><span class="sxs-lookup"><span data-stu-id="68fa3-153">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="68fa3-154"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> 属性</span><span class="sxs-lookup"><span data-stu-id="68fa3-154"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68fa3-155">请参阅</span><span class="sxs-lookup"><span data-stu-id="68fa3-155">See also</span></span>

- <xref:System.Xml.XmlNamespaceManager>
- [<span data-ttu-id="68fa3-156">XML 文档和数据</span><span class="sxs-lookup"><span data-stu-id="68fa3-156">XML Documents and Data</span></span>](index.md)
