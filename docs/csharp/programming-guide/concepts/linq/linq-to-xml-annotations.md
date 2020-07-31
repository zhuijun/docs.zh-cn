---
title: LINQ to XML 批注
description: 了解如何使用 LINQ to XML 中的注释将任意类型的任意对象与 XML 树中的任何 XML 组件相关联。
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: e7da666139c10b26de37816693202d96498f52d8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165581"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="d86f8-103">LINQ to XML 批注</span><span class="sxs-lookup"><span data-stu-id="d86f8-103">LINQ to XML Annotations</span></span>

<span data-ttu-id="d86f8-104">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的注释可将任意类型的任意对象与 XML 树中的任何 XML 组件相关联。</span><span class="sxs-lookup"><span data-stu-id="d86f8-104">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>

<span data-ttu-id="d86f8-105">若要向 XML 组件（例如 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute>）中添加批注，需调用 <xref:System.Xml.Linq.XObject.AddAnnotation%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d86f8-105">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="d86f8-106">批注是按类型检索的。</span><span class="sxs-lookup"><span data-stu-id="d86f8-106">You retrieve annotations by type.</span></span>

<span data-ttu-id="d86f8-107">请注意，批注不是 XML 信息集的一部分，不对它们进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="d86f8-107">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>

## <a name="methods"></a><span data-ttu-id="d86f8-108">方法</span><span class="sxs-lookup"><span data-stu-id="d86f8-108">Methods</span></span>

<span data-ttu-id="d86f8-109">处理批注时可以使用以下方法：</span><span class="sxs-lookup"><span data-stu-id="d86f8-109">You can use the following methods when working with annotations:</span></span>

|<span data-ttu-id="d86f8-110">方法</span><span class="sxs-lookup"><span data-stu-id="d86f8-110">Method</span></span>|<span data-ttu-id="d86f8-111">说明</span><span class="sxs-lookup"><span data-stu-id="d86f8-111">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="d86f8-112">向 <xref:System.Xml.Linq.XObject> 的批注列表中添加对象。</span><span class="sxs-lookup"><span data-stu-id="d86f8-112">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="d86f8-113">从 <xref:System.Xml.Linq.XObject> 获取指定类型的第一个批注对象。</span><span class="sxs-lookup"><span data-stu-id="d86f8-113">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="d86f8-114">获取 <xref:System.Xml.Linq.XObject> 的指定类型的批注集合。</span><span class="sxs-lookup"><span data-stu-id="d86f8-114">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="d86f8-115">从 <xref:System.Xml.Linq.XObject> 移除指定类型的批注。</span><span class="sxs-lookup"><span data-stu-id="d86f8-115">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
