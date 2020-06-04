---
title: 只能根据不带自变量的简单名称或限定名称推断范围变量名称
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: d6b155de0bb62f667ca76ec9454dec1466976a9b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400404"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="af765-102">只能根据不带自变量的简单名称或限定名称推断范围变量名称</span><span class="sxs-lookup"><span data-stu-id="af765-102">Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>

<span data-ttu-id="af765-103">采用一个或多个自变量的编程元素包含在 LINQ 查询中。</span><span class="sxs-lookup"><span data-stu-id="af765-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="af765-104">编译器无法从该编程元素推断范围变量。</span><span class="sxs-lookup"><span data-stu-id="af765-104">The compiler is unable to infer a range variable from that programming element.</span></span>

<span data-ttu-id="af765-105">**错误 ID：** BC36599</span><span class="sxs-lookup"><span data-stu-id="af765-105">**Error ID:** BC36599</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="af765-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="af765-106">To correct this error</span></span>

<span data-ttu-id="af765-107">提供编程元素的显式变量名，如下面的代码所示：</span><span class="sxs-lookup"><span data-stu-id="af765-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a><span data-ttu-id="af765-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="af765-108">See also</span></span>

- [<span data-ttu-id="af765-109">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="af765-109">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="af765-110">Select 子句</span><span class="sxs-lookup"><span data-stu-id="af765-110">Select Clause</span></span>](../queries/select-clause.md)
