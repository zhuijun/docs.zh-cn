---
title: 如何：创建固定值变量
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 04e08784b5cfbdeb6db73b9b00fe9afa201bd06d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410511"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="57b00-102">如何：创建固定值变量 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57b00-102">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>

<span data-ttu-id="57b00-103">不更改其值的变量的概念可能看似矛盾。</span><span class="sxs-lookup"><span data-stu-id="57b00-103">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="57b00-104">但在某些情况下，常量并不可行，并且具有固定值的变量很有用。</span><span class="sxs-lookup"><span data-stu-id="57b00-104">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="57b00-105">在这种情况下，可以使用[ReadOnly](../../../language-reference/modifiers/readonly.md)关键字定义成员变量。</span><span class="sxs-lookup"><span data-stu-id="57b00-105">In such a case you can define a member variable with the [ReadOnly](../../../language-reference/modifiers/readonly.md) keyword.</span></span>

<span data-ttu-id="57b00-106">在以下情况下，不能使用[Const 语句](../../../language-reference/statements/const-statement.md)来声明和分配常量值：</span><span class="sxs-lookup"><span data-stu-id="57b00-106">You cannot use the [Const Statement](../../../language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>

- <span data-ttu-id="57b00-107">`Const`语句不接受要使用的数据类型</span><span class="sxs-lookup"><span data-stu-id="57b00-107">The `Const` statement does not accept the data type you want to use</span></span>

- <span data-ttu-id="57b00-108">在编译时不知道值</span><span class="sxs-lookup"><span data-stu-id="57b00-108">You do not know the value at compile time</span></span>

- <span data-ttu-id="57b00-109">在编译时无法计算常量值</span><span class="sxs-lookup"><span data-stu-id="57b00-109">You are unable to compute the constant value at compile time</span></span>

### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="57b00-110">创建在值中不变的变量</span><span class="sxs-lookup"><span data-stu-id="57b00-110">To create a variable that does not change in value</span></span>

1. <span data-ttu-id="57b00-111">在模块级别，用[Dim 语句](../../../language-reference/statements/dim-statement.md)声明成员变量，并包括[ReadOnly](../../../language-reference/modifiers/readonly.md)关键字。</span><span class="sxs-lookup"><span data-stu-id="57b00-111">At module level, declare a member variable with the [Dim Statement](../../../language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../language-reference/modifiers/readonly.md) keyword.</span></span>

    ```vb
    Dim ReadOnly timeStarted
    ```

    <span data-ttu-id="57b00-112">`ReadOnly`只能在成员变量上指定。</span><span class="sxs-lookup"><span data-stu-id="57b00-112">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="57b00-113">这意味着必须在任何过程之外的模块级别定义变量。</span><span class="sxs-lookup"><span data-stu-id="57b00-113">This means you must define the variable at module level, outside of any procedure.</span></span>

2. <span data-ttu-id="57b00-114">如果可以在编译时在单个语句中计算该值，请在语句中使用初始化子句 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="57b00-114">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="57b00-115">使用等[As](../../../language-reference/statements/as-clause.md)号（ `=` ），后跟表达式作为语句。</span><span class="sxs-lookup"><span data-stu-id="57b00-115">Follow the [As](../../../language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="57b00-116">确保编译器可以将此表达式计算为常数值。</span><span class="sxs-lookup"><span data-stu-id="57b00-116">Be sure the compiler can evaluate this expression to a constant value.</span></span>

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    <span data-ttu-id="57b00-117">只能将一个值分配给一个 `ReadOnly` 变量。</span><span class="sxs-lookup"><span data-stu-id="57b00-117">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="57b00-118">完成此操作后，任何代码都不能更改其值。</span><span class="sxs-lookup"><span data-stu-id="57b00-118">Once you do so, no code can ever change its value.</span></span>

    <span data-ttu-id="57b00-119">如果你不知道编译时的值，或在编译时不能在单个语句中计算该值，则仍可在构造函数中的运行时分配该值。</span><span class="sxs-lookup"><span data-stu-id="57b00-119">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="57b00-120">为此，必须 `ReadOnly` 在类或结构级别声明变量。</span><span class="sxs-lookup"><span data-stu-id="57b00-120">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="57b00-121">在该类或结构的构造函数中，计算变量的固定值，并将其分配给变量，然后再从构造函数返回。</span><span class="sxs-lookup"><span data-stu-id="57b00-121">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>

## <a name="see-also"></a><span data-ttu-id="57b00-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="57b00-122">See also</span></span>

- [<span data-ttu-id="57b00-123">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="57b00-123">WriteOnly</span></span>](../../../language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="57b00-124">Const 语句</span><span class="sxs-lookup"><span data-stu-id="57b00-124">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
