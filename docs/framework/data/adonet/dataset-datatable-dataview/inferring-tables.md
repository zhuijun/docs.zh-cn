---
title: 推断表
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 4a3d7b239dbc405cf2acae967b5be401dc772e38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177548"
---
# <a name="inferring-tables"></a><span data-ttu-id="0c1a5-102">推断表</span><span class="sxs-lookup"><span data-stu-id="0c1a5-102">Inferring Tables</span></span>

<span data-ttu-id="0c1a5-103">当从 XML 文档推断 <xref:System.Data.DataSet> 的架构时，ADO.NET 首先会确定哪些 XML 元素表示表。</span><span class="sxs-lookup"><span data-stu-id="0c1a5-103">When inferring a schema for a <xref:System.Data.DataSet> from an XML document, ADO.NET first determines which XML elements represent tables.</span></span> <span data-ttu-id="0c1a5-104">以下 XML 结构将为 **数据集** 架构生成一个表：</span><span class="sxs-lookup"><span data-stu-id="0c1a5-104">The following XML structures result in a table for the **DataSet** schema:</span></span>  
  
- <span data-ttu-id="0c1a5-105">具有属性的元素</span><span class="sxs-lookup"><span data-stu-id="0c1a5-105">Elements with attributes</span></span>  
  
- <span data-ttu-id="0c1a5-106">具有子元素的元素</span><span class="sxs-lookup"><span data-stu-id="0c1a5-106">Elements with child elements</span></span>  
  
- <span data-ttu-id="0c1a5-107">重复元素</span><span class="sxs-lookup"><span data-stu-id="0c1a5-107">Repeating elements</span></span>  
  
## <a name="elements-with-attributes"></a><span data-ttu-id="0c1a5-108">具有属性的元素</span><span class="sxs-lookup"><span data-stu-id="0c1a5-108">Elements with Attributes</span></span>  

 <span data-ttu-id="0c1a5-109">在其中指定了属性的元素将生成推断表。</span><span class="sxs-lookup"><span data-stu-id="0c1a5-109">Elements that have attributes specified in them result in inferred tables.</span></span> <span data-ttu-id="0c1a5-110">例如，考虑以下 XML：</span><span class="sxs-lookup"><span data-stu-id="0c1a5-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0c1a5-111">推断过程将生成名为“Element1”的表。</span><span class="sxs-lookup"><span data-stu-id="0c1a5-111">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="0c1a5-112">**数据集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0c1a5-112">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0c1a5-113">**表：** Element1</span><span class="sxs-lookup"><span data-stu-id="0c1a5-113">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0c1a5-114">attr1</span><span class="sxs-lookup"><span data-stu-id="0c1a5-114">attr1</span></span>|<span data-ttu-id="0c1a5-115">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="0c1a5-115">Element1_Text</span></span>|  
|-----------|--------------------|  
|<span data-ttu-id="0c1a5-116">value1</span><span class="sxs-lookup"><span data-stu-id="0c1a5-116">value1</span></span>||  
|<span data-ttu-id="0c1a5-117">value2</span><span class="sxs-lookup"><span data-stu-id="0c1a5-117">value2</span></span>|<span data-ttu-id="0c1a5-118">Text1</span><span class="sxs-lookup"><span data-stu-id="0c1a5-118">Text1</span></span>|  
  
## <a name="elements-with-child-elements"></a><span data-ttu-id="0c1a5-119">具有子元素的元素</span><span class="sxs-lookup"><span data-stu-id="0c1a5-119">Elements with Child Elements</span></span>  

 <span data-ttu-id="0c1a5-120">具有子元素的元素将生成推断表。</span><span class="sxs-lookup"><span data-stu-id="0c1a5-120">Elements that have child elements result in inferred tables.</span></span> <span data-ttu-id="0c1a5-121">例如，考虑以下 XML：</span><span class="sxs-lookup"><span data-stu-id="0c1a5-121">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0c1a5-122">推断过程将生成名为“Element1”的表。</span><span class="sxs-lookup"><span data-stu-id="0c1a5-122">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="0c1a5-123">**数据集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0c1a5-123">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0c1a5-124">**表：** Element1</span><span class="sxs-lookup"><span data-stu-id="0c1a5-124">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0c1a5-125">ChildElement1</span><span class="sxs-lookup"><span data-stu-id="0c1a5-125">ChildElement1</span></span>|  
