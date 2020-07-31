---
title: 原子化的 XName 和 XNamespace 对象 (LINQ to XML) (C#)
description: 了解原子化的 XName 和 XNamespace 对象以及它们如何为查询提供性能优势。
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: 305a233adab5c860b5f9509ae25ccc5d633e7957
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104276"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a><span data-ttu-id="c3515-103">原子化的 XName 和 XNamespace 对象 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c3515-103">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="c3515-104"><xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 对象进行了原子化；即，如果这两个对象包含相同的限定名，则它们将引用同一个对象。</span><span class="sxs-lookup"><span data-stu-id="c3515-104"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="c3515-105">这将提高查询性能：当比较两个原子化名称是否相等时，基础中间语言只需确定这两个引用是否指向同一个对象。</span><span class="sxs-lookup"><span data-stu-id="c3515-105">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="c3515-106">基础代码不必进行很耗费时间的字符串比较。</span><span class="sxs-lookup"><span data-stu-id="c3515-106">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="c3515-107">原子化语义</span><span class="sxs-lookup"><span data-stu-id="c3515-107">Atomization Semantics</span></span>  
 <span data-ttu-id="c3515-108">原子化是指如果两个 <xref:System.Xml.Linq.XName> 对象具有相同的本地名称并且位于同一个命名空间中，则它们共享相同的实例。</span><span class="sxs-lookup"><span data-stu-id="c3515-108">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="c3515-109">同样，如果两个 <xref:System.Xml.Linq.XNamespace> 对象具有相同的命名空间 URI，则它们共享同一个实例。</span><span class="sxs-lookup"><span data-stu-id="c3515-109">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="c3515-110">对于启用原子化对象的类，该类的构造函数必须是私有的，而不是公共的。</span><span class="sxs-lookup"><span data-stu-id="c3515-110">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="c3515-111">这是因为如果构造函数是公共的，则您可以创建非原子化对象。</span><span class="sxs-lookup"><span data-stu-id="c3515-111">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="c3515-112"><xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 类实现一个隐式转换运算符，以将字符串转换为 <xref:System.Xml.Linq.XName> 或 <xref:System.Xml.Linq.XNamespace>。</span><span class="sxs-lookup"><span data-stu-id="c3515-112">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="c3515-113">这是获取这些对象的实例的方式。</span><span class="sxs-lookup"><span data-stu-id="c3515-113">This is how you get an instance of these objects.</span></span> <span data-ttu-id="c3515-114">不能通过使用构造函数来获得实例，因为构造函数是不可访问的。</span><span class="sxs-lookup"><span data-stu-id="c3515-114">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="c3515-115"><xref:System.Xml.Linq.XName> 和 <xref:System.Xml.Linq.XNamespace> 还实现相等运算符和不相等运算符，以确定进行比较的两个对象是否引用相同的实例。</span><span class="sxs-lookup"><span data-stu-id="c3515-115"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3515-116">示例</span><span class="sxs-lookup"><span data-stu-id="c3515-116">Example</span></span>  
 <span data-ttu-id="c3515-117">下面的代码创建一些 <xref:System.Xml.Linq.XElement> 对象，并演示相同的名称共享同一个实例。</span><span class="sxs-lookup"><span data-stu-id="c3515-117">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
```csharp  
XElement r1 = new XElement("Root", "data1");  
XElement r2 = XElement.Parse("<Root>data2</Root>");  
  
if ((object)r1.Name == (object)r2.Name)  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");  
else  
    Console.WriteLine("Different");  
  
XName n = "Root";  
  
if ((object)n == (object)r1.Name)  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");  
else  
    Console.WriteLine("Different");  
```  
  
 <span data-ttu-id="c3515-118">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="c3515-118">This example produces the following output:</span></span>  
  
```output  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="c3515-119">如前面所述，原子化对象的好处是：当使用某个采用 <xref:System.Xml.Linq.XName> 作为参数的轴方法时，该轴方法只需确定这两个名称引用同一个实例来选择所需的元素。</span><span class="sxs-lookup"><span data-stu-id="c3515-119">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="c3515-120">下面的示例将 <xref:System.Xml.Linq.XName> 传递给 <xref:System.Xml.Linq.XContainer.Descendants%2A> 方法调用，该调用会由于使用原子化模式而获得更好的性能。</span><span class="sxs-lookup"><span data-stu-id="c3515-120">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("C1", 1),  
    new XElement("Z1",  
        new XElement("C1", 2),  
        new XElement("C1", 1)  
    )  
);  
  
var query = from e in root.Descendants("C1")  
            where (int)e == 1  
            select e;  
  
foreach (var z in query)  
    Console.WriteLine(z);  
```  
  
 <span data-ttu-id="c3515-121">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="c3515-121">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
