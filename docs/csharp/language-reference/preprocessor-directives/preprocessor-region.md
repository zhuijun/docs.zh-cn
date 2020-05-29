---
title: '#region -C# 参考'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 66583d6e067b006b03130d8ff842b56bf57bcebc
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802776"
---
# <a name="region-c-reference"></a><span data-ttu-id="014a3-102">#region（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="014a3-102">#region (C# Reference)</span></span>
<span data-ttu-id="014a3-103">利用 `#region`，可以指定在使用代码编辑器的[大纲](/visualstudio/ide/outlining)功能时可展开或折叠的代码块。</span><span class="sxs-lookup"><span data-stu-id="014a3-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the code editor.</span></span> <span data-ttu-id="014a3-104">在较长的代码文件中，能够折叠或隐藏一个或多个区域会十分便利，这样，可将精力集中于当前处理的文件部分。</span><span class="sxs-lookup"><span data-stu-id="014a3-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="014a3-105">下面的示例演示如何定义区域：</span><span class="sxs-lookup"><span data-stu-id="014a3-105">The following example shows how to define a region:</span></span>  
  
```csharp
#region MyClass definition  
public class MyClass
{  
    static void Main()
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a><span data-ttu-id="014a3-106">备注</span><span class="sxs-lookup"><span data-stu-id="014a3-106">Remarks</span></span>  
 <span data-ttu-id="014a3-107">`#region` 块必须通过 [#endregion](./preprocessor-endregion.md) 指令终止。</span><span class="sxs-lookup"><span data-stu-id="014a3-107">A `#region` block must be terminated with a [#endregion](./preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="014a3-108">`#region` 块不能与 [#if](./preprocessor-if.md) 块重叠。</span><span class="sxs-lookup"><span data-stu-id="014a3-108">A `#region` block cannot overlap with a [#if](./preprocessor-if.md) block.</span></span> <span data-ttu-id="014a3-109">但是，可以将 `#region` 块嵌套在 `#if` 块内，或将 `#if` 块嵌套在 `#region` 块内。</span><span class="sxs-lookup"><span data-stu-id="014a3-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="014a3-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="014a3-110">See also</span></span>

- [<span data-ttu-id="014a3-111">C# 参考</span><span class="sxs-lookup"><span data-stu-id="014a3-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="014a3-112">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="014a3-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="014a3-113">C# 预处理器指令</span><span class="sxs-lookup"><span data-stu-id="014a3-113">C# Preprocessor Directives</span></span>](./index.md)
