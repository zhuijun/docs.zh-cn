---
title: 如何：创建新变量
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: 501c8f3aff4c5b204d231bdc26213e13d125a7cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410524"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="17c23-102">如何：创建新变量 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17c23-102">How to: Create a New Variable (Visual Basic)</span></span>

<span data-ttu-id="17c23-103">使用[Dim 语句](../../../language-reference/statements/dim-statement.md)创建变量。</span><span class="sxs-lookup"><span data-stu-id="17c23-103">You create a variable with a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span>

### <a name="to-create-a-new-variable"></a><span data-ttu-id="17c23-104">创建新变量</span><span class="sxs-lookup"><span data-stu-id="17c23-104">To create a new variable</span></span>

1. <span data-ttu-id="17c23-105">在语句中声明变量 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="17c23-105">Declare the variable in a `Dim` statement.</span></span>

    ```vb
    Dim newCustomer
    ```

2. <span data-ttu-id="17c23-106">包含变量特征的规范，如[Private](../../../language-reference/modifiers/private.md)、 [Static](../../../language-reference/modifiers/static.md)、 [Shadows](../../../language-reference/modifiers/shadows.md)或[WithEvents](../../../language-reference/modifiers/withevents.md)。</span><span class="sxs-lookup"><span data-stu-id="17c23-106">Include specifications for the variable's characteristics, such as [Private](../../../language-reference/modifiers/private.md), [Static](../../../language-reference/modifiers/static.md), [Shadows](../../../language-reference/modifiers/shadows.md), or [WithEvents](../../../language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="17c23-107">有关详细信息，请参阅[声明的元素特征](../declared-elements/declared-element-characteristics.md)。</span><span class="sxs-lookup"><span data-stu-id="17c23-107">For more information, see [Declared Element Characteristics](../declared-elements/declared-element-characteristics.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

    <span data-ttu-id="17c23-108">`Dim`如果在声明中使用其他关键字，则不需要使用关键字。</span><span class="sxs-lookup"><span data-stu-id="17c23-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>

3. <span data-ttu-id="17c23-109">请按照该规范的名称进行操作，该变量的名称必须遵循 Visual Basic 规则和约定。</span><span class="sxs-lookup"><span data-stu-id="17c23-109">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="17c23-110">有关详细信息，请参阅已[声明的元素名称](../declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="17c23-110">For more information, see [Declared Element Names](../declared-elements/declared-element-names.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

4. <span data-ttu-id="17c23-111">在名称后跟[As](../../../language-reference/statements/as-clause.md)子句以指定变量的数据类型。</span><span class="sxs-lookup"><span data-stu-id="17c23-111">Follow the name with the [As](../../../language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>

    ```vb
    Public Static newCustomer As Customer
    ```

    <span data-ttu-id="17c23-112">如果未指定数据类型，则将使用默认值： `Object` 。</span><span class="sxs-lookup"><span data-stu-id="17c23-112">If you do not specify the data type, it uses the default: `Object`.</span></span>

5. <span data-ttu-id="17c23-113">`As`使用等号（）跟随子句 `=` ，并在该变量的初始值后跟等号。</span><span class="sxs-lookup"><span data-stu-id="17c23-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>

    <span data-ttu-id="17c23-114">每次运行语句时，Visual Basic 都将指定的值分配给变量 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="17c23-114">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="17c23-115">如果不指定初始值，则 Visual Basic 在首次输入包含该语句的代码时，为该变量的数据类型分配默认初始值 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="17c23-115">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>

    <span data-ttu-id="17c23-116">如果变量是引用类型，则可以通过在子句中包含[New 运算符](../../../language-reference/operators/new-operator.md)关键字来创建其类的实例 `As` 。</span><span class="sxs-lookup"><span data-stu-id="17c23-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="17c23-117">如果不使用，则 `New` 变量的初始值为[Nothing](../../../language-reference/nothing.md)。</span><span class="sxs-lookup"><span data-stu-id="17c23-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../language-reference/nothing.md).</span></span>

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a><span data-ttu-id="17c23-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="17c23-118">See also</span></span>

- [<span data-ttu-id="17c23-119">变量</span><span class="sxs-lookup"><span data-stu-id="17c23-119">Variables</span></span>](index.md)
- [<span data-ttu-id="17c23-120">变量声明</span><span class="sxs-lookup"><span data-stu-id="17c23-120">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="17c23-121">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="17c23-121">Declared Element Names</span></span>](../declared-elements/declared-element-names.md)
- [<span data-ttu-id="17c23-122">已声明元素的特性</span><span class="sxs-lookup"><span data-stu-id="17c23-122">Declared Element Characteristics</span></span>](../declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="17c23-123">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="17c23-123">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="17c23-124">语句</span><span class="sxs-lookup"><span data-stu-id="17c23-124">Statements</span></span>](../../../language-reference/statements/index.md)
- [<span data-ttu-id="17c23-125">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="17c23-125">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="17c23-126">Option Infer 语句</span><span class="sxs-lookup"><span data-stu-id="17c23-126">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
