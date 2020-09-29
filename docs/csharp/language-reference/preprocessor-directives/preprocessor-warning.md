---
description: '#warning - C# 参考'
title: '#warning - C# 参考'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 9ade723bdca17597dcd56240f506e60f2debf6be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186414"
---
# <a name="warning-c-reference"></a><span data-ttu-id="83356-103">#warning（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="83356-103">#warning (C# Reference)</span></span>

<span data-ttu-id="83356-104">`#warning` 允许你从代码中的特定位置生成 [ CS1030](../../misc/cs1030.md) 第一级编译器警告。</span><span class="sxs-lookup"><span data-stu-id="83356-104">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="83356-105">例如：</span><span class="sxs-lookup"><span data-stu-id="83356-105">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="83356-106">备注</span><span class="sxs-lookup"><span data-stu-id="83356-106">Remarks</span></span>

 <span data-ttu-id="83356-107">`#warning` 常用于条件指令中。</span><span class="sxs-lookup"><span data-stu-id="83356-107">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="83356-108">还可使用 [#error](./preprocessor-error.md) 生成用户定义错误。</span><span class="sxs-lookup"><span data-stu-id="83356-108">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="83356-109">示例</span><span class="sxs-lookup"><span data-stu-id="83356-109">Example</span></span>  

```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="83356-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="83356-110">See also</span></span>

- [<span data-ttu-id="83356-111">C# 参考</span><span class="sxs-lookup"><span data-stu-id="83356-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="83356-112">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="83356-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="83356-113">C# 预处理器指令</span><span class="sxs-lookup"><span data-stu-id="83356-113">C# Preprocessor Directives</span></span>](./index.md)
