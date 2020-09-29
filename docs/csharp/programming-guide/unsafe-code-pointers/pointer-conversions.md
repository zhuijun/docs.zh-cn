---
title: 指针转换 - C# 编程指南
description: 了解指针转换。 参阅隐式和显式指针转换表格、代码示例，并查看其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 7a37c4e9f6333c00c7842df0fdaf353df516974d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205069"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="ea390-104">指针转换（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="ea390-104">Pointer Conversions (C# Programming Guide)</span></span>

<span data-ttu-id="ea390-105">下表显示预定义隐式指针转换。</span><span class="sxs-lookup"><span data-stu-id="ea390-105">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="ea390-106">隐式转换可能会在许多情况下出现（包括方法调用和赋值语句）。</span><span class="sxs-lookup"><span data-stu-id="ea390-106">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="ea390-107">隐式指针转换</span><span class="sxs-lookup"><span data-stu-id="ea390-107">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="ea390-108">From</span><span class="sxs-lookup"><span data-stu-id="ea390-108">From</span></span>|<span data-ttu-id="ea390-109">收件人</span><span class="sxs-lookup"><span data-stu-id="ea390-109">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="ea390-110">任何指针类型</span><span class="sxs-lookup"><span data-stu-id="ea390-110">Any pointer type</span></span>|<span data-ttu-id="ea390-111">void\*</span><span class="sxs-lookup"><span data-stu-id="ea390-111">void\*</span></span>|  
|<span data-ttu-id="ea390-112">null</span><span class="sxs-lookup"><span data-stu-id="ea390-112">null</span></span>|<span data-ttu-id="ea390-113">任何指针类型</span><span class="sxs-lookup"><span data-stu-id="ea390-113">Any pointer type</span></span>|  
  
 <span data-ttu-id="ea390-114">显式指针转换用于使用强制转换对不包含隐式转换的转换执行操作。</span><span class="sxs-lookup"><span data-stu-id="ea390-114">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="ea390-115">下表显示了这些转换。</span><span class="sxs-lookup"><span data-stu-id="ea390-115">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="ea390-116">显式指针转换</span><span class="sxs-lookup"><span data-stu-id="ea390-116">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="ea390-117">From</span><span class="sxs-lookup"><span data-stu-id="ea390-117">From</span></span>|<span data-ttu-id="ea390-118">收件人</span><span class="sxs-lookup"><span data-stu-id="ea390-118">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="ea390-119">任何指针类型</span><span class="sxs-lookup"><span data-stu-id="ea390-119">Any pointer type</span></span>|<span data-ttu-id="ea390-120">其他任何指针类型</span><span class="sxs-lookup"><span data-stu-id="ea390-120">Any other pointer type</span></span>|  
|<span data-ttu-id="ea390-121">sbyte、byte、short、ushort、int、uint、long 或 ulong</span><span class="sxs-lookup"><span data-stu-id="ea390-121">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="ea390-122">任何指针类型</span><span class="sxs-lookup"><span data-stu-id="ea390-122">Any pointer type</span></span>|  
|<span data-ttu-id="ea390-123">任何指针类型</span><span class="sxs-lookup"><span data-stu-id="ea390-123">Any pointer type</span></span>|<span data-ttu-id="ea390-124">sbyte、byte、short、ushort、int、uint、long 或 ulong</span><span class="sxs-lookup"><span data-stu-id="ea390-124">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ea390-125">示例</span><span class="sxs-lookup"><span data-stu-id="ea390-125">Example</span></span>  

 <span data-ttu-id="ea390-126">在下面的示例中，`int` 的指针将转换为 `byte` 的指针。</span><span class="sxs-lookup"><span data-stu-id="ea390-126">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="ea390-127">请注意，指针指向变量的最低寻址字节。</span><span class="sxs-lookup"><span data-stu-id="ea390-127">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="ea390-128">如果结果连续递增，直到达到 `int` 的大小（4 字节），可显示变量的其余字节。</span><span class="sxs-lookup"><span data-stu-id="ea390-128">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="ea390-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ea390-129">See also</span></span>

- [<span data-ttu-id="ea390-130">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="ea390-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ea390-131">指针类型</span><span class="sxs-lookup"><span data-stu-id="ea390-131">Pointer types</span></span>](pointer-types.md)
- [<span data-ttu-id="ea390-132">引用类型</span><span class="sxs-lookup"><span data-stu-id="ea390-132">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="ea390-133">值类型</span><span class="sxs-lookup"><span data-stu-id="ea390-133">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="ea390-134">unsafe</span><span class="sxs-lookup"><span data-stu-id="ea390-134">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="ea390-135">fixed 语句</span><span class="sxs-lookup"><span data-stu-id="ea390-135">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="ea390-136">stackalloc</span><span class="sxs-lookup"><span data-stu-id="ea390-136">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
