---
title: 运算符过程
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: a1dd183570c8aa50efff85bdaebef90bd3b0120f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364313"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="00a98-102">运算符过程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00a98-102">Operator Procedures (Visual Basic)</span></span>

<span data-ttu-id="00a98-103">运算符过程是一系列 Visual Basic 语句，用于定义标准运算符（如 `*` 、 `<>` 或 `And` ）在已定义的类或结构中的行为。</span><span class="sxs-lookup"><span data-stu-id="00a98-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="00a98-104">这也称为*运算符重载*。</span><span class="sxs-lookup"><span data-stu-id="00a98-104">This is also called *operator overloading*.</span></span>

## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="00a98-105">何时定义操作员过程</span><span class="sxs-lookup"><span data-stu-id="00a98-105">When to Define Operator Procedures</span></span>

<span data-ttu-id="00a98-106">定义了类或结构后，可以将变量声明为该类或结构的类型。</span><span class="sxs-lookup"><span data-stu-id="00a98-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="00a98-107">有时，此类变量需要作为表达式的一部分参与操作。</span><span class="sxs-lookup"><span data-stu-id="00a98-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="00a98-108">为此，它必须是运算符的操作数。</span><span class="sxs-lookup"><span data-stu-id="00a98-108">To do this, it must be an operand of an operator.</span></span>

<span data-ttu-id="00a98-109">Visual Basic 仅定义其基本数据类型的运算符。</span><span class="sxs-lookup"><span data-stu-id="00a98-109">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="00a98-110">如果两个操作数或其中一个操作数为类或结构的类型，则可以定义运算符的行为。</span><span class="sxs-lookup"><span data-stu-id="00a98-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>

