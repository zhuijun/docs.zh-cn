---
title: Shadows
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: 7aed6bec21bd484cca019b061bd5915de13a9eb8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402702"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="19b4f-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19b4f-102">Shadows (Visual Basic)</span></span>

<span data-ttu-id="19b4f-103">指定已声明的编程元素重新声明并隐藏基类中具有相同名称的元素或重载元素集。</span><span class="sxs-lookup"><span data-stu-id="19b4f-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>

## <a name="remarks"></a><span data-ttu-id="19b4f-104">备注</span><span class="sxs-lookup"><span data-stu-id="19b4f-104">Remarks</span></span>

<span data-ttu-id="19b4f-105">隐藏（也称为*按名称隐藏*）的主要目的是保留类成员的定义。</span><span class="sxs-lookup"><span data-stu-id="19b4f-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="19b4f-106">基类可能会发生更改，该更改将创建一个与已定义的元素同名的元素。</span><span class="sxs-lookup"><span data-stu-id="19b4f-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="19b4f-107">如果发生这种情况， `Shadows` 修饰符会强制通过类的引用解析为你定义的成员而不是新的基类元素。</span><span class="sxs-lookup"><span data-stu-id="19b4f-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>

<span data-ttu-id="19b4f-108">隐藏和重写操作都可重新定义继承的元素，但这两种方法之间又具有很大的差异。</span><span class="sxs-lookup"><span data-stu-id="19b4f-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="19b4f-109">有关详细信息，请参阅[Visual Basic 中的隐藏](../../programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="19b4f-109">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>

## <a name="rules"></a><span data-ttu-id="19b4f-110">规则</span><span class="sxs-lookup"><span data-stu-id="19b4f-110">Rules</span></span>

- <span data-ttu-id="19b4f-111">**声明上下文。**</span><span class="sxs-lookup"><span data-stu-id="19b4f-111">**Declaration Context.**</span></span> <span data-ttu-id="19b4f-112">只能 `Shadows` 在类级别使用。</span><span class="sxs-lookup"><span data-stu-id="19b4f-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="19b4f-113">这意味着元素的声明上下文 `Shadows` 必须是类，且不能是源文件、命名空间、接口、模块、结构或过程。</span><span class="sxs-lookup"><span data-stu-id="19b4f-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

  <span data-ttu-id="19b4f-114">只能在单个声明语句中声明一个隐藏元素。</span><span class="sxs-lookup"><span data-stu-id="19b4f-114">You can declare only one shadowing element in a single declaration statement.</span></span>

- <span data-ttu-id="19b4f-115">**组合修饰符。**</span><span class="sxs-lookup"><span data-stu-id="19b4f-115">**Combined Modifiers.**</span></span> <span data-ttu-id="19b4f-116">不能 `Shadows` `Overloads` `Overrides` `Static` 在同一声明中同时指定、或。</span><span class="sxs-lookup"><span data-stu-id="19b4f-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>

- <span data-ttu-id="19b4f-117">**元素类型。**</span><span class="sxs-lookup"><span data-stu-id="19b4f-117">**Element Types.**</span></span> <span data-ttu-id="19b4f-118">可以与任何其他类型一起隐藏任何类型的已声明元素。</span><span class="sxs-lookup"><span data-stu-id="19b4f-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="19b4f-119">如果使用另一个属性或过程来隐藏属性或过程，则参数和返回类型不必与基类属性或过程中的相同。</span><span class="sxs-lookup"><span data-stu-id="19b4f-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>

