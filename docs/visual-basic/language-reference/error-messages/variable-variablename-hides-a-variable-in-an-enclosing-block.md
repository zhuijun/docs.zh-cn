---
title: 变量“<variablename>”在封闭块中隐藏变量
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 04538be3431fb06518051db4378e986ea5711219
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875057"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="f3331-102">变量“\<variablename>”在封闭块中隐藏变量</span><span class="sxs-lookup"><span data-stu-id="f3331-102">Variable '\<variablename>' hides a variable in an enclosing block</span></span>

<span data-ttu-id="f3331-103">块中包含的变量与另一个本地变量的名称相同。</span><span class="sxs-lookup"><span data-stu-id="f3331-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="f3331-104">**错误 ID：** BC30616</span><span class="sxs-lookup"><span data-stu-id="f3331-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f3331-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="f3331-105">To correct this error</span></span>  
  
- <span data-ttu-id="f3331-106">重命名封闭块中的变量，使其与其他任何局部变量不同。</span><span class="sxs-lookup"><span data-stu-id="f3331-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="f3331-107">例如：</span><span class="sxs-lookup"><span data-stu-id="f3331-107">For example:</span></span>  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- <span data-ttu-id="f3331-108">此错误的一个常见原因是在 `Catch e As Exception` 事件处理程序内部使用。</span><span class="sxs-lookup"><span data-stu-id="f3331-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="f3331-109">如果是这种情况，请将 `Catch` 块变量命名为 `ex` 而不是 `e` 。</span><span class="sxs-lookup"><span data-stu-id="f3331-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
- <span data-ttu-id="f3331-110">此错误的另一个常见原因是尝试访问在单独块内的块内声明的局部变量 `Try` `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="f3331-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="f3331-111">若要更正此错误，请在结构外声明变量 `Try...Catch...Finally` 。</span><span class="sxs-lookup"><span data-stu-id="f3331-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3331-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f3331-112">See also</span></span>

- [<span data-ttu-id="f3331-113">Try...Catch...Finally 语句</span><span class="sxs-lookup"><span data-stu-id="f3331-113">Try...Catch...Finally Statement</span></span>](../statements/try-catch-finally-statement.md)
- [<span data-ttu-id="f3331-114">变量声明</span><span class="sxs-lookup"><span data-stu-id="f3331-114">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
