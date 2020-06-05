---
title: IsFalse 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 7c5ad5fa0b72370eeb19fbaced88807570467552
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370669"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="ae134-102">IsFalse 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae134-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="ae134-103">确定表达式是否为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="ae134-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="ae134-104">你不能 `IsFalse` 在代码中显式调用，但是 Visual Basic 编译器可以使用它来生成代码 from `AndAlso` 子句。</span><span class="sxs-lookup"><span data-stu-id="ae134-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="ae134-105">如果定义类或结构，然后在子句中使用该类型的变量 `AndAlso` ，则必须 `IsFalse` 在该类或结构上进行定义。</span><span class="sxs-lookup"><span data-stu-id="ae134-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="ae134-106">编译器将 `IsFalse` 和运算符视为 `IsTrue` *匹配的对*。</span><span class="sxs-lookup"><span data-stu-id="ae134-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="ae134-107">这意味着，如果定义其中一个类型，则还必须定义另一个。</span><span class="sxs-lookup"><span data-stu-id="ae134-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae134-108">`IsFalse`运算符可以*重载*，这意味着当类或结构的操作数具有该类或结构的类型时，该类或结构可以重新定义它的行为。</span><span class="sxs-lookup"><span data-stu-id="ae134-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="ae134-109">如果你的代码在该类或结构上使用此运算符，请确保了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="ae134-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ae134-110">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="ae134-110">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae134-111">示例</span><span class="sxs-lookup"><span data-stu-id="ae134-111">Example</span></span>  
 <span data-ttu-id="ae134-112">下面的代码示例定义了包含和运算符定义的结构的轮廓 `IsFalse` `IsTrue` 。</span><span class="sxs-lookup"><span data-stu-id="ae134-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="ae134-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ae134-113">See also</span></span>

- [<span data-ttu-id="ae134-114">IsTrue 运算符</span><span class="sxs-lookup"><span data-stu-id="ae134-114">IsTrue Operator</span></span>](istrue-operator.md)
- [<span data-ttu-id="ae134-115">如何：定义运算符</span><span class="sxs-lookup"><span data-stu-id="ae134-115">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="ae134-116">AndAlso 运算符</span><span class="sxs-lookup"><span data-stu-id="ae134-116">AndAlso Operator</span></span>](andalso-operator.md)
