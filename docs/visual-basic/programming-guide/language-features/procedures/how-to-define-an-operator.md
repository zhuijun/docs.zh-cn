---
title: 如何：定义运算符
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: 49b9c8d1a6db56a56b50c16b4a6bb5b928df6c7d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388032"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="6224d-102">如何：定义运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6224d-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="6224d-103">如果已定义类或结构，则可 `*` `<>` `And` 在一个或两个操作数为类或结构的类型时定义标准运算符（如、或）的行为。</span><span class="sxs-lookup"><span data-stu-id="6224d-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="6224d-104">将标准运算符定义为类或结构中的运算符过程。</span><span class="sxs-lookup"><span data-stu-id="6224d-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="6224d-105">所有运算符过程必须是 `Public` `Shared` 。</span><span class="sxs-lookup"><span data-stu-id="6224d-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="6224d-106">在类或结构上定义运算符也称为*重载*运算符。</span><span class="sxs-lookup"><span data-stu-id="6224d-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6224d-107">示例</span><span class="sxs-lookup"><span data-stu-id="6224d-107">Example</span></span>  
 <span data-ttu-id="6224d-108">下面的示例 `+` 为一个名为的结构定义运算符 `height` 。</span><span class="sxs-lookup"><span data-stu-id="6224d-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="6224d-109">结构使用以英尺和英寸为单位的高度。</span><span class="sxs-lookup"><span data-stu-id="6224d-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="6224d-110">一*英寸*为2.54 厘米，1*英尺*为12英寸。</span><span class="sxs-lookup"><span data-stu-id="6224d-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="6224d-111">为了确保标准化的值（英寸 < 12.0），构造函数执行*模*12 算术运算。</span><span class="sxs-lookup"><span data-stu-id="6224d-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="6224d-112">`+`运算符使用构造函数生成规范化值。</span><span class="sxs-lookup"><span data-stu-id="6224d-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 <span data-ttu-id="6224d-113">可以 `height` 通过以下代码测试结构。</span><span class="sxs-lookup"><span data-stu-id="6224d-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a><span data-ttu-id="6224d-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6224d-114">See also</span></span>

- [<span data-ttu-id="6224d-115">运算符过程</span><span class="sxs-lookup"><span data-stu-id="6224d-115">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="6224d-116">如何：定义转换运算符</span><span class="sxs-lookup"><span data-stu-id="6224d-116">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="6224d-117">如何：调用运算符过程</span><span class="sxs-lookup"><span data-stu-id="6224d-117">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="6224d-118">如何：使用定义运算符的类</span><span class="sxs-lookup"><span data-stu-id="6224d-118">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="6224d-119">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="6224d-119">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="6224d-120">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="6224d-120">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="6224d-121">如何：声明结构</span><span class="sxs-lookup"><span data-stu-id="6224d-121">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="6224d-122">Mod 运算符</span><span class="sxs-lookup"><span data-stu-id="6224d-122">Mod Operator</span></span>](../../../language-reference/operators/mod-operator.md)
