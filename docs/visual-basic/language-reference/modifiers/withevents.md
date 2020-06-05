---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 48261e27de302c1809c9725e6e2fc0705a803930
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386771"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="f6157-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6157-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="f6157-103">指定一个或多个已声明的成员变量引用可引发事件的类的实例。</span><span class="sxs-lookup"><span data-stu-id="f6157-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>

## <a name="remarks"></a><span data-ttu-id="f6157-104">备注</span><span class="sxs-lookup"><span data-stu-id="f6157-104">Remarks</span></span>

<span data-ttu-id="f6157-105">使用定义变量时 `WithEvents` ，可以通过声明方式指定方法使用关键字来处理变量的事件 `Handles` 。</span><span class="sxs-lookup"><span data-stu-id="f6157-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>

<span data-ttu-id="f6157-106">只能 `WithEvents` 在类或模块级别使用。</span><span class="sxs-lookup"><span data-stu-id="f6157-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="f6157-107">这意味着变量的声明上下文 `WithEvents` 必须是类或模块，不能是源文件、命名空间、结构或过程。</span><span class="sxs-lookup"><span data-stu-id="f6157-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>

<span data-ttu-id="f6157-108">不能 `WithEvents` 对结构成员使用。</span><span class="sxs-lookup"><span data-stu-id="f6157-108">You cannot use `WithEvents` on a structure member.</span></span>

<span data-ttu-id="f6157-109">只能声明单个变量（而不是数组） `WithEvents` 。</span><span class="sxs-lookup"><span data-stu-id="f6157-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>

## <a name="rules"></a><span data-ttu-id="f6157-110">规则</span><span class="sxs-lookup"><span data-stu-id="f6157-110">Rules</span></span>

<span data-ttu-id="f6157-111">**元素类型。**</span><span class="sxs-lookup"><span data-stu-id="f6157-111">**Element Types.**</span></span> <span data-ttu-id="f6157-112">您必须 `WithEvents` 将变量声明为对象变量，以便它们可以接受类实例。</span><span class="sxs-lookup"><span data-stu-id="f6157-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="f6157-113">但是，不能将它们声明为 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="f6157-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="f6157-114">您必须将它们声明为可引发事件的特定类。</span><span class="sxs-lookup"><span data-stu-id="f6157-114">You must declare them as the specific class that can raise the events.</span></span>

<span data-ttu-id="f6157-115">`WithEvents`修饰符可用于以下上下文： [Dim 语句](../statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="f6157-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../statements/dim-statement.md)</span></span>

## <a name="example"></a><span data-ttu-id="f6157-116">示例</span><span class="sxs-lookup"><span data-stu-id="f6157-116">Example</span></span>

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a><span data-ttu-id="f6157-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f6157-117">See also</span></span>

- [<span data-ttu-id="f6157-118">句柄数</span><span class="sxs-lookup"><span data-stu-id="f6157-118">Handles</span></span>](../statements/handles-clause.md)
- [<span data-ttu-id="f6157-119">关键字</span><span class="sxs-lookup"><span data-stu-id="f6157-119">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="f6157-120">事件</span><span class="sxs-lookup"><span data-stu-id="f6157-120">Events</span></span>](../../programming-guide/language-features/events/index.md)
