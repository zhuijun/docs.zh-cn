---
title: “<methodname>”具有多个带有相同签名的定义
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 2934a5666c55e1ca57b91ab86585261e6d71a2d3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873725"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="2ce5c-102">“\<methodname>”具有多个带有相同签名的定义</span><span class="sxs-lookup"><span data-stu-id="2ce5c-102">'\<methodname>' has multiple definitions with identical signatures</span></span>

<span data-ttu-id="2ce5c-103">`Function`或 `Sub` 过程声明使用相同的过程名称和参数列表作为前面的声明。</span><span class="sxs-lookup"><span data-stu-id="2ce5c-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="2ce5c-104">一个可能的原因是尝试重载原始过程。</span><span class="sxs-lookup"><span data-stu-id="2ce5c-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="2ce5c-105">重载过程必须具有不同的参数列表。</span><span class="sxs-lookup"><span data-stu-id="2ce5c-105">Overloaded procedures must have different argument lists.</span></span>  
  
 <span data-ttu-id="2ce5c-106">**错误 ID：** BC30269</span><span class="sxs-lookup"><span data-stu-id="2ce5c-106">**Error ID:** BC30269</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2ce5c-107">更正此错误</span><span class="sxs-lookup"><span data-stu-id="2ce5c-107">To correct this error</span></span>  
  
- <span data-ttu-id="2ce5c-108">更改过程名称或参数列表，或删除重复的声明。</span><span class="sxs-lookup"><span data-stu-id="2ce5c-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ce5c-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ce5c-109">See also</span></span>

- [<span data-ttu-id="2ce5c-110">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="2ce5c-110">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="2ce5c-111">重载过程注意事项</span><span class="sxs-lookup"><span data-stu-id="2ce5c-111">Considerations in Overloading Procedures</span></span>](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
