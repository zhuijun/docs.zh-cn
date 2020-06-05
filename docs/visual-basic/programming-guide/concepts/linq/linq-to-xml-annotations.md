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
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="59ed8-102">LINQ to XML 批注</span><span class="sxs-lookup"><span data-stu-id="59ed8-102">LINQ to XML Annotations</span></span>
<span data-ttu-id="59ed8-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的注释可将任意类型的任意对象与 XML 树中的任何 XML 组件相关联。</span><span class="sxs-lookup"><span data-stu-id="59ed8-103">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>  
  
 <span data-ttu-id="59ed8-104">若要向 XML 组件（例如 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute>）中添加批注，需调用 <xref:System.Xml.Linq.XObject.AddAnnotation%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="59ed8-104">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="59ed8-105">批注是按类型检索的。</span><span class="sxs-lookup"><span data-stu-id="59ed8-105">You retrieve annotations by type.</span></span>  
  
 <span data-ttu-id="59ed8-106">请注意，批注不是 XML 信息集的一部分，不对它们进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="59ed8-106">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59ed8-107">方法</span><span class="sxs-lookup"><span data-stu-id="59ed8-107">Methods</span></span>  
 <span data-ttu-id="59ed8-108">处理批注时可以使用以下方法：</span><span class="sxs-lookup"><span data-stu-id="59ed8-108">You can use the following methods when working with annotations:</span></span>  
  
|<span data-ttu-id="59ed8-109">方法</span><span class="sxs-lookup"><span data-stu-id="59ed8-109">Method</span></span>|<span data-ttu-id="59ed8-110">说明</span><span class="sxs-lookup"><span data-stu-id="59ed8-110">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="59ed8-111">向 <xref:System.Xml.Linq.XObject> 的批注列表中添加对象。</span><span class="sxs-lookup"><span data-stu-id="59ed8-111">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="59ed8-112">从 <xref:System.Xml.Linq.XObject> 获取指定类型的第一个批注对象。</span><span class="sxs-lookup"><span data-stu-id="59ed8-112">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="59ed8-113">获取 <xref:System.Xml.Linq.XObject> 的指定类型的批注集合。</span><span class="sxs-lookup"><span data-stu-id="59ed8-113">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="59ed8-114">从 <xref:System.Xml.Linq.XObject> 移除指定类型的批注。</span><span class="sxs-lookup"><span data-stu-id="59ed8-114">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59ed8-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="59ed8-115">See also</span></span>

- [<span data-ttu-id="59ed8-116">高级 LINQ to XML 编程（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="59ed8-116">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
