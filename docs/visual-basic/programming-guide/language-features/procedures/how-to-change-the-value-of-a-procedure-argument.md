---
title: 如何：更改过程参数的值
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: 46cf9062d01e248b6e90882a923a48210780f7f4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388499"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="bdb41-102">如何：更改过程参数的值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdb41-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="bdb41-103">调用过程时，提供的每个参数都对应于在过程中定义的参数之一。</span><span class="sxs-lookup"><span data-stu-id="bdb41-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="bdb41-104">在某些情况下，过程代码可以更改调用代码中的参数的基础值。</span><span class="sxs-lookup"><span data-stu-id="bdb41-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="bdb41-105">在其他情况下，该过程只能更改其参数的本地副本。</span><span class="sxs-lookup"><span data-stu-id="bdb41-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="bdb41-106">调用过程时，Visual Basic 将为每个传递了[ByVal](../../../language-reference/modifiers/byval.md)的参数创建一个本地副本。</span><span class="sxs-lookup"><span data-stu-id="bdb41-106">When you call the procedure, Visual Basic makes a local copy of every argument that is passed [ByVal](../../../language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="bdb41-107">对于传递了[ByRef](../../../language-reference/modifiers/byref.md)的每个参数，Visual Basic 为过程代码提供对调用代码中参数的基础编程元素的直接引用。</span><span class="sxs-lookup"><span data-stu-id="bdb41-107">For each argument passed [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="bdb41-108">如果调用代码中的基础元素是可修改的元素并且传递了参数 `ByRef` ，则过程代码可以使用直接引用更改调用代码中的元素的值。</span><span class="sxs-lookup"><span data-stu-id="bdb41-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="bdb41-109">更改基础值</span><span class="sxs-lookup"><span data-stu-id="bdb41-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="bdb41-110">更改调用代码中过程参数的基础值</span><span class="sxs-lookup"><span data-stu-id="bdb41-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1. <span data-ttu-id="bdb41-111">在过程声明中，为对应于参数的参数指定[ByRef](../../../language-reference/modifiers/byref.md) 。</span><span class="sxs-lookup"><span data-stu-id="bdb41-111">In the procedure declaration, specify [ByRef](../../../language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2. <span data-ttu-id="bdb41-112">在调用代码中，将可修改的编程元素作为参数传递。</span><span class="sxs-lookup"><span data-stu-id="bdb41-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3. <span data-ttu-id="bdb41-113">在调用代码中，不要将参数括在参数列表的括号中。</span><span class="sxs-lookup"><span data-stu-id="bdb41-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4. <span data-ttu-id="bdb41-114">在过程代码中，使用参数名称将值分配给调用代码中的基础元素。</span><span class="sxs-lookup"><span data-stu-id="bdb41-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="bdb41-115">有关演示，请参阅进一步的示例。</span><span class="sxs-lookup"><span data-stu-id="bdb41-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="bdb41-116">更改本地副本</span><span class="sxs-lookup"><span data-stu-id="bdb41-116">Changing Local Copies</span></span>  
 <span data-ttu-id="bdb41-117">如果调用代码中的基础元素是不可更改的元素，或者如果传递了参数 `ByVal` ，则该过程将无法更改调用代码中的值。</span><span class="sxs-lookup"><span data-stu-id="bdb41-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="bdb41-118">但是，该过程可以更改此类参数的本地副本。</span><span class="sxs-lookup"><span data-stu-id="bdb41-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="bdb41-119">更改过程代码中过程参数的副本</span><span class="sxs-lookup"><span data-stu-id="bdb41-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1. <span data-ttu-id="bdb41-120">在过程声明中，为对应于参数的参数指定[ByVal](../../../language-reference/modifiers/byval.md) 。</span><span class="sxs-lookup"><span data-stu-id="bdb41-120">In the procedure declaration, specify [ByVal](../../../language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="bdb41-121">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="bdb41-121">-or-</span></span>  
  
     <span data-ttu-id="bdb41-122">在调用代码中，将参数括在参数列表的括号中。</span><span class="sxs-lookup"><span data-stu-id="bdb41-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="bdb41-123">这会强制 Visual Basic 按值传递参数，即使相应的参数指定 `ByRef` 。</span><span class="sxs-lookup"><span data-stu-id="bdb41-123">This forces Visual Basic to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2. <span data-ttu-id="bdb41-124">在过程代码中，使用参数名称将值分配给参数的本地副本。</span><span class="sxs-lookup"><span data-stu-id="bdb41-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="bdb41-125">不会更改调用代码中的基础值。</span><span class="sxs-lookup"><span data-stu-id="bdb41-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdb41-126">示例</span><span class="sxs-lookup"><span data-stu-id="bdb41-126">Example</span></span>  
 <span data-ttu-id="bdb41-127">下面的示例演示了两个过程，这些过程使用数组变量并对其元素进行操作。</span><span class="sxs-lookup"><span data-stu-id="bdb41-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="bdb41-128">此 `increase` 过程只是向每个元素添加一个元素。</span><span class="sxs-lookup"><span data-stu-id="bdb41-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="bdb41-129">此 `replace` 过程将新数组分配给参数 `a()` ，然后将一个数组添加到每个元素。</span><span class="sxs-lookup"><span data-stu-id="bdb41-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 <span data-ttu-id="bdb41-130">第一次 `MsgBox` 调用显示 "在增加后（n）：11，21，31，41"。</span><span class="sxs-lookup"><span data-stu-id="bdb41-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="bdb41-131">由于数组 `n` 是引用类型，因此 `replace` 即使传递机制为，也可以更改其成员 `ByVal` 。</span><span class="sxs-lookup"><span data-stu-id="bdb41-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="bdb41-132">第二次 `MsgBox` 调用显示 "replace （n）：101，201，301" 之后的。</span><span class="sxs-lookup"><span data-stu-id="bdb41-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="bdb41-133">由于 `n` 是通过传递的 `ByRef` ，因此 `replace` 可以修改 `n` 调用代码中的变量并为其分配新数组。</span><span class="sxs-lookup"><span data-stu-id="bdb41-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="bdb41-134">由于 `n` 是引用类型，因此 `replace` 也可以更改其成员。</span><span class="sxs-lookup"><span data-stu-id="bdb41-134">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="bdb41-135">您可以防止过程在调用代码中修改变量本身。</span><span class="sxs-lookup"><span data-stu-id="bdb41-135">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="bdb41-136">请参阅[如何：针对值更改保护过程参数](./how-to-protect-a-procedure-argument-against-value-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="bdb41-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="bdb41-137">编译代码</span><span class="sxs-lookup"><span data-stu-id="bdb41-137">Compile the code</span></span>  
 <span data-ttu-id="bdb41-138">通过引用传递变量时，必须使用 `ByRef` 关键字来指定此机制。</span><span class="sxs-lookup"><span data-stu-id="bdb41-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="bdb41-139">Visual Basic 中的默认值是按值传递参数。</span><span class="sxs-lookup"><span data-stu-id="bdb41-139">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="bdb41-140">但是，将[ByVal](../../../language-reference/modifiers/byval.md)或[ByRef](../../../language-reference/modifiers/byref.md)关键字用于每个声明的参数是一种好的编程做法。</span><span class="sxs-lookup"><span data-stu-id="bdb41-140">However, it is good programming practice to include either the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="bdb41-141">这使代码更易于阅读。</span><span class="sxs-lookup"><span data-stu-id="bdb41-141">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="bdb41-142">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="bdb41-142">.NET Framework Security</span></span>  
 <span data-ttu-id="bdb41-143">允许过程更改调用代码中参数的基础值始终存在潜在风险。</span><span class="sxs-lookup"><span data-stu-id="bdb41-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="bdb41-144">请确保此值已更改，并在使用之前对其进行检查以确保其有效性。</span><span class="sxs-lookup"><span data-stu-id="bdb41-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb41-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bdb41-145">See also</span></span>

- [<span data-ttu-id="bdb41-146">过程</span><span class="sxs-lookup"><span data-stu-id="bdb41-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="bdb41-147">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="bdb41-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="bdb41-148">如何：将参数传递给过程</span><span class="sxs-lookup"><span data-stu-id="bdb41-148">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="bdb41-149">按值和按引用传递参数</span><span class="sxs-lookup"><span data-stu-id="bdb41-149">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="bdb41-150">可修改和不可修改参数之间的差异</span><span class="sxs-lookup"><span data-stu-id="bdb41-150">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="bdb41-151">通过值传递参数和通过引用传递参数之间的差异</span><span class="sxs-lookup"><span data-stu-id="bdb41-151">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="bdb41-152">如何：防止过程参数的值被更改</span><span class="sxs-lookup"><span data-stu-id="bdb41-152">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="bdb41-153">如何：强制通过值传递参数</span><span class="sxs-lookup"><span data-stu-id="bdb41-153">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="bdb41-154">按位置和按名称传递参数</span><span class="sxs-lookup"><span data-stu-id="bdb41-154">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="bdb41-155">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="bdb41-155">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
