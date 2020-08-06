---
title: 如何筛选可选元素 (C#)
description: 了解如何筛选可选元素，即使不能确定该元素是否存在于 XML 文档中，也是如此。
ms.date: 07/20/2015
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: a1cd93b70ea2c077437b58bd341f51f15f014871
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302862"
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="ce830-103">如何筛选可选元素 (C#)</span><span class="sxs-lookup"><span data-stu-id="ce830-103">How to filter on an optional element (C#)</span></span>
<span data-ttu-id="ce830-104">有时，尽管不能确定某个元素是否存在于 XML 文档中，您还是会尝试筛选该元素。</span><span class="sxs-lookup"><span data-stu-id="ce830-104">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="ce830-105">应当执行搜索，这样如果特定元素没有子元素，就不会因为筛选它而触发空引用异常。</span><span class="sxs-lookup"><span data-stu-id="ce830-105">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="ce830-106">在下面的示例中，`Child5` 元素没有 `Type` 子元素，但是查询仍可以正确执行。</span><span class="sxs-lookup"><span data-stu-id="ce830-106">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce830-107">示例</span><span class="sxs-lookup"><span data-stu-id="ce830-107">Example</span></span>  
 <span data-ttu-id="ce830-108">本示例使用 <xref:System.Xml.Linq.Extensions.Elements%2A> 扩展方法。</span><span class="sxs-lookup"><span data-stu-id="ce830-108">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
var cList =  
    from typeElement in root.Elements().Elements("Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element("Text");  
foreach(string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="ce830-109">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="ce830-109">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="ce830-110">示例</span><span class="sxs-lookup"><span data-stu-id="ce830-110">Example</span></span>  
 <span data-ttu-id="ce830-111">下面的示例演示如何对命名空间中的 XML 进行同样的查询。</span><span class="sxs-lookup"><span data-stu-id="ce830-111">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="ce830-112">有关详细信息，请参阅[命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="ce830-112">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
XNamespace ad = "http://www.adatum.com";  
var cList =  
    from typeElement in root.Elements().Elements(ad + "Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element(ad + "Text");  
foreach (string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="ce830-113">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="ce830-113">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce830-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="ce830-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ce830-115">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="ce830-115">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="ce830-116">投影运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="ce830-116">Projection Operations (C#)</span></span>](./projection-operations.md)
