---
title: 匿名类型
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
ms.openlocfilehash: 5ab3cf8c3c02ff35890f71ad6c7f314b51b87133
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075234"
---
# <a name="anonymous-types-visual-basic"></a><span data-ttu-id="3a184-102">匿名类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a184-102">Anonymous Types (Visual Basic)</span></span>

<span data-ttu-id="3a184-103">Visual Basic 支持匿名类型，这使您无需为数据类型编写类定义即可创建对象。</span><span class="sxs-lookup"><span data-stu-id="3a184-103">Visual Basic supports anonymous types, which enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="3a184-104">此时，编译器将为你生成类。</span><span class="sxs-lookup"><span data-stu-id="3a184-104">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="3a184-105">该类没有可使用的名称，直接从继承 <xref:System.Object> ，并且包含在声明对象时指定的属性。</span><span class="sxs-lookup"><span data-stu-id="3a184-105">The class has no usable name, inherits directly from <xref:System.Object>, and contains the properties you specify in declaring the object.</span></span> <span data-ttu-id="3a184-106">由于未指定数据类型的名称，因此它被称为 *匿名类型*。</span><span class="sxs-lookup"><span data-stu-id="3a184-106">Because the name of the data type is not specified, it is referred to as an *anonymous type*.</span></span>  
  
 <span data-ttu-id="3a184-107">下面的示例声明一个变量，并将 `product` 其创建为具有两个属性（和）的匿名类型的实例 `Name` `Price` 。</span><span class="sxs-lookup"><span data-stu-id="3a184-107">The following example declares and creates variable `product` as an instance of an anonymous type that has two properties, `Name` and `Price`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 <span data-ttu-id="3a184-108">*查询表达式*使用匿名类型来合并查询选择的数据列。</span><span class="sxs-lookup"><span data-stu-id="3a184-108">A *query expression* uses anonymous types to combine columns of data selected by a query.</span></span> <span data-ttu-id="3a184-109">不能提前定义结果类型，因为无法预测特定查询可能选择的列。</span><span class="sxs-lookup"><span data-stu-id="3a184-109">You cannot define the type of the result in advance, because you cannot predict the columns a particular query might select.</span></span> <span data-ttu-id="3a184-110">利用匿名类型，您可以编写一个查询，以任意顺序选择任意数量的列。</span><span class="sxs-lookup"><span data-stu-id="3a184-110">Anonymous types enable you to write a query that selects any number of columns, in any order.</span></span> <span data-ttu-id="3a184-111">编译器将创建与指定的属性和指定的顺序相匹配的数据类型。</span><span class="sxs-lookup"><span data-stu-id="3a184-111">The compiler creates a data type that matches the specified properties and the specified order.</span></span>  
  
 <span data-ttu-id="3a184-112">在下面的示例中， `products` 是产品对象的列表，其中每个对象都有多个属性。</span><span class="sxs-lookup"><span data-stu-id="3a184-112">In the following examples, `products` is a list of product objects, each of which has many properties.</span></span> <span data-ttu-id="3a184-113">变量 `namePriceQuery` 包含查询的定义，该查询在执行时返回具有两个属性（和）的匿名类型的实例的集合 `Name` `Price` 。</span><span class="sxs-lookup"><span data-stu-id="3a184-113">Variable `namePriceQuery` holds the definition of a query that, when it is executed, returns a collection of instances of an anonymous type that has two properties, `Name` and `Price`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#2)]  
  
 <span data-ttu-id="3a184-114">变量 `nameQuantityQuery` 包含查询的定义，该查询在执行时返回具有两个属性（和）的匿名类型的实例的集合 `Name` `OnHand` 。</span><span class="sxs-lookup"><span data-stu-id="3a184-114">Variable `nameQuantityQuery` holds the definition of a query that, when it is executed, returns a collection of instances of an anonymous type that has two properties, `Name` and `OnHand`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#3)]  
  
 <span data-ttu-id="3a184-115">有关编译器为匿名类型创建的代码的详细信息，请参阅 [匿名类型定义](anonymous-type-definition.md)。</span><span class="sxs-lookup"><span data-stu-id="3a184-115">For more information about the code created by the compiler for an anonymous type, see [Anonymous Type Definition](anonymous-type-definition.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="3a184-116">匿名类型的名称是编译器生成的，可能因编译而异。</span><span class="sxs-lookup"><span data-stu-id="3a184-116">The name of the anonymous type is compiler generated and may vary from compilation to compilation.</span></span> <span data-ttu-id="3a184-117">你的代码不应使用或依赖于匿名类型的名称，因为在重新编译项目时，名称可能会更改。</span><span class="sxs-lookup"><span data-stu-id="3a184-117">Your code should not use or rely on the name of an anonymous type because the name might change when a project is recompiled.</span></span>  
  
## <a name="declaring-an-anonymous-type"></a><span data-ttu-id="3a184-118">声明匿名类型</span><span class="sxs-lookup"><span data-stu-id="3a184-118">Declaring an Anonymous Type</span></span>  

 <span data-ttu-id="3a184-119">匿名类型的实例的声明使用初始值设定项列表指定该类型的属性。</span><span class="sxs-lookup"><span data-stu-id="3a184-119">The declaration of an instance of an anonymous type uses an initializer list to specify the properties of the type.</span></span> <span data-ttu-id="3a184-120">当你声明匿名类型而不是其他类元素（如方法或事件）时，只能指定属性。</span><span class="sxs-lookup"><span data-stu-id="3a184-120">You can specify only properties when you declare an anonymous type, not other class elements such as methods or events.</span></span> <span data-ttu-id="3a184-121">在下面的示例中， `product1` 是具有两个属性的匿名类型的实例： `Name` 和 `Price` 。</span><span class="sxs-lookup"><span data-stu-id="3a184-121">In the following example, `product1` is an instance of an anonymous type that has two properties: `Name` and `Price`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#4)]  
  
 <span data-ttu-id="3a184-122">如果将属性指定为键属性，则可以使用这些属性来比较两个匿名类型实例是否相等。</span><span class="sxs-lookup"><span data-stu-id="3a184-122">If you designate properties as key properties, you can use them to compare two anonymous type instances for equality.</span></span> <span data-ttu-id="3a184-123">但是，不能更改键属性的值。</span><span class="sxs-lookup"><span data-stu-id="3a184-123">However, the values of key properties cannot be changed.</span></span> <span data-ttu-id="3a184-124">有关详细信息，请参阅本主题后面的 "关键属性" 一节。</span><span class="sxs-lookup"><span data-stu-id="3a184-124">See the Key Properties section later in this topic for more information.</span></span>  
  
 <span data-ttu-id="3a184-125">请注意，声明匿名类型的实例类似于通过使用对象初始值设定项声明命名类型的实例：</span><span class="sxs-lookup"><span data-stu-id="3a184-125">Notice that declaring an instance of an anonymous type is like declaring an instance of a named type by using an object initializer:</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#5)]  
  
 <span data-ttu-id="3a184-126">有关指定匿名类型属性的其他方法的详细信息，请参阅 [如何：推断匿名类型声明中的属性名称和类型](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)。</span><span class="sxs-lookup"><span data-stu-id="3a184-126">For more information about other ways to specify anonymous type properties, see [How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="3a184-127">键属性</span><span class="sxs-lookup"><span data-stu-id="3a184-127">Key Properties</span></span>  

 <span data-ttu-id="3a184-128">键属性在几个基本方面不同于非键属性：</span><span class="sxs-lookup"><span data-stu-id="3a184-128">Key properties differ from non-key properties in several fundamental ways:</span></span>  
  
- <span data-ttu-id="3a184-129">仅比较键属性的值，以确定两个实例是否相等。</span><span class="sxs-lookup"><span data-stu-id="3a184-129">Only the values of key properties are compared in order to determine whether two instances are equal.</span></span>  
  
- <span data-ttu-id="3a184-130">键属性的值是只读的，无法更改。</span><span class="sxs-lookup"><span data-stu-id="3a184-130">The values of key properties are read-only and cannot be changed.</span></span>  
  
- <span data-ttu-id="3a184-131">编译器生成的匿名类型的哈希代码算法中只包含密钥属性值。</span><span class="sxs-lookup"><span data-stu-id="3a184-131">Only key property values are included in the compiler-generated hash code algorithm for an anonymous type.</span></span>  
  
### <a name="equality"></a><span data-ttu-id="3a184-132">等式</span><span class="sxs-lookup"><span data-stu-id="3a184-132">Equality</span></span>  

 <span data-ttu-id="3a184-133">仅当匿名类型的实例是同一匿名类型的实例时，才可以相等。</span><span class="sxs-lookup"><span data-stu-id="3a184-133">Instances of anonymous types can be equal only if they are instances of the same anonymous type.</span></span> <span data-ttu-id="3a184-134">如果两个实例满足以下条件，则编译器会将两个实例视为相同类型的实例：</span><span class="sxs-lookup"><span data-stu-id="3a184-134">The compiler treats two instances as instances of the same type if they meet the following conditions:</span></span>  
  
- <span data-ttu-id="3a184-135">它们是在同一程序集中声明的。</span><span class="sxs-lookup"><span data-stu-id="3a184-135">They are declared in the same assembly.</span></span>  
  
- <span data-ttu-id="3a184-136">它们的属性具有相同的名称、相同的推断类型，并按相同顺序进行声明。</span><span class="sxs-lookup"><span data-stu-id="3a184-136">Their properties have the same names, the same inferred types, and are declared in the same order.</span></span> <span data-ttu-id="3a184-137">名称比较不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="3a184-137">Name comparisons are not case-sensitive.</span></span>  
  
- <span data-ttu-id="3a184-138">每个中的相同属性都标记为键属性。</span><span class="sxs-lookup"><span data-stu-id="3a184-138">The same properties in each are marked as key properties.</span></span>  
  
- <span data-ttu-id="3a184-139">每个声明中至少有一个属性是键属性。</span><span class="sxs-lookup"><span data-stu-id="3a184-139">At least one property in each declaration is a key property.</span></span>  
  
 <span data-ttu-id="3a184-140">没有键属性的匿名类型的实例仅等于其自身。</span><span class="sxs-lookup"><span data-stu-id="3a184-140">An instance of an anonymous types that has no key properties is equal only to itself.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#6)]  
  
 <span data-ttu-id="3a184-141">如果其键属性的值相等，则同一匿名类型的两个实例相等。</span><span class="sxs-lookup"><span data-stu-id="3a184-141">Two instances of the same anonymous type are equal if the values of their key properties are equal.</span></span> <span data-ttu-id="3a184-142">下面的示例演示如何测试相等性。</span><span class="sxs-lookup"><span data-stu-id="3a184-142">The following examples illustrate how equality is tested.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#7)]  
  
### <a name="read-only-values"></a><span data-ttu-id="3a184-143">只读值</span><span class="sxs-lookup"><span data-stu-id="3a184-143">Read-Only Values</span></span>  

 <span data-ttu-id="3a184-144">键属性的值不能更改。</span><span class="sxs-lookup"><span data-stu-id="3a184-144">The values of key properties cannot be changed.</span></span> <span data-ttu-id="3a184-145">例如，在 `prod8` 前面的示例中， `Name` 和 `Price` 字段为 `read-only` ，但 `OnHand` 可以更改。</span><span class="sxs-lookup"><span data-stu-id="3a184-145">For example, in `prod8` in the previous example, the `Name` and `Price` fields are `read-only`, but `OnHand` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#8)]  
  
## <a name="anonymous-types-from-query-expressions"></a><span data-ttu-id="3a184-146">查询表达式中的匿名类型</span><span class="sxs-lookup"><span data-stu-id="3a184-146">Anonymous Types from Query Expressions</span></span>  

 <span data-ttu-id="3a184-147">查询表达式并不总是需要创建匿名类型。</span><span class="sxs-lookup"><span data-stu-id="3a184-147">Query expressions do not always require the creation of anonymous types.</span></span> <span data-ttu-id="3a184-148">如果可能，它们使用现有类型来保存列数据。</span><span class="sxs-lookup"><span data-stu-id="3a184-148">When possible, they use an existing type to hold the column data.</span></span> <span data-ttu-id="3a184-149">如果查询返回数据源中的全部记录，或者只返回每个记录中的一个字段，则会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="3a184-149">This occurs when the query returns either whole records from the data source, or only one field from each record.</span></span> <span data-ttu-id="3a184-150">在下面的代码示例中， `customers` 是类的对象的集合 `Customer` 。</span><span class="sxs-lookup"><span data-stu-id="3a184-150">In the following code examples, `customers` is a collection of objects of a `Customer` class.</span></span> <span data-ttu-id="3a184-151">类具有很多属性，并且可以按任意顺序在查询结果中包含一个或多个属性。</span><span class="sxs-lookup"><span data-stu-id="3a184-151">The class has many properties, and you can include one or more of them in the query result, in any order.</span></span> <span data-ttu-id="3a184-152">在前两个示例中，不需要匿名类型，因为查询选择了命名类型的元素：</span><span class="sxs-lookup"><span data-stu-id="3a184-152">In the first two examples, no anonymous types are required because the queries select elements of named types:</span></span>  
  
- <span data-ttu-id="3a184-153">`custs1` 包含字符串的集合，因为 `cust.Name` 是一个字符串。</span><span class="sxs-lookup"><span data-stu-id="3a184-153">`custs1` contains a collection of strings, because `cust.Name` is a string.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#30)]  
  
- <span data-ttu-id="3a184-154">`custs2` 包含对象的集合 `Customer` ，因为的每个元素 `customers` 都是一个 `Customer` 对象，并且整个元素都由查询选择。</span><span class="sxs-lookup"><span data-stu-id="3a184-154">`custs2` contains a collection of `Customer` objects, because each element of `customers` is a `Customer` object, and the whole element is selected by the query.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#31)]  
  
 <span data-ttu-id="3a184-155">但是，相应的命名类型并不始终可用。</span><span class="sxs-lookup"><span data-stu-id="3a184-155">However, appropriate named types are not always available.</span></span> <span data-ttu-id="3a184-156">你可能想要选择客户名称和地址以实现一个目的、为其他客户 ID 编号和位置，并为第三个帐户选择客户名称、地址和订单历史记录。</span><span class="sxs-lookup"><span data-stu-id="3a184-156">You might want to select customer names and addresses for one purpose, customer ID numbers and locations for another, and customer names, addresses, and order histories for a third.</span></span> <span data-ttu-id="3a184-157">匿名类型使你可以按任意顺序选择任何属性组合，而无需首先声明新的命名类型来保存结果。</span><span class="sxs-lookup"><span data-stu-id="3a184-157">Anonymous types enable you to select any combination of properties, in any order, without first declaring a new named type to hold the result.</span></span> <span data-ttu-id="3a184-158">相反，编译器会为每个属性编译创建一个匿名类型。</span><span class="sxs-lookup"><span data-stu-id="3a184-158">Instead, the compiler creates an anonymous type for each compilation of properties.</span></span> <span data-ttu-id="3a184-159">下面的查询从中的每个对象中仅选择客户的名称和 ID 号 `Customer` `customers` 。</span><span class="sxs-lookup"><span data-stu-id="3a184-159">The following query selects only the customer's name and ID number from each `Customer` object in `customers`.</span></span> <span data-ttu-id="3a184-160">因此，编译器将创建仅包含这两个属性的匿名类型。</span><span class="sxs-lookup"><span data-stu-id="3a184-160">Therefore, the compiler creates an anonymous type that contains only those two properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#32)]  
  
 <span data-ttu-id="3a184-161">匿名类型中的属性的名称和数据类型都是从到、和的参数中获取 `Select` 的 `cust.Name` `cust.ID` 。</span><span class="sxs-lookup"><span data-stu-id="3a184-161">Both the names and the data types of the properties in the anonymous type are taken from the arguments to `Select`, `cust.Name` and `cust.ID`.</span></span> <span data-ttu-id="3a184-162">由查询创建的匿名类型中的属性始终是键属性。</span><span class="sxs-lookup"><span data-stu-id="3a184-162">The properties in an anonymous type that is created by a query are always key properties.</span></span> <span data-ttu-id="3a184-163">当 `custs3` 在以下循环中执行时 `For Each` ，结果是具有两个键属性和的匿名类型的实例的集合 `Name` `ID` 。</span><span class="sxs-lookup"><span data-stu-id="3a184-163">When `custs3` is executed in the following `For Each` loop, the result is a collection of instances of an anonymous type with two key properties, `Name` and `ID`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#33)]  
  
 <span data-ttu-id="3a184-164">由表示的集合中的元素 `custs3` 是强类型的，您可以使用 IntelliSense 浏览可用属性并验证其类型。</span><span class="sxs-lookup"><span data-stu-id="3a184-164">The elements in the collection represented by `custs3` are strongly typed, and you can use IntelliSense to navigate through the available properties and to verify their types.</span></span>  
  
 <span data-ttu-id="3a184-165">有关详细信息，请参阅[Visual Basic 中的 LINQ 简介](../linq/introduction-to-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="3a184-165">For more information, see [Introduction to LINQ in Visual Basic](../linq/introduction-to-linq.md).</span></span>  
  
## <a name="deciding-whether-to-use-anonymous-types"></a><span data-ttu-id="3a184-166">确定是否使用匿名类型</span><span class="sxs-lookup"><span data-stu-id="3a184-166">Deciding Whether to Use Anonymous Types</span></span>  

 <span data-ttu-id="3a184-167">在将对象创建为匿名类的实例之前，请考虑这是否是最佳选项。</span><span class="sxs-lookup"><span data-stu-id="3a184-167">Before you create an object as an instance of an anonymous class, consider whether that is the best option.</span></span> <span data-ttu-id="3a184-168">例如，如果想要创建一个临时对象来包含相关数据，并且不需要完整类可能包含的其他字段和方法，则匿名类型是一个不错的解决方案。</span><span class="sxs-lookup"><span data-stu-id="3a184-168">For example, if you want to create a temporary object to contain related data, and you have no need for other fields and methods that a complete class might contain, an anonymous type is a good solution.</span></span> <span data-ttu-id="3a184-169">如果需要为每个声明选择不同的属性，或者要更改属性的顺序，则匿名类型也是非常方便的。</span><span class="sxs-lookup"><span data-stu-id="3a184-169">Anonymous types are also convenient if you want a different selection of properties for each declaration, or if you want to change the order of the properties.</span></span> <span data-ttu-id="3a184-170">但是，如果你的项目包含多个具有相同属性的对象（按固定顺序），则可以通过将命名类型用于类构造函数来更轻松地声明它们。</span><span class="sxs-lookup"><span data-stu-id="3a184-170">However, if your project includes several objects that have the same properties, in a fixed order, you can declare them more easily by using a named type with a class constructor.</span></span> <span data-ttu-id="3a184-171">例如，使用适当的构造函数时，声明类的多个实例 `Product` 比声明匿名类型的多个实例更容易。</span><span class="sxs-lookup"><span data-stu-id="3a184-171">For example, with an appropriate constructor, it is easier to declare several instances of a `Product` class than it is to declare several instances of an anonymous type.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#9)]  
  
 <span data-ttu-id="3a184-172">命名类型的另一个优点是编译器可能会捕获属性名称的意外的误。</span><span class="sxs-lookup"><span data-stu-id="3a184-172">Another advantage of named types is that the compiler can catch an accidental mistyping of a property name.</span></span> <span data-ttu-id="3a184-173">在前面的示例中，、 `firstProd2` `secondProd2` 和 `thirdProd2` 旨在作为相同匿名类型的实例。</span><span class="sxs-lookup"><span data-stu-id="3a184-173">In the previous examples, `firstProd2`, `secondProd2`, and `thirdProd2` are intended to be instances of the same anonymous type.</span></span> <span data-ttu-id="3a184-174">但是，如果您意外声明为 `thirdProd2` 以下某种方法，其类型将不同于和的类型 `firstProd2` `secondProd2` 。</span><span class="sxs-lookup"><span data-stu-id="3a184-174">However, if you were to accidentally declare `thirdProd2` in one of the following ways, its type would be different from that of `firstProd2` and `secondProd2`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#10)]  
  
 <span data-ttu-id="3a184-175">更重要的是，对不适用于命名类型实例的匿名类型的使用存在一些限制。</span><span class="sxs-lookup"><span data-stu-id="3a184-175">More importantly, there are limitations on the use of anonymous types that do not apply to instances of named types.</span></span> <span data-ttu-id="3a184-176">`firstProd2`、 `secondProd2` 和 `thirdProd2` 是相同匿名类型的实例。</span><span class="sxs-lookup"><span data-stu-id="3a184-176">`firstProd2`, `secondProd2`, and `thirdProd2` are instances of the same anonymous type.</span></span> <span data-ttu-id="3a184-177">但是，共享匿名类型的名称不可用，因此不能出现在代码中需要类型名称的位置。</span><span class="sxs-lookup"><span data-stu-id="3a184-177">However, the name for the shared anonymous type is not available and cannot appear where a type name is expected in your code.</span></span> <span data-ttu-id="3a184-178">例如，匿名类型不能用于定义方法签名，也不能声明其他变量或字段，也不能用于任何类型声明。</span><span class="sxs-lookup"><span data-stu-id="3a184-178">For example, an anonymous type cannot be used to define a method signature, to declare another variable or field, or in any type declaration.</span></span> <span data-ttu-id="3a184-179">因此，当必须跨方法共享信息时，匿名类型不适用。</span><span class="sxs-lookup"><span data-stu-id="3a184-179">As a result, anonymous types are not appropriate when you have to share information across methods.</span></span>  
  
## <a name="an-anonymous-type-definition"></a><span data-ttu-id="3a184-180">匿名类型定义</span><span class="sxs-lookup"><span data-stu-id="3a184-180">An Anonymous Type Definition</span></span>  

 <span data-ttu-id="3a184-181">在响应匿名类型的实例的声明时，编译器会创建一个新的类定义，其中包含指定的属性。</span><span class="sxs-lookup"><span data-stu-id="3a184-181">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties.</span></span>  
  
 <span data-ttu-id="3a184-182">如果匿名类型至少包含一个键属性，则定义将重写继承自的三个成员 <xref:System.Object> ： <xref:System.Object.Equals%2A> 、 <xref:System.Object.GetHashCode%2A> 和 <xref:System.Object.ToString%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3a184-182">If the anonymous type contains at least one key property, the definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="3a184-183">为测试相等性和确定哈希代码值而生成的代码只考虑键属性。</span><span class="sxs-lookup"><span data-stu-id="3a184-183">The code produced for testing equality and determining the hash code value considers only the key properties.</span></span> <span data-ttu-id="3a184-184">如果匿名类型不包含键属性，则只 <xref:System.Object.ToString%2A> 会重写。</span><span class="sxs-lookup"><span data-stu-id="3a184-184">If the anonymous type contains no key properties, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="3a184-185">匿名类型的显式命名属性不能与这些生成的方法冲突。</span><span class="sxs-lookup"><span data-stu-id="3a184-185">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="3a184-186">也就是说，不能使用 `.Equals` 、 `.GetHashCode` 或 `.ToString` 对属性命名。</span><span class="sxs-lookup"><span data-stu-id="3a184-186">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>  
  
 <span data-ttu-id="3a184-187">至少具有一个键属性的匿名类型定义还实现 <xref:System.IEquatable%601?displayProperty=nameWithType> 接口，其中 `T` 是匿名类型的类型。</span><span class="sxs-lookup"><span data-stu-id="3a184-187">Anonymous type definitions that have at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>  
  
 <span data-ttu-id="3a184-188">有关编译器创建的代码和重写的方法的功能的详细信息，请参阅 [匿名类型定义](anonymous-type-definition.md)。</span><span class="sxs-lookup"><span data-stu-id="3a184-188">For more information about the code created by the compiler and the functionality of the overridden methods, see [Anonymous Type Definition](anonymous-type-definition.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a184-189">请参阅</span><span class="sxs-lookup"><span data-stu-id="3a184-189">See also</span></span>

- [<span data-ttu-id="3a184-190">对象初始值设定项：命名和匿名类型</span><span class="sxs-lookup"><span data-stu-id="3a184-190">Object Initializers: Named and Anonymous Types</span></span>](object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="3a184-191">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="3a184-191">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="3a184-192">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="3a184-192">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="3a184-193">如何：推断匿名类型声明中的属性名和类型</span><span class="sxs-lookup"><span data-stu-id="3a184-193">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [<span data-ttu-id="3a184-194">匿名类型定义</span><span class="sxs-lookup"><span data-stu-id="3a184-194">Anonymous Type Definition</span></span>](anonymous-type-definition.md)
- [<span data-ttu-id="3a184-195">Key</span><span class="sxs-lookup"><span data-stu-id="3a184-195">Key</span></span>](../../../language-reference/modifiers/key.md)
