---
title: 如何检索元素的浅表值 (C#)
description: 了解如何获取元素的浅表值。 浅表值仅适用于特定的元素。
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 597859e5b66606aa0cff9c1a475e79e6b66c39fc
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301575"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a><span data-ttu-id="47cad-104">如何检索元素的浅表值 (C#)</span><span class="sxs-lookup"><span data-stu-id="47cad-104">How to retrieve the shallow value of an element (C#)</span></span>
<span data-ttu-id="47cad-105">本主题说明如何获取元素的浅值。</span><span class="sxs-lookup"><span data-stu-id="47cad-105">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="47cad-106">浅值只是特定元素的值，与深值相反，包括串联成一个单一字符串的所有子元素的值。</span><span class="sxs-lookup"><span data-stu-id="47cad-106">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="47cad-107">使用强制转换或 <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> 属性检索元素值时，您可以检索深值。</span><span class="sxs-lookup"><span data-stu-id="47cad-107">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="47cad-108">要检索浅值，可以使用 `ShallowValue` 扩展方法，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="47cad-108">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="47cad-109">当根据内容选择元素时，检索浅值十分有用。</span><span class="sxs-lookup"><span data-stu-id="47cad-109">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="47cad-110">下面的示例声明了检索元素浅值的扩展方法。</span><span class="sxs-lookup"><span data-stu-id="47cad-110">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="47cad-111">然后在查询中使用该扩展方法列出包含计算得出的值的所有元素。</span><span class="sxs-lookup"><span data-stu-id="47cad-111">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47cad-112">示例</span><span class="sxs-lookup"><span data-stu-id="47cad-112">Example</span></span>  
 <span data-ttu-id="47cad-113">下面的文本文件 Report.xml 是此示例的源。</span><span class="sxs-lookup"><span data-stu-id="47cad-113">The following text file, Report.xml, is the source for this example.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```csharp  
public static class MyExtensions  
{  
    public static string ShallowValue(this XElement xe)  
    {  
        return xe  
               .Nodes()  
               .OfType<XText>()  
               .Aggregate(new StringBuilder(),  
                          (s, c) => s.Append(c),  
                          s => s.ToString());  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement root = XElement.Load("Report.xml");  
  
        IEnumerable<XElement> query = from el in root.Descendants()  
                                      where el.ShallowValue().StartsWith("=")  
                                      select el;  
  
        foreach (var q in query)  
        {  
            Console.WriteLine("{0}{1}{2}",  
                q.Name.ToString().PadRight(8),  
                q.Attribute("Name").ToString().PadRight(20),  
                q.ShallowValue());  
        }  
    }  
}  
```  
  
 <span data-ttu-id="47cad-114">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="47cad-114">This example produces the following output:</span></span>  
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="47cad-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="47cad-115">See also</span></span>

- [<span data-ttu-id="47cad-116">LINQ to XML 轴 (C#)</span><span class="sxs-lookup"><span data-stu-id="47cad-116">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
