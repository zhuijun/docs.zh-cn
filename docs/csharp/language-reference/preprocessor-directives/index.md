---
description: C# 预处理器指令
title: C# 预处理器指令
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: 210a024a8062f5070b2a500384f51b37c9d802c0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157949"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="6b2aa-103">C# 预处理器指令</span><span class="sxs-lookup"><span data-stu-id="6b2aa-103">C# preprocessor directives</span></span>

<span data-ttu-id="6b2aa-104">本节介绍了以下 C# 预处理器指令：</span><span class="sxs-lookup"><span data-stu-id="6b2aa-104">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="6b2aa-105">#if</span><span class="sxs-lookup"><span data-stu-id="6b2aa-105">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="6b2aa-106">#else</span><span class="sxs-lookup"><span data-stu-id="6b2aa-106">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="6b2aa-107">#elif</span><span class="sxs-lookup"><span data-stu-id="6b2aa-107">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="6b2aa-108">#endif</span><span class="sxs-lookup"><span data-stu-id="6b2aa-108">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="6b2aa-109">#define</span><span class="sxs-lookup"><span data-stu-id="6b2aa-109">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="6b2aa-110">#undef</span><span class="sxs-lookup"><span data-stu-id="6b2aa-110">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="6b2aa-111">#warning</span><span class="sxs-lookup"><span data-stu-id="6b2aa-111">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="6b2aa-112">#error</span><span class="sxs-lookup"><span data-stu-id="6b2aa-112">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="6b2aa-113">#line</span><span class="sxs-lookup"><span data-stu-id="6b2aa-113">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="6b2aa-114">#region</span><span class="sxs-lookup"><span data-stu-id="6b2aa-114">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="6b2aa-115">#endregion</span><span class="sxs-lookup"><span data-stu-id="6b2aa-115">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="6b2aa-116">#pragma</span><span class="sxs-lookup"><span data-stu-id="6b2aa-116">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="6b2aa-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="6b2aa-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="6b2aa-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="6b2aa-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="6b2aa-119">请参阅各个主题了解更多信息和示例。</span><span class="sxs-lookup"><span data-stu-id="6b2aa-119">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="6b2aa-120">尽管编译器没有单独的预处理器，但本节中所述指令的处理方式与有预处理器时一样。</span><span class="sxs-lookup"><span data-stu-id="6b2aa-120">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="6b2aa-121">这些指令用于帮助条件编译。</span><span class="sxs-lookup"><span data-stu-id="6b2aa-121">They are used to help in conditional compilation.</span></span> <span data-ttu-id="6b2aa-122">不同于 C 和 C++ 指令，不能使用这些指令来创建宏。</span><span class="sxs-lookup"><span data-stu-id="6b2aa-122">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="6b2aa-123">预处理器指令必须是一行中唯一的说明。</span><span class="sxs-lookup"><span data-stu-id="6b2aa-123">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b2aa-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="6b2aa-124">See also</span></span>

- [<span data-ttu-id="6b2aa-125">C# 参考</span><span class="sxs-lookup"><span data-stu-id="6b2aa-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6b2aa-126">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="6b2aa-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
