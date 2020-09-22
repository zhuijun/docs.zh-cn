---
title: '- 运算符'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: b5129c2dbb361940fa6da2cb424ee23736ba72c5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875325"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="987a3-102">- 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="987a3-102">- Operator (Visual Basic)</span></span>

<span data-ttu-id="987a3-103">返回数值表达式的两个数值表达式或负值之间的差。</span><span class="sxs-lookup"><span data-stu-id="987a3-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="987a3-104">语法</span><span class="sxs-lookup"><span data-stu-id="987a3-104">Syntax</span></span>  
  
```vb  
expression1 – expression2
```
  
<span data-ttu-id="987a3-105">or</span><span class="sxs-lookup"><span data-stu-id="987a3-105">or</span></span>

```vb  
–expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="987a3-106">组成部分</span><span class="sxs-lookup"><span data-stu-id="987a3-106">Parts</span></span>  

 `expression1`  
 <span data-ttu-id="987a3-107">必需。</span><span class="sxs-lookup"><span data-stu-id="987a3-107">Required.</span></span> <span data-ttu-id="987a3-108">任何数值表达式。</span><span class="sxs-lookup"><span data-stu-id="987a3-108">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="987a3-109">必需，除非 `–` 操作员计算负值。</span><span class="sxs-lookup"><span data-stu-id="987a3-109">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="987a3-110">任何数值表达式。</span><span class="sxs-lookup"><span data-stu-id="987a3-110">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="987a3-111">结果</span><span class="sxs-lookup"><span data-stu-id="987a3-111">Result</span></span>  

 <span data-ttu-id="987a3-112">结果是与的差 `expression1` 或的 `expression2` 求反值 `expression1` 。</span><span class="sxs-lookup"><span data-stu-id="987a3-112">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="987a3-113">Result 数据类型是适用于和的数据类型的数值类型 `expression1` `expression2` 。</span><span class="sxs-lookup"><span data-stu-id="987a3-113">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="987a3-114">请参阅 [运算符结果的数据类型](data-types-of-operator-results.md)中的 "整数算法" 表。</span><span class="sxs-lookup"><span data-stu-id="987a3-114">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="987a3-115">支持的类型</span><span class="sxs-lookup"><span data-stu-id="987a3-115">Supported Types</span></span>  

 <span data-ttu-id="987a3-116">所有数值类型。</span><span class="sxs-lookup"><span data-stu-id="987a3-116">All numeric types.</span></span> <span data-ttu-id="987a3-117">这包括无符号和浮点类型和 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="987a3-117">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="987a3-118">备注</span><span class="sxs-lookup"><span data-stu-id="987a3-118">Remarks</span></span>  

 <span data-ttu-id="987a3-119">在前面所示的语法中所示的第一个用法中， `–` 运算符是两个数值表达式之差的 *二进制* 算术减法运算符。</span><span class="sxs-lookup"><span data-stu-id="987a3-119">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="987a3-120">在前面所示的语法中所示的第二个用法中， `–` 运算符是表达式的负值的 *一元* 求反运算符。</span><span class="sxs-lookup"><span data-stu-id="987a3-120">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="987a3-121">在这种意义上，否定包含反转的符号， `expression1` 因此如果为负，则结果为正 `expression1` 。</span><span class="sxs-lookup"><span data-stu-id="987a3-121">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="987a3-122">如果其中一个表达式的计算结果为 [Nothing](../nothing.md)，则 `–` 运算符将其视为零。</span><span class="sxs-lookup"><span data-stu-id="987a3-122">If either expression evaluates to [Nothing](../nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="987a3-123">`–`运算符可以*重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="987a3-123">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="987a3-124">如果代码对这样的类或结构使用此运算符，请确保了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="987a3-124">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="987a3-125">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="987a3-125">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="987a3-126">示例</span><span class="sxs-lookup"><span data-stu-id="987a3-126">Example</span></span>  

 <span data-ttu-id="987a3-127">下面的示例使用 `–` 运算符计算并返回两个数字之间的差，然后对数字求反。</span><span class="sxs-lookup"><span data-stu-id="987a3-127">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 <span data-ttu-id="987a3-128">执行这些语句后， `binaryResult` 包含124.45， `unaryResult` 包含–334.90。</span><span class="sxs-lookup"><span data-stu-id="987a3-128">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="987a3-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="987a3-129">See also</span></span>

- [<span data-ttu-id="987a3-130">-= 运算符 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="987a3-130">-= Operator (Visual Basic)</span></span>](subtraction-assignment-operator.md)
- [<span data-ttu-id="987a3-131">算术运算符</span><span class="sxs-lookup"><span data-stu-id="987a3-131">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="987a3-132">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="987a3-132">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="987a3-133">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="987a3-133">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="987a3-134">算术运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="987a3-134">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
