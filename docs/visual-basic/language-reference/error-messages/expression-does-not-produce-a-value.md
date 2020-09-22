---
title: 表达式不产生值
ms.date: 07/20/2015
f1_keywords:
- vbc30491
- bc30491
helpviewer_keywords:
- BC30491
ms.assetid: 8399d7ae-bc0a-49e6-81dc-2e7229708bc9
ms.openlocfilehash: eaa6633996b6fef8ba949e1d8aa7f19d7d5fb6a4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874267"
---
# <a name="expression-does-not-produce-a-value"></a><span data-ttu-id="0127e-102">表达式不产生值</span><span class="sxs-lookup"><span data-stu-id="0127e-102">Expression does not produce a value</span></span>

<span data-ttu-id="0127e-103">您尝试使用的表达式不在生成值的上下文中生成值，如 `Sub` 在所需的上下文中调用 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="0127e-103">You have tried to use an expression that does not produce a value in a value-producing context, such as calling a `Sub` in a context where a `Function` is expected.</span></span>  
  
 <span data-ttu-id="0127e-104">**错误 ID：** BC30491</span><span class="sxs-lookup"><span data-stu-id="0127e-104">**Error ID:** BC30491</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0127e-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="0127e-105">To correct this error</span></span>  
  
- <span data-ttu-id="0127e-106">将表达式更改为一个生成值的表达式。</span><span class="sxs-lookup"><span data-stu-id="0127e-106">Change the expression to one that produces a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0127e-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0127e-107">See also</span></span>

- [<span data-ttu-id="0127e-108">错误类型</span><span class="sxs-lookup"><span data-stu-id="0127e-108">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
