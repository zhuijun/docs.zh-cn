---
title: Alias 子句
ms.date: 07/20/2015
f1_keywords:
- vb.Alias
helpviewer_keywords:
- Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
ms.openlocfilehash: c28e931a376b20b2058a7187551405cd9523d4fe
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408466"
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="623cc-102">Alias 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="623cc-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="623cc-103">指示外部过程在其 DLL 中有另一个名称。</span><span class="sxs-lookup"><span data-stu-id="623cc-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="623cc-104">备注</span><span class="sxs-lookup"><span data-stu-id="623cc-104">Remarks</span></span>  
 <span data-ttu-id="623cc-105">`Alias`关键字可以在此上下文中使用：</span><span class="sxs-lookup"><span data-stu-id="623cc-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="623cc-106">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="623cc-106">Declare Statement</span></span>](declare-statement.md)  
  
 <span data-ttu-id="623cc-107">在下面的示例中， `Alias` 关键字用于提供 advapi32.dll 中的函数的名称， `GetUserNameA` `getUserName` 此名称用于替代本示例中的。</span><span class="sxs-lookup"><span data-stu-id="623cc-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="623cc-108">`getUserName`在 sub 中调用函数 `getUser` ，该函数显示当前用户的名称。</span><span class="sxs-lookup"><span data-stu-id="623cc-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="623cc-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="623cc-109">See also</span></span>

- [<span data-ttu-id="623cc-110">关键字</span><span class="sxs-lookup"><span data-stu-id="623cc-110">Keywords</span></span>](../keywords/index.md)
