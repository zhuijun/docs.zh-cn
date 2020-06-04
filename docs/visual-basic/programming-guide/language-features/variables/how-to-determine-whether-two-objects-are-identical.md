---
title: 如何：确定两个对象是否相同
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 67c3af8b7bdac3ad1c7e4908f1ac2684df7a87aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410472"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="f8991-102">如何：确定两个对象是否相同 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8991-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="f8991-103">在 Visual Basic 中，如果两个变量引用相同，即两个变量都指向内存中的同一个类实例，则将其视为相同。</span><span class="sxs-lookup"><span data-stu-id="f8991-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="f8991-104">例如，在 Windows 窗体应用程序中，您可能需要进行比较以确定当前实例（）是否与 `Me` 特定实例（如）相同 `Form2` 。</span><span class="sxs-lookup"><span data-stu-id="f8991-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="f8991-105">Visual Basic 提供了两个运算符来比较指针。</span><span class="sxs-lookup"><span data-stu-id="f8991-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="f8991-106">如果对象相同，[则 Is 运算符](../../../language-reference/operators/is-operator.md)返回 `True` ; 如果不是，则为[IsNot 运算符](../../../language-reference/operators/isnot-operator.md) `True` 。</span><span class="sxs-lookup"><span data-stu-id="f8991-106">The [Is Operator](../../../language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="f8991-107">确定两个对象是否相同</span><span class="sxs-lookup"><span data-stu-id="f8991-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="f8991-108">确定两个对象是否相同</span><span class="sxs-lookup"><span data-stu-id="f8991-108">To determine if two objects are identical</span></span>  
  
1. <span data-ttu-id="f8991-109">设置 `Boolean` 用于测试两个对象的表达式。</span><span class="sxs-lookup"><span data-stu-id="f8991-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="f8991-110">在测试表达式中，对 `Is` 两个对象使用运算符作为操作数。</span><span class="sxs-lookup"><span data-stu-id="f8991-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="f8991-111">`Is``True`如果对象指向相同的类实例，则返回。</span><span class="sxs-lookup"><span data-stu-id="f8991-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="f8991-112">确定两个对象是否不相同</span><span class="sxs-lookup"><span data-stu-id="f8991-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="f8991-113">有时，如果两个对象不完全相同，则需要执行一个操作，例如，将和组合起来会很难 `Not` `Is` `If Not obj1 Is obj2` 。</span><span class="sxs-lookup"><span data-stu-id="f8991-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="f8991-114">在这种情况下，可以使用 `IsNot` 运算符。</span><span class="sxs-lookup"><span data-stu-id="f8991-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="f8991-115">确定两个对象是否不相同</span><span class="sxs-lookup"><span data-stu-id="f8991-115">To determine if two objects are not identical</span></span>  
  
1. <span data-ttu-id="f8991-116">设置 `Boolean` 用于测试两个对象的表达式。</span><span class="sxs-lookup"><span data-stu-id="f8991-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="f8991-117">在测试表达式中，对 `IsNot` 两个对象使用运算符作为操作数。</span><span class="sxs-lookup"><span data-stu-id="f8991-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="f8991-118">`IsNot``True`如果对象未指向同一类实例，则返回。</span><span class="sxs-lookup"><span data-stu-id="f8991-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8991-119">示例</span><span class="sxs-lookup"><span data-stu-id="f8991-119">Example</span></span>  
 <span data-ttu-id="f8991-120">下面的示例测试变量对 `Object` ，以确定它们是否指向相同的类实例。</span><span class="sxs-lookup"><span data-stu-id="f8991-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 <span data-ttu-id="f8991-121">前面的示例显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="f8991-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="f8991-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f8991-122">See also</span></span>

- [<span data-ttu-id="f8991-123">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="f8991-123">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="f8991-124">对象变量</span><span class="sxs-lookup"><span data-stu-id="f8991-124">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="f8991-125">对象变量值</span><span class="sxs-lookup"><span data-stu-id="f8991-125">Object Variable Values</span></span>](object-variable-values.md)
- [<span data-ttu-id="f8991-126">Is 运算符</span><span class="sxs-lookup"><span data-stu-id="f8991-126">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="f8991-127">IsNot 运算符</span><span class="sxs-lookup"><span data-stu-id="f8991-127">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="f8991-128">如何：确定两个对象是否相关</span><span class="sxs-lookup"><span data-stu-id="f8991-128">How to: Determine Whether Two Objects Are Related</span></span>](how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="f8991-129">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="f8991-129">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
