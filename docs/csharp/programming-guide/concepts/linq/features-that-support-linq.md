---
title: 支持 LINQ 的 C# 功能
description: 了解要用于 LINQ 查询和其他上下文中的 C# 功能。 C# 3.0 中引入了这些语言构造。
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: f72b82180d794086dcea9f11a7a057dc26ab0b26
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105428"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="a3416-104">支持 LINQ 的 C# 功能</span><span class="sxs-lookup"><span data-stu-id="a3416-104">C# Features That Support LINQ</span></span>

<span data-ttu-id="a3416-105">下一节介绍 C# 3.0 中引入的新语言构造。</span><span class="sxs-lookup"><span data-stu-id="a3416-105">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="a3416-106">虽然这些新功能在一定程度上都用于 LINQ 查询，但并不限于 LINQ，如果认为有用，在任何情况下都可以使用这些新功能。</span><span class="sxs-lookup"><span data-stu-id="a3416-106">Although these new features are all used to a degree with LINQ queries, they are not limited to LINQ and can be used in any context where you find them useful.</span></span>

## <a name="query-expressions"></a><span data-ttu-id="a3416-107">查询表达式</span><span class="sxs-lookup"><span data-stu-id="a3416-107">Query Expressions</span></span>

<span data-ttu-id="a3416-108">查询表达式使用类似于 SQL 或 XQuery 的声明性语法来查询 IEnumerable 集合。</span><span class="sxs-lookup"><span data-stu-id="a3416-108">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="a3416-109">在编译时，查询语法转换为对 LINQ 提供程序的标准查询运算符扩展方法实现的方法调用。</span><span class="sxs-lookup"><span data-stu-id="a3416-109">At compile time query syntax is converted to method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="a3416-110">应用程序通过使用 `using` 指令指定适当的命名空间来控制范围内的标准查询运算符。</span><span class="sxs-lookup"><span data-stu-id="a3416-110">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="a3416-111">下面的查询表达式获取一个字符串数组，按字符串中的第一个字符对字符串进行分组，然后对各组进行排序。</span><span class="sxs-lookup"><span data-stu-id="a3416-111">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

