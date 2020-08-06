---
title: 如何针对命名空间中的 XML 编写查询 (C#)
description: 了解如何针对命名空间中的 XML 编写查询。 对于这些查询，必须使用具有正确命名空间的 XName 对象。
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 64eb9df1cde3b434a11e2e5410aab96993dc0fa1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303174"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a><span data-ttu-id="918c2-104">如何针对命名空间中的 XML 编写查询 (C#)</span><span class="sxs-lookup"><span data-stu-id="918c2-104">How to write queries on XML in namespaces (C#)</span></span>
<span data-ttu-id="918c2-105">若要针对命名空间中的 XML 编写查询，必须使用具有正确命名空间的 <xref:System.Xml.Linq.XName> 对象。</span><span class="sxs-lookup"><span data-stu-id="918c2-105">To write a query on XML that is in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>  
  
 <span data-ttu-id="918c2-106">对于 C#，最常用的方法是使用包含 URI 的字符串初始化 <xref:System.Xml.Linq.XNamespace>，然后使用加法运算符重载来组合命名空间和本地名称。</span><span class="sxs-lookup"><span data-stu-id="918c2-106">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>  
  
 <span data-ttu-id="918c2-107">本主题的第一个示例集演示如何在默认命名空间中创建一个 XML 树。</span><span class="sxs-lookup"><span data-stu-id="918c2-107">The first set of examples in this topic shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="918c2-108">第二个示例集演示如何在带有前缀的命名空间中创建一个 XML 树。</span><span class="sxs-lookup"><span data-stu-id="918c2-108">The second set shows how to create an XML tree in a namespace with a prefix.</span></span>  
  
## <a name="example"></a><span data-ttu-id="918c2-109">示例</span><span class="sxs-lookup"><span data-stu-id="918c2-109">Example</span></span>  
 <span data-ttu-id="918c2-110">下面的示例创建一个位于默认命名空间中的 XML 树。</span><span class="sxs-lookup"><span data-stu-id="918c2-110">The following example creates an XML tree that is in a default namespace.</span></span> <span data-ttu-id="918c2-111">然后检索元素的集合。</span><span class="sxs-lookup"><span data-stu-id="918c2-111">It then retrieves a collection of elements.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 <span data-ttu-id="918c2-112">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="918c2-112">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a><span data-ttu-id="918c2-113">示例</span><span class="sxs-lookup"><span data-stu-id="918c2-113">Example</span></span>  
 <span data-ttu-id="918c2-114">在 C# 中，无论是在使用带前缀的命名空间的 XML 树上编写查询，还是在使用默认命名空间的 XML 树上编写查询，都使用相同的方式。</span><span class="sxs-lookup"><span data-stu-id="918c2-114">In C#, you write queries in the same way regardless of whether you are writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>  
  
 <span data-ttu-id="918c2-115">下面的示例创建一个位于具有前缀的默认命名空间中的 XML 树。</span><span class="sxs-lookup"><span data-stu-id="918c2-115">The following example creates an XML tree that is in a namespace with a prefix.</span></span> <span data-ttu-id="918c2-116">然后检索元素的集合。</span><span class="sxs-lookup"><span data-stu-id="918c2-116">It then retrieves a collection of elements.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
    <aw:Child>1</aw:Child>  
    <aw:Child>2</aw:Child>  
    <aw:Child>3</aw:Child>  
    <aw:AnotherChild>4</aw:AnotherChild>  
    <aw:AnotherChild>5</aw:AnotherChild>  
    <aw:AnotherChild>6</aw:AnotherChild>  
</aw:Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 <span data-ttu-id="918c2-117">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="918c2-117">This example produces the following output:</span></span>  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a><span data-ttu-id="918c2-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="918c2-118">See also</span></span>

- [<span data-ttu-id="918c2-119">命名空间概述(LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="918c2-119">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
