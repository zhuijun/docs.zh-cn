---
title: 如何：强制通过值传递参数
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 0be49e7d4aacbb30956bda7f6ee8494a7ded8b78
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071620"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="6fcef-102">如何：强制通过值传递参数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fcef-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>

<span data-ttu-id="6fcef-103">过程声明确定传递机制。</span><span class="sxs-lookup"><span data-stu-id="6fcef-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="6fcef-104">如果参数声明为 [ByRef](../../../language-reference/modifiers/byref.md)，则 Visual Basic 要求按引用传递相应的参数。</span><span class="sxs-lookup"><span data-stu-id="6fcef-104">If a parameter is declared [ByRef](../../../language-reference/modifiers/byref.md), Visual Basic expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="6fcef-105">这使过程可以更改调用代码中参数的基础编程元素的值。</span><span class="sxs-lookup"><span data-stu-id="6fcef-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="6fcef-106">如果要针对此类更改保护基础元素，则可以 `ByRef` 通过将参数名称括在括号中来覆盖过程调用中的传递机制。</span><span class="sxs-lookup"><span data-stu-id="6fcef-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="6fcef-107">除了在调用中包含参数列表的括号外，还需要用到这些括号。</span><span class="sxs-lookup"><span data-stu-id="6fcef-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="6fcef-108">调用代码无法重写 [ByVal](../../../language-reference/modifiers/byval.md) 机制。</span><span class="sxs-lookup"><span data-stu-id="6fcef-108">The calling code cannot override a [ByVal](../../../language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="6fcef-109">强制按值传递参数</span><span class="sxs-lookup"><span data-stu-id="6fcef-109">To force an argument to be passed by value</span></span>  
  
- <span data-ttu-id="6fcef-110">如果在过程中声明了相应的参数 `ByVal` ，则无需执行任何其他步骤。</span><span class="sxs-lookup"><span data-stu-id="6fcef-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> <span data-ttu-id="6fcef-111">Visual Basic 已经要求按值传递参数。</span><span class="sxs-lookup"><span data-stu-id="6fcef-111">Visual Basic already expects to pass the argument by value.</span></span>  
  
- <span data-ttu-id="6fcef-112">如果在过程中声明了相应的参数 `ByRef` ，请在过程调用中将参数括在括号中。</span><span class="sxs-lookup"><span data-stu-id="6fcef-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fcef-113">示例</span><span class="sxs-lookup"><span data-stu-id="6fcef-113">Example</span></span>  

 <span data-ttu-id="6fcef-114">下面的示例重写 `ByRef` 参数声明。</span><span class="sxs-lookup"><span data-stu-id="6fcef-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="6fcef-115">在强制的调用中 `ByVal` ，请注意两个级别的括号。</span><span class="sxs-lookup"><span data-stu-id="6fcef-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 <span data-ttu-id="6fcef-116">如果 `str` 将括在参数列表内的额外括号中，则该 `setNewString` 过程将无法在调用代码中更改其值，并 `MsgBox` 显示 "如果传递了 ByVal，则无法替换"。</span><span class="sxs-lookup"><span data-stu-id="6fcef-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="6fcef-117">当不 `str` 用多余的括号括起来时，该过程可以更改它并 `MsgBox` 显示 "这是 inString 参数的新值"。</span><span class="sxs-lookup"><span data-stu-id="6fcef-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="6fcef-118">编译代码</span><span class="sxs-lookup"><span data-stu-id="6fcef-118">Compile the code</span></span>  

 <span data-ttu-id="6fcef-119">通过引用传递变量时，必须使用 `ByRef` 关键字来指定此机制。</span><span class="sxs-lookup"><span data-stu-id="6fcef-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="6fcef-120">Visual Basic 中的默认值是按值传递参数。</span><span class="sxs-lookup"><span data-stu-id="6fcef-120">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="6fcef-121">但是，将 [ByVal](../../../language-reference/modifiers/byval.md) 或 [ByRef](../../../language-reference/modifiers/byref.md) 关键字用于每个声明的参数是一种好的编程做法。</span><span class="sxs-lookup"><span data-stu-id="6fcef-121">However, it is good programming practice to include either the [ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="6fcef-122">这使代码更易于阅读。</span><span class="sxs-lookup"><span data-stu-id="6fcef-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6fcef-123">可靠编程</span><span class="sxs-lookup"><span data-stu-id="6fcef-123">Robust Programming</span></span>  

 <span data-ttu-id="6fcef-124">如果过程声明了参数 [ByRef](../../../language-reference/modifiers/byref.md)，代码的正确执行可能取决于是否能够更改调用代码中的基础元素。</span><span class="sxs-lookup"><span data-stu-id="6fcef-124">If a procedure declares a parameter [ByRef](../../../language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="6fcef-125">如果调用代码通过将参数括在括号中来重写此调用机制，或者如果传递了不可修改参数，则该过程不能更改基础元素。</span><span class="sxs-lookup"><span data-stu-id="6fcef-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="6fcef-126">这可能会在调用代码中产生意外结果。</span><span class="sxs-lookup"><span data-stu-id="6fcef-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6fcef-127">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="6fcef-127">.NET Framework Security</span></span>  

 <span data-ttu-id="6fcef-128">允许过程更改调用代码中参数的基础值始终存在潜在风险。</span><span class="sxs-lookup"><span data-stu-id="6fcef-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="6fcef-129">请确保此值已更改，并在使用之前对其进行检查以确保其有效性。</span><span class="sxs-lookup"><span data-stu-id="6fcef-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fcef-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="6fcef-130">See also</span></span>

- [<span data-ttu-id="6fcef-131">过程</span><span class="sxs-lookup"><span data-stu-id="6fcef-131">Procedures</span></span>](./index.md)
- [<span data-ttu-id="6fcef-132">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="6fcef-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="6fcef-133">如何：将参数传递给过程</span><span class="sxs-lookup"><span data-stu-id="6fcef-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="6fcef-134">按值和按引用传递参数</span><span class="sxs-lookup"><span data-stu-id="6fcef-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="6fcef-135">可修改和不可修改参数之间的差异</span><span class="sxs-lookup"><span data-stu-id="6fcef-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="6fcef-136">通过值传递参数和通过引用传递参数之间的差异</span><span class="sxs-lookup"><span data-stu-id="6fcef-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="6fcef-137">如何：更改过程参数的值</span><span class="sxs-lookup"><span data-stu-id="6fcef-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="6fcef-138">如何：防止过程参数的值被更改</span><span class="sxs-lookup"><span data-stu-id="6fcef-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="6fcef-139">按位置和按名称传递自变量</span><span class="sxs-lookup"><span data-stu-id="6fcef-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="6fcef-140">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="6fcef-140">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
