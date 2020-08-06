---
title: 修改 XML 树中的元素、特性和节点
description: 了解修改元素、元素的子节点或元素属性时可以使用的方法和属性。
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: bfff882dc57a4f6f4b228563ac923122097d88d0
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303161"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="3ea25-103">修改 XML 树中的元素、特性和节点</span><span class="sxs-lookup"><span data-stu-id="3ea25-103">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="3ea25-104">下表汇总了修改元素、元素的子元素或元素属性 (Attribute) 时可以使用的方法和属性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="3ea25-104">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="3ea25-105">下面的方法修改 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="3ea25-105">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="3ea25-106">方法</span><span class="sxs-lookup"><span data-stu-id="3ea25-106">Method</span></span>|<span data-ttu-id="3ea25-107">说明</span><span class="sxs-lookup"><span data-stu-id="3ea25-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="3ea25-108">用已分析的 XML 替换元素。</span><span class="sxs-lookup"><span data-stu-id="3ea25-108">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="3ea25-109">移除元素的所有内容（子节点和属性）。</span><span class="sxs-lookup"><span data-stu-id="3ea25-109">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="3ea25-110">移除元素的属性。</span><span class="sxs-lookup"><span data-stu-id="3ea25-110">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="3ea25-111">替换元素的所有内容（子节点和属性）。</span><span class="sxs-lookup"><span data-stu-id="3ea25-111">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="3ea25-112">替换元素的属性。</span><span class="sxs-lookup"><span data-stu-id="3ea25-112">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="3ea25-113">设置属性的值。</span><span class="sxs-lookup"><span data-stu-id="3ea25-113">Sets the value of an attribute.</span></span> <span data-ttu-id="3ea25-114">如果该属性不存在，则创建该属性。</span><span class="sxs-lookup"><span data-stu-id="3ea25-114">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="3ea25-115">如果值设置为 `null`，则移除该属性。</span><span class="sxs-lookup"><span data-stu-id="3ea25-115">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="3ea25-116">设置子元素的值。</span><span class="sxs-lookup"><span data-stu-id="3ea25-116">Sets the value of a child element.</span></span> <span data-ttu-id="3ea25-117">如果该元素不存在，则创建该元素。</span><span class="sxs-lookup"><span data-stu-id="3ea25-117">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="3ea25-118">如果值设置为 `null`，则移除该元素。</span><span class="sxs-lookup"><span data-stu-id="3ea25-118">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="3ea25-119">用指定的文本替换元素的内容（子节点）。</span><span class="sxs-lookup"><span data-stu-id="3ea25-119">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="3ea25-120">设置元素的值。</span><span class="sxs-lookup"><span data-stu-id="3ea25-120">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="3ea25-121">下面的方法修改 <xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="3ea25-121">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="3ea25-122">方法</span><span class="sxs-lookup"><span data-stu-id="3ea25-122">Method</span></span>|<span data-ttu-id="3ea25-123">说明</span><span class="sxs-lookup"><span data-stu-id="3ea25-123">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="3ea25-124">设置属性的值。</span><span class="sxs-lookup"><span data-stu-id="3ea25-124">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="3ea25-125">设置属性的值。</span><span class="sxs-lookup"><span data-stu-id="3ea25-125">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="3ea25-126">下面的方法修改 <xref:System.Xml.Linq.XNode>（包括 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>）。</span><span class="sxs-lookup"><span data-stu-id="3ea25-126">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="3ea25-127">方法</span><span class="sxs-lookup"><span data-stu-id="3ea25-127">Method</span></span>|<span data-ttu-id="3ea25-128">说明</span><span class="sxs-lookup"><span data-stu-id="3ea25-128">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="3ea25-129">用新内容替换节点。</span><span class="sxs-lookup"><span data-stu-id="3ea25-129">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="3ea25-130">下面的方法修改 <xref:System.Xml.Linq.XContainer>（<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>）。</span><span class="sxs-lookup"><span data-stu-id="3ea25-130">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="3ea25-131">方法</span><span class="sxs-lookup"><span data-stu-id="3ea25-131">Method</span></span>|<span data-ttu-id="3ea25-132">说明</span><span class="sxs-lookup"><span data-stu-id="3ea25-132">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="3ea25-133">用新内容替换子节点。</span><span class="sxs-lookup"><span data-stu-id="3ea25-133">Replaces the children nodes with new content.</span></span>|  
