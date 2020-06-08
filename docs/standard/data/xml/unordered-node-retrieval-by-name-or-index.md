---
title: 按名称或索引检索未排序节点
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
ms.openlocfilehash: 6847f3c5d233b720f8f4c41cfc52ac663e5e810f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288623"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a><span data-ttu-id="c3010-102">按名称或索引检索未排序节点</span><span class="sxs-lookup"><span data-stu-id="c3010-102">Unordered Node Retrieval by Name or Index</span></span>
<span data-ttu-id="c3010-103">XmlNamedNodeMap  在万维网联合会 (W3C) 规范中被描述为 NamedNodeMap，它对于处理未排序的节点集并能够按节点名称或索引引用节点是必需的。</span><span class="sxs-lookup"><span data-stu-id="c3010-103">The **XmlNamedNodeMap** is described in the World Wide Web Consortium (W3C) specification as the NamedNodeMap and is required to handle an unordered set of nodes with the ability to reference nodes by their name or index.</span></span> <span data-ttu-id="c3010-104">访问 XmlNamedNodeMap  的唯一方式是通过方法或属性返回 XmlNamedNodeMap  。</span><span class="sxs-lookup"><span data-stu-id="c3010-104">The only way you have access to an **XmlNamedNodeMap** is when an **XmlNamedNodeMap** is returned through a method or property.</span></span> <span data-ttu-id="c3010-105">有三个方法或属性返回 XmlNamedNodeMap  ：</span><span class="sxs-lookup"><span data-stu-id="c3010-105">There are three methods or properties that return an **XmlNamedNodeMap**:</span></span>  
  
- <span data-ttu-id="c3010-106">XmlElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="c3010-106">XmlElement.Attributes</span></span>  
  
- <span data-ttu-id="c3010-107">XmlDocumentType.Entities</span><span class="sxs-lookup"><span data-stu-id="c3010-107">XmlDocumentType.Entities</span></span>  
  
- <span data-ttu-id="c3010-108">XmlDocumentType.Notations</span><span class="sxs-lookup"><span data-stu-id="c3010-108">XmlDocumentType.Notations</span></span>  
  
 <span data-ttu-id="c3010-109">例如，XmlDocumentType.Entities  属性获取在文档类型声明中声明的 XmlEntity  节点集合。</span><span class="sxs-lookup"><span data-stu-id="c3010-109">For example, the **XmlDocumentType.Entities** property gets the collection of **XmlEntity** nodes declared in the document type declaration.</span></span> <span data-ttu-id="c3010-110">此集合作为 XmlNamedNodeMap  返回，可以使用 Count  属性循环访问此集合并显示实体信息。</span><span class="sxs-lookup"><span data-stu-id="c3010-110">This collection is returned as an **XmlNamedNodeMap**, and you can iterate through the collection with the use of the **Count** property and display entity information.</span></span> <span data-ttu-id="c3010-111">有关循环访问 XmlNamedNodeMap  的示例，请参见 <xref:System.Xml.XmlDocumentType.Entities%2A>。</span><span class="sxs-lookup"><span data-stu-id="c3010-111">For an example of iterating through an **XmlNamedNodeMap**, see <xref:System.Xml.XmlDocumentType.Entities%2A>.</span></span>  
  
 <span data-ttu-id="c3010-112"> XmlAttributeCollection 派生自 XmlNamedNodeMap  ，且只有属性是可以修改的，而表示法和实体则是只读的。</span><span class="sxs-lookup"><span data-stu-id="c3010-112">The **XmlAttributeCollection** is derived from **XmlNamedNodeMap** and only attributes are modifiable, while notations and entities are read-only.</span></span> <span data-ttu-id="c3010-113">通过将 XmlNamedNodeMap  用于属性，可以基于属性的 XML 名称获取这些属性的节点。</span><span class="sxs-lookup"><span data-stu-id="c3010-113">Using the **XmlNamedNodeMap** for the attributes, you can get nodes for those attributes based on their XML names.</span></span> <span data-ttu-id="c3010-114">这样，提供了一个处理元素节点的属性集合的简单方法。</span><span class="sxs-lookup"><span data-stu-id="c3010-114">This provides an easy method for manipulating the collection of attributes on an element node.</span></span> <span data-ttu-id="c3010-115">该方法可与 XmlNodeList  直接进行比较，后者也实现 IEnumerable  接口但使用的是索引访问器而不是字符串。</span><span class="sxs-lookup"><span data-stu-id="c3010-115">This can be contrasted directly with **XmlNodeList**, which also implements the **IEnumerable** interface, but with an index accessor rather than a string.</span></span> <span data-ttu-id="c3010-116">RemoveNamedItem  和 SetNamedItem  方法只针对 XmlAttributeCollection  使用。</span><span class="sxs-lookup"><span data-stu-id="c3010-116">The **RemoveNamedItem** and **SetNamedItem** methods are only used against an **XmlAttributeCollection**.</span></span> <span data-ttu-id="c3010-117">属性集合中的添加或移除操作（无论是使用 AttributeCollection  还是 XmlNamedNodeMap  实现）将修改元素的属性集合。</span><span class="sxs-lookup"><span data-stu-id="c3010-117">Adding or removing from an attribute collection, whether using the **AttributeCollection** or the **XmlNamedNodeMap** implementation, modifies the attribute collection on the element.</span></span> <span data-ttu-id="c3010-118">下面的代码示例显示如何移动属性并创建新属性。</span><span class="sxs-lookup"><span data-stu-id="c3010-118">The following code example shows how to move an attribute and create a new attribute.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
  
