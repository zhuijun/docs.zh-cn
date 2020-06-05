---
title: LINQ to XML Annotations2
ms.date: 07/20/2015
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
ms.openlocfilehash: 917129a06483ce2001e178d744440504533d28d6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84369006"
---
# <a name="linq-to-xml-annotations"></a>LINQ to XML 批注
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的注释可将任意类型的任意对象与 XML 树中的任何 XML 组件相关联。  
  
 若要向 XML 组件（例如 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute>）中添加批注，需调用 <xref:System.Xml.Linq.XObject.AddAnnotation%2A> 方法。 批注是按类型检索的。  
  
 请注意，批注不是 XML 信息集的一部分，不对它们进行序列化和反序列化。  
  
## <a name="methods"></a>方法  
 处理批注时可以使用以下方法：  
  
|方法|说明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|向 <xref:System.Xml.Linq.XObject> 的批注列表中添加对象。|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|从 <xref:System.Xml.Linq.XObject> 获取指定类型的第一个批注对象。|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|获取 <xref:System.Xml.Linq.XObject> 的指定类型的批注集合。|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|从 <xref:System.Xml.Linq.XObject> 移除指定类型的批注。|  
  
## <a name="see-also"></a>另请参阅

- [高级 LINQ to XML 编程（Visual Basic）](advanced-linq-to-xml-programming.md)
