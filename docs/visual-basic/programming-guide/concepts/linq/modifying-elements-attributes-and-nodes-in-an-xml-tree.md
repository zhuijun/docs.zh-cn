---
title: 修改 XML Tree1 中的元素、特性和节点
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: 002e87d58ad1a3730889225bf4b3e50448431f2d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360925"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>修改 XML 树中的元素、特性和节点
下表汇总了修改元素、元素的子元素或元素属性 (Attribute) 时可以使用的方法和属性 (Property)。  
  
 下面的方法修改 <xref:System.Xml.Linq.XElement>。  
  
|方法|说明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|用已分析的 XML 替换元素。|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|移除元素的所有内容（子节点和属性）。|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|移除元素的属性。|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|替换元素的所有内容（子节点和属性）。|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|替换元素的属性。|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|设置属性的值。 如果该属性不存在，则创建该属性。 如果值设置为 `null`，则移除该属性。|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|设置子元素的值。 如果该元素不存在，则创建该元素。 如果值设置为 `null`，则移除该元素。|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|用指定的文本替换元素的内容（子节点）。|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|设置元素的值。|  
  
 下面的方法修改 <xref:System.Xml.Linq.XAttribute>。  
  
|方法|说明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|设置属性的值。|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|设置属性的值。|  
  
 下面的方法修改 <xref:System.Xml.Linq.XNode>（包括 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>）。  
  
|方法|说明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|用新内容替换节点。|  
  
 下面的方法修改 <xref:System.Xml.Linq.XContainer>（<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>）。  
  
|方法|说明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|用新内容替换子节点。|  
  
## <a name="see-also"></a>另请参阅

- [修改 XML 树（LINQ to XML）（Visual Basic）](modifying-xml-trees-linq-to-xml.md)
