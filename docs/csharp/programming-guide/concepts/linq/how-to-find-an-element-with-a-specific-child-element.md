---
title: 如何查找具有特定子元素的元素 (C#)
description: 了解如何查找具有特定子元素的元素。 查看代码示例和其他资源。
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 1d02f3d3af0a3711a5361941727e2e0b6c8bbdc9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301705"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a>如何查找具有特定子元素的元素 (C#)
本主题演示如何查找特定元素，该特定元素包含具有特定值的子元素。  
  
## <a name="example"></a>示例  
 示例查找 `Test` 元素，该元素包含具有值为“Examp2.EXE”的 `CommandLine` 子元素。  
  
 本示例使用下面的 XML 文档：[示例 XML 文件：测试配置 (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md)。  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 此代码生成以下输出：  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何对命名空间中的 XML 进行同样的查询。 有关详细信息，请参阅[命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。  
  
 本示例使用下面的 XML 文档：[示例 XML 文件：命名空间中的测试配置](./sample-xml-file-test-configuration-in-a-namespace1.md)。  
  
```csharp  
XElement root = XElement.Load("TestConfigInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<XElement> tests =  
    from el in root.Elements(ad + "Test")  
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 此代码生成以下输出：  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [标准查询运算符概述 (C#)](./standard-query-operators-overview.md)
- [投影运算 (C#)](./projection-operations.md)
