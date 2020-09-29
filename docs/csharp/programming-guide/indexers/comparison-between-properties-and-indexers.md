---
title: 比较属性和索引器 - C# 编程指南
description: 比较 C# 中的索引器与属性的相似之处。 除一些差别外，对属性访问器定义的所有规则同样适用于索引器访问器。
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: fff20ca965e7614d26f7da32321a829d13292389
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192524"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="f3c1b-104">属性和索引器之间的比较（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="f3c1b-104">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="f3c1b-105">索引器与属性相似。</span><span class="sxs-lookup"><span data-stu-id="f3c1b-105">Indexers are like properties.</span></span> <span data-ttu-id="f3c1b-106">除下表所示的差别外，对属性访问器定义的所有规则也适用于索引器访问器。</span><span class="sxs-lookup"><span data-stu-id="f3c1b-106">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="f3c1b-107">Property</span><span class="sxs-lookup"><span data-stu-id="f3c1b-107">Property</span></span>|<span data-ttu-id="f3c1b-108">索引器</span><span class="sxs-lookup"><span data-stu-id="f3c1b-108">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="f3c1b-109">允许以将方法视作公共数据成员的方式调用方法。</span><span class="sxs-lookup"><span data-stu-id="f3c1b-109">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="f3c1b-110">通过在对象自身上使用数组表示法，允许访问对象内部集合的元素。</span><span class="sxs-lookup"><span data-stu-id="f3c1b-110">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="f3c1b-111">通过简单名称访问。</span><span class="sxs-lookup"><span data-stu-id="f3c1b-111">Accessed through a simple name.</span></span>|<span data-ttu-id="f3c1b-112">通过索引访问。</span><span class="sxs-lookup"><span data-stu-id="f3c1b-112">Accessed through an index.</span></span>|  
|<span data-ttu-id="f3c1b-113">可为静态成员或实例成员。</span><span class="sxs-lookup"><span data-stu-id="f3c1b-113">Can be a static or an instance member.</span></span>|<span data-ttu-id="f3c1b-114">必须是实例成员。</span><span class="sxs-lookup"><span data-stu-id="f3c1b-114">Must be an instance member.</span></span>|  
|<span data-ttu-id="f3c1b-115">属性的 [get](../../language-reference/keywords/get.md) 访问器没有任何参数。</span><span class="sxs-lookup"><span data-stu-id="f3c1b-115">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="f3c1b-116">索引器的 `get` 访问器具有与索引器相同的形参列表。</span><span class="sxs-lookup"><span data-stu-id="f3c1b-116">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="f3c1b-117">属性的 [set](../../language-reference/keywords/set.md) 访问器包含隐式 `value` 参数。</span><span class="sxs-lookup"><span data-stu-id="f3c1b-117">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="f3c1b-118">索引器的 `set` 访问器具有与索引器相同的形参列表，[value](../../language-reference/keywords/value.md) 参数也是如此。</span><span class="sxs-lookup"><span data-stu-id="f3c1b-118">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="f3c1b-119">通过[自动实现的属性](../classes-and-structs/auto-implemented-properties.md)支持简短语法。</span><span class="sxs-lookup"><span data-stu-id="f3c1b-119">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="f3c1b-120">支持仅使用索引器的 expression-bodied 成员。</span><span class="sxs-lookup"><span data-stu-id="f3c1b-120">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3c1b-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f3c1b-121">See also</span></span>

- [<span data-ttu-id="f3c1b-122">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="f3c1b-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f3c1b-123">索引器</span><span class="sxs-lookup"><span data-stu-id="f3c1b-123">Indexers</span></span>](./index.md)
- [<span data-ttu-id="f3c1b-124">属性</span><span class="sxs-lookup"><span data-stu-id="f3c1b-124">Properties</span></span>](../classes-and-structs/properties.md)
