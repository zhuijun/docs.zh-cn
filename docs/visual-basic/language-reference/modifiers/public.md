---
title: 公用
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: f2b6a126435b111ef56ee2a9870ea6fbddf87901
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867683"
---
# <a name="public-visual-basic"></a><span data-ttu-id="685d8-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="685d8-102">Public (Visual Basic)</span></span>

<span data-ttu-id="685d8-103">指定一个或多个已声明的编程元素不具有访问限制。</span><span class="sxs-lookup"><span data-stu-id="685d8-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="685d8-104">备注</span><span class="sxs-lookup"><span data-stu-id="685d8-104">Remarks</span></span>  

 <span data-ttu-id="685d8-105">如果要发布一个组件或一组组件（如类库），通常会希望与程序集互操作的任何代码都可以访问编程元素。</span><span class="sxs-lookup"><span data-stu-id="685d8-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="685d8-106">若要在某个元素上协商这种无限制的访问权限，可以使用对其进行声明 `Public` 。</span><span class="sxs-lookup"><span data-stu-id="685d8-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="685d8-107">当不需要限制对编程元素的访问权限时，公共访问是该元素的正常级别。</span><span class="sxs-lookup"><span data-stu-id="685d8-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="685d8-108">请注意，在接口、模块、类或结构中声明的元素的访问级别默认为（ `Public` 如果你未声明）。</span><span class="sxs-lookup"><span data-stu-id="685d8-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="685d8-109">规则</span><span class="sxs-lookup"><span data-stu-id="685d8-109">Rules</span></span>  
  
- <span data-ttu-id="685d8-110">**声明上下文。**</span><span class="sxs-lookup"><span data-stu-id="685d8-110">**Declaration Context.**</span></span> <span data-ttu-id="685d8-111">`Public`只能在模块、接口或命名空间级别使用。</span><span class="sxs-lookup"><span data-stu-id="685d8-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="685d8-112">这意味着元素的声明上下文 `Public` 必须是源文件、命名空间、接口、模块、类或结构，不能是过程。</span><span class="sxs-lookup"><span data-stu-id="685d8-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="685d8-113">行为</span><span class="sxs-lookup"><span data-stu-id="685d8-113">Behavior</span></span>  
  
- <span data-ttu-id="685d8-114">**访问级别。**</span><span class="sxs-lookup"><span data-stu-id="685d8-114">**Access Level.**</span></span> <span data-ttu-id="685d8-115">可以访问模块、类或结构的所有代码都可以访问其 `Public` 元素。</span><span class="sxs-lookup"><span data-stu-id="685d8-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
- <span data-ttu-id="685d8-116">**默认访问权限。**</span><span class="sxs-lookup"><span data-stu-id="685d8-116">**Default Access.**</span></span> <span data-ttu-id="685d8-117">过程中的局部变量默认为公共访问，您不能对其使用任何访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="685d8-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
- <span data-ttu-id="685d8-118">**访问修饰符。**</span><span class="sxs-lookup"><span data-stu-id="685d8-118">**Access Modifiers.**</span></span> <span data-ttu-id="685d8-119">指定访问级别的关键字称为 *访问修饰符*。</span><span class="sxs-lookup"><span data-stu-id="685d8-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="685d8-120">有关访问修饰符的比较，请参阅 [Visual Basic 中的访问级别](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="685d8-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="685d8-121">`Public` 修饰符可用于下面的上下文中：</span><span class="sxs-lookup"><span data-stu-id="685d8-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="685d8-122">Class 语句</span><span class="sxs-lookup"><span data-stu-id="685d8-122">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="685d8-123">Const 语句</span><span class="sxs-lookup"><span data-stu-id="685d8-123">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="685d8-124">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="685d8-124">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="685d8-125">Delegate 语句</span><span class="sxs-lookup"><span data-stu-id="685d8-125">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="685d8-126">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="685d8-126">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="685d8-127">Enum 语句</span><span class="sxs-lookup"><span data-stu-id="685d8-127">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="685d8-128">Event 语句</span><span class="sxs-lookup"><span data-stu-id="685d8-128">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="685d8-129">Function 语句</span><span class="sxs-lookup"><span data-stu-id="685d8-129">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="685d8-130">Interface 语句</span><span class="sxs-lookup"><span data-stu-id="685d8-130">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="685d8-131">Module 语句</span><span class="sxs-lookup"><span data-stu-id="685d8-131">Module Statement</span></span>](../statements/module-statement.md)  
  
 [<span data-ttu-id="685d8-132">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="685d8-132">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 [<span data-ttu-id="685d8-133">Property Statement</span><span class="sxs-lookup"><span data-stu-id="685d8-133">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="685d8-134">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="685d8-134">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="685d8-135">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="685d8-135">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="685d8-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="685d8-136">See also</span></span>

- [<span data-ttu-id="685d8-137">避免</span><span class="sxs-lookup"><span data-stu-id="685d8-137">Protected</span></span>](protected.md)
- [<span data-ttu-id="685d8-138">Friend</span><span class="sxs-lookup"><span data-stu-id="685d8-138">Friend</span></span>](friend.md)
- [<span data-ttu-id="685d8-139">专用</span><span class="sxs-lookup"><span data-stu-id="685d8-139">Private</span></span>](private.md)
- [<span data-ttu-id="685d8-140">私有受保护</span><span class="sxs-lookup"><span data-stu-id="685d8-140">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="685d8-141">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="685d8-141">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="685d8-142">Visual Basic 中的访问级别</span><span class="sxs-lookup"><span data-stu-id="685d8-142">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="685d8-143">过程</span><span class="sxs-lookup"><span data-stu-id="685d8-143">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="685d8-144">结构</span><span class="sxs-lookup"><span data-stu-id="685d8-144">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="685d8-145">对象和类</span><span class="sxs-lookup"><span data-stu-id="685d8-145">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
