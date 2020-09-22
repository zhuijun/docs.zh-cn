---
title: '&amp;= 运算符'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: 9b77c44aa77afd59e36e1d21451205d3929ef527
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874873"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="73810-102">&amp;= 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73810-102">&amp;= Operator (Visual Basic)</span></span>

<span data-ttu-id="73810-103">将 `String` 表达式连接到 `String` 变量或属性，并将结果赋给变量或属性。</span><span class="sxs-lookup"><span data-stu-id="73810-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73810-104">语法</span><span class="sxs-lookup"><span data-stu-id="73810-104">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="73810-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="73810-105">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="73810-106">必需。</span><span class="sxs-lookup"><span data-stu-id="73810-106">Required.</span></span> <span data-ttu-id="73810-107">任何 `String` 变量或属性。</span><span class="sxs-lookup"><span data-stu-id="73810-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="73810-108">必需。</span><span class="sxs-lookup"><span data-stu-id="73810-108">Required.</span></span> <span data-ttu-id="73810-109">任何 `String` 表达式。</span><span class="sxs-lookup"><span data-stu-id="73810-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73810-110">备注</span><span class="sxs-lookup"><span data-stu-id="73810-110">Remarks</span></span>  

 <span data-ttu-id="73810-111">运算符左侧的元素 `&=` 可以是简单的标量变量、属性或数组的元素。</span><span class="sxs-lookup"><span data-stu-id="73810-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="73810-112">变量或属性不能是 [只读](../modifiers/readonly.md)的。</span><span class="sxs-lookup"><span data-stu-id="73810-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="73810-113">`&=`运算符将 `String` 其右侧的表达式连接到左侧的 `String` 变量或属性，并将结果赋给其左侧的变量或属性。</span><span class="sxs-lookup"><span data-stu-id="73810-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="73810-114">重载</span><span class="sxs-lookup"><span data-stu-id="73810-114">Overloading</span></span>  

 <span data-ttu-id="73810-115">可以*重载* [& 运算符](concatenation-operator.md)，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="73810-115">The [& Operator](concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="73810-116">重载 `&` 运算符会影响运算符的行为 `&=` 。</span><span class="sxs-lookup"><span data-stu-id="73810-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="73810-117">如果你的代码 `&=` 在重载的类或结构上使用 `&` ，请确保你了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="73810-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="73810-118">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="73810-118">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="73810-119">示例</span><span class="sxs-lookup"><span data-stu-id="73810-119">Example</span></span>  

 <span data-ttu-id="73810-120">下面的示例使用 `&=` 运算符将两个变量连接起来 `String` ，并将结果赋给第一个变量。</span><span class="sxs-lookup"><span data-stu-id="73810-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="73810-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="73810-121">See also</span></span>

- [<span data-ttu-id="73810-122">& 运算符</span><span class="sxs-lookup"><span data-stu-id="73810-122">& Operator</span></span>](concatenation-operator.md)
- [<span data-ttu-id="73810-123">+ = 运算符</span><span class="sxs-lookup"><span data-stu-id="73810-123">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="73810-124">赋值运算符</span><span class="sxs-lookup"><span data-stu-id="73810-124">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="73810-125">串联运算符</span><span class="sxs-lookup"><span data-stu-id="73810-125">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="73810-126">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="73810-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="73810-127">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="73810-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="73810-128">语句</span><span class="sxs-lookup"><span data-stu-id="73810-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
