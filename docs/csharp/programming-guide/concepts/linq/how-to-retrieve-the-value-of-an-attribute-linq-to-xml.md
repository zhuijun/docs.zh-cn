---
title: 如何检索特性的值 (LINQ to XML) (C#)
description: 了解如何获取属性的值。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 5ee6995a54829b6d992e2982e6a6effcabf76470
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301549"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="16af3-104">如何检索特性的值 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="16af3-104">How to retrieve the value of an attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="16af3-105">本主题说明如何获取属性的值。</span><span class="sxs-lookup"><span data-stu-id="16af3-105">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="16af3-106">主要有两种方法：可以将 <xref:System.Xml.Linq.XAttribute> 强制转换为所需的类型；然后，显式转换运算符将元素或属性的内容转换为指定的类型。</span><span class="sxs-lookup"><span data-stu-id="16af3-106">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="16af3-107">此外，还可以使用 <xref:System.Xml.Linq.XAttribute.Value%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="16af3-107">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="16af3-108">但是，强制转换通常是更好的方法。</span><span class="sxs-lookup"><span data-stu-id="16af3-108">However, casting is generally the better approach.</span></span> <span data-ttu-id="16af3-109">在检索不一定存在的属性的值时，如果将属性强制转换为可以为 null 的值类型，则代码会更易于编写。</span><span class="sxs-lookup"><span data-stu-id="16af3-109">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="16af3-110">有关此技术的示例，请参阅[如何检索元素的值 (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="16af3-110">For examples of this technique, see [How to retrieve the value of an element (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="16af3-111">示例</span><span class="sxs-lookup"><span data-stu-id="16af3-111">Example</span></span>  
 <span data-ttu-id="16af3-112">若要检索属性的值，只需将 <xref:System.Xml.Linq.XAttribute> 对象强制转换为所需的类型即可。</span><span class="sxs-lookup"><span data-stu-id="16af3-112">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="16af3-113">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="16af3-113">This example produces the following output:</span></span>  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="16af3-114">示例</span><span class="sxs-lookup"><span data-stu-id="16af3-114">Example</span></span>  
 <span data-ttu-id="16af3-115">下面的示例演示在属性处于命名空间中时，如何检索属性的值。</span><span class="sxs-lookup"><span data-stu-id="16af3-115">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="16af3-116">有关详细信息，请参阅[命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="16af3-116">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="16af3-117">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="16af3-117">This example produces the following output:</span></span>  
  
```output  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="16af3-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="16af3-118">See also</span></span>

- [<span data-ttu-id="16af3-119">LINQ to XML 轴 (C#)</span><span class="sxs-lookup"><span data-stu-id="16af3-119">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
