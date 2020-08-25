---
title: IsNot 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- comparison operators [Visual Basic]
- TypeOf...IsNot expression
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ea978f8874cee20fb3a005189fd846f7564da777
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811036"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="0d3b6-102">IsNot 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d3b6-102">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="0d3b6-103">比较两个对象引用变量。</span><span class="sxs-lookup"><span data-stu-id="0d3b6-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d3b6-104">语法</span><span class="sxs-lookup"><span data-stu-id="0d3b6-104">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="0d3b6-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="0d3b6-105">Parts</span></span>

- `result`

  <span data-ttu-id="0d3b6-106">必需。</span><span class="sxs-lookup"><span data-stu-id="0d3b6-106">Required.</span></span> <span data-ttu-id="0d3b6-107">一个 `Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="0d3b6-107">A `Boolean` value.</span></span>

- `object1`

  <span data-ttu-id="0d3b6-108">必需。</span><span class="sxs-lookup"><span data-stu-id="0d3b6-108">Required.</span></span> <span data-ttu-id="0d3b6-109">任何 `Object` 变量或表达式。</span><span class="sxs-lookup"><span data-stu-id="0d3b6-109">Any `Object` variable or expression.</span></span>

- `object2`

  <span data-ttu-id="0d3b6-110">必需。</span><span class="sxs-lookup"><span data-stu-id="0d3b6-110">Required.</span></span> <span data-ttu-id="0d3b6-111">任何 `Object` 变量或表达式。</span><span class="sxs-lookup"><span data-stu-id="0d3b6-111">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d3b6-112">注解</span><span class="sxs-lookup"><span data-stu-id="0d3b6-112">Remarks</span></span>

<span data-ttu-id="0d3b6-113">`IsNot`运算符确定两个对象引用是否引用不同的对象。</span><span class="sxs-lookup"><span data-stu-id="0d3b6-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="0d3b6-114">但是，它不会执行值比较。</span><span class="sxs-lookup"><span data-stu-id="0d3b6-114">However, it doesn't perform value comparisons.</span></span> <span data-ttu-id="0d3b6-115">如果 `object1` 和 `object2` 都引用完全相同的对象实例，则 `result` 为 `False` ; 如果不是，则为; 如果不是， `result` 则为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="0d3b6-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they don't, `result` is `True`.</span></span>

<span data-ttu-id="0d3b6-116">`IsNot` 与 `Is` 运算符相反。</span><span class="sxs-lookup"><span data-stu-id="0d3b6-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="0d3b6-117">的优点 `IsNot` 是，您可以避免使用 `Not` 和 `Is` 难以理解语法，这会很难阅读。</span><span class="sxs-lookup"><span data-stu-id="0d3b6-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="0d3b6-118">您可以使用 `Is` 和 `IsNot` 运算符来测试早期绑定对象和后期绑定对象。</span><span class="sxs-lookup"><span data-stu-id="0d3b6-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="0d3b6-119">示例</span><span class="sxs-lookup"><span data-stu-id="0d3b6-119">Example</span></span>

<span data-ttu-id="0d3b6-120">下面的代码示例使用 `Is` 运算符和 `IsNot` 运算符来完成相同的比较。</span><span class="sxs-lookup"><span data-stu-id="0d3b6-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

[!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="use-typeof-operator-with-isnot-operator"></a><span data-ttu-id="0d3b6-121">对 IsNot 运算符使用 TypeOf 运算符</span><span class="sxs-lookup"><span data-stu-id="0d3b6-121">Use TypeOf operator with IsNot operator</span></span>

<span data-ttu-id="0d3b6-122">从 Visual Basic 14 开始，可以将 `TypeOf` 运算符与运算符一起使用， `IsNot` 以测试对象是否与数据类型 *不* 兼容。</span><span class="sxs-lookup"><span data-stu-id="0d3b6-122">Starting with Visual Basic 14, you can use the `TypeOf` operator with the `IsNot` operator to test whether an object is *not* compatible with a data type.</span></span> <span data-ttu-id="0d3b6-123">例如：</span><span class="sxs-lookup"><span data-stu-id="0d3b6-123">For example:</span></span>

```vb
If TypeOf sender IsNot Button Then
```

## <a name="see-also"></a><span data-ttu-id="0d3b6-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0d3b6-124">See also</span></span>

- [<span data-ttu-id="0d3b6-125">Is 运算符</span><span class="sxs-lookup"><span data-stu-id="0d3b6-125">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="0d3b6-126">TypeOf 运算符</span><span class="sxs-lookup"><span data-stu-id="0d3b6-126">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="0d3b6-127">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="0d3b6-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="0d3b6-128">如何：测试两个对象是否相同</span><span class="sxs-lookup"><span data-stu-id="0d3b6-128">How to: Test Whether Two Objects Are the Same</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
