---
title: 如何查找具有特定元素名称的后代 (C#)
description: 了解如何使用子代轴查找具有特定名称的所有子代。 查看代码示例和其他资源。
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: 96ebf2d10a9ed5e07aab2870142f9869903ad442
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303239"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a><span data-ttu-id="ba679-104">如何查找具有特定元素名称的后代 (C#)</span><span class="sxs-lookup"><span data-stu-id="ba679-104">How to find descendants with a specific element name (C#)</span></span>
<span data-ttu-id="ba679-105">有时，您想要查找所有具有特定名称的子代。</span><span class="sxs-lookup"><span data-stu-id="ba679-105">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="ba679-106">可以编写代码用于循环访问所有子代，但使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 轴更简单。</span><span class="sxs-lookup"><span data-stu-id="ba679-106">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba679-107">示例</span><span class="sxs-lookup"><span data-stu-id="ba679-107">Example</span></span>  
 <span data-ttu-id="ba679-108">下面的示例演示如何根据元素名称查找子代。</span><span class="sxs-lookup"><span data-stu-id="ba679-108">The following example shows how to find descendants based on the element name.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<root>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
IEnumerable<string> textSegs =  
    from seg in root.Descendants("t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="ba679-109">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="ba679-109">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="ba679-110">示例</span><span class="sxs-lookup"><span data-stu-id="ba679-110">Example</span></span>  
 <span data-ttu-id="ba679-111">下面的示例演示如何对命名空间中的 XML 进行同样的查询。</span><span class="sxs-lookup"><span data-stu-id="ba679-111">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="ba679-112">有关详细信息，请参阅[命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="ba679-112">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<root xmlns='http://www.adatum.com'>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<string> textSegs =  
    from seg in root.Descendants(ad + "t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="ba679-113">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="ba679-113">This code produces the following output:</span></span>  
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba679-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ba679-114">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
