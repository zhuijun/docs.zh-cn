---
description: '#endif - C# 参考'
title: '#endif - C# 参考'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 8068a6e437145178fd5c88763c86692a8700c349
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138158"
---
# <a name="endif-c-reference"></a><span data-ttu-id="95184-103">#endif（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="95184-103">#endif (C# Reference)</span></span>
<span data-ttu-id="95184-104">`#endif` 指定条件指令的末尾，以 [#if](./preprocessor-if.md) 指令开头。</span><span class="sxs-lookup"><span data-stu-id="95184-104">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="95184-105">例如，应用于对象的</span><span class="sxs-lookup"><span data-stu-id="95184-105">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="95184-106">备注</span><span class="sxs-lookup"><span data-stu-id="95184-106">Remarks</span></span>  
 <span data-ttu-id="95184-107">以 `#if` 指令开头的条件指令必须以 `#endif` 指令显式终止。</span><span class="sxs-lookup"><span data-stu-id="95184-107">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="95184-108">有关如何使用 `#endif` 的示例，请参阅 [#if](./preprocessor-if.md)。</span><span class="sxs-lookup"><span data-stu-id="95184-108">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95184-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="95184-109">See also</span></span>

- [<span data-ttu-id="95184-110">C# 参考</span><span class="sxs-lookup"><span data-stu-id="95184-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="95184-111">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="95184-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="95184-112">C# 预处理器指令</span><span class="sxs-lookup"><span data-stu-id="95184-112">C# Preprocessor Directives</span></span>](./index.md)
