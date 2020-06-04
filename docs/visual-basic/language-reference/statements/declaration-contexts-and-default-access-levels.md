---
title: 声明上下文和默认访问级别
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: b5bb943a062ac648f88645fb6de1acb42213071c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404792"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a><span data-ttu-id="aa8f4-102">声明上下文和默认访问级别 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa8f4-102">Declaration Contexts and Default Access Levels (Visual Basic)</span></span>
<span data-ttu-id="aa8f4-103">本主题介绍了哪些 Visual Basic 类型可以在哪些其他类型中进行声明，如果未指定，它们的访问级别将默认为。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-103">This topic describes which Visual Basic types can be declared within which other types, and what their access levels default to if not specified.</span></span>  
  
## <a name="declaration-context-levels"></a><span data-ttu-id="aa8f4-104">声明上下文级别</span><span class="sxs-lookup"><span data-stu-id="aa8f4-104">Declaration Context Levels</span></span>  
 <span data-ttu-id="aa8f4-105">编程元素的*声明上下文*是声明它的代码区域。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-105">The *declaration context* of a programming element is the region of code in which it is declared.</span></span> <span data-ttu-id="aa8f4-106">这通常是另一个编程元素，该元素称为 "*包含元素*"。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-106">This is often another programming element, which is then called the *containing element*.</span></span>  
  
 <span data-ttu-id="aa8f4-107">声明上下文的级别如下：</span><span class="sxs-lookup"><span data-stu-id="aa8f4-107">The levels for declaration contexts are the following:</span></span>  
  
- <span data-ttu-id="aa8f4-108">*命名空间级别*-在源文件或命名空间中，但不在类、结构、模块或接口中</span><span class="sxs-lookup"><span data-stu-id="aa8f4-108">*Namespace level* — within a source file or namespace but not within a class, structure, module, or interface</span></span>  
  
- <span data-ttu-id="aa8f4-109">*模块级别*-在类、结构、模块或接口中，但不在过程或块中</span><span class="sxs-lookup"><span data-stu-id="aa8f4-109">*Module level* — within a class, structure, module, or interface but not within a procedure or block</span></span>  
  
- <span data-ttu-id="aa8f4-110">*过程级别*-在过程或块（如 `If` 或）内 `For`</span><span class="sxs-lookup"><span data-stu-id="aa8f4-110">*Procedure level* — within a procedure or block (such as `If` or `For`)</span></span>  
  
 <span data-ttu-id="aa8f4-111">下表显示了各种已声明的编程元素的默认访问级别，具体取决于它们的声明上下文。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-111">The following table shows the default access levels for various declared programming elements, depending on their declaration contexts.</span></span>  
  
