---
title: 泛型和数组 - C# 编程指南
description: 了解 C# 编程中的泛型和数组。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: f3d9e9e0c84d954278780e7598545f80aea0e58c
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299040"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="2837b-104">泛型和数组（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="2837b-104">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="2837b-105">在 C# 2.0 和更高版本中，下限为零的单维数组自动实现 <xref:System.Collections.Generic.IList%601>。</span><span class="sxs-lookup"><span data-stu-id="2837b-105">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="2837b-106">这可使你创建可使用相同代码循环访问数组和其他集合类型的泛型方法。</span><span class="sxs-lookup"><span data-stu-id="2837b-106">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="2837b-107">此技术的主要用处在于读取集合中的数据。</span><span class="sxs-lookup"><span data-stu-id="2837b-107">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="2837b-108"><xref:System.Collections.Generic.IList%601> 接口无法用于添加元素或从数组删除元素。</span><span class="sxs-lookup"><span data-stu-id="2837b-108">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="2837b-109">如果在此上下文中尝试对数组调用 <xref:System.Collections.Generic.IList%601> 方法（例如 <xref:System.Collections.Generic.IList%601.RemoveAt%2A>），则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="2837b-109">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="2837b-110">如下代码示例演示具有 <xref:System.Collections.Generic.IList%601> 输入参数的单个泛型方法如何可循环访问列表和数组（此例中为整数数组）。</span><span class="sxs-lookup"><span data-stu-id="2837b-110">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="2837b-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2837b-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="2837b-112">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="2837b-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2837b-113">泛型</span><span class="sxs-lookup"><span data-stu-id="2837b-113">Generics</span></span>](./index.md)
- [<span data-ttu-id="2837b-114">数组</span><span class="sxs-lookup"><span data-stu-id="2837b-114">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="2837b-115">泛型</span><span class="sxs-lookup"><span data-stu-id="2837b-115">Generics</span></span>](../../../standard/generics/index.md)
