---
title: 维护名称-值对 (C#)
description: LINQ to XML 包含一些方法，这些方法使维护名称/值对变得更容易，无论是作为属性还是作为一组子元素。
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 92a45d160cbb1ef470d93bf740d0b6f584681e72
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165278"
---
# <a name="maintaining-namevalue-pairs-c"></a><span data-ttu-id="6c30f-103">维护名称/值对 (C#)</span><span class="sxs-lookup"><span data-stu-id="6c30f-103">Maintaining Name/Value Pairs (C#)</span></span>
<span data-ttu-id="6c30f-104">很多应用程序都必须维护需要保存为名称/值对的信息。</span><span class="sxs-lookup"><span data-stu-id="6c30f-104">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="6c30f-105">此信息可能是配置信息或全局设置。</span><span class="sxs-lookup"><span data-stu-id="6c30f-105">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="6c30f-106">包含一些方法，能轻松保存一组名称/值对。</span><span class="sxs-lookup"><span data-stu-id="6c30f-106">contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="6c30f-107">可以将这些信息保存为属性，也可以保存为一组子元素。</span><span class="sxs-lookup"><span data-stu-id="6c30f-107">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="6c30f-108">将信息保存为属性和保存为子元素之间的区别在于属性具有约束，对于一个元素，只能有一个属性具有特定的名称。</span><span class="sxs-lookup"><span data-stu-id="6c30f-108">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="6c30f-109">而这种限制不适用于子元素。</span><span class="sxs-lookup"><span data-stu-id="6c30f-109">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="6c30f-110">SetAttributeValue 与 SetElementValue</span><span class="sxs-lookup"><span data-stu-id="6c30f-110">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="6c30f-111">两种有助于保存名称/值对的方法是 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 和 <xref:System.Xml.Linq.XElement.SetElementValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c30f-111">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="6c30f-112">这两种方法具有相似的语义。</span><span class="sxs-lookup"><span data-stu-id="6c30f-112">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="6c30f-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 可以添加、修改或移除元素的属性。</span><span class="sxs-lookup"><span data-stu-id="6c30f-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
- <span data-ttu-id="6c30f-114">如果使用不存在的属性的名称调用 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>，则该方法会创建一个新属性并将该属性添加到指定的元素中。</span><span class="sxs-lookup"><span data-stu-id="6c30f-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="6c30f-115">如果使用现有属性的名称调用 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>，并指定一些内容，则会用指定内容替换属性的内容。</span><span class="sxs-lookup"><span data-stu-id="6c30f-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="6c30f-116">如果使用现有属性的名称调用 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>，并指定内容为空，则会从该属性的父级移除该属性。</span><span class="sxs-lookup"><span data-stu-id="6c30f-116">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="6c30f-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A> 可以添加、修改或移除元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="6c30f-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
- <span data-ttu-id="6c30f-118">如果使用不存在的子元素的名称调用 <xref:System.Xml.Linq.XElement.SetElementValue%2A>，则该方法会创建一个新元素并将该新元素添加到指定的元素中。</span><span class="sxs-lookup"><span data-stu-id="6c30f-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
- <span data-ttu-id="6c30f-119">如果使用现有元素的名称调用 <xref:System.Xml.Linq.XElement.SetElementValue%2A>，并指定一些内容，则会用指定内容替换元素的内容。</span><span class="sxs-lookup"><span data-stu-id="6c30f-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
- <span data-ttu-id="6c30f-120">如果使用现有元素的名称调用 <xref:System.Xml.Linq.XElement.SetElementValue%2A>，并指定内容为空，则会从该元素的父级移除该元素。</span><span class="sxs-lookup"><span data-stu-id="6c30f-120">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c30f-121">示例</span><span class="sxs-lookup"><span data-stu-id="6c30f-121">Example</span></span>  
 <span data-ttu-id="6c30f-122">下面的示例创建一个没有属性的元素。</span><span class="sxs-lookup"><span data-stu-id="6c30f-122">The following example creates an element with no attributes.</span></span> <span data-ttu-id="6c30f-123">之后使用 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 方法创建一个名称/值对列表并维护该列表。</span><span class="sxs-lookup"><span data-stu-id="6c30f-123">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22);  
root.SetAttributeValue("Left", 20);  
root.SetAttributeValue("Bottom", 122);  
root.SetAttributeValue("Right", 300);  
root.SetAttributeValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
  
// Replace the value of Top.  
root.SetAttributeValue("Top", 10);  
Console.WriteLine(root);  
  
// Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="6c30f-124">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="6c30f-124">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="6c30f-125">示例</span><span class="sxs-lookup"><span data-stu-id="6c30f-125">Example</span></span>  
 <span data-ttu-id="6c30f-126">下面的示例创建一个没有子元素的元素。</span><span class="sxs-lookup"><span data-stu-id="6c30f-126">The following example creates an element with no child elements.</span></span> <span data-ttu-id="6c30f-127">之后使用 <xref:System.Xml.Linq.XElement.SetElementValue%2A> 方法创建一个名称/值对列表并维护该列表。</span><span class="sxs-lookup"><span data-stu-id="6c30f-127">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22);  
root.SetElementValue("Left", 20);  
root.SetElementValue("Bottom", 122);  
root.SetElementValue("Right", 300);  
root.SetElementValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Replace the value of Top.  
root.SetElementValue("Top", 10);  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Remove DefaultColor.  
root.SetElementValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="6c30f-128">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="6c30f-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6c30f-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="6c30f-129">See also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
- [<span data-ttu-id="6c30f-130">修改 XML 树 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6c30f-130">Modifying XML Trees (LINQ to XML) (C#)</span></span>](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)