|<span data-ttu-id="aa8f4-112">已声明的元素</span><span class="sxs-lookup"><span data-stu-id="aa8f4-112">Declared element</span></span>|<span data-ttu-id="aa8f4-113">命名空间级别</span><span class="sxs-lookup"><span data-stu-id="aa8f4-113">Namespace level</span></span>|<span data-ttu-id="aa8f4-114">模块级别</span><span class="sxs-lookup"><span data-stu-id="aa8f4-114">Module level</span></span>|<span data-ttu-id="aa8f4-115">过程级别</span><span class="sxs-lookup"><span data-stu-id="aa8f4-115">Procedure level</span></span>|  
|----------------------|---------------------|------------------|---------------------|  
|<span data-ttu-id="aa8f4-116">Variable （[Dim 语句](dim-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-116">Variable ([Dim Statement](dim-statement.md))</span></span>|<span data-ttu-id="aa8f4-117">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-117">Not allowed</span></span>|<span data-ttu-id="aa8f4-118">`Private`（ `Public` 在中 `Structure` 不允许 `Interface` ）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-118">`Private` (`Public` in `Structure`, not allowed in `Interface`)</span></span>|`Public`|  
|<span data-ttu-id="aa8f4-119">常量（[Const 语句](const-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-119">Constant ([Const Statement](const-statement.md))</span></span>|<span data-ttu-id="aa8f4-120">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-120">Not allowed</span></span>|<span data-ttu-id="aa8f4-121">`Private`（ `Public` 在中 `Structure` 不允许 `Interface` ）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-121">`Private` (`Public` in `Structure`, not allowed in `Interface`)</span></span>|`Public`|  
|<span data-ttu-id="aa8f4-122">枚举（[Enum 语句](enum-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-122">Enumeration ([Enum Statement](enum-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="aa8f4-123">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-123">Not allowed</span></span>|  
|<span data-ttu-id="aa8f4-124">Class （[Class 语句](class-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-124">Class ([Class Statement](class-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="aa8f4-125">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-125">Not allowed</span></span>|  
|<span data-ttu-id="aa8f4-126">Structure （[结构语句](structure-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-126">Structure ([Structure Statement](structure-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="aa8f4-127">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-127">Not allowed</span></span>|  
|<span data-ttu-id="aa8f4-128">Module （[Module 语句](module-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-128">Module ([Module Statement](module-statement.md))</span></span>|`Friend`|<span data-ttu-id="aa8f4-129">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-129">Not allowed</span></span>|<span data-ttu-id="aa8f4-130">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-130">Not allowed</span></span>|  
|<span data-ttu-id="aa8f4-131">Interface （[Interface 语句](interface-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-131">Interface ([Interface Statement](interface-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="aa8f4-132">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-132">Not allowed</span></span>|  
|<span data-ttu-id="aa8f4-133">Procedure （[Function 语句](function-statement.md)， [Sub 语句](sub-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-133">Procedure ([Function Statement](function-statement.md), [Sub Statement](sub-statement.md))</span></span>|<span data-ttu-id="aa8f4-134">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-134">Not allowed</span></span>|`Public`|<span data-ttu-id="aa8f4-135">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-135">Not allowed</span></span>|  
|<span data-ttu-id="aa8f4-136">外部引用（[Declare 语句](declare-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-136">External reference ([Declare Statement](declare-statement.md))</span></span>|<span data-ttu-id="aa8f4-137">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-137">Not allowed</span></span>|<span data-ttu-id="aa8f4-138">`Public`（在中不允许 `Interface` ）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-138">`Public` (not allowed in `Interface`)</span></span>|<span data-ttu-id="aa8f4-139">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-139">Not allowed</span></span>|  
|<span data-ttu-id="aa8f4-140">运算符（[Operator 语句](operator-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-140">Operator ([Operator Statement](operator-statement.md))</span></span>|<span data-ttu-id="aa8f4-141">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-141">Not allowed</span></span>|<span data-ttu-id="aa8f4-142">`Public`（在或中不允许 `Interface` `Module` ）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-142">`Public` (not allowed in `Interface` or `Module`)</span></span>|<span data-ttu-id="aa8f4-143">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-143">Not allowed</span></span>|  
|<span data-ttu-id="aa8f4-144">属性（[Property 语句](property-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-144">Property ([Property Statement](property-statement.md))</span></span>|<span data-ttu-id="aa8f4-145">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-145">Not allowed</span></span>|`Public`|<span data-ttu-id="aa8f4-146">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-146">Not allowed</span></span>|  
|<span data-ttu-id="aa8f4-147">Default 属性（[默认值](../modifiers/default.md)）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-147">Default property ([Default](../modifiers/default.md))</span></span>|<span data-ttu-id="aa8f4-148">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-148">Not allowed</span></span>|<span data-ttu-id="aa8f4-149">`Public`（在中不允许 `Module` ）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-149">`Public` (not allowed in `Module`)</span></span>|<span data-ttu-id="aa8f4-150">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-150">Not allowed</span></span>|  
|<span data-ttu-id="aa8f4-151">事件（[事件语句](event-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-151">Event ([Event Statement](event-statement.md))</span></span>|<span data-ttu-id="aa8f4-152">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-152">Not allowed</span></span>|`Public`|<span data-ttu-id="aa8f4-153">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-153">Not allowed</span></span>|  
|<span data-ttu-id="aa8f4-154">委托（[委托语句](delegate-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="aa8f4-154">Delegate ([Delegate Statement](delegate-statement.md))</span></span>|`Friend`|`Public`|<span data-ttu-id="aa8f4-155">不允许</span><span class="sxs-lookup"><span data-stu-id="aa8f4-155">Not allowed</span></span>|  
  
 <span data-ttu-id="aa8f4-156">有关详细信息，请参阅[Visual Basic 中的访问级别](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-156">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa8f4-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aa8f4-157">See also</span></span>

- [<span data-ttu-id="aa8f4-158">友好</span><span class="sxs-lookup"><span data-stu-id="aa8f4-158">Friend</span></span>](../modifiers/friend.md)
- <span data-ttu-id="aa8f4-159">专用 </span><span class="sxs-lookup"><span data-stu-id="aa8f4-159">[Private](../modifiers/private.md)</span></span>
- [<span data-ttu-id="aa8f4-160">公共</span><span class="sxs-lookup"><span data-stu-id="aa8f4-160">Public</span></span>](../modifiers/public.md)
