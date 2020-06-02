---
title: 共享
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: bc63de4bda1e8e605e25fbe293686c187dd4d005
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290988"
---
# <a name="shared-visual-basic"></a><span data-ttu-id="ef071-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef071-102">Shared (Visual Basic)</span></span>

<span data-ttu-id="ef071-103">指定一个或多个已声明的编程元素与较大的类或结构关联，而不是与类或结构的特定实例相关联。</span><span class="sxs-lookup"><span data-stu-id="ef071-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>

## <a name="when-to-use-shared"></a><span data-ttu-id="ef071-104">何时使用共享</span><span class="sxs-lookup"><span data-stu-id="ef071-104">When to Use Shared</span></span>

<span data-ttu-id="ef071-105">共享类或结构的成员使其可用于每个实例，而不是*非共享*，其中每个实例都保留其自己的副本。</span><span class="sxs-lookup"><span data-stu-id="ef071-105">Sharing a member of a class or structure makes it available to every instance, rather than *non-shared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="ef071-106">例如，如果将变量的值应用于整个应用程序，则此方法很有用。</span><span class="sxs-lookup"><span data-stu-id="ef071-106">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="ef071-107">如果将该变量声明为 `Shared` ，则所有实例都将访问相同的存储位置，并且如果一个实例更改该变量的值，则所有实例都将访问更新的值。</span><span class="sxs-lookup"><span data-stu-id="ef071-107">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>

<span data-ttu-id="ef071-108">共享不会更改成员的访问级别。</span><span class="sxs-lookup"><span data-stu-id="ef071-108">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="ef071-109">例如，类成员可以是共享的，也可以是专用的（只能从类中访问），也可以是非共享的和公共的。</span><span class="sxs-lookup"><span data-stu-id="ef071-109">For example, a class member can be shared and private (accessible only from within the class), or non-shared and public.</span></span> <span data-ttu-id="ef071-110">有关详细信息，请参阅[Visual Basic 中的访问级别](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="ef071-110">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

## <a name="rules"></a><span data-ttu-id="ef071-111">规则</span><span class="sxs-lookup"><span data-stu-id="ef071-111">Rules</span></span>

- <span data-ttu-id="ef071-112">**声明上下文。**</span><span class="sxs-lookup"><span data-stu-id="ef071-112">**Declaration Context.**</span></span> <span data-ttu-id="ef071-113">只能在模块级别使用 `Shared`。</span><span class="sxs-lookup"><span data-stu-id="ef071-113">You can use `Shared` only at module level.</span></span> <span data-ttu-id="ef071-114">这意味着元素的声明上下文 `Shared` 必须是类或结构，不能是源文件、命名空间或过程。</span><span class="sxs-lookup"><span data-stu-id="ef071-114">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="ef071-115">**组合修饰符。**</span><span class="sxs-lookup"><span data-stu-id="ef071-115">**Combined Modifiers.**</span></span> <span data-ttu-id="ef071-116">不能 `Shared` 在同一声明中同时指定[替代](../../../visual-basic/language-reference/modifiers/overrides.md)、[重写](../../../visual-basic/language-reference/modifiers/overridable.md)、 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)、 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)或[静态](../../../visual-basic/language-reference/modifiers/static.md)。</span><span class="sxs-lookup"><span data-stu-id="ef071-116">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>

- <span data-ttu-id="ef071-117">**访问.**</span><span class="sxs-lookup"><span data-stu-id="ef071-117">**Accessing.**</span></span> <span data-ttu-id="ef071-118">使用共享元素的类或结构名称（而不是其类或结构的特定实例的变量名称）来限定共享元素。</span><span class="sxs-lookup"><span data-stu-id="ef071-118">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="ef071-119">甚至不必创建类或结构的实例即可访问其共享成员。</span><span class="sxs-lookup"><span data-stu-id="ef071-119">You do not even have to create an instance of a class or structure to access its shared members.</span></span>

     <span data-ttu-id="ef071-120">下面的示例调用结构公开的共享过程 <xref:System.Double.IsNaN%2A> <xref:System.Double> 。</span><span class="sxs-lookup"><span data-stu-id="ef071-120">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>

     ```vb
     If Double.IsNaN(result) Then Console.WriteLine("Result is mathematically undefined.")
     ```

- <span data-ttu-id="ef071-121">**隐式共享。**</span><span class="sxs-lookup"><span data-stu-id="ef071-121">**Implicit Sharing.**</span></span> <span data-ttu-id="ef071-122">不能 `Shared` 在[Const 语句](../../../visual-basic/language-reference/statements/const-statement.md)中使用修饰符，而是隐式共享常量。</span><span class="sxs-lookup"><span data-stu-id="ef071-122">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="ef071-123">同样，不能将模块或接口的成员声明为 `Shared` ，但它们是隐式共享的。</span><span class="sxs-lookup"><span data-stu-id="ef071-123">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>

## <a name="behavior"></a><span data-ttu-id="ef071-124">行为</span><span class="sxs-lookup"><span data-stu-id="ef071-124">Behavior</span></span>

