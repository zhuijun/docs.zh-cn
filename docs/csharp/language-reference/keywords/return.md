---
description: return 语句 - C# 参考
title: return 语句 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 486db846304c0972942ff58f3d5b276083681abe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136991"
---
# <a name="return-c-reference"></a><span data-ttu-id="7bffe-103">return（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="7bffe-103">return (C# Reference)</span></span>

<span data-ttu-id="7bffe-104">`return` 语句可终止它所在的方法的执行，并将控制权返回给调用方法。</span><span class="sxs-lookup"><span data-stu-id="7bffe-104">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="7bffe-105">它还可以返回可选值。</span><span class="sxs-lookup"><span data-stu-id="7bffe-105">It can also return an optional value.</span></span> <span data-ttu-id="7bffe-106">如果方法是 `void` 类型，则 `return` 语句可以省略。</span><span class="sxs-lookup"><span data-stu-id="7bffe-106">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="7bffe-107">如果 return 语句位于 `try` 块中，则 `finally` 块（如果存在）会在控制权返回给调用方法之前进行执行。</span><span class="sxs-lookup"><span data-stu-id="7bffe-107">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="7bffe-108">示例</span><span class="sxs-lookup"><span data-stu-id="7bffe-108">Example</span></span>

 <span data-ttu-id="7bffe-109">在下面的示例中，方法 `CalculateArea()` 将局部变量 `area` 作为 `double` 值返回。</span><span class="sxs-lookup"><span data-stu-id="7bffe-109">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="7bffe-110">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="7bffe-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7bffe-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="7bffe-111">See also</span></span>

- [<span data-ttu-id="7bffe-112">C# 参考</span><span class="sxs-lookup"><span data-stu-id="7bffe-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7bffe-113">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="7bffe-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7bffe-114">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="7bffe-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7bffe-115">return 语句</span><span class="sxs-lookup"><span data-stu-id="7bffe-115">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
