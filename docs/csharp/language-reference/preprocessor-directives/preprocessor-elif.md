---
description: '#elif - C# 参考'
title: '#elif - C# 参考'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: 3aa9082b392b352091b9fde74a85f9dd155ad7b1
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132282"
---
# <a name="elif-c-reference"></a><span data-ttu-id="8cdb1-103">#elif（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="8cdb1-103">#elif (C# Reference)</span></span>
<span data-ttu-id="8cdb1-104">`#elif` 可以创建复合条件指令。</span><span class="sxs-lookup"><span data-stu-id="8cdb1-104">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="8cdb1-105">如果之前的 [#if](./preprocessor-if.md) 和任何之前的可选 `#elif` 指令表达式的值为 `true`，则计算 `#elif` 表达式。</span><span class="sxs-lookup"><span data-stu-id="8cdb1-105">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="8cdb1-106">如果 `#elif` 表达式计算结果为 `true`，编译器将计算 `#elif` 和下一条件指令间的所有代码。</span><span class="sxs-lookup"><span data-stu-id="8cdb1-106">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="8cdb1-107">例如：</span><span class="sxs-lookup"><span data-stu-id="8cdb1-107">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="8cdb1-108">可以使用运算符 `==`（相等）、`!=`（不相等）、`&&`（和）以及`||`（或）计算多个符号。</span><span class="sxs-lookup"><span data-stu-id="8cdb1-108">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="8cdb1-109">还可以用括号对符号和运算符进行分组。</span><span class="sxs-lookup"><span data-stu-id="8cdb1-109">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8cdb1-110">备注</span><span class="sxs-lookup"><span data-stu-id="8cdb1-110">Remarks</span></span>  
 <span data-ttu-id="8cdb1-111">`#elif` 等效于使用：</span><span class="sxs-lookup"><span data-stu-id="8cdb1-111">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="8cdb1-112">使用 `#elif` 更简单，因为每个 `#if` 均需要 [#endif](./preprocessor-endif.md)，但 `#elif` 可在没有匹配的 `#endif` 的情况下使用。</span><span class="sxs-lookup"><span data-stu-id="8cdb1-112">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="8cdb1-113">有关如何使用 `#elif` 的示例，请参阅 [#if](./preprocessor-if.md)。</span><span class="sxs-lookup"><span data-stu-id="8cdb1-113">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cdb1-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="8cdb1-114">See also</span></span>

- [<span data-ttu-id="8cdb1-115">C# 参考</span><span class="sxs-lookup"><span data-stu-id="8cdb1-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8cdb1-116">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="8cdb1-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8cdb1-117">C# 预处理器指令</span><span class="sxs-lookup"><span data-stu-id="8cdb1-117">C# Preprocessor Directives</span></span>](./index.md)
