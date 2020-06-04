---
title: 变量“<variablename>”在封闭块中隐藏变量
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 474a920c9cfdfba7a8157320d9c88b8677958425
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406516"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="5eb11-102">变量“\<variablename>”在封闭块中隐藏变量</span><span class="sxs-lookup"><span data-stu-id="5eb11-102">Variable '\<variablename>' hides a variable in an enclosing block</span></span>
<span data-ttu-id="5eb11-103">块中包含的变量与另一个本地变量的名称相同。</span><span class="sxs-lookup"><span data-stu-id="5eb11-103">A variable enclosed in a block has the same name as another local variable.</span></span>  
  
 <span data-ttu-id="5eb11-104">**错误 ID：** BC30616</span><span class="sxs-lookup"><span data-stu-id="5eb11-104">**Error ID:** BC30616</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5eb11-105">更正此错误</span><span class="sxs-lookup"><span data-stu-id="5eb11-105">To correct this error</span></span>  
  
- <span data-ttu-id="5eb11-106">重命名封闭块中的变量，使其与其他任何局部变量不同。</span><span class="sxs-lookup"><span data-stu-id="5eb11-106">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="5eb11-107">例如：</span><span class="sxs-lookup"><span data-stu-id="5eb11-107">For example:</span></span>  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- <span data-ttu-id="5eb11-108">此错误的一个常见原因是在 `Catch e As Exception` 事件处理程序内部使用。</span><span class="sxs-lookup"><span data-stu-id="5eb11-108">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="5eb11-109">如果是这种情况，请将 `Catch` 块变量命名为 `ex` 而不是 `e` 。</span><span class="sxs-lookup"><span data-stu-id="5eb11-109">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>  
  
- <span data-ttu-id="5eb11-110">此错误的另一个常见原因是尝试访问在单独块内的块内声明的局部变量 `Try` `Catch` 。</span><span class="sxs-lookup"><span data-stu-id="5eb11-110">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="5eb11-111">若要更正此错误，请在结构外声明变量 `Try...Catch...Finally` 。</span><span class="sxs-lookup"><span data-stu-id="5eb11-111">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eb11-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5eb11-112">See also</span></span>

- [<span data-ttu-id="5eb11-113">Try...Catch...Finally 语句</span><span class="sxs-lookup"><span data-stu-id="5eb11-113">Try...Catch...Finally Statement</span></span>](../statements/try-catch-finally-statement.md)
- [<span data-ttu-id="5eb11-114">变量声明</span><span class="sxs-lookup"><span data-stu-id="5eb11-114">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
