---
title: C# 中默认命名空间的范围
description: 了解如何在 C# 的 LINQ to XML 中查询默认 XML 命名空间。 使用 XNamespace 变量和本地名称来创建查询的限定名称。
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 912e47099f89daa9b80ac58b422d39d598509ac9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302394"
---
# <a name="scope-of-default-namespaces-in-c"></a>C\# 中默认命名空间的范围
XML 树中表示的默认命名空间不在查询范围内。 如果您的 XML 在默认命名空间内，仍须声明一个 <xref:System.Xml.Linq.XNamespace> 变量，并将该变量与本地名称组合在一起，生成一个限定名，在查询中使用。  
  
 查询 XML 树时遇到的一个最常见问题是，如果 XML 树具有默认命名空间，开发人员在编写查询时，有时会将 XML 视为不在命名空间内。  
  
 本主题的第一个示例集演示一种加载但是按不正确方式查询默认命名空间中的 XML 的典型方式。  
  
 第二个示例集演示必需的更正，以便可以查询命名空间中的 XML。  
  
## <a name="example"></a>示例  
 此示例演示如何在命名空间中创建 XML 和一个返回空结果集的查询。  
  
### <a name="code"></a>代码  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### <a name="comments"></a>注释  
 此示例产生下面的结果：  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>示例  
 本示例演示如何在命名空间中创建 XML 和一个正确编码的查询。  
  
 与上述不正确编码的示例相比，使用 C# 时的正确方法是声明和初始化一个 <xref:System.Xml.Linq.XNamespace> 对象，并在指定 <xref:System.Xml.Linq.XName> 对象时使用它。 在这种情况下，<xref:System.Xml.Linq.XContainer.Elements%2A> 方法的参数是一个 <xref:System.Xml.Linq.XName> 对象。  
  
### <a name="code"></a>代码  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### <a name="comments"></a>注释  
 此示例产生下面的结果：  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>请参阅

- [命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)
