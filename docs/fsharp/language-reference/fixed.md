---
title: Fixed 关键字
description: '了解如何在堆栈上 "固定" 本地以防止使用 F # "fixed" 关键字收集。'
ms.date: 08/15/2020
ms.openlocfilehash: 786ffd706c243fc83f8fb3afc2201d2a34536372
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559175"
---
# <a name="the-fixed-keyword"></a><span data-ttu-id="ab39b-103">Fixed 关键字</span><span class="sxs-lookup"><span data-stu-id="ab39b-103">The fixed keyword</span></span>

<span data-ttu-id="ab39b-104">`fixed`关键字允许你将本地固定到堆栈上，以防止在垃圾回收过程中收集或移动该堆栈。</span><span class="sxs-lookup"><span data-stu-id="ab39b-104">The `fixed` keyword allows you to "pin" a local onto the stack to prevent it from being collected or moved during garbage-collection.</span></span>  <span data-ttu-id="ab39b-105">它用于低级编程方案。</span><span class="sxs-lookup"><span data-stu-id="ab39b-105">It is used for low-level programming scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="ab39b-106">语法</span><span class="sxs-lookup"><span data-stu-id="ab39b-106">Syntax</span></span>

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a><span data-ttu-id="ab39b-107">备注</span><span class="sxs-lookup"><span data-stu-id="ab39b-107">Remarks</span></span>

<span data-ttu-id="ab39b-108">这将扩展表达式的语法，以允许提取指针，并将其绑定到在垃圾回收期间阻止收集或移动的名称。</span><span class="sxs-lookup"><span data-stu-id="ab39b-108">This extends the syntax of expressions to allow extracting a pointer and binding it to a name which is prevented from being collected or moved during garbage-collection.</span></span>  

<span data-ttu-id="ab39b-109">通过将关键字通过关键字绑定到标识符，可以通过将表达式中的指针固定 `fixed` `use` 。</span><span class="sxs-lookup"><span data-stu-id="ab39b-109">A pointer from an expression is fixed via the `fixed` keyword is bound to an identifier via the `use` keyword.</span></span>  <span data-ttu-id="ab39b-110">此的语义类似于通过关键字进行的资源管理 `use` 。</span><span class="sxs-lookup"><span data-stu-id="ab39b-110">The semantics of this are similar to resource management via the `use` keyword.</span></span>  <span data-ttu-id="ab39b-111">如果指针在范围内，则将其固定，一旦超出范围，它就不再是固定的。</span><span class="sxs-lookup"><span data-stu-id="ab39b-111">The pointer is fixed while it is in scope, and once it is out of scope, it is no longer fixed.</span></span>  <span data-ttu-id="ab39b-112">`fixed` 不能在绑定的上下文之外使用 `use` 。</span><span class="sxs-lookup"><span data-stu-id="ab39b-112">`fixed` cannot be used outside the context of a `use` binding.</span></span>  <span data-ttu-id="ab39b-113">必须使用将指针绑定到名称 `use` 。</span><span class="sxs-lookup"><span data-stu-id="ab39b-113">You must bind the pointer to a name with `use`.</span></span>

<span data-ttu-id="ab39b-114">的使用 `fixed` 必须出现在函数或方法的表达式中。</span><span class="sxs-lookup"><span data-stu-id="ab39b-114">Use of `fixed` must occur within an expression in a function or a method.</span></span>  <span data-ttu-id="ab39b-115">它不能在脚本级或模块级范围内使用。</span><span class="sxs-lookup"><span data-stu-id="ab39b-115">It cannot be used at a script-level or module-level scope.</span></span>

<span data-ttu-id="ab39b-116">与所有指针代码一样，这是一项不安全的功能，在使用时将发出警告。</span><span class="sxs-lookup"><span data-stu-id="ab39b-116">Like all pointer code, this is an unsafe feature and will emit a warning when used.</span></span>

## <a name="example"></a><span data-ttu-id="ab39b-117">示例</span><span class="sxs-lookup"><span data-stu-id="ab39b-117">Example</span></span>

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn "pnt before - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn "pnt after - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a><span data-ttu-id="ab39b-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab39b-118">See also</span></span>

- [<span data-ttu-id="ab39b-119">NativePtr 模块</span><span class="sxs-lookup"><span data-stu-id="ab39b-119">NativePtr Module</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-nativeinterop-nativeptrmodule.html)
