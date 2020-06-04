---
title: 自变量不可选
ms.date: 07/20/2015
f1_keywords:
- vbrID449
ms.assetid: 76e7bcf3-24ed-4cd5-945b-b98f1c76944b
ms.openlocfilehash: cac81d364d71af65d922faa2f2db5d7ede415126
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409980"
---
# <a name="argument-not-optional-visual-basic"></a><span data-ttu-id="e7e4c-102">非可选自变量 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7e4c-102">Argument not optional (Visual Basic)</span></span>

<span data-ttu-id="e7e4c-103">参数的数量和类型必须与需要的参数匹配。</span><span class="sxs-lookup"><span data-stu-id="e7e4c-103">The number and types of arguments must match those expected.</span></span> <span data-ttu-id="e7e4c-104">参数的数目不正确，或者省略的参数不是可选的。</span><span class="sxs-lookup"><span data-stu-id="e7e4c-104">Either there is an incorrect number of arguments, or an omitted argument is not optional.</span></span> <span data-ttu-id="e7e4c-105">如果在过程定义中声明了某个参数，则只能通过对用户定义的过程的调用来省略此参数 `Optional` 。</span><span class="sxs-lookup"><span data-stu-id="e7e4c-105">An argument can only be omitted from a call to a user-defined procedure if it was declared `Optional` in the procedure definition.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e7e4c-106">更正此错误</span><span class="sxs-lookup"><span data-stu-id="e7e4c-106">To correct this error</span></span>  
  
1. <span data-ttu-id="e7e4c-107">提供所有必需的参数。</span><span class="sxs-lookup"><span data-stu-id="e7e4c-107">Supply all necessary arguments.</span></span>  
  
2. <span data-ttu-id="e7e4c-108">请确保省略的参数是可选的。</span><span class="sxs-lookup"><span data-stu-id="e7e4c-108">Make sure omitted arguments are optional.</span></span> <span data-ttu-id="e7e4c-109">如果不是，则在调用中提供参数，或在定义中声明参数 `Optional` 。</span><span class="sxs-lookup"><span data-stu-id="e7e4c-109">If they are not, either supply the argument in the call, or declare the parameter `Optional` in the definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7e4c-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e7e4c-110">See also</span></span>

- [<span data-ttu-id="e7e4c-111">错误类型</span><span class="sxs-lookup"><span data-stu-id="e7e4c-111">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
