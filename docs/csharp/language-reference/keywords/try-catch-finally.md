---
description: try-catch-finally - C# 参考
title: try-catch-finally - C# 参考
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 6e85330e12c53e0728ef671530709748090ebe02
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142006"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="23d39-103">try-catch-finally（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="23d39-103">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="23d39-104">`catch` 和 `finally` 的常见用法是获得并使用 `try` 块中的资源、处理 `catch` 块中的异常情况，以及释放 `finally` 块中的资源。</span><span class="sxs-lookup"><span data-stu-id="23d39-104">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="23d39-105">有关重新引发异常的详细信息和示例，请参阅 [try-catch](try-catch.md) 和[引发异常](../../../standard/exceptions/index.md)。</span><span class="sxs-lookup"><span data-stu-id="23d39-105">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="23d39-106">有关 `finally` 块的详细信息，请参阅 [try-finally](try-finally.md)。</span><span class="sxs-lookup"><span data-stu-id="23d39-106">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="23d39-107">示例</span><span class="sxs-lookup"><span data-stu-id="23d39-107">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="23d39-108">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="23d39-108">C# language specification</span></span>

<span data-ttu-id="23d39-109">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的 [try 语句](~/_csharplang/spec/statements.md#the-try-statement)部分。</span><span class="sxs-lookup"><span data-stu-id="23d39-109">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="23d39-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="23d39-110">See also</span></span>

- [<span data-ttu-id="23d39-111">C# 参考</span><span class="sxs-lookup"><span data-stu-id="23d39-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="23d39-112">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="23d39-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="23d39-113">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="23d39-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="23d39-114">try、throw 和 catch 语句 (C++)</span><span class="sxs-lookup"><span data-stu-id="23d39-114">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="23d39-115">throw</span><span class="sxs-lookup"><span data-stu-id="23d39-115">throw</span></span>](throw.md)
- [<span data-ttu-id="23d39-116">如何：显式抛出异常</span><span class="sxs-lookup"><span data-stu-id="23d39-116">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="23d39-117">using 语句</span><span class="sxs-lookup"><span data-stu-id="23d39-117">using Statement</span></span>](using-statement.md)
