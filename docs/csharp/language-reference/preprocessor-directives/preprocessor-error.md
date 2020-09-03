---
description: '#error - C# 参考'
title: '#error - C# 参考'
ms.date: 08/24/2020
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 76325901c5e39f340545b186a0aa9546cd853ff8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138093"
---
# <a name="error-c-reference"></a><span data-ttu-id="c618d-103">#error（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="c618d-103">#error (C# Reference)</span></span>

<span data-ttu-id="c618d-104">`#error` 可从代码中的特定位置生成 [CS1029](../compiler-messages/cs1029.md) 用户定义的错误。</span><span class="sxs-lookup"><span data-stu-id="c618d-104">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="c618d-105">例如：</span><span class="sxs-lookup"><span data-stu-id="c618d-105">For example:</span></span>

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> <span data-ttu-id="c618d-106">编译器以特殊的方式处理 `#error version` 并报告编译器错误 CS8304，消息中包含使用的编译器和语言版本。</span><span class="sxs-lookup"><span data-stu-id="c618d-106">The compiler treats `#error version` in a special way and reports a compiler error, CS8304, with a message containing the used compiler and language versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="c618d-107">备注</span><span class="sxs-lookup"><span data-stu-id="c618d-107">Remarks</span></span>

<span data-ttu-id="c618d-108">`#error` 常用于条件指令中。</span><span class="sxs-lookup"><span data-stu-id="c618d-108">A common use of `#error` is in a conditional directive.</span></span>

<span data-ttu-id="c618d-109">还可使用 [#warning](./preprocessor-warning.md) 生成用户定义警告。</span><span class="sxs-lookup"><span data-stu-id="c618d-109">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>

## <a name="example"></a><span data-ttu-id="c618d-110">示例</span><span class="sxs-lookup"><span data-stu-id="c618d-110">Example</span></span>

```csharp
// preprocessor_error.cs
// CS1029 expected
#define DEBUG
class MainClass
{
    static void Main()
    {
#if DEBUG
#error DEBUG is defined
#endif
    }
}
```

## <a name="see-also"></a><span data-ttu-id="c618d-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="c618d-111">See also</span></span>

- [<span data-ttu-id="c618d-112">C# 参考</span><span class="sxs-lookup"><span data-stu-id="c618d-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c618d-113">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="c618d-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c618d-114">C# 预处理器指令</span><span class="sxs-lookup"><span data-stu-id="c618d-114">C# Preprocessor Directives</span></span>](./index.md)
