---
title: 如何：定义转换运算符
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 2fabcf6c6ceb38fe77d4eed4f02dcb5a5e447bf1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085667"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="d5c01-102">如何：定义转换运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5c01-102">How to: Define a Conversion Operator (Visual Basic)</span></span>

<span data-ttu-id="d5c01-103">如果已定义类或结构，则可以在类或结构的类型与另一种数据类型 (如 `Integer` 、或) 之间定义类型转换运算符 `Double` `String` 。</span><span class="sxs-lookup"><span data-stu-id="d5c01-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="d5c01-104">将类型转换定义为类或结构中的 [CType 函数](../../../language-reference/functions/ctype-function.md) 过程。</span><span class="sxs-lookup"><span data-stu-id="d5c01-104">Define the type conversion as a [CType Function](../../../language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="d5c01-105">所有转换过程必须是 `Public Shared` ，并且每个转换过程必须指定 [扩大](../../../language-reference/modifiers/widening.md) 或 [收缩](../../../language-reference/modifiers/narrowing.md)。</span><span class="sxs-lookup"><span data-stu-id="d5c01-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../language-reference/modifiers/widening.md) or [Narrowing](../../../language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="d5c01-106">在类或结构上定义运算符也称为 *重载* 运算符。</span><span class="sxs-lookup"><span data-stu-id="d5c01-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5c01-107">示例</span><span class="sxs-lookup"><span data-stu-id="d5c01-107">Example</span></span>  

 <span data-ttu-id="d5c01-108">下面的示例定义了名为和的结构之间的转换运算符 `digit` `Byte` 。</span><span class="sxs-lookup"><span data-stu-id="d5c01-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 <span data-ttu-id="d5c01-109">可以 `digit` 通过以下代码测试结构。</span><span class="sxs-lookup"><span data-stu-id="d5c01-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="d5c01-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="d5c01-110">See also</span></span>

- [<span data-ttu-id="d5c01-111">运算符过程</span><span class="sxs-lookup"><span data-stu-id="d5c01-111">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="d5c01-112">如何：定义运算符</span><span class="sxs-lookup"><span data-stu-id="d5c01-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="d5c01-113">如何：调用运算符过程</span><span class="sxs-lookup"><span data-stu-id="d5c01-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="d5c01-114">如何：使用定义运算符的类</span><span class="sxs-lookup"><span data-stu-id="d5c01-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="d5c01-115">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="d5c01-115">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="d5c01-116">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="d5c01-116">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="d5c01-117">如何：声明结构</span><span class="sxs-lookup"><span data-stu-id="d5c01-117">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="d5c01-118">隐式转换和显式转换</span><span class="sxs-lookup"><span data-stu-id="d5c01-118">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="d5c01-119">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="d5c01-119">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
