---
description: new 约束 - C# 参考
title: new 约束 - C# 参考
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: f7b097729fe973aba7b85c48e1b1033aade83080
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139445"
---
# <a name="new-constraint-c-reference"></a><span data-ttu-id="cfe0d-103">new 约束（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="cfe0d-103">new constraint (C# Reference)</span></span>

<span data-ttu-id="cfe0d-104">`new` 约束指定泛型类声明中的类型实参必须有公共的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="cfe0d-104">The `new` constraint specifies that a type argument in a generic class declaration must have a public parameterless constructor.</span></span> <span data-ttu-id="cfe0d-105">若要使用 `new` 约束，则该类型不能为抽象类型。</span><span class="sxs-lookup"><span data-stu-id="cfe0d-105">To use the `new` constraint, the type cannot be abstract.</span></span>

<span data-ttu-id="cfe0d-106">当泛型类创建类型的新实例时，请将 `new` 约束应用于类型参数，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="cfe0d-106">Apply the `new` constraint to a type parameter when a generic class creates new instances of the type, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

<span data-ttu-id="cfe0d-107">当与其他约束一起使用时，`new()` 约束必须最后指定：</span><span class="sxs-lookup"><span data-stu-id="cfe0d-107">When you use the `new()` constraint with other constraints, it must be specified last:</span></span>

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

<span data-ttu-id="cfe0d-108">有关详细信息，请参阅[类型参数的约束](../../programming-guide/generics/constraints-on-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="cfe0d-108">For more information, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

<span data-ttu-id="cfe0d-109">`new` 关键字还可用于[创建类型的实例](../operators/new-operator.md)或用作[成员声明修饰符](new-modifier.md)。</span><span class="sxs-lookup"><span data-stu-id="cfe0d-109">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [member declaration modifier](new-modifier.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cfe0d-110">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="cfe0d-110">C# language specification</span></span>

<span data-ttu-id="cfe0d-111">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的[类型参数约束](~/_csharplang/spec/classes.md#type-parameter-constraints)部分。</span><span class="sxs-lookup"><span data-stu-id="cfe0d-111">For more information, see the [Type parameter constraints](~/_csharplang/spec/classes.md#type-parameter-constraints) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cfe0d-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="cfe0d-112">See also</span></span>

- [<span data-ttu-id="cfe0d-113">C# 参考</span><span class="sxs-lookup"><span data-stu-id="cfe0d-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cfe0d-114">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="cfe0d-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cfe0d-115">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="cfe0d-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="cfe0d-116">泛型</span><span class="sxs-lookup"><span data-stu-id="cfe0d-116">Generics</span></span>](../../programming-guide/generics/index.md)