|-------------------|  
|<span data-ttu-id="0c1a5-126">Text1</span><span class="sxs-lookup"><span data-stu-id="0c1a5-126">Text1</span></span>|  
  
 <span data-ttu-id="0c1a5-127">如果文档元素（即根元素）具有将被推断为列的属性或子元素，将生成推断表。</span><span class="sxs-lookup"><span data-stu-id="0c1a5-127">The document, or root, element result in an inferred table if it has attributes or child elements that are inferred as columns.</span></span> <span data-ttu-id="0c1a5-128">如果文档元素没有属性，并且没有任何子元素将被推断为列，则该元素将被推断为 **数据集**。</span><span class="sxs-lookup"><span data-stu-id="0c1a5-128">If the document element has no attributes and no child elements that would be inferred as columns, the element is inferred as a **DataSet**.</span></span> <span data-ttu-id="0c1a5-129">例如，考虑以下 XML：</span><span class="sxs-lookup"><span data-stu-id="0c1a5-129">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0c1a5-130">推断过程将生成名为“DocumentElement”的表。</span><span class="sxs-lookup"><span data-stu-id="0c1a5-130">The inference process produces a table named "DocumentElement."</span></span>  
  
 <span data-ttu-id="0c1a5-131">**数据集：** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="0c1a5-131">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="0c1a5-132">**表：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0c1a5-132">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="0c1a5-133">Element1</span><span class="sxs-lookup"><span data-stu-id="0c1a5-133">Element1</span></span>|<span data-ttu-id="0c1a5-134">Element2</span><span class="sxs-lookup"><span data-stu-id="0c1a5-134">Element2</span></span>|  
|--------------|--------------|  
|<span data-ttu-id="0c1a5-135">Text1</span><span class="sxs-lookup"><span data-stu-id="0c1a5-135">Text1</span></span>|<span data-ttu-id="0c1a5-136">Text2</span><span class="sxs-lookup"><span data-stu-id="0c1a5-136">Text2</span></span>|  
  
 <span data-ttu-id="0c1a5-137">或者，考虑以下 XML：</span><span class="sxs-lookup"><span data-stu-id="0c1a5-137">Alternatively, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0c1a5-138">推理过程将生成一个名为 "DocumentElement" 的 **数据集** ，其中包含一个名为 "Element1" 的表。</span><span class="sxs-lookup"><span data-stu-id="0c1a5-138">The inference process produces a **DataSet** named "DocumentElement" that contains a table named "Element1."</span></span>  
  
 <span data-ttu-id="0c1a5-139">**数据集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0c1a5-139">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0c1a5-140">**表：** Element1</span><span class="sxs-lookup"><span data-stu-id="0c1a5-140">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0c1a5-141">attr1</span><span class="sxs-lookup"><span data-stu-id="0c1a5-141">attr1</span></span>|<span data-ttu-id="0c1a5-142">attr2</span><span class="sxs-lookup"><span data-stu-id="0c1a5-142">attr2</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="0c1a5-143">value1</span><span class="sxs-lookup"><span data-stu-id="0c1a5-143">value1</span></span>|<span data-ttu-id="0c1a5-144">value2</span><span class="sxs-lookup"><span data-stu-id="0c1a5-144">value2</span></span>|  
  
## <a name="repeating-elements"></a><span data-ttu-id="0c1a5-145">重复元素</span><span class="sxs-lookup"><span data-stu-id="0c1a5-145">Repeating Elements</span></span>  

 <span data-ttu-id="0c1a5-146">重复的元素将生成单个推断表。</span><span class="sxs-lookup"><span data-stu-id="0c1a5-146">Elements that repeat result in a single inferred table.</span></span> <span data-ttu-id="0c1a5-147">例如，考虑以下 XML：</span><span class="sxs-lookup"><span data-stu-id="0c1a5-147">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="0c1a5-148">推断过程将生成名为“Element1”的表。</span><span class="sxs-lookup"><span data-stu-id="0c1a5-148">The inference process produces a table named "Element1."</span></span>  
  
 <span data-ttu-id="0c1a5-149">**数据集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="0c1a5-149">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="0c1a5-150">**表：** Element1</span><span class="sxs-lookup"><span data-stu-id="0c1a5-150">**Table:** Element1</span></span>  
  
|<span data-ttu-id="0c1a5-151">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="0c1a5-151">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="0c1a5-152">Text1</span><span class="sxs-lookup"><span data-stu-id="0c1a5-152">Text1</span></span>|  
|<span data-ttu-id="0c1a5-153">Text2</span><span class="sxs-lookup"><span data-stu-id="0c1a5-153">Text2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c1a5-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="0c1a5-154">See also</span></span>

- [<span data-ttu-id="0c1a5-155">从 XML 推断数据集关系结构</span><span class="sxs-lookup"><span data-stu-id="0c1a5-155">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="0c1a5-156">从 XML 加载数据集</span><span class="sxs-lookup"><span data-stu-id="0c1a5-156">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="0c1a5-157">从 XML 加载数据集架构信息</span><span class="sxs-lookup"><span data-stu-id="0c1a5-157">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="0c1a5-158">在数据集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="0c1a5-158">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="0c1a5-159">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="0c1a5-159">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="0c1a5-160">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="0c1a5-160">ADO.NET Overview</span></span>](../ado-net-overview.md)
