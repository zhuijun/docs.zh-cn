---
description: 方法参数 - C# 参考
title: 方法参数 - C# 参考
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 7090bf1c3df65cf1e65942404f883b49612e7521
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134401"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="69c3c-103">方法参数（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="69c3c-103">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="69c3c-104">为不具有 [in](./in-parameter-modifier.md)、[ref](./ref.md) 或 [out](./out-parameter-modifier.md) 的方法声明的参数会按值传递给调用的方法。</span><span class="sxs-lookup"><span data-stu-id="69c3c-104">Parameters declared for a method without [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="69c3c-105">可以在方法中更改该值，但当控制传递回调用过程时，不会保留更改后的值。</span><span class="sxs-lookup"><span data-stu-id="69c3c-105">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="69c3c-106">可以通过使用方法参数关键字更改此行为。</span><span class="sxs-lookup"><span data-stu-id="69c3c-106">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="69c3c-107">本部分介绍声明方法参数时可以使用的关键字：</span><span class="sxs-lookup"><span data-stu-id="69c3c-107">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
- <span data-ttu-id="69c3c-108">[params](./params.md) 指定此参数采用可变数量的参数。</span><span class="sxs-lookup"><span data-stu-id="69c3c-108">[params](./params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
- <span data-ttu-id="69c3c-109">[in](./in-parameter-modifier.md) 指定此参数由引用传递，但只由调用方法读取。</span><span class="sxs-lookup"><span data-stu-id="69c3c-109">[in](./in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
- <span data-ttu-id="69c3c-110">[ref](./ref.md) 指定此参数由引用传递，可能由调用方法读取或写入。</span><span class="sxs-lookup"><span data-stu-id="69c3c-110">[ref](./ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
- <span data-ttu-id="69c3c-111">[out](./out-parameter-modifier.md) 指定此参数由引用传递，由调用方法写入。</span><span class="sxs-lookup"><span data-stu-id="69c3c-111">[out](./out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="69c3c-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="69c3c-112">See also</span></span>

- [<span data-ttu-id="69c3c-113">C# 参考</span><span class="sxs-lookup"><span data-stu-id="69c3c-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="69c3c-114">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="69c3c-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="69c3c-115">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="69c3c-115">C# Keywords</span></span>](./index.md)
