---
title: 异常类型
description: '了解如何定义和使用 F # 异常类型。'
ms.date: 05/16/2016
ms.openlocfilehash: 8b4ceec31a2d68abbcd025812ffeeefc0c090efb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557224"
---
# <a name="exception-types"></a><span data-ttu-id="fb3db-103">异常类型</span><span class="sxs-lookup"><span data-stu-id="fb3db-103">Exception Types</span></span>

<span data-ttu-id="fb3db-104">F #： .NET 异常类型和 F # 异常类型中有两种类别的异常。</span><span class="sxs-lookup"><span data-stu-id="fb3db-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="fb3db-105">本主题介绍如何定义和使用 F # 异常类型。</span><span class="sxs-lookup"><span data-stu-id="fb3db-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="fb3db-106">语法</span><span class="sxs-lookup"><span data-stu-id="fb3db-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="fb3db-107">备注</span><span class="sxs-lookup"><span data-stu-id="fb3db-107">Remarks</span></span>

<span data-ttu-id="fb3db-108">在前面的语法中， *exception 类型* 是新 F # 异常类型的名称，而 *参数类型* 表示当你引发此类型的异常时可以提供的参数的类型。</span><span class="sxs-lookup"><span data-stu-id="fb3db-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="fb3db-109">您可以通过使用 *参数类型*的元组类型指定多个参数。</span><span class="sxs-lookup"><span data-stu-id="fb3db-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="fb3db-110">F # 异常的典型定义如下所示。</span><span class="sxs-lookup"><span data-stu-id="fb3db-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="fb3db-111">您可以使用函数生成此类型的异常 `raise` ，如下所示。</span><span class="sxs-lookup"><span data-stu-id="fb3db-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="fb3db-112">您可以直接在表达式的筛选器中使用 F # 异常类型 `try...with` ，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="fb3db-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="fb3db-113">使用 F # 中的关键字定义的异常类型 `exception` 是从继承的新类型 `System.Exception` 。</span><span class="sxs-lookup"><span data-stu-id="fb3db-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb3db-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="fb3db-114">See also</span></span>

- [<span data-ttu-id="fb3db-115">异常处理</span><span class="sxs-lookup"><span data-stu-id="fb3db-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="fb3db-116">异常：`raise` 函数</span><span class="sxs-lookup"><span data-stu-id="fb3db-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="fb3db-117">异常层次结构</span><span class="sxs-lookup"><span data-stu-id="fb3db-117">Exception Hierarchy</span></span>](../../../standard/exceptions/index.md)
