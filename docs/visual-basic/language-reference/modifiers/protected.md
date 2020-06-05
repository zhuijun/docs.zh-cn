---
title: Protected
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: d66ed68004f8b6ef21ae703f02b317589814764b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398215"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="d9a41-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9a41-102">Protected (Visual Basic)</span></span>

<span data-ttu-id="d9a41-103">一个成员访问修饰符，它指定一个或多个已声明的编程元素只能从自己的类或派生类中访问。</span><span class="sxs-lookup"><span data-stu-id="d9a41-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>

## <a name="remarks"></a><span data-ttu-id="d9a41-104">备注</span><span class="sxs-lookup"><span data-stu-id="d9a41-104">Remarks</span></span>

<span data-ttu-id="d9a41-105">有时，在类中声明的编程元素包含敏感数据或受限制的代码，并希望限制对元素的访问。</span><span class="sxs-lookup"><span data-stu-id="d9a41-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="d9a41-106">但是，如果类可继承并且你需要派生类的层次结构，则这些派生类可能需要访问数据或代码。</span><span class="sxs-lookup"><span data-stu-id="d9a41-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="d9a41-107">在这种情况下，你希望可以从基类和所有派生类中访问元素。</span><span class="sxs-lookup"><span data-stu-id="d9a41-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="d9a41-108">若要以这种方式限制对元素的访问，可使用声明 `Protected` 。</span><span class="sxs-lookup"><span data-stu-id="d9a41-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>

> [!NOTE]
> <span data-ttu-id="d9a41-109">`Protected`访问修饰符可以与其他两个修饰符结合使用：</span><span class="sxs-lookup"><span data-stu-id="d9a41-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
>
> - <span data-ttu-id="d9a41-110">[受保护的 Friend](protected-friend.md)修饰符使类成员可从该类、派生类以及在其中定义该类的同一程序集中访问。</span><span class="sxs-lookup"><span data-stu-id="d9a41-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span>
> - <span data-ttu-id="d9a41-111">[私有受保护](private-protected.md)的修饰符使类成员可由派生类型访问，但仅包含在其包含的程序集中。</span><span class="sxs-lookup"><span data-stu-id="d9a41-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="d9a41-112">规则</span><span class="sxs-lookup"><span data-stu-id="d9a41-112">Rules</span></span>

<span data-ttu-id="d9a41-113">**声明上下文。**</span><span class="sxs-lookup"><span data-stu-id="d9a41-113">**Declaration Context.**</span></span> <span data-ttu-id="d9a41-114">`Protected`只能在类级别使用。</span><span class="sxs-lookup"><span data-stu-id="d9a41-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="d9a41-115">这意味着元素的声明上下文 `Protected` 必须是类，且不能是源文件、命名空间、接口、模块、结构或过程。</span><span class="sxs-lookup"><span data-stu-id="d9a41-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="d9a41-116">行为</span><span class="sxs-lookup"><span data-stu-id="d9a41-116">Behavior</span></span>

- <span data-ttu-id="d9a41-117">**访问级别。**</span><span class="sxs-lookup"><span data-stu-id="d9a41-117">**Access Level.**</span></span> <span data-ttu-id="d9a41-118">类中的所有代码都可以访问其元素。</span><span class="sxs-lookup"><span data-stu-id="d9a41-118">All code in a class can access its elements.</span></span> <span data-ttu-id="d9a41-119">从基类派生的任何类中的代码都可以访问基类的所有 `Protected` 元素。</span><span class="sxs-lookup"><span data-stu-id="d9a41-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="d9a41-120">这适用于派生的所有代。</span><span class="sxs-lookup"><span data-stu-id="d9a41-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="d9a41-121">这意味着，类可以访问 `Protected` 基类的基类的元素，依此类推。</span><span class="sxs-lookup"><span data-stu-id="d9a41-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>

     <span data-ttu-id="d9a41-122">受保护的访问不是友元访问的超集或子集。</span><span class="sxs-lookup"><span data-stu-id="d9a41-122">Protected access is not a superset or subset of friend access.</span></span>

- <span data-ttu-id="d9a41-123">**访问修饰符。**</span><span class="sxs-lookup"><span data-stu-id="d9a41-123">**Access Modifiers.**</span></span> <span data-ttu-id="d9a41-124">指定访问级别的关键字称为*访问修饰符*。</span><span class="sxs-lookup"><span data-stu-id="d9a41-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="d9a41-125">有关访问修饰符的比较，请参阅[Visual Basic 中的访问级别](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="d9a41-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="d9a41-126">`Protected` 修饰符可用于下面的上下文中：</span><span class="sxs-lookup"><span data-stu-id="d9a41-126">The `Protected` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="d9a41-127">Class 语句</span><span class="sxs-lookup"><span data-stu-id="d9a41-127">Class Statement</span></span>](../statements/class-statement.md)

- [<span data-ttu-id="d9a41-128">Const 语句</span><span class="sxs-lookup"><span data-stu-id="d9a41-128">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="d9a41-129">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="d9a41-129">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="d9a41-130">Delegate 语句</span><span class="sxs-lookup"><span data-stu-id="d9a41-130">Delegate Statement</span></span>](../statements/delegate-statement.md)

- [<span data-ttu-id="d9a41-131">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="d9a41-131">Dim Statement</span></span>](../statements/dim-statement.md)

- [<span data-ttu-id="d9a41-132">Enum 语句</span><span class="sxs-lookup"><span data-stu-id="d9a41-132">Enum Statement</span></span>](../statements/enum-statement.md)

- [<span data-ttu-id="d9a41-133">Event 语句</span><span class="sxs-lookup"><span data-stu-id="d9a41-133">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="d9a41-134">Function 语句</span><span class="sxs-lookup"><span data-stu-id="d9a41-134">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="d9a41-135">Interface 语句</span><span class="sxs-lookup"><span data-stu-id="d9a41-135">Interface Statement</span></span>](../statements/interface-statement.md)

- [<span data-ttu-id="d9a41-136">Property Statement</span><span class="sxs-lookup"><span data-stu-id="d9a41-136">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="d9a41-137">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="d9a41-137">Structure Statement</span></span>](../statements/structure-statement.md)

- [<span data-ttu-id="d9a41-138">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="d9a41-138">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="d9a41-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d9a41-139">See also</span></span>

- [<span data-ttu-id="d9a41-140">公共</span><span class="sxs-lookup"><span data-stu-id="d9a41-140">Public</span></span>](public.md)
- [<span data-ttu-id="d9a41-141">友好</span><span class="sxs-lookup"><span data-stu-id="d9a41-141">Friend</span></span>](friend.md)
- <span data-ttu-id="d9a41-142">专用 </span><span class="sxs-lookup"><span data-stu-id="d9a41-142">[Private](private.md)</span></span>
- [<span data-ttu-id="d9a41-143">私有受保护</span><span class="sxs-lookup"><span data-stu-id="d9a41-143">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="d9a41-144">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="d9a41-144">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="d9a41-145">Visual Basic 中的访问级别</span><span class="sxs-lookup"><span data-stu-id="d9a41-145">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="d9a41-146">过程</span><span class="sxs-lookup"><span data-stu-id="d9a41-146">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="d9a41-147">结构</span><span class="sxs-lookup"><span data-stu-id="d9a41-147">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="d9a41-148">对象和类</span><span class="sxs-lookup"><span data-stu-id="d9a41-148">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