- <span data-ttu-id="ef071-125">**储存.**</span><span class="sxs-lookup"><span data-stu-id="ef071-125">**Storage.**</span></span> <span data-ttu-id="ef071-126">共享的变量或事件只存储在内存中，无论您创建的是多少或几个实例的类或结构。</span><span class="sxs-lookup"><span data-stu-id="ef071-126">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="ef071-127">同样，共享过程或属性仅保存一组局部变量。</span><span class="sxs-lookup"><span data-stu-id="ef071-127">Similarly, a shared procedure or property holds only one set of local variables.</span></span>

- <span data-ttu-id="ef071-128">**通过实例变量访问。**</span><span class="sxs-lookup"><span data-stu-id="ef071-128">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="ef071-129">可以通过使用包含其类或结构的特定实例的变量的名称来限定共享元素，从而访问该共享元素。</span><span class="sxs-lookup"><span data-stu-id="ef071-129">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="ef071-130">虽然这通常按预期方式工作，但编译器会生成一条警告消息，并通过类或结构名称而不是变量来进行访问。</span><span class="sxs-lookup"><span data-stu-id="ef071-130">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>

- <span data-ttu-id="ef071-131">**通过实例表达式访问。**</span><span class="sxs-lookup"><span data-stu-id="ef071-131">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="ef071-132">如果通过返回类或结构的实例的表达式访问共享元素，编译器将通过类或结构名称进行访问，而不是计算表达式。</span><span class="sxs-lookup"><span data-stu-id="ef071-132">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="ef071-133">如果你希望表达式执行其他操作以及返回实例，则会产生意外的结果。</span><span class="sxs-lookup"><span data-stu-id="ef071-133">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="ef071-134">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="ef071-134">The following example illustrates this.</span></span>
  
    ```vb
    Sub Main()
        ' The following line is the preferred way to access Total.
        ShareTotal.Total = 10

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of through
        ' the variable instanceVar. This works as expected and adds
        ' 100 to Total.
        Dim instanceVar As New ShareTotal
        instanceVar.Total += 100

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of calling
        ' ReturnClass(). This adds 1000 to total but does not work as
        ' expected, because the WriteLine in ReturnClass() does not run.
        Console.WriteLine("Value of total is " & CStr(ShareTotal.Total))
        ReturnClass().Total += 1000
    End Sub

    Public Function ReturnClass() As ShareTotal
        Console.WriteLine("Function ReturnClass() called")
        Return New ShareTotal
    End Function

    Public Class ShareTotal
        Public Shared Property Total As Integer
    End Class
    ```

     <span data-ttu-id="ef071-135">在前面的示例中，编译器会在代码通过实例访问共享属性时生成警告消息 `Total` 。</span><span class="sxs-lookup"><span data-stu-id="ef071-135">In the preceding example, the compiler generates a warning message both times the code accesses the shared property `Total` through an instance.</span></span> <span data-ttu-id="ef071-136">在每种情况下，它会直接通过类进行访问 `ShareTotal` ，而不会使用任何实例。</span><span class="sxs-lookup"><span data-stu-id="ef071-136">In each case it makes the access directly through the class `ShareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="ef071-137">对于对过程的预期调用 `ReturnClass` ，这意味着它甚至不会生成对的调用 `ReturnClass` ，因此，不会执行显示 "Function ReturnClass （）" 的其他操作。</span><span class="sxs-lookup"><span data-stu-id="ef071-137">In the case of the intended call to the procedure `ReturnClass`, this means it does not even generate a call to `ReturnClass`, so the additional action of displaying "Function ReturnClass() called" is not performed.</span></span>

<span data-ttu-id="ef071-138">`Shared` 修饰符可用于下面的上下文中：</span><span class="sxs-lookup"><span data-stu-id="ef071-138">The `Shared` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="ef071-139">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="ef071-139">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="ef071-140">Event 语句</span><span class="sxs-lookup"><span data-stu-id="ef071-140">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="ef071-141">Function 语句</span><span class="sxs-lookup"><span data-stu-id="ef071-141">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="ef071-142">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="ef071-142">Operator Statement</span></span>](../operator-statement.md)
- [<span data-ttu-id="ef071-143">Property Statement</span><span class="sxs-lookup"><span data-stu-id="ef071-143">Property Statement</span></span>](../property-statement.md)
- [<span data-ttu-id="ef071-144">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="ef071-144">Sub Statement</span></span>](../sub-statement.md)
  
## <a name="see-also"></a><span data-ttu-id="ef071-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef071-145">See also</span></span>

- [<span data-ttu-id="ef071-146">Shadows</span><span class="sxs-lookup"><span data-stu-id="ef071-146">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="ef071-147">静态</span><span class="sxs-lookup"><span data-stu-id="ef071-147">Static</span></span>](static.md)
- [<span data-ttu-id="ef071-148">Visual Basic 中的生存期</span><span class="sxs-lookup"><span data-stu-id="ef071-148">Lifetime in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="ef071-149">过程</span><span class="sxs-lookup"><span data-stu-id="ef071-149">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="ef071-150">结构</span><span class="sxs-lookup"><span data-stu-id="ef071-150">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="ef071-151">对象和类</span><span class="sxs-lookup"><span data-stu-id="ef071-151">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
