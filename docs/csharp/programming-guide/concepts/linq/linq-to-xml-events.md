---
title: LINQ to XML 事件 (C#)
description: 使用 C# 将 LINQ to XML 事件添加到任意 XObject 实例中。 修改该 XObject 的 XML 树时，事件处理程序将收到事件。
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 576b0a5d0472bddd66e01d3bef8f3affa1c9458b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165416"
---
# <a name="linq-to-xml-events-c"></a><span data-ttu-id="25057-104">LINQ to XML 事件 (C#)</span><span class="sxs-lookup"><span data-stu-id="25057-104">LINQ to XML Events (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="25057-105">事件使你可以在 XML 树发生改变时得到通知。</span><span class="sxs-lookup"><span data-stu-id="25057-105">events enable you to be notified when an XML tree is altered.</span></span>  
  
 <span data-ttu-id="25057-106">可以将事件添加到任何 <xref:System.Xml.Linq.XObject> 的实例。</span><span class="sxs-lookup"><span data-stu-id="25057-106">You can add events to an instance of any <xref:System.Xml.Linq.XObject>.</span></span> <span data-ttu-id="25057-107">事件处理程序然后将接收对该 <xref:System.Xml.Linq.XObject> 及其所有子代进行修改的事件。</span><span class="sxs-lookup"><span data-stu-id="25057-107">The event handler will then receive events for modifications to that <xref:System.Xml.Linq.XObject> and any of its descendants.</span></span> <span data-ttu-id="25057-108">例如，可以将事件处理程序添加到树根，然后从该事件处理程序中处理对树进行的所有修改。</span><span class="sxs-lookup"><span data-stu-id="25057-108">For example, you can add an event handler to the root of the tree, and handle all modifications to the tree from that event handler.</span></span>  
  
 <span data-ttu-id="25057-109">有关 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 事件的示例，请参阅 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed>。</span><span class="sxs-lookup"><span data-stu-id="25057-109">For examples of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] events, see <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed>.</span></span>  
  
## <a name="types-and-events"></a><span data-ttu-id="25057-110">类型和事件</span><span class="sxs-lookup"><span data-stu-id="25057-110">Types and Events</span></span>  
 <span data-ttu-id="25057-111">在处理事件时使用下面的类型：</span><span class="sxs-lookup"><span data-stu-id="25057-111">You use the following types when working with events:</span></span>  
  
|<span data-ttu-id="25057-112">类型</span><span class="sxs-lookup"><span data-stu-id="25057-112">Type</span></span>|<span data-ttu-id="25057-113">描述</span><span class="sxs-lookup"><span data-stu-id="25057-113">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|<span data-ttu-id="25057-114">当 <xref:System.Xml.Linq.XObject> 发生事件时指定事件类型。</span><span class="sxs-lookup"><span data-stu-id="25057-114">Specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|<span data-ttu-id="25057-115">提供有关 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed> 事件的数据。</span><span class="sxs-lookup"><span data-stu-id="25057-115">Provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>|  
  
 <span data-ttu-id="25057-116">修改 XML 树时将引发以下事件：</span><span class="sxs-lookup"><span data-stu-id="25057-116">The following events are raised when you modify an XML tree:</span></span>  
  
|<span data-ttu-id="25057-117">事件</span><span class="sxs-lookup"><span data-stu-id="25057-117">Event</span></span>|<span data-ttu-id="25057-118">描述</span><span class="sxs-lookup"><span data-stu-id="25057-118">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|<span data-ttu-id="25057-119">在此 <xref:System.Xml.Linq.XObject> 或它的任何子代即将发生更改之前发生。</span><span class="sxs-lookup"><span data-stu-id="25057-119">Occurs just before this <xref:System.Xml.Linq.XObject> or any of its descendants is going to change.</span></span>|  
|<xref:System.Xml.Linq.XObject.Changed>|<span data-ttu-id="25057-120">在 <xref:System.Xml.Linq.XObject> 或它的任何子代已经更改时发生。</span><span class="sxs-lookup"><span data-stu-id="25057-120">Occurs when an <xref:System.Xml.Linq.XObject> has changed or any of its descendants have changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="25057-121">示例</span><span class="sxs-lookup"><span data-stu-id="25057-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="25057-122">说明</span><span class="sxs-lookup"><span data-stu-id="25057-122">Description</span></span>  
 <span data-ttu-id="25057-123">当您希望在 XML 树中保留一些聚合信息时事件非常有用。</span><span class="sxs-lookup"><span data-stu-id="25057-123">Events are useful when you want to maintain some aggregate information in an XML tree.</span></span> <span data-ttu-id="25057-124">例如，您可能想保留一份发票合计，计算发票上各个项目的总和。</span><span class="sxs-lookup"><span data-stu-id="25057-124">For example, you may want maintain an invoice total that is the sum of the line items of the invoice.</span></span> <span data-ttu-id="25057-125">本示例使用事件来维护复杂元素 `Items` 之下所有子元素的总和。</span><span class="sxs-lookup"><span data-stu-id="25057-125">This example uses events to maintain the total of all of the child elements under the complex element `Items`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="25057-126">代码</span><span class="sxs-lookup"><span data-stu-id="25057-126">Code</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Total", "0"),  
    new XElement("Items")  
);  
XElement total = root.Element("Total");  
XElement items = root.Element("Items");  
items.Changed += (object sender, XObjectChangeEventArgs cea) =>  
{  
    switch (cea.ObjectChange)  
    {  
        case XObjectChange.Add:  
            if (sender is XElement)  
                total.Value = ((int)total + (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total + (int)((XText)sender).Parent).ToString();  
            break;  
        case XObjectChange.Remove:  
            if (sender is XElement)  
                total.Value = ((int)total - (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total - Int32.Parse(((XText)sender).Value)).ToString();  
            break;  
    }  
    Console.WriteLine("Changed {0} {1}",  
      sender.GetType().ToString(), cea.ObjectChange.ToString());  
};  
items.SetElementValue("Item1", 25);  
items.SetElementValue("Item2", 50);  
items.SetElementValue("Item2", 75);  
items.SetElementValue("Item3", 133);  
items.SetElementValue("Item1", null);  
items.SetElementValue("Item4", 100);  
Console.WriteLine("Total:{0}", (int)total);  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a><span data-ttu-id="25057-127">注释</span><span class="sxs-lookup"><span data-stu-id="25057-127">Comments</span></span>  
 <span data-ttu-id="25057-128">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="25057-128">This code produces the following output:</span></span>  
  
```output  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  