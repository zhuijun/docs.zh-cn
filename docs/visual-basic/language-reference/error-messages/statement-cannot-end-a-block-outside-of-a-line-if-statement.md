---
title: 语句不能在“If”语句行之外结束块
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 3fe3faaa3637446bb6ab443ba1d6e1d1004b4d48
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400313"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="396e2-102">语句不能在“If”语句行之外结束块</span><span class="sxs-lookup"><span data-stu-id="396e2-102">Statement cannot end a block outside of a line 'If' statement</span></span>
<span data-ttu-id="396e2-103">单行 `If` 语句包含用冒号（:) 分隔的多个语句，其中一个语句 `End` 用于单个行外的控制块 `If` 。</span><span class="sxs-lookup"><span data-stu-id="396e2-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="396e2-104">单行 `If` 语句不使用 `End If` 语句。</span><span class="sxs-lookup"><span data-stu-id="396e2-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="396e2-105">**错误 ID：** BC32005</span><span class="sxs-lookup"><span data-stu-id="396e2-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="396e2-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="396e2-106">To correct this error</span></span>  
  
- <span data-ttu-id="396e2-107">在 `If` 包含语句的控制块外移动单行语句 `End If` 。</span><span class="sxs-lookup"><span data-stu-id="396e2-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="396e2-108">另请参阅</span><span class="sxs-lookup"><span data-stu-id="396e2-108">See also</span></span>

- [<span data-ttu-id="396e2-109">If...Then...Else 语句</span><span class="sxs-lookup"><span data-stu-id="396e2-109">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
