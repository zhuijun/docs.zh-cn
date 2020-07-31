---
title: 如何控制命名空间前缀 (C#) (LINQ to XML)
description: 了解如何使用 C# 中的 LINQ to XML 序列化 XML 树时控制命名空间前缀。 在某些情况下，需要控制命名空间前缀。
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: b0c5cbfa7488f3a7105595830ef6765e6bfb1f12
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105306"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a><span data-ttu-id="ca2be-104">如何控制命名空间前缀 (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ca2be-104">How to control namespace prefixes (C#) (LINQ to XML)</span></span>
<span data-ttu-id="ca2be-105">本主题介绍在序列化 XML 树时如何控制命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="ca2be-105">This topic describes how you can control namespace prefixes when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="ca2be-106">在很多情况下，不需要控制命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="ca2be-106">In many situations, it is not necessary to control namespace prefixes.</span></span>  
  
 <span data-ttu-id="ca2be-107">但是，某些 XML 编程工具需要命名空间前缀的特定控制。</span><span class="sxs-lookup"><span data-stu-id="ca2be-107">However, certain XML programming tools require specific control of namespace prefixes.</span></span> <span data-ttu-id="ca2be-108">例如，您可能正在操作 XSLT 样式表或 XAML 文档，其中包含引用特定命名空间前缀的嵌入式 XPath 表达式，在这种情况下，一定要使用这些特定前缀对文档进行序列化。</span><span class="sxs-lookup"><span data-stu-id="ca2be-108">For example, you might be manipulating an XSLT style sheet or a XAML document that contains embedded XPath expressions that refer to specific namespace prefixes; in this case, it is important that the document be serialized with those specific prefixes.</span></span>  
  
 <span data-ttu-id="ca2be-109">这是控制命名空间前缀的最常见的原因。</span><span class="sxs-lookup"><span data-stu-id="ca2be-109">This is the most common reason for controlling namespace prefixes.</span></span>  
  
 <span data-ttu-id="ca2be-110">需要控制命名空间前缀的另一个常见原因是：您希望用户手动编辑 XML 文档，而且您希望创建方便用户键入的命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="ca2be-110">Another common reason for controlling namespace prefixes is that you want users to edit the XML document manually, and you want to create namespace prefixes that are convenient for the user to type.</span></span> <span data-ttu-id="ca2be-111">例如，您可能正在生成 XSD 文档。</span><span class="sxs-lookup"><span data-stu-id="ca2be-111">For example, you might be generating an XSD document.</span></span> <span data-ttu-id="ca2be-112">架构约定建议您使用 `xs` 或 `xsd` 作为架构命名空间的前缀。</span><span class="sxs-lookup"><span data-stu-id="ca2be-112">Conventions for schemas suggest that you use either `xs` or `xsd` as the prefix for the schema namespace.</span></span>  
  
 <span data-ttu-id="ca2be-113">若要控制命名空间前缀，请插入声明命名空间的属性。</span><span class="sxs-lookup"><span data-stu-id="ca2be-113">To control namespace prefixes, you insert attributes that declare namespaces.</span></span> <span data-ttu-id="ca2be-114">如果使用特定前缀声明命名空间，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 将在序列化时尝试接受此命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="ca2be-114">If you declare the namespaces with specific prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will attempt to honor the namespace prefixes when serializing.</span></span>  
  
 <span data-ttu-id="ca2be-115">若要创建一个声明具有前缀的命名空间的属性，请创建一个属性，该属性的名称的命名空间为 <xref:System.Xml.Linq.XNamespace.Xmlns%2A>，该属性的名称为命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="ca2be-115">To create an attribute that declares a namespace with a prefix, you create an attribute where the namespace of the name of the attribute is <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, and the name of the attribute is the namespace prefix.</span></span> <span data-ttu-id="ca2be-116">该属性的值即是命名空间的 URI。</span><span class="sxs-lookup"><span data-stu-id="ca2be-116">The value of the attribute is the URI of the namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca2be-117">示例</span><span class="sxs-lookup"><span data-stu-id="ca2be-117">Example</span></span>  
 <span data-ttu-id="ca2be-118">本示例声明两个命名空间。</span><span class="sxs-lookup"><span data-stu-id="ca2be-118">This example declares two namespaces.</span></span> <span data-ttu-id="ca2be-119">它指定 `http://www.adventure-works.com` 命名空间具有 `aw` 前缀，`www.fourthcoffee.com` 命名空间具有 `fc` 前缀。</span><span class="sxs-lookup"><span data-stu-id="ca2be-119">It specifies that the `http://www.adventure-works.com` namespace has the prefix of `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="ca2be-120">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="ca2be-120">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca2be-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="ca2be-121">See also</span></span>

- [<span data-ttu-id="ca2be-122">命名空间概述(LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ca2be-122">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
