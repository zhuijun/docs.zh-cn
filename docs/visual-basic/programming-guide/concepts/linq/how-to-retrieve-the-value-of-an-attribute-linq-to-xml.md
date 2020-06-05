---
title: 如何：检索属性的值 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
ms.openlocfilehash: 48ad3c0ab079012793fd9eea89d52fc3a7b1698f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397799"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="6ff46-102">如何：检索特性的值（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="6ff46-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="6ff46-103">本主题说明如何获取属性的值。</span><span class="sxs-lookup"><span data-stu-id="6ff46-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="6ff46-104">主要有两种方法：可以将 <xref:System.Xml.Linq.XAttribute> 强制转换为所需的类型；然后，显式转换运算符将元素或属性的内容转换为指定的类型。</span><span class="sxs-lookup"><span data-stu-id="6ff46-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="6ff46-105">此外，还可以使用 <xref:System.Xml.Linq.XAttribute.Value%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="6ff46-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="6ff46-106">但是，强制转换通常是更好的方法。</span><span class="sxs-lookup"><span data-stu-id="6ff46-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="6ff46-107">在检索不一定存在的属性的值时，如果将属性强制转换为可以为 null 的值类型，则代码会更易于编写。</span><span class="sxs-lookup"><span data-stu-id="6ff46-107">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="6ff46-108">有关此技术的示例，请参阅[如何：检索元素的值（LINQ to XML）（Visual Basic）](how-to-retrieve-the-value-of-an-element-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff46-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ff46-109">示例</span><span class="sxs-lookup"><span data-stu-id="6ff46-109">Example</span></span>  
 <span data-ttu-id="6ff46-110">在 Visual Basic 中，可以使用集成的属性 (Attribute) 属性 (Property) 来检索属性 (Attribute) 的值。</span><span class="sxs-lookup"><span data-stu-id="6ff46-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="6ff46-111">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="6ff46-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="6ff46-112">示例</span><span class="sxs-lookup"><span data-stu-id="6ff46-112">Example</span></span>  
 <span data-ttu-id="6ff46-113">在 Visual Basic 中，可以使用集成的属性 (Attribute) 属性 (Property) 来设置属性 (Attribute) 的值。</span><span class="sxs-lookup"><span data-stu-id="6ff46-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="6ff46-114">此外，如果使用集成的属性 (Attribute) 属性 (Property) 来设置不存在的属性 (Attribute) 的值，则会创建该属性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="6ff46-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="6ff46-115">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="6ff46-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="6ff46-116">示例</span><span class="sxs-lookup"><span data-stu-id="6ff46-116">Example</span></span>  
 <span data-ttu-id="6ff46-117">下面的示例演示在属性处于命名空间中时，如何检索属性的值。</span><span class="sxs-lookup"><span data-stu-id="6ff46-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="6ff46-118">有关详细信息，请参阅[命名空间概述（LINQ to XML）（Visual Basic）](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff46-118">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>  
        Dim str As String = root.@aw:Attr  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="6ff46-119">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="6ff46-119">This example produces the following output:</span></span>  
  
```console  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ff46-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="6ff46-120">See also</span></span>

- [<span data-ttu-id="6ff46-121">LINQ to XML 轴 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ff46-121">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