<span data-ttu-id="00a98-111">有关详细信息，请参阅[Operator 语句](../../../language-reference/statements/operator-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="00a98-111">For more information, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>

## <a name="types-of-operator-procedure"></a><span data-ttu-id="00a98-112">运算符过程的类型</span><span class="sxs-lookup"><span data-stu-id="00a98-112">Types of Operator Procedure</span></span>

<span data-ttu-id="00a98-113">操作员过程可以是以下类型之一：</span><span class="sxs-lookup"><span data-stu-id="00a98-113">An operator procedure can be one of the following types:</span></span>

- <span data-ttu-id="00a98-114">一元运算符的定义，其中的参数是你的类或结构的类型。</span><span class="sxs-lookup"><span data-stu-id="00a98-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="00a98-115">二元运算符的定义，其中至少有一个参数是你的类或结构的类型。</span><span class="sxs-lookup"><span data-stu-id="00a98-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>

- <span data-ttu-id="00a98-116">转换运算符的定义，其中的参数属于你的类或结构的类型。</span><span class="sxs-lookup"><span data-stu-id="00a98-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="00a98-117">返回类或结构的类型的转换运算符的定义。</span><span class="sxs-lookup"><span data-stu-id="00a98-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>

 <span data-ttu-id="00a98-118">转换运算符始终为一元运算符，并且你始终使用 `CType` 作为正在定义的运算符。</span><span class="sxs-lookup"><span data-stu-id="00a98-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="00a98-119">声明语法</span><span class="sxs-lookup"><span data-stu-id="00a98-119">Declaration Syntax</span></span>

<span data-ttu-id="00a98-120">声明运算符过程的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="00a98-120">The syntax for declaring an operator procedure is as follows:</span></span>

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

<span data-ttu-id="00a98-121">`Widening` `Narrowing` 仅对类型转换运算符使用或关键字。</span><span class="sxs-lookup"><span data-stu-id="00a98-121">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="00a98-122">对于类型转换运算符，运算符符号始终是[CType 函数](../../../language-reference/functions/ctype-function.md)。</span><span class="sxs-lookup"><span data-stu-id="00a98-122">The operator symbol is always [CType Function](../../../language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>

<span data-ttu-id="00a98-123">您可以声明两个操作数来定义一个二元运算符，并声明一个操作数来定义一元运算符，包括类型转换运算符。</span><span class="sxs-lookup"><span data-stu-id="00a98-123">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="00a98-124">必须声明所有操作数 `ByVal` 。</span><span class="sxs-lookup"><span data-stu-id="00a98-124">All operands must be declared `ByVal`.</span></span>

<span data-ttu-id="00a98-125">声明每个操作数的方式与声明[Sub 过程](./sub-procedures.md)的参数的方式相同。</span><span class="sxs-lookup"><span data-stu-id="00a98-125">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="00a98-126">数据类型</span><span class="sxs-lookup"><span data-stu-id="00a98-126">Data Type</span></span>

<span data-ttu-id="00a98-127">由于你在定义的类或结构上定义运算符，因此至少一个操作数必须是该类或结构的数据类型。</span><span class="sxs-lookup"><span data-stu-id="00a98-127">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="00a98-128">对于类型转换运算符，操作数或返回类型必须是类或结构的数据类型。</span><span class="sxs-lookup"><span data-stu-id="00a98-128">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>

<span data-ttu-id="00a98-129">有关更多详细信息，请参阅[Operator 语句](../../../language-reference/statements/operator-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="00a98-129">For more details, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="00a98-130">调用语法</span><span class="sxs-lookup"><span data-stu-id="00a98-130">Calling Syntax</span></span>

<span data-ttu-id="00a98-131">通过在表达式中使用运算符符号，可以隐式调用运算符过程。</span><span class="sxs-lookup"><span data-stu-id="00a98-131">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="00a98-132">提供操作数的方式与预定义运算符相同。</span><span class="sxs-lookup"><span data-stu-id="00a98-132">You supply the operands the same way you do for predefined operators.</span></span>

<span data-ttu-id="00a98-133">对运算符过程的隐式调用的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="00a98-133">The syntax for an implicit call to an operator procedure is as follows:</span></span>

<span data-ttu-id="00a98-134">`Dim testStruct As`  *structurename*</span><span class="sxs-lookup"><span data-stu-id="00a98-134">`Dim testStruct As`  *structurename*</span></span>

<span data-ttu-id="00a98-135">`Dim testNewStruct As`  *structurename* `= testStruct`*operatorsymbol*      `10`</span><span class="sxs-lookup"><span data-stu-id="00a98-135">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="00a98-136">声明和调用的插图</span><span class="sxs-lookup"><span data-stu-id="00a98-136">Illustration of Declaration and Call</span></span>

<span data-ttu-id="00a98-137">下面的结构将已签名的128位整数值存储为构成的高序位和低序位部分。</span><span class="sxs-lookup"><span data-stu-id="00a98-137">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="00a98-138">它定义 `+` 运算符以添加两个 `veryLong` 值并生成一个结果 `veryLong` 值。</span><span class="sxs-lookup"><span data-stu-id="00a98-138">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

<span data-ttu-id="00a98-139">下面的示例演示对 `+` 上定义的运算符的典型调用 `veryLong` 。</span><span class="sxs-lookup"><span data-stu-id="00a98-139">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="00a98-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="00a98-140">See also</span></span>

- [<span data-ttu-id="00a98-141">过程</span><span class="sxs-lookup"><span data-stu-id="00a98-141">Procedures</span></span>](./index.md)
- [<span data-ttu-id="00a98-142">Sub 过程</span><span class="sxs-lookup"><span data-stu-id="00a98-142">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="00a98-143">Function 过程</span><span class="sxs-lookup"><span data-stu-id="00a98-143">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="00a98-144">Property 过程</span><span class="sxs-lookup"><span data-stu-id="00a98-144">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="00a98-145">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="00a98-145">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="00a98-146">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="00a98-146">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="00a98-147">如何：定义运算符</span><span class="sxs-lookup"><span data-stu-id="00a98-147">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="00a98-148">如何：定义转换运算符</span><span class="sxs-lookup"><span data-stu-id="00a98-148">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="00a98-149">如何：调用运算符过程</span><span class="sxs-lookup"><span data-stu-id="00a98-149">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="00a98-150">如何：使用定义运算符的类</span><span class="sxs-lookup"><span data-stu-id="00a98-150">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
