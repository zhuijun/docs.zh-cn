---
title: 序列化包含 XElement 对象的对象图
ms.date: 07/20/2015
ms.assetid: c0cc5c92-5ca3-44b1-98dd-371601df721b
ms.openlocfilehash: 5390cfaa77229b60af6388fc643544c539c15fe9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360678"
---
# <a name="serializing-object-graphs-that-contain-xelement-objects-visual-basic"></a><span data-ttu-id="2a9f6-102">序列化包含 System.xml.linq.xelement> 对象的对象图（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="2a9f6-102">Serializing Object Graphs that Contain XElement Objects (Visual Basic)</span></span>
<span data-ttu-id="2a9f6-103">本主题介绍序列化对象图的功能，其中对象图包含对类型为 <xref:System.Xml.Linq.XElement> 的对象的引用。</span><span class="sxs-lookup"><span data-stu-id="2a9f6-103">This topic introduces the capability of serializing object graphs that contain references to objects of type <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="2a9f6-104">为便于执行这种类型的序列化，<xref:System.Xml.Linq.XElement> 实现了 <xref:System.Xml.Serialization.IXmlSerializable> 接口。</span><span class="sxs-lookup"><span data-stu-id="2a9f6-104">To facility this type of serializing, <xref:System.Xml.Linq.XElement> implements the <xref:System.Xml.Serialization.IXmlSerializable> interface.</span></span>  
  
 <span data-ttu-id="2a9f6-105">请注意，只有 <xref:System.Xml.Linq.XElement> 类才实现序列化。</span><span class="sxs-lookup"><span data-stu-id="2a9f6-105">Note that only the <xref:System.Xml.Linq.XElement> class implements serialization.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2a9f6-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="2a9f6-106">In This Section</span></span>  
  
|<span data-ttu-id="2a9f6-107">主题</span><span class="sxs-lookup"><span data-stu-id="2a9f6-107">Topic</span></span>|<span data-ttu-id="2a9f6-108">说明</span><span class="sxs-lookup"><span data-stu-id="2a9f6-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2a9f6-109">如何：使用 XmlSerializer 进行序列化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a9f6-109">How to: Serialize Using XmlSerializer (Visual Basic)</span></span>](how-to-serialize-using-xmlserializer.md)|<span data-ttu-id="2a9f6-110">演示如何使用 <xref:System.Xml.Serialization.XmlSerializer> 进行序列化。</span><span class="sxs-lookup"><span data-stu-id="2a9f6-110">Demonstrates how to serialize using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|[<span data-ttu-id="2a9f6-111">如何：使用 DataContractSerializer 进行序列化（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="2a9f6-111">How to: Serialize Using DataContractSerializer (Visual Basic)</span></span>](how-to-serialize-using-datacontractserializer.md)|<span data-ttu-id="2a9f6-112">演示如何使用 <xref:System.Runtime.Serialization.DataContractSerializer> 进行序列化。</span><span class="sxs-lookup"><span data-stu-id="2a9f6-112">Demonstrates how to serialize using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a9f6-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2a9f6-113">See also</span></span>

- [<span data-ttu-id="2a9f6-114">高级 LINQ to XML 编程（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="2a9f6-114">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
