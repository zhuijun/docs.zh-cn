---
title: 对象和集合初始值设定项 - C# 编程指南
description: 在调用构造函数后，C# 中的对象初始值设定项在创建时将值分配给对象的可访问字段或属性。
ms.date: 12/19/2018
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
ms.openlocfilehash: 81deed8a21bff10364524c3e0784c562d4e727e6
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864769"
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="0db1d-103">对象和集合初始值设定项（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="0db1d-103">Object and Collection Initializers (C# Programming Guide)</span></span>

<span data-ttu-id="0db1d-104">使用 C# 可以在单条语句中实例化对象或集合并执行成员分配。</span><span class="sxs-lookup"><span data-stu-id="0db1d-104">C# lets you instantiate an object or collection and perform member assignments in a single statement.</span></span>

## <a name="object-initializers"></a><span data-ttu-id="0db1d-105">对象初始值设定项</span><span class="sxs-lookup"><span data-stu-id="0db1d-105">Object initializers</span></span>

<span data-ttu-id="0db1d-106">使用对象初始值设定项，你可以在创建对象时向对象的任何可访问字段或属性分配值，而无需调用后跟赋值语句行的构造函数。</span><span class="sxs-lookup"><span data-stu-id="0db1d-106">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="0db1d-107">利用对象初始值设定项语法，你可为构造函数指定参数或忽略参数（以及括号语法）。</span><span class="sxs-lookup"><span data-stu-id="0db1d-107">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="0db1d-108">以下示例演示如何使用具有命名类型 `Cat` 的对象初始值设定项以及如何调用无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="0db1d-108">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the parameterless constructor.</span></span> <span data-ttu-id="0db1d-109">请注意，自动实现的属性在 `Cat` 类中的用法。</span><span class="sxs-lookup"><span data-stu-id="0db1d-109">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="0db1d-110">有关详细信息，请参阅[自动实现的属性](auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="0db1d-110">For more information, see [Auto-Implemented Properties](auto-implemented-properties.md).</span></span>  
  
[!code-csharp[ObjectInitializer1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#CatDeclaration)]  
[!code-csharp[ObjectInitializer1a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ObjectPropertyInitialization)]  

<span data-ttu-id="0db1d-111">对象初始值设定项语法允许你创建一个实例，然后将具有其分配属性的新建对象指定给赋值中的变量。</span><span class="sxs-lookup"><span data-stu-id="0db1d-111">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>

<span data-ttu-id="0db1d-112">从 C# 6 开始，除了分配字段和属性外，对象初始值设定项还可以设置索引器。</span><span class="sxs-lookup"><span data-stu-id="0db1d-112">Starting with C# 6, object initializers can set indexers, in addition to assigning fields and properties.</span></span> <span data-ttu-id="0db1d-113">请思考这个基本的 `Matrix` 类：</span><span class="sxs-lookup"><span data-stu-id="0db1d-113">Consider this basic `Matrix` class:</span></span>

[!code-csharp[ObjectInitializer2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixDeclaration)]  

<span data-ttu-id="0db1d-114">可以使用以下代码初始化标识矩阵：</span><span class="sxs-lookup"><span data-stu-id="0db1d-114">You could initialize the identity matrix with the following code:</span></span>

[!code-csharp[ObjectInitializer2a](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#MatrixInitialization)]  

<span data-ttu-id="0db1d-115">包含可访问资源库的任何可访问索引器都可以用作对象初始值设定项中的表达式之一，这与参数的数量或类型无关。</span><span class="sxs-lookup"><span data-stu-id="0db1d-115">Any accessible indexer that contains an accessible setter can be used as one of the expressions in an object initializer, regardless of the number or types of arguments.</span></span> <span data-ttu-id="0db1d-116">索引参数构成左侧赋值，而表达式右侧是值。</span><span class="sxs-lookup"><span data-stu-id="0db1d-116">The index arguments form the left side of the assignment, and the value is the right side of the expression.</span></span>  <span data-ttu-id="0db1d-117">例如，如果 `IndexersExample` 具有适当的索引器，则这些都是有效的：</span><span class="sxs-lookup"><span data-stu-id="0db1d-117">For example, these are all valid if `IndexersExample` has the appropriate indexers:</span></span>

```csharp
var thing = new IndexersExample {
    name = "object one",
    [1] = '1',
    [2] = '4',
    [3] = '9',
    Size = Math.PI,
    ['C',4] = "Middle C"
}
```

<span data-ttu-id="0db1d-118">对于要进行编译的前面的代码，`IndexersExample` 类型必须具有以下成员：</span><span class="sxs-lookup"><span data-stu-id="0db1d-118">For the preceding code to compile, the `IndexersExample` type must have the following members:</span></span>

```csharp
public string name;
public double Size { set { ... }; }
public char this[int i] { set { ... }; }
public string this[char c, int i] {  set { ... }; }
```

## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="0db1d-119">具有匿名类型的对象初始值设定项</span><span class="sxs-lookup"><span data-stu-id="0db1d-119">Object Initializers with anonymous types</span></span>

<span data-ttu-id="0db1d-120">尽管对象初始值设定项可用于任何上下文中，但它们在 LINQ 查询表达式中特别有用。</span><span class="sxs-lookup"><span data-stu-id="0db1d-120">Although object initializers can be used in any context, they are especially useful in LINQ query expressions.</span></span> <span data-ttu-id="0db1d-121">查询表达式常使用只能通过使用对象初始值设定项进行初始化的[匿名类型](./anonymous-types.md)，如下面的声明所示。</span><span class="sxs-lookup"><span data-stu-id="0db1d-121">Query expressions make frequent use of [anonymous types](./anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  

```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```

<span data-ttu-id="0db1d-122">利用匿名类型，LINQ 查询表达式中的 `select` 子句可以将原始序列的对象转换为其值和形状可能不同于原始序列的对象。</span><span class="sxs-lookup"><span data-stu-id="0db1d-122">Anonymous types enable the `select` clause in a LINQ query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="0db1d-123">如果你只想存储某个序列中每个对象的部分信息，则这很有用。</span><span class="sxs-lookup"><span data-stu-id="0db1d-123">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="0db1d-124">在下面的示例中，假定产品对象 (`p`) 包含很多字段和方法，而你只想创建包含产品名和单价的对象序列。</span><span class="sxs-lookup"><span data-stu-id="0db1d-124">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
[!code-csharp[ObjectInitializer3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#AnonymousUse)]  

<span data-ttu-id="0db1d-125">执行此查询时，`productInfos` 变量将包含一系列对象，这些对象可以在 `foreach` 语句中进行访问，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="0db1d-125">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  

```csharp
foreach(var p in productInfos){...}  
```

<span data-ttu-id="0db1d-126">新的匿名类型中的每个对象都具有两个公共属性，这两个属性接收与原始对象中的属性或字段相同的名称。</span><span class="sxs-lookup"><span data-stu-id="0db1d-126">Each object in the new anonymous type has two public properties that receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="0db1d-127">你还可在创建匿名类型时重命名字段；下面的示例将 `UnitPrice` 字段重命名为 `Price`。</span><span class="sxs-lookup"><span data-stu-id="0db1d-127">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  

```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```

## <a name="collection-initializers"></a><span data-ttu-id="0db1d-128">集合初始值设定项</span><span class="sxs-lookup"><span data-stu-id="0db1d-128">Collection initializers</span></span>

<span data-ttu-id="0db1d-129">在初始化实现 <xref:System.Collections.IEnumerable> 的集合类型和初始化使用适当的签名作为实例方法或扩展方法的 `Add` 时，集合初始值设定项允许指定一个或多个元素初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="0db1d-129">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="0db1d-130">元素初始值设定项可以是简单的值、表达式或对象初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="0db1d-130">The element initializers can be a simple value, an expression, or an object initializer.</span></span> <span data-ttu-id="0db1d-131">通过使用集合初始值设定项，无需指定多个调用；编译器将自动添加这些调用。</span><span class="sxs-lookup"><span data-stu-id="0db1d-131">By using a collection initializer, you do not have to specify multiple calls; the compiler adds the calls automatically.</span></span>  
  
<span data-ttu-id="0db1d-132">下面的示例演示了两个简单的集合初始值设定项：</span><span class="sxs-lookup"><span data-stu-id="0db1d-132">The following example shows two simple collection initializers:</span></span>  

```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```

<span data-ttu-id="0db1d-133">下面的集合初始值设定项使用对象初始值设定项来初始化上一个示例中定义的 `Cat` 类的对象。</span><span class="sxs-lookup"><span data-stu-id="0db1d-133">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="0db1d-134">请注意，各个对象初始值设定项分别括在大括号中且用逗号隔开。</span><span class="sxs-lookup"><span data-stu-id="0db1d-134">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
[!code-csharp[ListInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitializer)]  
  
<span data-ttu-id="0db1d-135">如果集合的 `Add` 方法允许，则可以将 [null](../../language-reference/keywords/null.md) 指定为集合初始值设定项中的一个元素。</span><span class="sxs-lookup"><span data-stu-id="0db1d-135">You can specify [null](../../language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
[!code-csharp[ListInitializerNull](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#ListInitialerWithNull)]  
  
 <span data-ttu-id="0db1d-136">如果集合支持读取/写入索引，可以指定索引元素。</span><span class="sxs-lookup"><span data-stu-id="0db1d-136">You can specify indexed elements if the collection supports read / write indexing.</span></span>
  
[!code-csharp[DictionaryInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryIndexerInitializer)]  

<span data-ttu-id="0db1d-137">前面的示例生成调用 <xref:System.Collections.Generic.Dictionary%602.Item(%600)> 以设置值的代码。</span><span class="sxs-lookup"><span data-stu-id="0db1d-137">The preceding sample generates code that calls the <xref:System.Collections.Generic.Dictionary%602.Item(%600)> to set the values.</span></span> <span data-ttu-id="0db1d-138">在 C# 6 之前，可以使用以下语法初始化字典和其他关联容器。</span><span class="sxs-lookup"><span data-stu-id="0db1d-138">Before C# 6, you could initialize dictionaries and other associative containers using the following syntax.</span></span> <span data-ttu-id="0db1d-139">请注意，它使用具有多个值的对象，而不是带括号和赋值的索引器语法：</span><span class="sxs-lookup"><span data-stu-id="0db1d-139">Notice that instead of indexer syntax, with parentheses and an assignment, it uses an object with multiple values:</span></span>

[!code-csharp[DictionaryAddInitializer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#DictionaryAddInitializer)]  

<span data-ttu-id="0db1d-140">此初始值设定项示例调用 <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)>，将这三个项添加到字典中。</span><span class="sxs-lookup"><span data-stu-id="0db1d-140">This initializer example calls <xref:System.Collections.Generic.Dictionary%602.Add(%600,%601)> to add the three items into the dictionary.</span></span> <span data-ttu-id="0db1d-141">由于编译器生成的方法调用不同，这两种初始化关联集合的不同方法的行为略有不同。</span><span class="sxs-lookup"><span data-stu-id="0db1d-141">These two different ways to initialize associative collections have slightly different behavior because of the method calls the compiler generates.</span></span> <span data-ttu-id="0db1d-142">这两种变量都适用于 `Dictionary` 类。</span><span class="sxs-lookup"><span data-stu-id="0db1d-142">Both variants work with the `Dictionary` class.</span></span> <span data-ttu-id="0db1d-143">其他类型根据它们的公共 API 可能只支持两者中的一种。</span><span class="sxs-lookup"><span data-stu-id="0db1d-143">Other types may only support one or the other based on their public API.</span></span>

## <a name="examples"></a><span data-ttu-id="0db1d-144">示例</span><span class="sxs-lookup"><span data-stu-id="0db1d-144">Examples</span></span>

<span data-ttu-id="0db1d-145">下例结合了对象和集合初始值设定项的概念。</span><span class="sxs-lookup"><span data-stu-id="0db1d-145">The following example combines the concepts of object and collection initializers.</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullExample)]  

<span data-ttu-id="0db1d-146">下面的示例展示了实现 <xref:System.Collections.IEnumerable> 且包含具有多个参数的 `Add` 方法的一个对象，它使用在列表中每项具有多个元素的集合初始值设定项，这些元素对应于 `Add` 方法的签名。</span><span class="sxs-lookup"><span data-stu-id="0db1d-146">The following example shows an object that implements <xref:System.Collections.IEnumerable> and contains an `Add` method with multiple parameters, It uses a collection initializer with multiple elements per item in the list that correspond to the signature of the `Add` method.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullListExample)]  

<span data-ttu-id="0db1d-147">`Add` 方法可使用 `params` 关键字来获取可变数量的自变量，如下例中所示。</span><span class="sxs-lookup"><span data-stu-id="0db1d-147">`Add` methods can use the `params` keyword to take a variable number of arguments, as shown in the following example.</span></span> <span data-ttu-id="0db1d-148">此示例还演示了索引器的自定义实现，以使用索引初始化集合。</span><span class="sxs-lookup"><span data-stu-id="0db1d-148">This example also demonstrates the custom implementation of an indexer to initialize a collection using indexes.</span></span>

[!code-csharp[InitializerListExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/BasicObjectInitializers.cs#FullDictionaryInitializer)]  

## <a name="see-also"></a><span data-ttu-id="0db1d-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="0db1d-149">See also</span></span>

- [<span data-ttu-id="0db1d-150">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="0db1d-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0db1d-151">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="0db1d-151">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="0db1d-152">匿名类型</span><span class="sxs-lookup"><span data-stu-id="0db1d-152">Anonymous Types</span></span>](anonymous-types.md)
