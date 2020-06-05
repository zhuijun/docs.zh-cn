---
title: 如何：通过 LINQ to XML 使用字典
ms.date: 07/20/2015
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
ms.openlocfilehash: 14c9c35693f323292849f01af79ae81f92921611
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397669"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a><span data-ttu-id="182bc-102">如何：使用 LINQ to XML （Visual Basic）使用词典</span><span class="sxs-lookup"><span data-stu-id="182bc-102">How to: Work with Dictionaries Using LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="182bc-103">通常需要将各种数据结构转换为 XML 和将 XML 转换回其他数据结构。</span><span class="sxs-lookup"><span data-stu-id="182bc-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="182bc-104">本主题通过 <xref:System.Collections.Generic.Dictionary%602> 和 XML 的相互转换演示这一常规方法的具体实现。</span><span class="sxs-lookup"><span data-stu-id="182bc-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="182bc-105">示例</span><span class="sxs-lookup"><span data-stu-id="182bc-105">Example</span></span>  
 <span data-ttu-id="182bc-106">此示例在嵌入式表达式中使用 XML 文本和查询。</span><span class="sxs-lookup"><span data-stu-id="182bc-106">This example uses XML literals and a query in an embedded expression.</span></span> <span data-ttu-id="182bc-107">查询投影新 <xref:System.Xml.Linq.XElement> 对象，该对象随后成为对象的新内容 `Root` <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="182bc-107">The query projects new <xref:System.Xml.Linq.XElement> objects, which then become the new content for the `Root` <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```vb  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()  
dict.Add("Child1", "Value1")  
dict.Add("Child2", "Value2")  
dict.Add("Child3", "Value3")  
dict.Add("Child4", "Value4")  
Dim root As XElement = _  
    <Root>  
        <%= From keyValue In dict _  
            Select New XElement(keyValue.Key, keyValue.Value) %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="182bc-108">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="182bc-108">This code produces the following output:</span></span>  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="182bc-109">示例</span><span class="sxs-lookup"><span data-stu-id="182bc-109">Example</span></span>  
 <span data-ttu-id="182bc-110">下面的代码从 XML 创建一个字典。</span><span class="sxs-lookup"><span data-stu-id="182bc-110">The following code creates a dictionary from XML.</span></span>  
  
```vb  
Dim root As XElement = _  
        <Root>  
            <Child1>Value1</Child1>  
            <Child2>Value2</Child2>  
            <Child3>Value3</Child3>  
            <Child4>Value4</Child4>  
        </Root>  
  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)  
For Each el As XElement In root.Elements  
    dict.Add(el.Name.LocalName, el.Value)  
Next  
For Each str As String In dict.Keys  
    Console.WriteLine("{0}:{1}", str, dict(str))  
Next  
```  
  
 <span data-ttu-id="182bc-111">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="182bc-111">This code produces the following output:</span></span>  
  
```console  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a><span data-ttu-id="182bc-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="182bc-112">See also</span></span>

- [<span data-ttu-id="182bc-113">投影和转换（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="182bc-113">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)
