---
title: .NET 性能提示
description: 探索性能提示，提高 .NET 中程序的执行速度。 请参阅有关装箱和取消装箱、字符串和析构函数的提示。
ms.date: 03/30/2017
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c5e3f692c2bf754ccd35324019246ee905e8c591
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554640"
---
# <a name="net-performance-tips"></a><span data-ttu-id="9c9d4-104">.NET 性能提示</span><span class="sxs-lookup"><span data-stu-id="9c9d4-104">.NET Performance Tips</span></span>
<span data-ttu-id="9c9d4-105">术语“性能”通常指程序的执行速度。\*\*</span><span class="sxs-lookup"><span data-stu-id="9c9d4-105">The term *performance* generally refers to the execution speed of a program.</span></span> <span data-ttu-id="9c9d4-106">有时通过遵循源代码中的一些基本规则便可以提高执行速度。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-106">You can sometimes increase execution speed by following certain basic rules in your source code.</span></span> <span data-ttu-id="9c9d4-107">在某些程序中，十分重要的一点是需要仔细检查代码并使用探查器确保程序尽可能快地运行。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-107">In some programs, it is important to examine code closely and use profilers to make sure that it is running as fast as possible.</span></span> <span data-ttu-id="9c9d4-108">而在其他程序中，由于代码在编写时便运行得足够快，因此不必执行此类优化。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-108">In other programs, you do not have to perform such optimization because the code is running acceptably fast as it is written.</span></span> <span data-ttu-id="9c9d4-109">本文列出了一些性能可能遭受影响的常见领域以及相关改进建议，并提供其他性能主题的链接。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-109">This article lists some common areas where performance can suffer and tips for improving it as well as links to additional performance topics.</span></span> <span data-ttu-id="9c9d4-110">有关规划和测量性能的详细信息，请参阅[性能](index.md)</span><span class="sxs-lookup"><span data-stu-id="9c9d4-110">For more information about planning and measuring for performance, see [Performance](index.md)</span></span>  
  
## <a name="boxing-and-unboxing"></a><span data-ttu-id="9c9d4-111">装箱和取消装箱</span><span class="sxs-lookup"><span data-stu-id="9c9d4-111">Boxing and Unboxing</span></span>  
 <span data-ttu-id="9c9d4-112">如果值类型必须被频繁装箱，那么在这些情况下最好避免使用值类型（例如在诸如 <xref:System.Collections.ArrayList?displayProperty=nameWithType> 的非泛型集合类中）。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-112">It is best to avoid using value types in situations where they must be boxed a high number of times, for example in non-generic collections classes such as <xref:System.Collections.ArrayList?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9c9d4-113">可通过使用泛型集合（例如 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>）来避免装箱值类型。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-113">You can avoid boxing of value types by using generic collections such as <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9c9d4-114">装箱和取消装箱过程需要进行大量的计算。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-114">Boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="9c9d4-115">对值类型进行装箱时，必须创建一个全新的对象。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-115">When a value type is boxed, an entirely new object must be created.</span></span> <span data-ttu-id="9c9d4-116">这可能比简单的引用赋值用时最多长 20 倍。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-116">This can take up to 20 times longer than a simple reference assignment.</span></span> <span data-ttu-id="9c9d4-117">取消装箱的过程所需时间可达赋值操作的四倍。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-117">When unboxing, the casting process can take four times as long as an assignment.</span></span> <span data-ttu-id="9c9d4-118">有关详细信息，请参阅[装箱和取消装箱](../../csharp/programming-guide/types/boxing-and-unboxing.md)。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-118">For more information, see [Boxing and Unboxing](../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="strings"></a><span data-ttu-id="9c9d4-119">字符串</span><span class="sxs-lookup"><span data-stu-id="9c9d4-119">Strings</span></span>  
 <span data-ttu-id="9c9d4-120">在连接大量字符串变量时，例如在紧凑循环中，请使用 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 而不是 C# [+ 运算符](../../csharp/language-reference/operators/addition-operator.md)或 Visual Basic [串联运算符](../../visual-basic/language-reference/operators/concatenation-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-120">When you concatenate a large number of string variables, for example in a tight loop, use <xref:System.Text.StringBuilder?displayProperty=nameWithType> instead of the C# [+ operator](../../csharp/language-reference/operators/addition-operator.md) or the Visual Basic [Concatenation Operators](../../visual-basic/language-reference/operators/concatenation-operators.md).</span></span> <span data-ttu-id="9c9d4-121">有关详细信息，请参阅如何[在 Visual Basic 中](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)[串联多个字符串](../../csharp/how-to/concatenate-multiple-strings.md)和串联运算符。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-121">For more information, see [How to concatenate multiple strings](../../csharp/how-to/concatenate-multiple-strings.md) and [Concatenation Operators in Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).</span></span>  
  
