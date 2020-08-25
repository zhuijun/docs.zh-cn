---
title: Is 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 1c2d87ef0a8202332c87af552f488d652c400213
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812258"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="d98f6-102">Is 运算符 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="d98f6-102">Is operator (Visual Basic)</span></span>

<span data-ttu-id="d98f6-103">比较两个对象引用变量。</span><span class="sxs-lookup"><span data-stu-id="d98f6-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="d98f6-104">语法</span><span class="sxs-lookup"><span data-stu-id="d98f6-104">Syntax</span></span>

```vb
result = object1 Is object2
```

## <a name="parts"></a><span data-ttu-id="d98f6-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="d98f6-105">Parts</span></span>

 `result`  
 <span data-ttu-id="d98f6-106">必需。</span><span class="sxs-lookup"><span data-stu-id="d98f6-106">Required.</span></span> <span data-ttu-id="d98f6-107">任何 `Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="d98f6-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="d98f6-108">必需。</span><span class="sxs-lookup"><span data-stu-id="d98f6-108">Required.</span></span> <span data-ttu-id="d98f6-109">任意 `Object` 名称。</span><span class="sxs-lookup"><span data-stu-id="d98f6-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="d98f6-110">必需。</span><span class="sxs-lookup"><span data-stu-id="d98f6-110">Required.</span></span> <span data-ttu-id="d98f6-111">任意 `Object` 名称。</span><span class="sxs-lookup"><span data-stu-id="d98f6-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d98f6-112">注解</span><span class="sxs-lookup"><span data-stu-id="d98f6-112">Remarks</span></span>

<span data-ttu-id="d98f6-113">`Is`运算符确定两个对象引用是否引用同一对象。</span><span class="sxs-lookup"><span data-stu-id="d98f6-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="d98f6-114">但是，它不会执行值比较。</span><span class="sxs-lookup"><span data-stu-id="d98f6-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="d98f6-115">如果 `object1` 和 `object2` 都引用完全相同的对象实例，则 `result` 为 `True` ; 如果不是，则为; 如果不是，则 `result` 为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="d98f6-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>

> [!NOTE]
> <span data-ttu-id="d98f6-116">`Is`关键字还用于[Select .。。Case 语句](../statements/select-case-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="d98f6-116">The `Is` keyword is also used in the [Select...Case Statement](../statements/select-case-statement.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="d98f6-117">示例</span><span class="sxs-lookup"><span data-stu-id="d98f6-117">Example</span></span>

<span data-ttu-id="d98f6-118">下面的示例使用 `Is` 运算符比较对象引用对。</span><span class="sxs-lookup"><span data-stu-id="d98f6-118">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="d98f6-119">将结果分配给一个 `Boolean` 值，该值表示两个对象是否相同。</span><span class="sxs-lookup"><span data-stu-id="d98f6-119">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>

[!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]

<span data-ttu-id="d98f6-120">如前面的示例所示，可以使用 `Is` 运算符来测试早期绑定和晚期绑定对象。</span><span class="sxs-lookup"><span data-stu-id="d98f6-120">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>

## <a name="use-typeof-operator-with-is-operator"></a><span data-ttu-id="d98f6-121">对 Is 运算符使用 TypeOf 运算符</span><span class="sxs-lookup"><span data-stu-id="d98f6-121">Use TypeOf operator with Is operator</span></span>

<span data-ttu-id="d98f6-122">`Is` 运算符还可与关键字一起使用 `TypeOf` ，以生成 `TypeOf` ... `Is` 表达式，该表达式测试对象变量是否与数据类型兼容。</span><span class="sxs-lookup"><span data-stu-id="d98f6-122">`Is` operator can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span> <span data-ttu-id="d98f6-123">例如：</span><span class="sxs-lookup"><span data-stu-id="d98f6-123">For example:</span></span>

```vb
If TypeOf sender Is Button Then
```

## <a name="see-also"></a><span data-ttu-id="d98f6-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d98f6-124">See also</span></span>

- [<span data-ttu-id="d98f6-125">TypeOf 运算符</span><span class="sxs-lookup"><span data-stu-id="d98f6-125">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="d98f6-126">IsNot 运算符</span><span class="sxs-lookup"><span data-stu-id="d98f6-126">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="d98f6-127">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d98f6-127">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="d98f6-128">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="d98f6-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="d98f6-129">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="d98f6-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="d98f6-130">运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="d98f6-130">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