Class test  
  
    Public Shared Sub Main()  
        Dim doc As New XmlDocument()  
        doc.LoadXml("<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> ")  
  
        ' Get the attributes of node "child2 "  
        Dim ac As XmlAttributeCollection = doc.DocumentElement.ChildNodes(1).Attributes  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
        Dim i As Integer  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Get the 'attr1' from child1.  
        Dim attr As XmlAttribute = doc.DocumentElement.ChildNodes(0).Attributes(0)  
  
        ' Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem(attr)  
  
        ''attr1' will be removed from 'child1' and added to 'child2'.  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Create a new attribute and add to the collection.  
        Dim attr2 As XmlAttribute = doc.CreateAttribute("attr4")  
        attr2.Value = "val4"  
        ac.SetNamedItem(attr2)  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
    End Sub 'Main  
End Class 'test  
```  
  
```csharp  
using System;  
using System.Xml;  
class test {  
    public static void Main() {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml( "<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> " );  
  
        // Get the attributes of node "child2"  
        XmlAttributeCollection ac = doc.DocumentElement.ChildNodes[1].Attributes;  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );  
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );
  
        // Get the 'attr1' from child1.  
        XmlAttribute attr = doc.DocumentElement.ChildNodes[0].Attributes[0];  
  
        // Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem( attr );  
  
        // 'attr1' will be removed from 'child1' and added to 'child2'.  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );
  
        // Create a new attribute and add to the collection.  
        XmlAttribute attr2 = doc.CreateAttribute( "attr4" );  
        attr2.Value = "val4";  
        ac.SetNamedItem( attr2 );  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );
  
    }  
}  
```  
  
 <span data-ttu-id="c3010-119">若要查看另一个显示从 AttributeCollection  中移除属性的代码示例，请参见 [XmlNamedNodeMap.RemoveNamedItem 方法](xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A)。</span><span class="sxs-lookup"><span data-stu-id="c3010-119">To see an additional code example which shows an attribute being removed from an **AttributeCollection**, see [XmlNamedNodeMap.RemoveNamedItem Method](xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A).</span></span> <span data-ttu-id="c3010-120">有关方法和属性的更多信息，请参见 [XmlNamedNodeMap 成员](xref:System.Xml.XmlNamedNodeMap)。</span><span class="sxs-lookup"><span data-stu-id="c3010-120">For more information on the methods and properties, see [XmlNamedNodeMap Members](xref:System.Xml.XmlNamedNodeMap).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3010-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="c3010-121">See also</span></span>

- [<span data-ttu-id="c3010-122">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="c3010-122">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
