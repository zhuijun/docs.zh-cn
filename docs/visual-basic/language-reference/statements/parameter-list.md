---
title: 参数列表
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: 706fc2414806db5608cce410bf4156839ec2d83e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404312"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="fa53d-102">参数列表 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa53d-102">Parameter List (Visual Basic)</span></span>

<span data-ttu-id="fa53d-103">指定在调用过程时过程需要的参数。</span><span class="sxs-lookup"><span data-stu-id="fa53d-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="fa53d-104">多个参数之间用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="fa53d-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="fa53d-105">下面是一个参数的语法。</span><span class="sxs-lookup"><span data-stu-id="fa53d-105">The following is the syntax for one parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="fa53d-106">语法</span><span class="sxs-lookup"><span data-stu-id="fa53d-106">Syntax</span></span>

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a><span data-ttu-id="fa53d-107">组成部分</span><span class="sxs-lookup"><span data-stu-id="fa53d-107">Parts</span></span>

`attributelist`  
<span data-ttu-id="fa53d-108">可选。</span><span class="sxs-lookup"><span data-stu-id="fa53d-108">Optional.</span></span> <span data-ttu-id="fa53d-109">应用于此参数的特性列表。</span><span class="sxs-lookup"><span data-stu-id="fa53d-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="fa53d-110">必须将[特性列表](attribute-list.md)括在尖括号（" `<` " 和 " `>` "）中。</span><span class="sxs-lookup"><span data-stu-id="fa53d-110">You must enclose the [Attribute List](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

`Optional`  
<span data-ttu-id="fa53d-111">可选。</span><span class="sxs-lookup"><span data-stu-id="fa53d-111">Optional.</span></span> <span data-ttu-id="fa53d-112">指定在调用过程时不需要此参数。</span><span class="sxs-lookup"><span data-stu-id="fa53d-112">Specifies that this parameter is not required when the procedure is called.</span></span>

`ByVal`  
<span data-ttu-id="fa53d-113">可选。</span><span class="sxs-lookup"><span data-stu-id="fa53d-113">Optional.</span></span> <span data-ttu-id="fa53d-114">指定过程不能替换或重新分配调用代码中的相应参数的基础变量元素。</span><span class="sxs-lookup"><span data-stu-id="fa53d-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>

`ByRef`  
<span data-ttu-id="fa53d-115">可选。</span><span class="sxs-lookup"><span data-stu-id="fa53d-115">Optional.</span></span> <span data-ttu-id="fa53d-116">指定过程可以采用与调用代码本身相同的方式来修改调用代码中的基础变量元素。</span><span class="sxs-lookup"><span data-stu-id="fa53d-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>

`ParamArray`  
<span data-ttu-id="fa53d-117">可选。</span><span class="sxs-lookup"><span data-stu-id="fa53d-117">Optional.</span></span> <span data-ttu-id="fa53d-118">指定参数列表中的最后一个参数是指定数据类型的元素的可选数组。</span><span class="sxs-lookup"><span data-stu-id="fa53d-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="fa53d-119">这样，调用代码就可以将任意数量的参数传递给该过程。</span><span class="sxs-lookup"><span data-stu-id="fa53d-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>

`parametername`  
<span data-ttu-id="fa53d-120">必需。</span><span class="sxs-lookup"><span data-stu-id="fa53d-120">Required.</span></span> <span data-ttu-id="fa53d-121">表示参数的局部变量的名称。</span><span class="sxs-lookup"><span data-stu-id="fa53d-121">Name of the local variable representing the parameter.</span></span>

`parametertype`  
<span data-ttu-id="fa53d-122">如果 `Option Strict` 为，则为必需 `On` 。</span><span class="sxs-lookup"><span data-stu-id="fa53d-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="fa53d-123">表示参数的局部变量的数据类型。</span><span class="sxs-lookup"><span data-stu-id="fa53d-123">Data type of the local variable representing the parameter.</span></span>

`defaultvalue`  
<span data-ttu-id="fa53d-124">参数需要 `Optional` 。</span><span class="sxs-lookup"><span data-stu-id="fa53d-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="fa53d-125">计算结果为参数的数据类型的任何常量或常量表达式。</span><span class="sxs-lookup"><span data-stu-id="fa53d-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="fa53d-126">如果类型为 `Object` ，或类、接口、数组或结构，则默认值只能是 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="fa53d-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>

## <a name="remarks"></a><span data-ttu-id="fa53d-127">备注</span><span class="sxs-lookup"><span data-stu-id="fa53d-127">Remarks</span></span>

<span data-ttu-id="fa53d-128">参数括在括号内并用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="fa53d-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="fa53d-129">参数可以使用任何数据类型进行声明。</span><span class="sxs-lookup"><span data-stu-id="fa53d-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="fa53d-130">如果不指定 `parametertype` ，则默认为 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="fa53d-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>

<span data-ttu-id="fa53d-131">当调用代码调用过程时，它会将*参数*传递给每个必需的参数。</span><span class="sxs-lookup"><span data-stu-id="fa53d-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="fa53d-132">有关详细信息，请参阅[参数和参数之间的差异](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="fa53d-132">For more information, see [Differences Between Parameters and Arguments](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>

