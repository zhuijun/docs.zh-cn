---
description: 分部方法 - C# 参考
title: 分部方法 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: d6c433fd30f6ec51355bdefee90d815783487c1b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134375"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="2575d-103">分部方法（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="2575d-103">partial method (C# Reference)</span></span>

<span data-ttu-id="2575d-104">分部方法在分部类型的一部分中定义了签名，并在该类型的另一部分中定义了实现。</span><span class="sxs-lookup"><span data-stu-id="2575d-104">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="2575d-105">通过分部方法，类设计器可提供与事件处理程序类似的方法挂钩，以便开发者决定是否实现。</span><span class="sxs-lookup"><span data-stu-id="2575d-105">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="2575d-106">如果开发者不提供实现，则编译器在编译时删除签名。</span><span class="sxs-lookup"><span data-stu-id="2575d-106">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="2575d-107">以下条件适用于分部方法：</span><span class="sxs-lookup"><span data-stu-id="2575d-107">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="2575d-108">分部类型各部分中的签名必须匹配。</span><span class="sxs-lookup"><span data-stu-id="2575d-108">Signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="2575d-109">方法必须返回 void。</span><span class="sxs-lookup"><span data-stu-id="2575d-109">The method must return void.</span></span>

- <span data-ttu-id="2575d-110">不允许使用访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="2575d-110">No access modifiers are allowed.</span></span> <span data-ttu-id="2575d-111">分部方法是隐式专用的。</span><span class="sxs-lookup"><span data-stu-id="2575d-111">Partial methods are implicitly private.</span></span>

<span data-ttu-id="2575d-112">下列示例显示在分部类的两个部分中定义的分部方法：</span><span class="sxs-lookup"><span data-stu-id="2575d-112">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="2575d-113">有关详细信息，请参阅[分部类和方法](../../programming-guide/classes-and-structs/partial-classes-and-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="2575d-113">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2575d-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="2575d-114">See also</span></span>

- [<span data-ttu-id="2575d-115">C# 参考</span><span class="sxs-lookup"><span data-stu-id="2575d-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2575d-116">分部类型</span><span class="sxs-lookup"><span data-stu-id="2575d-116">partial type</span></span>](partial-type.md)