<span data-ttu-id="a3416-112">有关详细信息，请参阅 [LINQ 查询表达式](../../../linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a3416-112">For more information, see [LINQ Query Expressions](../../../linq/index.md).</span></span>

## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="a3416-113">隐式类型化变量 (var)</span><span class="sxs-lookup"><span data-stu-id="a3416-113">Implicitly Typed Variables (var)</span></span>

<span data-ttu-id="a3416-114">可以使用 [var](../../../language-reference/keywords/var.md) 修饰符来指示编译器推断并分配类型，而不必在声明并初始化变量时显式指定类型，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a3416-114">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

<span data-ttu-id="a3416-115">声明为 `var` 的变量与显式指定其类型的变量一样都是强类型。</span><span class="sxs-lookup"><span data-stu-id="a3416-115">Variables declared as `var` are just as strongly typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="a3416-116">通过使用 `var`，可以创建匿名类型，但它只能用于本地变量。</span><span class="sxs-lookup"><span data-stu-id="a3416-116">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="a3416-117">也可以使用隐式类型声明数组。</span><span class="sxs-lookup"><span data-stu-id="a3416-117">Arrays can also be declared with implicit typing.</span></span>

<span data-ttu-id="a3416-118">有关详细信息，请参阅[隐式类型局部变量](../../classes-and-structs/implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="a3416-118">For more information, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

## <a name="object-and-collection-initializers"></a><span data-ttu-id="a3416-119">对象和集合初始值设定项</span><span class="sxs-lookup"><span data-stu-id="a3416-119">Object and Collection Initializers</span></span>

<span data-ttu-id="a3416-120">通过对象和集合初始值设定项，初始化对象时无需为对象显式调用构造函数。</span><span class="sxs-lookup"><span data-stu-id="a3416-120">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="a3416-121">初始值设定项通常用在将源数据投影到新数据类型的查询表达式中。</span><span class="sxs-lookup"><span data-stu-id="a3416-121">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="a3416-122">假定一个类名为 `Customer`，具有公共 `Name` 和 `Phone` 属性，可以按下列代码中所示使用对象初始值设定项：</span><span class="sxs-lookup"><span data-stu-id="a3416-122">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

<span data-ttu-id="a3416-123">继续我们的 `Customer` 类，假设有一个名为 `IncomingOrders` 的数据源，并且每个订单具有一个较大的 `OrderSize`，我们希望基于该订单创建新的 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="a3416-123">Continuing with our `Customer` class, assume that there is a data source called `IncomingOrders`, and that for each order with a large `OrderSize`, we would like to create a new `Customer` based off of that order.</span></span> <span data-ttu-id="a3416-124">可以在此数据源上执行 LINQ 查询，并使用对象初始化来填充集合：</span><span class="sxs-lookup"><span data-stu-id="a3416-124">A LINQ query can be executed on this data source and use object initialization to fill a collection:</span></span>

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

<span data-ttu-id="a3416-125">数据源可能具有比 `Customer` 类更多的属性，例如 `OrderSize`，但执行对象初始化后，从查询返回的数据被定型为所需的数据类型；我们选择与我们的类相关的数据。</span><span class="sxs-lookup"><span data-stu-id="a3416-125">The data source may have more properties lying under the hood than the `Customer` class such as `OrderSize`, but with object initialization, the data returned from the query is molded into the desired data type; we choose the data that is relevant to our class.</span></span> <span data-ttu-id="a3416-126">因此，我们现在有填充了我们想要的多个新 `Customer` 的 `IEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="a3416-126">As a result, we now have an `IEnumerable` filled with the new `Customer`s we wanted.</span></span> <span data-ttu-id="a3416-127">上述代码也可以使用 LINQ 的方法语法编写：</span><span class="sxs-lookup"><span data-stu-id="a3416-127">The above can also be written in LINQ's method syntax:</span></span>

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

<span data-ttu-id="a3416-128">有关详情，请参阅：</span><span class="sxs-lookup"><span data-stu-id="a3416-128">For more information, see:</span></span>

- [<span data-ttu-id="a3416-129">对象和集合初始值设定项</span><span class="sxs-lookup"><span data-stu-id="a3416-129">Object and Collection Initializers</span></span>](../../classes-and-structs/object-and-collection-initializers.md)

- [<span data-ttu-id="a3416-130">标准查询运算符的查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="a3416-130">Query Expression Syntax for Standard Query Operators</span></span>](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a><span data-ttu-id="a3416-131">匿名类型</span><span class="sxs-lookup"><span data-stu-id="a3416-131">Anonymous Types</span></span>

<span data-ttu-id="a3416-132">匿名类型由编译器构造，且类型名称只可用于编译器。</span><span class="sxs-lookup"><span data-stu-id="a3416-132">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="a3416-133">匿名类型提供一种在查询结果中对一组属性临时分组的简便方法，无需定义单独的命名类型。</span><span class="sxs-lookup"><span data-stu-id="a3416-133">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="a3416-134">使用新的表达式和对象初始值设定项初始化匿名类型，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a3416-134">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

<span data-ttu-id="a3416-135">有关详细信息，请参阅[匿名类型](../../classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a3416-135">For more information, see [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>

## <a name="extension-methods"></a><span data-ttu-id="a3416-136">扩展方法</span><span class="sxs-lookup"><span data-stu-id="a3416-136">Extension Methods</span></span>

<span data-ttu-id="a3416-137">扩展方法是一种可与类型关联的静态方法，因此可以像实例方法那样对类型调用它。</span><span class="sxs-lookup"><span data-stu-id="a3416-137">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="a3416-138">实际上，利用此功能，可以将新方法“添加”到现有类型，而不会实际修改它们。</span><span class="sxs-lookup"><span data-stu-id="a3416-138">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="a3416-139">标准查询运算符是一组扩展方法，它们为实现 <xref:System.Collections.Generic.IEnumerable%601> 的任何类型提供 LINQ 查询功能。</span><span class="sxs-lookup"><span data-stu-id="a3416-139">The standard query operators are a set of extension methods that provide LINQ query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

<span data-ttu-id="a3416-140">有关详细信息，请参阅[扩展方法](../../classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="a3416-140">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="a3416-141">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="a3416-141">Lambda Expressions</span></span>

<span data-ttu-id="a3416-142">Lambda 表达式是一种内联函数，该函数使用 => 运算符将输入参数与函数体分离，并且可以在编译时转换为委托或表达式树。</span><span class="sxs-lookup"><span data-stu-id="a3416-142">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="a3416-143">在 LINQ 编程中，在对标准查询运算符进行直接方法调用时，会遇到 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="a3416-143">In LINQ programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>

<span data-ttu-id="a3416-144">有关详细信息，请参见:</span><span class="sxs-lookup"><span data-stu-id="a3416-144">For more information, see:</span></span>

- [<span data-ttu-id="a3416-145">匿名函数</span><span class="sxs-lookup"><span data-stu-id="a3416-145">Anonymous Functions</span></span>](../../statements-expressions-operators/anonymous-functions.md)

- [<span data-ttu-id="a3416-146">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="a3416-146">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)

- [<span data-ttu-id="a3416-147">表达式树 (C#)</span><span class="sxs-lookup"><span data-stu-id="a3416-147">Expression Trees (C#)</span></span>](../expression-trees/index.md)

## <a name="see-also"></a><span data-ttu-id="a3416-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="a3416-148">See also</span></span>

- [<span data-ttu-id="a3416-149">语言集成查询 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a3416-149">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
