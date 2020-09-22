---
title: '&amp; 运算符'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: 20c2e2088691e68221872cc1dfc5486413515a4d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867148"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="5eb21-102">&amp; 操作员 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="5eb21-102">&amp; Operator (Visual Basic)</span></span>

<span data-ttu-id="5eb21-103">生成两个表达式的字符串串联。</span><span class="sxs-lookup"><span data-stu-id="5eb21-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eb21-104">语法</span><span class="sxs-lookup"><span data-stu-id="5eb21-104">Syntax</span></span>  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="5eb21-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="5eb21-105">Parts</span></span>  

 `result`  
 <span data-ttu-id="5eb21-106">必需。</span><span class="sxs-lookup"><span data-stu-id="5eb21-106">Required.</span></span> <span data-ttu-id="5eb21-107">Any `String` 或 `Object` variable。</span><span class="sxs-lookup"><span data-stu-id="5eb21-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="5eb21-108">必需。</span><span class="sxs-lookup"><span data-stu-id="5eb21-108">Required.</span></span> <span data-ttu-id="5eb21-109">数据类型扩大到的任何表达式 `String` 。</span><span class="sxs-lookup"><span data-stu-id="5eb21-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="5eb21-110">必需。</span><span class="sxs-lookup"><span data-stu-id="5eb21-110">Required.</span></span> <span data-ttu-id="5eb21-111">数据类型扩大到的任何表达式 `String` 。</span><span class="sxs-lookup"><span data-stu-id="5eb21-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5eb21-112">备注</span><span class="sxs-lookup"><span data-stu-id="5eb21-112">Remarks</span></span>  

 <span data-ttu-id="5eb21-113">如果或的数据类型 `expression1` `expression2` 不能 `String` 扩大到，则 `String` 会将其转换为 `String` 。</span><span class="sxs-lookup"><span data-stu-id="5eb21-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="5eb21-114">如果数据类型之一不能扩大到 `String` ，编译器将生成错误。</span><span class="sxs-lookup"><span data-stu-id="5eb21-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="5eb21-115">的数据类型 `result` 为 `String` 。</span><span class="sxs-lookup"><span data-stu-id="5eb21-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="5eb21-116">如果一个或两个表达式的计算结果都不为，或者其 [值为](../nothing.md) <xref:System.DBNull.Value?displayProperty=nameWithType> ，则将它们视为值为 "" 的字符串。</span><span class="sxs-lookup"><span data-stu-id="5eb21-116">If one or both expressions evaluate to [Nothing](../nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5eb21-117">`&`运算符可以*重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="5eb21-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5eb21-118">如果你的代码在该类或结构上使用此运算符，请确保了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="5eb21-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="5eb21-119">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="5eb21-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5eb21-120">与号 ( # A0) 字符也可用于将变量标识为类型 `Long` 。</span><span class="sxs-lookup"><span data-stu-id="5eb21-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="5eb21-121">有关详细信息，请参阅 [类型字符](../../programming-guide/language-features/data-types/type-characters.md)。</span><span class="sxs-lookup"><span data-stu-id="5eb21-121">For more information, see [Type Characters](../../programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5eb21-122">示例</span><span class="sxs-lookup"><span data-stu-id="5eb21-122">Example</span></span>  

 <span data-ttu-id="5eb21-123">此示例使用 `&` 运算符强制字符串连接。</span><span class="sxs-lookup"><span data-stu-id="5eb21-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="5eb21-124">结果是一个表示两个字符串操作数串联的字符串值。</span><span class="sxs-lookup"><span data-stu-id="5eb21-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5eb21-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5eb21-125">See also</span></span>

- [<span data-ttu-id="5eb21-126">&= 运算符</span><span class="sxs-lookup"><span data-stu-id="5eb21-126">&= Operator</span></span>](and-assignment-operator.md)
- [<span data-ttu-id="5eb21-127">串联运算符</span><span class="sxs-lookup"><span data-stu-id="5eb21-127">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="5eb21-128">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="5eb21-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="5eb21-129">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="5eb21-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="5eb21-130">串联运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5eb21-130">Concatenation Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