## <a name="destructors"></a><span data-ttu-id="9c9d4-122">析构函数</span><span class="sxs-lookup"><span data-stu-id="9c9d4-122">Destructors</span></span>  
 <span data-ttu-id="9c9d4-123">不应使用空的析构函数。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-123">Empty destructors should not be used.</span></span> <span data-ttu-id="9c9d4-124">如果类包含析构函数，则 Finalize 队列中会创建一个条目。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-124">When a class contains a destructor, an entry is created in the Finalize queue.</span></span> <span data-ttu-id="9c9d4-125">调用析构函数时，将调用垃圾回收器来处理此队列。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-125">When the destructor is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="9c9d4-126">如果析构函数为空，只会导致性能损失。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-126">If the destructor is empty, this simply results in a loss of performance.</span></span> <span data-ttu-id="9c9d4-127">有关详细信息，请参阅[析构函数](../../csharp/programming-guide/classes-and-structs/destructors.md)和[对象生存期：如何创建和销毁对象](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)。</span><span class="sxs-lookup"><span data-stu-id="9c9d4-127">For more information, see [Destructors](../../csharp/programming-guide/classes-and-structs/destructors.md) and [Object Lifetime: How Objects Are Created and Destroyed](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
## <a name="other-resources"></a><span data-ttu-id="9c9d4-128">其他资源</span><span class="sxs-lookup"><span data-stu-id="9c9d4-128">Other Resources</span></span>  
  
- <span data-ttu-id="9c9d4-129">[编写更快的托管代码：了解代价](/previous-versions/dotnet/articles/ms973852(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="9c9d4-129">[Writing Faster Managed Code: Know What Things Cost](/previous-versions/dotnet/articles/ms973852(v=msdn.10))</span></span>  
  
- <span data-ttu-id="9c9d4-130">[编写高性能的托管应用程序：入门](/previous-versions/dotnet/articles/ms973858(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="9c9d4-130">[Writing High-Performance Managed Applications: A Primer](/previous-versions/dotnet/articles/ms973858(v=msdn.10))</span></span>  
  
- <span data-ttu-id="9c9d4-131">[垃圾回收器基础知识和性能提示](/previous-versions/dotnet/articles/ms973837(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="9c9d4-131">[Garbage Collector Basics and Performance Hints](/previous-versions/dotnet/articles/ms973837(v=msdn.10))</span></span>  
  
- <span data-ttu-id="9c9d4-132">[.NET 应用程序的性能提示和技巧](/previous-versions/dotnet/articles/ms973839(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="9c9d4-132">[Performance Tips and Tricks in .NET Applications](/previous-versions/dotnet/articles/ms973839(v=msdn.10))</span></span>  

- [<span data-ttu-id="9c9d4-133">Rico Mariani 关于性能问题的见解</span><span class="sxs-lookup"><span data-stu-id="9c9d4-133">Rico Mariani's Performance Tidbits</span></span>](/archive/blogs/ricom/)  

- [<span data-ttu-id="9c9d4-134">Vance Morrison 的博客</span><span class="sxs-lookup"><span data-stu-id="9c9d4-134">Vance Morrison's Blog</span></span>](/archive/blogs/vancem/)
  
## <a name="see-also"></a><span data-ttu-id="9c9d4-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="9c9d4-135">See also</span></span>

- [<span data-ttu-id="9c9d4-136">“性能”</span><span class="sxs-lookup"><span data-stu-id="9c9d4-136">Performance</span></span>](index.md)
- [<span data-ttu-id="9c9d4-137">Visual Basic 编程指南</span><span class="sxs-lookup"><span data-stu-id="9c9d4-137">Visual Basic Programming Guide</span></span>](../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="9c9d4-138">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="9c9d4-138">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)