<span data-ttu-id="fa53d-133">调用代码传递给每个参数的参数是指向调用代码中的基础元素的指针。</span><span class="sxs-lookup"><span data-stu-id="fa53d-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="fa53d-134">如果此元素不是*变量*（常量、文本、枚举或表达式），则任何代码都不能对其进行更改。</span><span class="sxs-lookup"><span data-stu-id="fa53d-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="fa53d-135">如果它是*变量*元素（已声明的变量、字段、属性、数组元素或结构元素），则调用代码可以更改它。</span><span class="sxs-lookup"><span data-stu-id="fa53d-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="fa53d-136">有关详细信息，请参阅可[修改和不可修改参数之间的差异](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="fa53d-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>

<span data-ttu-id="fa53d-137">如果传递了 variable 元素 `ByRef` ，则该过程也可以更改它。</span><span class="sxs-lookup"><span data-stu-id="fa53d-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="fa53d-138">有关详细信息，请参阅[按值传递参数和通过引用传递参数之间的差异](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="fa53d-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>

## <a name="rules"></a><span data-ttu-id="fa53d-139">规则</span><span class="sxs-lookup"><span data-stu-id="fa53d-139">Rules</span></span>

- <span data-ttu-id="fa53d-140">**括号.**</span><span class="sxs-lookup"><span data-stu-id="fa53d-140">**Parentheses.**</span></span> <span data-ttu-id="fa53d-141">如果指定参数列表，则必须将其括在括号中。</span><span class="sxs-lookup"><span data-stu-id="fa53d-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="fa53d-142">如果没有参数，仍可使用括空列表的括号。</span><span class="sxs-lookup"><span data-stu-id="fa53d-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="fa53d-143">这可以通过阐明元素是一个过程来提高代码的可读性。</span><span class="sxs-lookup"><span data-stu-id="fa53d-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>

- <span data-ttu-id="fa53d-144">**可选参数。**</span><span class="sxs-lookup"><span data-stu-id="fa53d-144">**Optional Parameters.**</span></span> <span data-ttu-id="fa53d-145">如果对参数使用 `Optional` 修饰符，则列表中的所有后续参数也必须是可选的，并且可以使用修饰符进行声明 `Optional` 。</span><span class="sxs-lookup"><span data-stu-id="fa53d-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>

     <span data-ttu-id="fa53d-146">每个可选参数声明都必须提供 `defaultvalue` 子句。</span><span class="sxs-lookup"><span data-stu-id="fa53d-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>

     <span data-ttu-id="fa53d-147">有关详细信息，请参阅[可选参数](../../programming-guide/language-features/procedures/optional-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="fa53d-147">For more information, see [Optional Parameters](../../programming-guide/language-features/procedures/optional-parameters.md).</span></span>

- <span data-ttu-id="fa53d-148">**参数数组。**</span><span class="sxs-lookup"><span data-stu-id="fa53d-148">**Parameter Arrays.**</span></span> <span data-ttu-id="fa53d-149">必须 `ByVal` 为 `ParamArray` 参数指定。</span><span class="sxs-lookup"><span data-stu-id="fa53d-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>

     <span data-ttu-id="fa53d-150">`Optional` `ParamArray` 在同一参数列表中不能同时使用和。</span><span class="sxs-lookup"><span data-stu-id="fa53d-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>

     <span data-ttu-id="fa53d-151">有关详细信息，请参阅[参数数组](../../programming-guide/language-features/procedures/parameter-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="fa53d-151">For more information, see [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>

- <span data-ttu-id="fa53d-152">**传递机制。**</span><span class="sxs-lookup"><span data-stu-id="fa53d-152">**Passing Mechanism.**</span></span> <span data-ttu-id="fa53d-153">每个参数的默认机制为 `ByVal` ，这意味着过程无法更改基础变量元素。</span><span class="sxs-lookup"><span data-stu-id="fa53d-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="fa53d-154">但是，如果该元素是引用类型，则该过程可以修改基础对象的内容或成员，即使它无法替换或重新分配对象本身。</span><span class="sxs-lookup"><span data-stu-id="fa53d-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>

- <span data-ttu-id="fa53d-155">**参数名称。**</span><span class="sxs-lookup"><span data-stu-id="fa53d-155">**Parameter Names.**</span></span> <span data-ttu-id="fa53d-156">如果参数的数据类型为数组，请在后面 `parametername` 紧跟括号。</span><span class="sxs-lookup"><span data-stu-id="fa53d-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="fa53d-157">有关参数名称的详细信息，请参阅已[声明的元素名称](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="fa53d-157">For more information on parameter names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="example"></a><span data-ttu-id="fa53d-158">示例</span><span class="sxs-lookup"><span data-stu-id="fa53d-158">Example</span></span>

<span data-ttu-id="fa53d-159">下面的示例演示了一个 `Function` 用于定义两个参数的过程。</span><span class="sxs-lookup"><span data-stu-id="fa53d-159">The following example shows a `Function` procedure that defines two parameters.</span></span>

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="fa53d-160">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fa53d-160">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="fa53d-161">Function 语句</span><span class="sxs-lookup"><span data-stu-id="fa53d-161">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="fa53d-162">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="fa53d-162">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="fa53d-163">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="fa53d-163">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="fa53d-164">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="fa53d-164">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="fa53d-165">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="fa53d-165">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="fa53d-166">属性概述</span><span class="sxs-lookup"><span data-stu-id="fa53d-166">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="fa53d-167">如何：在代码中拆分和合并语句</span><span class="sxs-lookup"><span data-stu-id="fa53d-167">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
