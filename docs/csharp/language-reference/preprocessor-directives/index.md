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
ms.openlocfilehash: a7ffca8b39f1bd9f05193bccbb6d90e67fa262c9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132360"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="67772-103">C# 预处理器指令</span><span class="sxs-lookup"><span data-stu-id="67772-103">C# preprocessor directives</span></span>
<span data-ttu-id="67772-104">本节介绍了以下 C# 预处理器指令：</span><span class="sxs-lookup"><span data-stu-id="67772-104">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="67772-105">#if</span><span class="sxs-lookup"><span data-stu-id="67772-105">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="67772-106">#else</span><span class="sxs-lookup"><span data-stu-id="67772-106">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="67772-107">#elif</span><span class="sxs-lookup"><span data-stu-id="67772-107">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="67772-108">#endif</span><span class="sxs-lookup"><span data-stu-id="67772-108">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="67772-109">#define</span><span class="sxs-lookup"><span data-stu-id="67772-109">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="67772-110">#undef</span><span class="sxs-lookup"><span data-stu-id="67772-110">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="67772-111">#warning</span><span class="sxs-lookup"><span data-stu-id="67772-111">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="67772-112">#error</span><span class="sxs-lookup"><span data-stu-id="67772-112">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="67772-113">#line</span><span class="sxs-lookup"><span data-stu-id="67772-113">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="67772-114">#region</span><span class="sxs-lookup"><span data-stu-id="67772-114">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="67772-115">#endregion</span><span class="sxs-lookup"><span data-stu-id="67772-115">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="67772-116">#pragma</span><span class="sxs-lookup"><span data-stu-id="67772-116">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="67772-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="67772-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="67772-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="67772-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="67772-119">请参阅各个主题了解更多信息和示例。</span><span class="sxs-lookup"><span data-stu-id="67772-119">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="67772-120">尽管编译器没有单独的预处理器，但本节中所述指令的处理方式与有预处理器时一样。</span><span class="sxs-lookup"><span data-stu-id="67772-120">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="67772-121">这些指令用于帮助条件编译。</span><span class="sxs-lookup"><span data-stu-id="67772-121">They are used to help in conditional compilation.</span></span> <span data-ttu-id="67772-122">不同于 C 和 C++ 指令，不能使用这些指令来创建宏。</span><span class="sxs-lookup"><span data-stu-id="67772-122">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="67772-123">预处理器指令必须是一行中唯一的说明。</span><span class="sxs-lookup"><span data-stu-id="67772-123">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="67772-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="67772-124">See also</span></span>

- [<span data-ttu-id="67772-125">C# 参考</span><span class="sxs-lookup"><span data-stu-id="67772-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="67772-126">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="67772-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
