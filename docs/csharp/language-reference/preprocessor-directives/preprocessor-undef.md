---
description: '#undef - C# 参考'
title: '#undef - C# 参考'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 7db79be7ea9d8462e09b6ae874bf0ae7d265afe2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150552"
---
# <a name="undef-c-reference"></a><span data-ttu-id="bcf18-103">#undef（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="bcf18-103">#undef (C# Reference)</span></span>

<span data-ttu-id="bcf18-104">`#undef` 允许你定义一个符号，这样一来，通过将该符号用作 [#if](./preprocessor-if.md) 指令中的表达式，表达式将计算为 `false`。</span><span class="sxs-lookup"><span data-stu-id="bcf18-104">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="bcf18-105">可使用 [#define](./preprocessor-define.md) 指令或 [-define](../compiler-options/define-compiler-option.md) 编译器选项来定义符号。</span><span class="sxs-lookup"><span data-stu-id="bcf18-105">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="bcf18-106">文件中必须先出现 `#undef` 指令，才能使用任何非指令的语句。</span><span class="sxs-lookup"><span data-stu-id="bcf18-106">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcf18-107">示例</span><span class="sxs-lookup"><span data-stu-id="bcf18-107">Example</span></span>  

```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass
{  
    static void Main()
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```

<span data-ttu-id="bcf18-108">未定义 DEBUG\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="bcf18-108">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="bcf18-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="bcf18-109">See also</span></span>

- [<span data-ttu-id="bcf18-110">C# 参考</span><span class="sxs-lookup"><span data-stu-id="bcf18-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bcf18-111">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="bcf18-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bcf18-112">C# 预处理器指令</span><span class="sxs-lookup"><span data-stu-id="bcf18-112">C# Preprocessor Directives</span></span>](./index.md)
