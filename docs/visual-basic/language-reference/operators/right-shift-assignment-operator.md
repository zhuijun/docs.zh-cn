---
title: '>>= 运算符'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: a1c2331791644155504183d3cf5767470a3bf17b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873357"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="7c54d-102">>>= 运算符 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="7c54d-102">>>= Operator (Visual Basic)</span></span>

<span data-ttu-id="7c54d-103">对变量或属性的值执行算术右移位，并将结果赋回给变量或属性。</span><span class="sxs-lookup"><span data-stu-id="7c54d-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c54d-104">语法</span><span class="sxs-lookup"><span data-stu-id="7c54d-104">Syntax</span></span>  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="7c54d-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="7c54d-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="7c54d-106">必需。</span><span class="sxs-lookup"><span data-stu-id="7c54d-106">Required.</span></span> <span data-ttu-id="7c54d-107">整数类型的变量或属性 (`SByte` 、、、、、、 `Byte` `Short` `UShort` `Integer` `UInteger` `Long` 或 `ULong`) 。</span><span class="sxs-lookup"><span data-stu-id="7c54d-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="7c54d-108">必需。</span><span class="sxs-lookup"><span data-stu-id="7c54d-108">Required.</span></span> <span data-ttu-id="7c54d-109">扩大到的数据类型的数值表达式 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="7c54d-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c54d-110">备注</span><span class="sxs-lookup"><span data-stu-id="7c54d-110">Remarks</span></span>  

 <span data-ttu-id="7c54d-111">运算符左侧的元素 `>>=` 可以是简单的标量变量、属性或数组的元素。</span><span class="sxs-lookup"><span data-stu-id="7c54d-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="7c54d-112">变量或属性不能是 [只读](../modifiers/readonly.md)的。</span><span class="sxs-lookup"><span data-stu-id="7c54d-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="7c54d-113">`>>=`运算符首先对变量或属性的值执行算术右移位运算。</span><span class="sxs-lookup"><span data-stu-id="7c54d-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="7c54d-114">然后，运算符将该操作的结果赋给变量或属性。</span><span class="sxs-lookup"><span data-stu-id="7c54d-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="7c54d-115">算术移位不是循环的，这意味着，不会在另一端重新引入结果的末尾以外的位。</span><span class="sxs-lookup"><span data-stu-id="7c54d-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="7c54d-116">在算术右移位时，将丢弃超出最右位位置的位，并将最左侧的位传播到左端空出的位位置。</span><span class="sxs-lookup"><span data-stu-id="7c54d-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="7c54d-117">这意味着，如果 `variableorproperty` 具有负值，空出位置将设置为1。</span><span class="sxs-lookup"><span data-stu-id="7c54d-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="7c54d-118">如果 `variableorproperty` 为正，或者其数据类型为无符号类型，则空出位置将设置为零。</span><span class="sxs-lookup"><span data-stu-id="7c54d-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="7c54d-119">重载</span><span class="sxs-lookup"><span data-stu-id="7c54d-119">Overloading</span></span>  

 <span data-ttu-id="7c54d-120">可以*重载* [>> 运算符](right-shift-operator.md)，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="7c54d-120">The [>> Operator](right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="7c54d-121">重载 `>>` 运算符会影响运算符的行为 `>>=` 。</span><span class="sxs-lookup"><span data-stu-id="7c54d-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="7c54d-122">如果你的代码 `>>=` 在重载的类或结构上使用 `>>` ，请确保你了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="7c54d-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="7c54d-123">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="7c54d-123">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c54d-124">示例</span><span class="sxs-lookup"><span data-stu-id="7c54d-124">Example</span></span>  

 <span data-ttu-id="7c54d-125">下面的示例使用 `>>=` 运算符将变量的位模式右移指定的 `Integer` 量，并将结果赋给该变量。</span><span class="sxs-lookup"><span data-stu-id="7c54d-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="7c54d-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7c54d-126">See also</span></span>

- [<span data-ttu-id="7c54d-127">>> 运算符</span><span class="sxs-lookup"><span data-stu-id="7c54d-127">>> Operator</span></span>](right-shift-operator.md)
- [<span data-ttu-id="7c54d-128">赋值运算符</span><span class="sxs-lookup"><span data-stu-id="7c54d-128">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="7c54d-129">移位运算符</span><span class="sxs-lookup"><span data-stu-id="7c54d-129">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="7c54d-130">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="7c54d-130">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="7c54d-131">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="7c54d-131">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="7c54d-132">语句</span><span class="sxs-lookup"><span data-stu-id="7c54d-132">Statements</span></span>](../../programming-guide/language-features/statements.md)
