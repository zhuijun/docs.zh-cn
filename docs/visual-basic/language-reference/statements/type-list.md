---
title: Type List
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: 7e22ad6e32ec13f081391e1d47a80df8b1e65063
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412983"
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="a4975-102">类型列表 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4975-102">Type List (Visual Basic)</span></span>

<span data-ttu-id="a4975-103">指定*泛型*编程元素的*类型参数*。</span><span class="sxs-lookup"><span data-stu-id="a4975-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="a4975-104">多个参数之间用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="a4975-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="a4975-105">下面是一个类型参数的语法。</span><span class="sxs-lookup"><span data-stu-id="a4975-105">Following is the syntax for one type parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="a4975-106">语法</span><span class="sxs-lookup"><span data-stu-id="a4975-106">Syntax</span></span>

```vb
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a><span data-ttu-id="a4975-107">组成部分</span><span class="sxs-lookup"><span data-stu-id="a4975-107">Parts</span></span>

|<span data-ttu-id="a4975-108">术语</span><span class="sxs-lookup"><span data-stu-id="a4975-108">Term</span></span>|<span data-ttu-id="a4975-109">定义</span><span class="sxs-lookup"><span data-stu-id="a4975-109">Definition</span></span>|
|---|---|
|`genericmodifier`|<span data-ttu-id="a4975-110">可选。</span><span class="sxs-lookup"><span data-stu-id="a4975-110">Optional.</span></span> <span data-ttu-id="a4975-111">只能在泛型接口和委托中使用。</span><span class="sxs-lookup"><span data-stu-id="a4975-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="a4975-112">可以通过使用[Out](../modifiers/out-generic-modifier.md)关键字或逆变，使用[In](../modifiers/in-generic-modifier.md)关键字声明类型协变。</span><span class="sxs-lookup"><span data-stu-id="a4975-112">You can declare a type covariant by using the [Out](../modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="a4975-113">请参阅 [协变和逆变](../../programming-guide/concepts/covariance-contravariance/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a4975-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|
|`typename`|<span data-ttu-id="a4975-114">必需。</span><span class="sxs-lookup"><span data-stu-id="a4975-114">Required.</span></span> <span data-ttu-id="a4975-115">类型参数的名称。</span><span class="sxs-lookup"><span data-stu-id="a4975-115">Name of the type parameter.</span></span> <span data-ttu-id="a4975-116">这是占位符，将替换为相应类型参数提供的定义类型。</span><span class="sxs-lookup"><span data-stu-id="a4975-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|
|`constraintlist`|<span data-ttu-id="a4975-117">可选。</span><span class="sxs-lookup"><span data-stu-id="a4975-117">Optional.</span></span> <span data-ttu-id="a4975-118">约束可提供的数据类型的要求列表 `typename` 。</span><span class="sxs-lookup"><span data-stu-id="a4975-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="a4975-119">如果有多个约束，请将它们括在大括号（）中，并用 `{ }` 逗号分隔它们。</span><span class="sxs-lookup"><span data-stu-id="a4975-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="a4975-120">必须引入包含[As](as-clause.md)关键字的约束列表。</span><span class="sxs-lookup"><span data-stu-id="a4975-120">You must introduce the constraint list with the [As](as-clause.md) keyword.</span></span> <span data-ttu-id="a4975-121">在 `As` 列表的开头只使用一次。</span><span class="sxs-lookup"><span data-stu-id="a4975-121">You use `As` only once, at the beginning of the list.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a4975-122">备注</span><span class="sxs-lookup"><span data-stu-id="a4975-122">Remarks</span></span>

<span data-ttu-id="a4975-123">每个泛型编程元素都必须采用至少一个类型参数。</span><span class="sxs-lookup"><span data-stu-id="a4975-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="a4975-124">类型参数是客户端代码在创建泛型类型的实例时指定的特定类型（*构造元素*）的占位符。</span><span class="sxs-lookup"><span data-stu-id="a4975-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="a4975-125">可以定义泛型类、结构、接口、过程或委托。</span><span class="sxs-lookup"><span data-stu-id="a4975-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>

<span data-ttu-id="a4975-126">有关何时定义泛型类型的详细信息，请参阅[Visual Basic 中的泛型类型](../../programming-guide/language-features/data-types/generic-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a4975-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="a4975-127">有关类型参数名称的详细信息，请参阅已[声明的元素名称](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="a4975-127">For more information on type parameter names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="rules"></a><span data-ttu-id="a4975-128">规则</span><span class="sxs-lookup"><span data-stu-id="a4975-128">Rules</span></span>

- <span data-ttu-id="a4975-129">**括号.**</span><span class="sxs-lookup"><span data-stu-id="a4975-129">**Parentheses.**</span></span> <span data-ttu-id="a4975-130">如果提供类型参数列表，则必须将其括在括号内，并且必须[使用关键字 of](of-clause.md)引入列表。</span><span class="sxs-lookup"><span data-stu-id="a4975-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](of-clause.md) keyword.</span></span> <span data-ttu-id="a4975-131">在 `Of` 列表的开头只使用一次。</span><span class="sxs-lookup"><span data-stu-id="a4975-131">You use `Of` only once, at the beginning of the list.</span></span>

- <span data-ttu-id="a4975-132">**约束.**</span><span class="sxs-lookup"><span data-stu-id="a4975-132">**Constraints.**</span></span> <span data-ttu-id="a4975-133">类型形参上的*约束*列表可以包括以下各项：</span><span class="sxs-lookup"><span data-stu-id="a4975-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>

  - <span data-ttu-id="a4975-134">任意数量的接口。</span><span class="sxs-lookup"><span data-stu-id="a4975-134">Any number of interfaces.</span></span> <span data-ttu-id="a4975-135">提供的类型必须实现此列表中的每个接口。</span><span class="sxs-lookup"><span data-stu-id="a4975-135">The supplied type must implement every interface in this list.</span></span>

  - <span data-ttu-id="a4975-136">最多一个类。</span><span class="sxs-lookup"><span data-stu-id="a4975-136">At most one class.</span></span> <span data-ttu-id="a4975-137">提供的类型必须从该类继承。</span><span class="sxs-lookup"><span data-stu-id="a4975-137">The supplied type must inherit from that class.</span></span>

  - <span data-ttu-id="a4975-138">`New` 关键字。</span><span class="sxs-lookup"><span data-stu-id="a4975-138">The `New` keyword.</span></span> <span data-ttu-id="a4975-139">提供的类型必须公开您的泛型类型可以访问的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="a4975-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="a4975-140">如果通过一个或多个接口约束类型参数，则此方法很有用。</span><span class="sxs-lookup"><span data-stu-id="a4975-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="a4975-141">实现接口的类型不一定公开构造函数，并且根据构造函数的访问级别，泛型类型中的代码可能无法访问该构造函数。</span><span class="sxs-lookup"><span data-stu-id="a4975-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>

  - <span data-ttu-id="a4975-142">`Class`关键字或 `Structure` 关键字。</span><span class="sxs-lookup"><span data-stu-id="a4975-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="a4975-143">`Class`关键字约束泛型类型参数，要求传递给它的任何类型参数都是引用类型，例如字符串、数组或委托，或者是从类创建的对象。</span><span class="sxs-lookup"><span data-stu-id="a4975-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="a4975-144">`Structure`关键字约束泛型类型参数，要求传递给它的任何类型参数都是值类型，例如结构、枚举或基本数据类型。</span><span class="sxs-lookup"><span data-stu-id="a4975-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="a4975-145">不能同时包含 `Class` 和 `Structure` `constraintlist` 。</span><span class="sxs-lookup"><span data-stu-id="a4975-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>

  <span data-ttu-id="a4975-146">提供的类型必须满足中包含的每项要求 `constraintlist` 。</span><span class="sxs-lookup"><span data-stu-id="a4975-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>

  <span data-ttu-id="a4975-147">每个类型参数的约束与其他类型参数上的约束无关。</span><span class="sxs-lookup"><span data-stu-id="a4975-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>

## <a name="behavior"></a><span data-ttu-id="a4975-148">行为</span><span class="sxs-lookup"><span data-stu-id="a4975-148">Behavior</span></span>

- <span data-ttu-id="a4975-149">**编译时替换。**</span><span class="sxs-lookup"><span data-stu-id="a4975-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="a4975-150">当你从泛型编程元素创建构造类型时，将为每个类型参数提供一个定义的类型。</span><span class="sxs-lookup"><span data-stu-id="a4975-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="a4975-151">Visual Basic 编译器将为泛型元素内的每个匹配项替换提供的类型 `typename` 。</span><span class="sxs-lookup"><span data-stu-id="a4975-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>

- <span data-ttu-id="a4975-152">**缺少约束。**</span><span class="sxs-lookup"><span data-stu-id="a4975-152">**Absence of Constraints.**</span></span> <span data-ttu-id="a4975-153">如果未在类型参数上指定任何约束，则代码仅限于该类型参数的[对象数据类型](../data-types/object-data-type.md)支持的操作和成员。</span><span class="sxs-lookup"><span data-stu-id="a4975-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../data-types/object-data-type.md) for that type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="a4975-154">示例</span><span class="sxs-lookup"><span data-stu-id="a4975-154">Example</span></span>

<span data-ttu-id="a4975-155">下面的示例演示了泛型字典类的主干定义，其中包括用于向字典中添加新条目的主干函数。</span><span class="sxs-lookup"><span data-stu-id="a4975-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a><span data-ttu-id="a4975-156">示例</span><span class="sxs-lookup"><span data-stu-id="a4975-156">Example</span></span>

<span data-ttu-id="a4975-157">由于 `dictionary` 是泛型的，使用它的代码可从其创建各种对象，每个对象具有相同的功能，但在不同的数据类型上进行操作。</span><span class="sxs-lookup"><span data-stu-id="a4975-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="a4975-158">下面的示例演示了创建 `dictionary` 包含 `String` 项和键的对象的代码行 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="a4975-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a><span data-ttu-id="a4975-159">示例</span><span class="sxs-lookup"><span data-stu-id="a4975-159">Example</span></span>

<span data-ttu-id="a4975-160">下面的示例演示前面的示例生成的等效主干定义。</span><span class="sxs-lookup"><span data-stu-id="a4975-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="a4975-161">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a4975-161">See also</span></span>

- [<span data-ttu-id="a4975-162">个</span><span class="sxs-lookup"><span data-stu-id="a4975-162">Of</span></span>](of-clause.md)
- [<span data-ttu-id="a4975-163">New 运算符</span><span class="sxs-lookup"><span data-stu-id="a4975-163">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="a4975-164">Visual Basic 中的访问级别</span><span class="sxs-lookup"><span data-stu-id="a4975-164">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="a4975-165">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="a4975-165">Object Data Type</span></span>](../data-types/object-data-type.md)
- [<span data-ttu-id="a4975-166">Function 语句</span><span class="sxs-lookup"><span data-stu-id="a4975-166">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="a4975-167">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="a4975-167">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="a4975-168">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="a4975-168">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="a4975-169">如何：使用泛型类</span><span class="sxs-lookup"><span data-stu-id="a4975-169">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="a4975-170">协变和逆变</span><span class="sxs-lookup"><span data-stu-id="a4975-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="a4975-171">在</span><span class="sxs-lookup"><span data-stu-id="a4975-171">In</span></span>](../modifiers/in-generic-modifier.md)
- [<span data-ttu-id="a4975-172">弄</span><span class="sxs-lookup"><span data-stu-id="a4975-172">Out</span></span>](../modifiers/out-generic-modifier.md)
