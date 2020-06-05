---
title: 如何：查找具有特定元素名称的后代
ms.date: 07/20/2015
ms.assetid: 78915518-0d25-4051-ab55-929779989510
ms.openlocfilehash: 19e0807f3bb7e83061b2076a177107eec126e717
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405204"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-visual-basic"></a><span data-ttu-id="bde4a-102">如何：查找具有特定元素名称的子代（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="bde4a-102">How to: Find Descendants with a Specific Element Name (Visual Basic)</span></span>
<span data-ttu-id="bde4a-103">有时，您想要查找所有具有特定名称的子代。</span><span class="sxs-lookup"><span data-stu-id="bde4a-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="bde4a-104">可以编写代码用于循环访问所有子代，但使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 轴更简单。</span><span class="sxs-lookup"><span data-stu-id="bde4a-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bde4a-105">示例</span><span class="sxs-lookup"><span data-stu-id="bde4a-105">Example</span></span>  
 <span data-ttu-id="bde4a-106">下面的示例演示如何根据元素名称查找子代。</span><span class="sxs-lookup"><span data-stu-id="bde4a-106">The following example shows how to find descendants based on the element name.</span></span>  
  
```vb  
Dim root As XElement = _  
    <root>  
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
    </root>  
  
Dim textSegs As IEnumerable(Of String) = _  
    From seg In root...<t> _  
    Select seg.Value  
  
Dim str As String = textSegs.Aggregate( _  
    New StringBuilder, _  
    Function(sb, i) sb.Append(i), _  
    Function(sb) sb.ToString)  
  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="bde4a-107">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="bde4a-107">This code produces the following output:</span></span>  
  
```console  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="bde4a-108">示例</span><span class="sxs-lookup"><span data-stu-id="bde4a-108">Example</span></span>  
 <span data-ttu-id="bde4a-109">下面的示例演示如何对命名空间中的 XML 进行同样的查询。</span><span class="sxs-lookup"><span data-stu-id="bde4a-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="bde4a-110">有关详细信息，请参阅[命名空间概述（LINQ to XML）（Visual Basic）](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="bde4a-110">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <root>  
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
            </root>  
  
        Dim textSegs As IEnumerable(Of String) = _  
            From seg In root...<t> _  
            Select seg.Value  
  
        Dim str As String = textSegs.Aggregate( _  
            New StringBuilder, _  
            Function(sb, i) sb.Append(i), _  
            Function(sb) sb.ToString)  
  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="bde4a-111">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="bde4a-111">This code produces the following output:</span></span>  
  
```console  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="bde4a-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bde4a-112">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- [<span data-ttu-id="bde4a-113">基本查询（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="bde4a-113">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)
