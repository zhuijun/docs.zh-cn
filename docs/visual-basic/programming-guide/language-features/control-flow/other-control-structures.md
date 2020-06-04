---
title: 其他控件结构
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: c6d80b237c7c3512c2904547842fdeb3c69bef68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402013"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="1020c-102">其他控件结构 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1020c-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="1020c-103">Visual Basic 提供了控制结构，可帮助您释放资源或减少必须重复对象引用的次数。</span><span class="sxs-lookup"><span data-stu-id="1020c-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="1020c-104">使用 .。。使用构造结束</span><span class="sxs-lookup"><span data-stu-id="1020c-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="1020c-105">`Using...End Using`构造建立了一个语句块，其中使用了诸如 SQL 连接等资源。</span><span class="sxs-lookup"><span data-stu-id="1020c-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="1020c-106">您可以选择获取带有语句的资源 `Using` 。</span><span class="sxs-lookup"><span data-stu-id="1020c-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="1020c-107">退出 `Using` 块时，Visual Basic 会自动释放资源，以便其他代码可以使用该资源。</span><span class="sxs-lookup"><span data-stu-id="1020c-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="1020c-108">资源必须是本地的，并且是可释放的。</span><span class="sxs-lookup"><span data-stu-id="1020c-108">The resource must be local and disposable.</span></span> <span data-ttu-id="1020c-109">有关详细信息，请参阅[Using 语句](../../../language-reference/statements/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="1020c-109">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="1020c-110">用 .。。以构造结尾</span><span class="sxs-lookup"><span data-stu-id="1020c-110">With...End With Construction</span></span>  
 <span data-ttu-id="1020c-111">`With...End With`构造使你可以指定一个对象引用一次，并运行一系列访问其成员的语句。</span><span class="sxs-lookup"><span data-stu-id="1020c-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="1020c-112">这可以简化代码和提高性能，因为 Visual Basic 不必为访问它的每个语句重新建立引用。</span><span class="sxs-lookup"><span data-stu-id="1020c-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="1020c-113">有关详细信息，请参阅[With .。。End With 语句](../../../language-reference/statements/with-end-with-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="1020c-113">For more information, see [With...End With Statement](../../../language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1020c-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1020c-114">See also</span></span>

- [<span data-ttu-id="1020c-115">控制流</span><span class="sxs-lookup"><span data-stu-id="1020c-115">Control Flow</span></span>](index.md)
- [<span data-ttu-id="1020c-116">决策结构</span><span class="sxs-lookup"><span data-stu-id="1020c-116">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="1020c-117">循环结构</span><span class="sxs-lookup"><span data-stu-id="1020c-117">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="1020c-118">嵌套的控件结构</span><span class="sxs-lookup"><span data-stu-id="1020c-118">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="1020c-119">Using 语句</span><span class="sxs-lookup"><span data-stu-id="1020c-119">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
- [<span data-ttu-id="1020c-120">With...End With 语句</span><span class="sxs-lookup"><span data-stu-id="1020c-120">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