- <span data-ttu-id="19b4f-120">**访问.**</span><span class="sxs-lookup"><span data-stu-id="19b4f-120">**Accessing.**</span></span> <span data-ttu-id="19b4f-121">通常，基类中隐藏的元素在隐藏它的派生类中不可用。</span><span class="sxs-lookup"><span data-stu-id="19b4f-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="19b4f-122">不过，请注意以下事项。</span><span class="sxs-lookup"><span data-stu-id="19b4f-122">However, the following considerations apply.</span></span>

  - <span data-ttu-id="19b4f-123">如果不能从引用它的代码访问隐藏元素，则会将引用解析为隐藏的元素。</span><span class="sxs-lookup"><span data-stu-id="19b4f-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="19b4f-124">例如，如果某个 `Private` 元素隐藏了一个基类元素，则没有访问该元素的权限的代码将 `Private` 改为访问该基类元素。</span><span class="sxs-lookup"><span data-stu-id="19b4f-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>

  - <span data-ttu-id="19b4f-125">如果隐藏元素，仍然可以通过使用基类的类型声明的对象访问隐藏的元素。</span><span class="sxs-lookup"><span data-stu-id="19b4f-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="19b4f-126">你还可以通过来访问它 `MyBase` 。</span><span class="sxs-lookup"><span data-stu-id="19b4f-126">You can also access it through `MyBase`.</span></span>

<span data-ttu-id="19b4f-127">`Shadows` 修饰符可用于下面的上下文中：</span><span class="sxs-lookup"><span data-stu-id="19b4f-127">The `Shadows` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="19b4f-128">Class 语句</span><span class="sxs-lookup"><span data-stu-id="19b4f-128">Class Statement</span></span>](../statements/class-statement.md)

- [<span data-ttu-id="19b4f-129">Const 语句</span><span class="sxs-lookup"><span data-stu-id="19b4f-129">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="19b4f-130">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="19b4f-130">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="19b4f-131">Delegate 语句</span><span class="sxs-lookup"><span data-stu-id="19b4f-131">Delegate Statement</span></span>](../statements/delegate-statement.md)

- [<span data-ttu-id="19b4f-132">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="19b4f-132">Dim Statement</span></span>](../statements/dim-statement.md)

- [<span data-ttu-id="19b4f-133">Enum 语句</span><span class="sxs-lookup"><span data-stu-id="19b4f-133">Enum Statement</span></span>](../statements/enum-statement.md)

- [<span data-ttu-id="19b4f-134">Event 语句</span><span class="sxs-lookup"><span data-stu-id="19b4f-134">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="19b4f-135">Function 语句</span><span class="sxs-lookup"><span data-stu-id="19b4f-135">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="19b4f-136">Interface 语句</span><span class="sxs-lookup"><span data-stu-id="19b4f-136">Interface Statement</span></span>](../statements/interface-statement.md)

- [<span data-ttu-id="19b4f-137">Property Statement</span><span class="sxs-lookup"><span data-stu-id="19b4f-137">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="19b4f-138">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="19b4f-138">Structure Statement</span></span>](../statements/structure-statement.md)

- [<span data-ttu-id="19b4f-139">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="19b4f-139">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="19b4f-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="19b4f-140">See also</span></span>

- [<span data-ttu-id="19b4f-141">共享</span><span class="sxs-lookup"><span data-stu-id="19b4f-141">Shared</span></span>](shared.md)
- [<span data-ttu-id="19b4f-142">静态</span><span class="sxs-lookup"><span data-stu-id="19b4f-142">Static</span></span>](static.md)
- <span data-ttu-id="19b4f-143">专用 </span><span class="sxs-lookup"><span data-stu-id="19b4f-143">[Private](private.md)</span></span>
- [<span data-ttu-id="19b4f-144">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="19b4f-144">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="19b4f-145">继承基础知识</span><span class="sxs-lookup"><span data-stu-id="19b4f-145">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="19b4f-146">New</span><span class="sxs-lookup"><span data-stu-id="19b4f-146">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="19b4f-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="19b4f-147">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="19b4f-148">重载</span><span class="sxs-lookup"><span data-stu-id="19b4f-148">Overloads</span></span>](overloads.md)
- [<span data-ttu-id="19b4f-149">Overrides</span><span class="sxs-lookup"><span data-stu-id="19b4f-149">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="19b4f-150">替代</span><span class="sxs-lookup"><span data-stu-id="19b4f-150">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="19b4f-151">Visual Basic 中的隐藏</span><span class="sxs-lookup"><span data-stu-id="19b4f-151">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
