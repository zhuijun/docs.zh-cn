---
title: 如何：定义可对不同数据类型提供相同功能的类
ms.date: 07/20/2015
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
ms.openlocfilehash: 268daf333dc5463e5436304cec188a9e6d477166
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077119"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="6537b-102">如何：定义可对不同数据类型提供相同功能的类 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6537b-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>

<span data-ttu-id="6537b-103">你可以定义这样一个类：你可以通过该类创建可在不同数据类型上提供相同功能的对象。</span><span class="sxs-lookup"><span data-stu-id="6537b-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="6537b-104">为此，你可以在定义中指定一个或多个 *类型形参* 。</span><span class="sxs-lookup"><span data-stu-id="6537b-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="6537b-105">然后，该类将能够充当使用不同数据类型的对象的模板。</span><span class="sxs-lookup"><span data-stu-id="6537b-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="6537b-106">通过这种方式定义的类称为 *泛型类*。</span><span class="sxs-lookup"><span data-stu-id="6537b-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="6537b-107">定义泛型类这种做法的优点在于：你只需定义一次泛型类，代码便可以利用它来创建使用各种数据类型的多个对象。</span><span class="sxs-lookup"><span data-stu-id="6537b-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="6537b-108">相对于使用 `Object` 类型定义类而言，这样做的性能将会更好。</span><span class="sxs-lookup"><span data-stu-id="6537b-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="6537b-109">除了类之外，你还可以定义和使用泛型结构、接口、过程和委托。</span><span class="sxs-lookup"><span data-stu-id="6537b-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="6537b-110">使用类型形参定义类</span><span class="sxs-lookup"><span data-stu-id="6537b-110">To define a class with a type parameter</span></span>  
  
1. <span data-ttu-id="6537b-111">采用常规方式定义类。</span><span class="sxs-lookup"><span data-stu-id="6537b-111">Define the class in the normal way.</span></span>  
  
2. <span data-ttu-id="6537b-112">`(Of` *typeparameter* `)` 紧靠类名称之后添加 typeparameter，以指定一个类型参数。</span><span class="sxs-lookup"><span data-stu-id="6537b-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3. <span data-ttu-id="6537b-113">如果有一个以上的类型形参，请在括号内列出这些参数（以逗号分隔）。</span><span class="sxs-lookup"><span data-stu-id="6537b-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="6537b-114">不要重复 `Of` 关键字。</span><span class="sxs-lookup"><span data-stu-id="6537b-114">Do not repeat the `Of` keyword.</span></span>  
  
4. <span data-ttu-id="6537b-115">如果代码是对类型形参执行操作，而不是简单的赋值，请在该类型形参后添加一个 `As` 子句，以便添加一个或多个 *约束*。</span><span class="sxs-lookup"><span data-stu-id="6537b-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="6537b-116">约束可保证为该类型形参提供的类型满足如下所示的要求：</span><span class="sxs-lookup"><span data-stu-id="6537b-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    - <span data-ttu-id="6537b-117">支持代码执行的运算（如 `>`）</span><span class="sxs-lookup"><span data-stu-id="6537b-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    - <span data-ttu-id="6537b-118">支持代码访问的成员（如方法）</span><span class="sxs-lookup"><span data-stu-id="6537b-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    - <span data-ttu-id="6537b-119">公开无参数构造函数</span><span class="sxs-lookup"><span data-stu-id="6537b-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="6537b-120">如果未指定任何约束，则代码只能使用 [Object Data Type](../../../language-reference/data-types/object-data-type.md)支持的那些运算和成员。</span><span class="sxs-lookup"><span data-stu-id="6537b-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="6537b-121">有关详细信息，请参阅 [Type List](../../../language-reference/statements/type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="6537b-121">For more information, see [Type List](../../../language-reference/statements/type-list.md).</span></span>  
  
5. <span data-ttu-id="6537b-122">标识要使用所提供类型声明的每个类成员，然后将其声明为 `As` `typeparameter` 。</span><span class="sxs-lookup"><span data-stu-id="6537b-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="6537b-123">这适用于内部存储、过程参数和返回值。</span><span class="sxs-lookup"><span data-stu-id="6537b-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6. <span data-ttu-id="6537b-124">确保代码只使用它可提供给 `itemType`的任何数据类型所支持的运算和方法。</span><span class="sxs-lookup"><span data-stu-id="6537b-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="6537b-125">下面的示例定义了一个类，用于管理一个非常简单的列表。</span><span class="sxs-lookup"><span data-stu-id="6537b-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="6537b-126">它将列表保存在内部数组 `items`中，并且使用代码可声明列表元素的数据类型。</span><span class="sxs-lookup"><span data-stu-id="6537b-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="6537b-127">参数化构造函数允许使用代码设置的上限 `items` ，而无参数构造函数将此项设置为9个 (，总计10个项) 。</span><span class="sxs-lookup"><span data-stu-id="6537b-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the parameterless constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     <span data-ttu-id="6537b-128">你可以声明来自 `simpleList` 的一个类来保存 `Integer` 值的列表，声明另一个类来保存 `String` 值的列表，再声明一个类来保存 `Date` 值。</span><span class="sxs-lookup"><span data-stu-id="6537b-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="6537b-129">除了列表成员的数据类型外，依据所有这些类创建的对象的行为方式都相同。</span><span class="sxs-lookup"><span data-stu-id="6537b-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="6537b-130">所用代码提供给 `itemType` 的类型实参可以是内部类型（如 `Boolean` 或 `Double`）、结构、枚举或任何类型的类，包括应用程序定义的类。</span><span class="sxs-lookup"><span data-stu-id="6537b-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="6537b-131">可以使用以下代码测试类 `simpleList` 。</span><span class="sxs-lookup"><span data-stu-id="6537b-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="6537b-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="6537b-132">See also</span></span>

- [<span data-ttu-id="6537b-133">数据类型</span><span class="sxs-lookup"><span data-stu-id="6537b-133">Data Types</span></span>](index.md)
- [<span data-ttu-id="6537b-134">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6537b-134">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="6537b-135">语言独立性和与语言无关的组件</span><span class="sxs-lookup"><span data-stu-id="6537b-135">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="6537b-136">个</span><span class="sxs-lookup"><span data-stu-id="6537b-136">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="6537b-137">Type List</span><span class="sxs-lookup"><span data-stu-id="6537b-137">Type List</span></span>](../../../language-reference/statements/type-list.md)
- [<span data-ttu-id="6537b-138">如何：使用泛型类</span><span class="sxs-lookup"><span data-stu-id="6537b-138">How to: Use a Generic Class</span></span>](how-to-use-a-generic-class.md)
- [<span data-ttu-id="6537b-139">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="6537b-139">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
