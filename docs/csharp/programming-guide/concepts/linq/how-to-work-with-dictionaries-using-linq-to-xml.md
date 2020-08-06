---
title: 如何通过 LINQ to XML 使用字典 (C#)
description: 了解如何通过 LINQ to XML 使用字典。 查看将字典转换为 XML 并将 XML 转换回其他数据结构的示例。
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: bdba7a2b3dfc16fab1e239ac804c317dfefb7d9e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302615"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a>如何通过 LINQ to XML 使用字典 (C#)
通常需要将各种数据结构转换为 XML 和将 XML 转换回其他数据结构。 本主题通过 <xref:System.Collections.Generic.Dictionary%602> 和 XML 的相互转换演示这一常规方法的具体实现。  
  
## <a name="example"></a>示例  
 本示例使用函数构造形式：查询投影新 <xref:System.Xml.Linq.XElement> 对象，生成的集合作为自变量传递给根 <xref:System.Xml.Linq.XElement> 对象的构造函数。  
  
```csharp  
Dictionary<string, string> dict = new Dictionary<string, string>();  
dict.Add("Child1", "Value1");  
dict.Add("Child2", "Value2");  
dict.Add("Child3", "Value3");  
dict.Add("Child4", "Value4");  
XElement root = new XElement("Root",  
    from keyValue in dict  
    select new XElement(keyValue.Key, keyValue.Value)  
);  
Console.WriteLine(root);  
```  
  
 此代码生成以下输出：  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>示例  
 下面的代码从 XML 创建一个字典。  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "Value1"),  
    new XElement("Child2", "Value2"),  
    new XElement("Child3", "Value3"),  
    new XElement("Child4", "Value4")  
);  
  
Dictionary<string, string> dict = new Dictionary<string, string>();  
foreach (XElement el in root.Elements())  
    dict.Add(el.Name.LocalName, el.Value);  
foreach (string str in dict.Keys)  
    Console.WriteLine("{0}:{1}", str, dict[str]);  
```  
  
 此代码生成以下输出：  
  
```output  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
