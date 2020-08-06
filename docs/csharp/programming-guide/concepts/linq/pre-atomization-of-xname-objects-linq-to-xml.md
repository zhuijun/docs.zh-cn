---
title: XName 对象的预原子化 (LINQ to XML) (C#)
description: 了解 XName 对象的预原子化。 当创建重复出现特定名称的大型 XML 树时，预原子化对象可以提高性能。
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 4d217f6c78dc5d83ce424fb3ba95785f2dac0b73
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302823"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a><span data-ttu-id="efa56-104">XName 对象的预原子化 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="efa56-104">Pre-Atomization of XName Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="efa56-105">提高 LINQ to XML 中的性能的一种方法是预原子化 <xref:System.Xml.Linq.XName> 对象。</span><span class="sxs-lookup"><span data-stu-id="efa56-105">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="efa56-106">预原子化是指在通过使用 <xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XElement> 类的构造函数创建 XML 树之前，先将字符串分配给 <xref:System.Xml.Linq.XAttribute> 对象。</span><span class="sxs-lookup"><span data-stu-id="efa56-106">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="efa56-107">然后传递初始化的 <xref:System.Xml.Linq.XName> 对象，而不是将字符串传递给构造函数（此过程将使用从字符串到 <xref:System.Xml.Linq.XName> 的隐式转换）。</span><span class="sxs-lookup"><span data-stu-id="efa56-107">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="efa56-108">当创建其中重复出现特定名称的大型 XML 树时，这样可以提高性能。</span><span class="sxs-lookup"><span data-stu-id="efa56-108">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="efa56-109">为此，请在构造 XML 树之前声明和初始化 <xref:System.Xml.Linq.XName> 对象，然后使用 <xref:System.Xml.Linq.XName> 对象，而不是指定元素和属性名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="efa56-109">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="efa56-110">当创建大量具有相同名称的元素（或属性）时，此技术可以显著提高性能。</span><span class="sxs-lookup"><span data-stu-id="efa56-110">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="efa56-111">应针对您的方案测试预原子化以确定是否应使用它。</span><span class="sxs-lookup"><span data-stu-id="efa56-111">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efa56-112">示例</span><span class="sxs-lookup"><span data-stu-id="efa56-112">Example</span></span>  
 <span data-ttu-id="efa56-113">下面的示例演示这一操作。</span><span class="sxs-lookup"><span data-stu-id="efa56-113">The following example demonstrates this.</span></span>  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="efa56-114">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="efa56-114">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="efa56-115">下面的示例演示针对命名空间中的 XML 文档的相同技术：</span><span class="sxs-lookup"><span data-stu-id="efa56-115">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XName Root = aw + "Root";  
XName Data = aw + "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XAttribute(XNamespace.Xmlns + "aw", aw),  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="efa56-116">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="efa56-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="efa56-117">下面的示例更类似于实际中可能遇到的情况。</span><span class="sxs-lookup"><span data-stu-id="efa56-117">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="efa56-118">在此示例中，元素的内容由查询提供：</span><span class="sxs-lookup"><span data-stu-id="efa56-118">In this example, the content of the element is supplied by a query:</span></span>  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
DateTime t1 = DateTime.Now;  
XElement root = new XElement(Root,  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement(Data,  
        new XAttribute(ID, i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
 <span data-ttu-id="efa56-119">上一示例的执行性能优于下面的示例（其中未对名称进行预原子化）：</span><span class="sxs-lookup"><span data-stu-id="efa56-119">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
```csharp  
DateTime t1 = DateTime.Now;  
XElement root = new XElement("Root",  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement("Data",  
        new XAttribute("ID", i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="efa56-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="efa56-120">See also</span></span>

- [<span data-ttu-id="efa56-121">原子化的 XName 和 XNamespace 对象 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="efa56-121">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>](./atomized-xname-and-xnamespace-objects-linq-to-xml.md)
