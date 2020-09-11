---
title: 属性
description: 了解 C# 属性，包括验证功能、计算值、迟缓计算及属性更改通知。
ms.technology: csharp-fundamentals
ms.date: 04/25/2018
ms.openlocfilehash: 28050a77e1f7b0ac148bba6112aa79ef4d46b710
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/02/2020
ms.locfileid: "89358903"
---
# <a name="properties"></a><span data-ttu-id="4c7d4-103">属性</span><span class="sxs-lookup"><span data-stu-id="4c7d4-103">Properties</span></span>

<span data-ttu-id="4c7d4-104">属性是 C# 中的一等公民。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-104">Properties are first class citizens in C#.</span></span> <span data-ttu-id="4c7d4-105">借助该语言所定义的语法，开发人员能够编写出准确表达其设计意图的代码。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-105">The language defines syntax that enables developers to write code that accurately expresses their design intent.</span></span>

<span data-ttu-id="4c7d4-106">访问属性时，其行为类似于字段。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-106">Properties behave like fields when they are accessed.</span></span>
<span data-ttu-id="4c7d4-107">但与字段不同的是，属性通过访问器实现；访问器用于定义访问属性或为属性赋值时执行的语句。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-107">However, unlike fields, properties are implemented with accessors that define the statements executed when a property is accessed or assigned.</span></span>

## <a name="property-syntax"></a><span data-ttu-id="4c7d4-108">属性语法</span><span class="sxs-lookup"><span data-stu-id="4c7d4-108">Property syntax</span></span>

<span data-ttu-id="4c7d4-109">属性语法是字段的自然延伸。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-109">The syntax for properties is a natural extension to fields.</span></span> <span data-ttu-id="4c7d4-110">字段定义存储位置：</span><span class="sxs-lookup"><span data-stu-id="4c7d4-110">A field defines a storage location:</span></span>

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

<span data-ttu-id="4c7d4-111">属性定义包含 `get` 和 `set` 访问器的声明，这两个访问器用于检索该属性的值以及对其赋值：</span><span class="sxs-lookup"><span data-stu-id="4c7d4-111">A property definition contains declarations for a `get` and `set` accessor that retrieves and assigns the value of that property:</span></span>

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

<span data-ttu-id="4c7d4-112">上述语法是*自动属性*语法。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-112">The syntax shown above is the *auto property* syntax.</span></span> <span data-ttu-id="4c7d4-113">编译器生成支持该属性的字段的存储位置。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-113">The compiler generates the storage location for the field that backs up the property.</span></span> <span data-ttu-id="4c7d4-114">编译器还实现 `get` 和 `set` 访问器的正文。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-114">The compiler also implements the body of the `get` and `set` accessors.</span></span>

<span data-ttu-id="4c7d4-115">有时，需要将属性初始化为其类型默认值以外的值。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-115">Sometimes, you need to initialize a property to a value other than the default for its type.</span></span>  <span data-ttu-id="4c7d4-116">C# 通过在属性的右括号后设置值达到此目的。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-116">C# enables that by setting a value after the closing brace for the property.</span></span> <span data-ttu-id="4c7d4-117">对于 `FirstName` 属性的的初始值，你可能更希望设置为空字符串而非 `null`。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-117">You may prefer the initial value for the `FirstName` property to be the empty string rather than `null`.</span></span> <span data-ttu-id="4c7d4-118">可按如下所示进行指定：</span><span class="sxs-lookup"><span data-stu-id="4c7d4-118">You would specify that as shown below:</span></span>

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

<span data-ttu-id="4c7d4-119">特定初始化对于只读属性最有用，本文后面部分将进行介绍。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-119">Specific initialization is most useful for read-only properties, as you'll see later in this article.</span></span>

<span data-ttu-id="4c7d4-120">你也可以自行定义存储，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4c7d4-120">You can also define the storage yourself, as shown below:</span></span>

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

<span data-ttu-id="4c7d4-121">属性实现是单个表达式时，可为 getter 或 setter 使用 expression-bodied 成员\*\*：</span><span class="sxs-lookup"><span data-stu-id="4c7d4-121">When a property implementation is a single expression, you can use *expression-bodied members* for the getter or setter:</span></span>

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

<span data-ttu-id="4c7d4-122">在本文中，将在所有适用之处使用此简化的语法。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-122">This simplified syntax will be used where applicable throughout this article.</span></span>

<span data-ttu-id="4c7d4-123">上述属性定义是读-写属性。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-123">The property definition shown above is a read-write property.</span></span> <span data-ttu-id="4c7d4-124">注意 set 访问器中的关键字 `value`。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-124">Notice the keyword `value` in the set accessor.</span></span> <span data-ttu-id="4c7d4-125">`set` 访问器始终具有一个名为 `value` 的参数。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-125">The `set` accessor always has a single parameter named `value`.</span></span> <span data-ttu-id="4c7d4-126">`get` 访问器必须返回一个值，该值可转换为该属性的类型（本例中为 `string`）。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-126">The `get` accessor must return a value that is convertible to the type of the property (`string` in this example).</span></span>

<span data-ttu-id="4c7d4-127">这就是该语法的基础知识。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-127">That's the basics of the syntax.</span></span> <span data-ttu-id="4c7d4-128">有许多不同的语法变体，支持着各种不同的设计习惯。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-128">There are many different variations that support a variety of different design idioms.</span></span> <span data-ttu-id="4c7d4-129">接下来我们将了解这些变体，以及每个变体的语法选项。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-129">Let's explore, and learn the syntax options for each.</span></span>

## <a name="scenarios"></a><span data-ttu-id="4c7d4-130">方案</span><span class="sxs-lookup"><span data-stu-id="4c7d4-130">Scenarios</span></span>

<span data-ttu-id="4c7d4-131">上述示例介绍了属性定义中最简单的一种情况：不进行验证的读-写属性。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-131">The examples above showed one of the simplest cases of property definition: a read-write property with no validation.</span></span> <span data-ttu-id="4c7d4-132">通过在 `get` 和 `set` 访问器中编写所需的代码，可以创建多种不同的方案。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-132">By writing the code you want in the `get` and `set` accessors, you can create many different scenarios.</span></span>

### <a name="validation"></a><span data-ttu-id="4c7d4-133">验证</span><span class="sxs-lookup"><span data-stu-id="4c7d4-133">Validation</span></span>

<span data-ttu-id="4c7d4-134">可以在 `set` 访问器中编写代码，确保由某个属性表示的值始终有效。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-134">You can write code in the `set` accessor to ensure that the values represented by a property are always valid.</span></span> <span data-ttu-id="4c7d4-135">例如，假设 `Person` 类的一个规则是姓名不得为空白或空白符。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-135">For example, suppose one rule for the `Person` class is that the name cannot be blank or white space.</span></span> <span data-ttu-id="4c7d4-136">可按如下方式编写：</span><span class="sxs-lookup"><span data-stu-id="4c7d4-136">You would write that as follows:</span></span>

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

<span data-ttu-id="4c7d4-137">可通过将 `throw` 表达式用作属性资源库验证的一部分来简化前面的示例：</span><span class="sxs-lookup"><span data-stu-id="4c7d4-137">The preceding example can be simplified by using a `throw` expression as part of the property setter validation:</span></span>

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

<span data-ttu-id="4c7d4-138">上面的示例强制执行名字不得为空白或空白符的规则。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-138">The example above enforces the rule that the first name must not be blank or white space.</span></span> <span data-ttu-id="4c7d4-139">如果开发人员编写</span><span class="sxs-lookup"><span data-stu-id="4c7d4-139">If a developer writes</span></span>

```csharp
hero.FirstName = "";
```

<span data-ttu-id="4c7d4-140">该赋值会引发 `ArgumentException`。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-140">That assignment throws an `ArgumentException`.</span></span> <span data-ttu-id="4c7d4-141">由于属性 set 访问器必须具有 void 返回类型，因此将通过引发异常来报告 set 访问器中的错误。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-141">Because a property set accessor must have a void return type, you report errors in the set accessor by throwing an exception.</span></span>

<span data-ttu-id="4c7d4-142">你可以根据自己的情况随意扩展此语法。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-142">You can extend this same syntax to anything needed in your scenario.</span></span> <span data-ttu-id="4c7d4-143">可以检查不同属性之间的关系，或根据任何外部条件进行验证。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-143">You can check the relationships between different properties, or validate against any external conditions.</span></span> <span data-ttu-id="4c7d4-144">任何有效的 C# 语句在属性访问器中都是有效的。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-144">Any valid C# statements are valid in a property accessor.</span></span>

### <a name="read-only"></a><span data-ttu-id="4c7d4-145">只读</span><span class="sxs-lookup"><span data-stu-id="4c7d4-145">Read-only</span></span>

<span data-ttu-id="4c7d4-146">到目前为止，你了解的所有属性定义都是具有公共访问器的读/写属性。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-146">Up to this point, all the property definitions you have seen are read/write properties with public accessors.</span></span> <span data-ttu-id="4c7d4-147">但这不是属性唯一有效的可访问性。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-147">That's not the only valid accessibility for properties.</span></span>
<span data-ttu-id="4c7d4-148">你可以创建只读属性，或者对 set 和 get 访问器提供不同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-148">You can create read-only properties, or give different accessibility to the set and get accessors.</span></span> <span data-ttu-id="4c7d4-149">假设 `Person` 类只能从该类的其他方法中启用 `FirstName` 属性值更改。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-149">Suppose that your `Person` class should only enable changing the value of the `FirstName` property from other methods in that class.</span></span> <span data-ttu-id="4c7d4-150">可以为 set 访问器提供 `private` 可访问性，而不是 `public` 可访问性：</span><span class="sxs-lookup"><span data-stu-id="4c7d4-150">You could give the set accessor `private` accessibility instead of `public`:</span></span>

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

<span data-ttu-id="4c7d4-151">现在，可以从任意代码访问 `FirstName` 属性，但只能从 `Person` 类中的其他代码对其赋值。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-151">Now, the `FirstName` property can be accessed from any code, but it can only be assigned from other code in the `Person` class.</span></span>

<span data-ttu-id="4c7d4-152">可以向 set 和 get 访问器添加任何严格访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-152">You can add any restrictive access modifier to either the set or get accessors.</span></span> <span data-ttu-id="4c7d4-153">在单个访问器上放置的任何访问修饰符都必须比属性定义上的访问修饰符提供更严格的限制。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-153">Any access modifier you place on the individual accessor must be more limited than the access modifier on the property definition.</span></span> <span data-ttu-id="4c7d4-154">上述做法是合法的，因为 `FirstName` 属性为 `public`，但 set 访问器为 `private`。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-154">The above is legal because the `FirstName` property is `public`, but the set accessor is `private`.</span></span> <span data-ttu-id="4c7d4-155">不能声明具有 `public` 访问器的 `private` 属性。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-155">You could not declare a `private` property with a `public` accessor.</span></span> <span data-ttu-id="4c7d4-156">属性声明还可以声明为 `protected`、`internal`、`protected internal`，甚至 `private`。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-156">Property declarations can also be declared `protected`, `internal`, `protected internal`, or, even `private`.</span></span>

<span data-ttu-id="4c7d4-157">在 `get` 访问器上放置限制性更强的修饰符也是合法的。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-157">It is also legal to place the more restrictive modifier on the `get` accessor.</span></span> <span data-ttu-id="4c7d4-158">例如，可以有一个 `public` 属性，但将 `get` 访问器限制为 `private`。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-158">For example, you could have a `public` property, but restrict the `get` accessor to `private`.</span></span> <span data-ttu-id="4c7d4-159">不过实际情况下很少这么做。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-159">That scenario is rarely done in practice.</span></span>

<span data-ttu-id="4c7d4-160">还可以限制对属性的修改，以便只能在构造函数或属性初始化表达式中设置属性。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-160">You can also restrict modifications to a property so that it can only be set in a constructor or a property initializer.</span></span> <span data-ttu-id="4c7d4-161">可按照这种方式修改 `Person` 类，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4c7d4-161">You can modify the `Person` class so as follows:</span></span>

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

<span data-ttu-id="4c7d4-162">此功能通常用于初始化作为只读属性公开的集合：</span><span class="sxs-lookup"><span data-stu-id="4c7d4-162">This feature is most commonly used for initializing collections that are exposed as read-only properties:</span></span>

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a><span data-ttu-id="4c7d4-163">计算属性</span><span class="sxs-lookup"><span data-stu-id="4c7d4-163">Computed properties</span></span>

<span data-ttu-id="4c7d4-164">属性无需只返回某个成员字段的值。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-164">A property does not need to simply return the value of a member field.</span></span> <span data-ttu-id="4c7d4-165">可以创建返回计算值的属性。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-165">You can create properties that return a computed value.</span></span> <span data-ttu-id="4c7d4-166">让我们展开 `Person` 对象，返回通过串联名字和姓氏计算得出的全名：</span><span class="sxs-lookup"><span data-stu-id="4c7d4-166">Let's expand the `Person` object to return the full name, computed by concatenating the first and last names:</span></span>

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

<span data-ttu-id="4c7d4-167">上面的示例使用[字符串内插](./language-reference/tokens/interpolated.md)功能来创建全名的格式化字符串。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-167">The example above uses the [string interpolation](./language-reference/tokens/interpolated.md) feature to create the formatted string for the full name.</span></span>

<span data-ttu-id="4c7d4-168">也可以使用 expression-bodied 成员，以更简洁的方式来创建 `FullName` 计算属性\*\*：</span><span class="sxs-lookup"><span data-stu-id="4c7d4-168">You can also use an *expression-bodied member*, which provides a more succinct way to create the computed `FullName` property:</span></span>

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

<span data-ttu-id="4c7d4-169">expression-bodied 成员使用 lambda 表达式语法来定义包含单个表达式的方法\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-169">*Expression-bodied members* use the *lambda expression* syntax to define methods that contain a single expression.</span></span> <span data-ttu-id="4c7d4-170">在这里，该表达式返回 person 对象的全名。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-170">Here, that expression returns the full name for the person object.</span></span>

### <a name="cached-evaluated-properties"></a><span data-ttu-id="4c7d4-171">缓存的计算属性</span><span class="sxs-lookup"><span data-stu-id="4c7d4-171">Cached evaluated properties</span></span>

<span data-ttu-id="4c7d4-172">可以将计算属性和存储的概念混合起来，创建“缓存的计算属性”\*\*。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-172">You can mix the concept of a computed property with storage and create a *cached evaluated property*.</span></span>  <span data-ttu-id="4c7d4-173">例如，可以更新 `FullName` 属性，以便仅在第一次访问该属性时进行字符串格式设置：</span><span class="sxs-lookup"><span data-stu-id="4c7d4-173">For example, you could update the `FullName` property so that the string formatting only happened the first time it was accessed:</span></span>

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

<span data-ttu-id="4c7d4-174">不过，上面的代码含有 bug。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-174">The above code contains a bug though.</span></span> <span data-ttu-id="4c7d4-175">如果代码更新 `FirstName` 或 `LastName` 属性的值，那么，以前计算的 `fullName` 字段将无效。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-175">If code updates the value of either the `FirstName` or `LastName` property, the previously evaluated `fullName` field is invalid.</span></span> <span data-ttu-id="4c7d4-176">修改 `FirstName` 和 `LastName` 属性的 `set` 访问器，以便重新计算 `fullName` 字段：</span><span class="sxs-lookup"><span data-stu-id="4c7d4-176">You modify the `set` accessors of the `FirstName` and `LastName` property so that the `fullName` field is calculated again:</span></span>

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

<span data-ttu-id="4c7d4-177">此最终版本仅在必要时计算 `FullName` 属性。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-177">This final version evaluates the `FullName` property only when needed.</span></span>
<span data-ttu-id="4c7d4-178">如果以前计算的版本有效，则使用它。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-178">If the previously calculated version is valid, it's used.</span></span> <span data-ttu-id="4c7d4-179">如果另一个状态更改使以前计算的版本失效，则重新计算。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-179">If another state change invalidates the previously calculated version, it will be recalculated.</span></span> <span data-ttu-id="4c7d4-180">使用此类的开发人员无需了解实现的细枝末节。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-180">Developers that use this class do not need to know the details of the implementation.</span></span> <span data-ttu-id="4c7d4-181">这些内部更改不会影响 Person 对象的使用。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-181">None of these internal changes affect the use of the Person object.</span></span> <span data-ttu-id="4c7d4-182">这是使用属性公开对象的数据成员的关键原因。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-182">That's the key reason for using Properties to expose data members of an object.</span></span>

### <a name="attaching-attributes-to-auto-implemented-properties"></a><span data-ttu-id="4c7d4-183">将特性附加到自动实现的属性</span><span class="sxs-lookup"><span data-stu-id="4c7d4-183">Attaching attributes to auto-implemented properties</span></span>

<span data-ttu-id="4c7d4-184">从 C# 7.3 开始，可在自动实现的属性中将字段特性附加到编译器生成的支持字段。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-184">Beginning with C# 7.3, field attributes can be attached to the compiler generated backing field in auto-implemented properties.</span></span> <span data-ttu-id="4c7d4-185">例如，可考虑添加唯一整数 `Person` 属性的 `Id` 类的修订。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-185">For example, consider a revision to the `Person` class that adds a unique integer `Id` property.</span></span>
<span data-ttu-id="4c7d4-186">使用自动实现的属性编写 `Id` 属性，但是该设计不需要保留 `Id` 属性。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-186">You write the`Id` property using an auto-implemented property, but your design does not call for persisting the `Id` property.</span></span> <span data-ttu-id="4c7d4-187"><xref:System.NonSerializedAttribute> 只能附加到字段，不能附加到属性。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-187">The <xref:System.NonSerializedAttribute> can only be attached to fields, not properties.</span></span> <span data-ttu-id="4c7d4-188">可使用特性上的 `field:` 说明符将 <xref:System.NonSerializedAttribute> 附加到 `Id` 属性的支持字段，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="4c7d4-188">You can attach the <xref:System.NonSerializedAttribute> to the backing field for the `Id` property by using the `field:` specifier on the attribute, as shown in the following example:</span></span>

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

<span data-ttu-id="4c7d4-189">该技术适用于附加到自动实现的属性上的支持字段的所有特性。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-189">This technique works for any attribute you attach to the backing field on the auto-implemented property.</span></span>

### <a name="implementing-inotifypropertychanged"></a><span data-ttu-id="4c7d4-190">实现 INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="4c7d4-190">Implementing INotifyPropertyChanged</span></span>

<span data-ttu-id="4c7d4-191">需要在属性访问器中编写代码的最后一种情形是为了支持 <xref:System.ComponentModel.INotifyPropertyChanged> 接口，该接口用于通知数据绑定客户端值已更改。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-191">A final scenario where you need to write code in a property accessor is to support the <xref:System.ComponentModel.INotifyPropertyChanged> interface used to notify data binding clients that a value has changed.</span></span> <span data-ttu-id="4c7d4-192">当属性值发生更改时，该对象引发 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> 事件来指示更改。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-192">When the value of a property changes, the object raises the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> event to indicate the change.</span></span> <span data-ttu-id="4c7d4-193">数据绑定库则基于该更改来更新显示元素。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-193">The data binding libraries, in turn, update display elements based on that change.</span></span> <span data-ttu-id="4c7d4-194">下面的代码演示如何为此 person 类的 `FirstName` 属性实现 `INotifyPropertyChanged`。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-194">The code below shows how you would implement `INotifyPropertyChanged` for the `FirstName` property of this person class.</span></span>

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

<span data-ttu-id="4c7d4-195">`?.` 运算符称作 *null 条件运算符*。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-195">The `?.` operator is called the *null conditional operator*.</span></span> <span data-ttu-id="4c7d4-196">它在计算运算符右侧之前会检查是否存在空引用。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-196">It checks for a null reference before evaluating the right side of the operator.</span></span> <span data-ttu-id="4c7d4-197">最终结果为：如果 `PropertyChanged` 事件没有订阅者，则不执行用于引发该事件的代码。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-197">The end result is that if there are no subscribers to the `PropertyChanged` event, the code to raise the event doesn't execute.</span></span> <span data-ttu-id="4c7d4-198">在这种情况下，如果不执行此检查，则会引发 `NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-198">It would throw a `NullReferenceException` without this check in that case.</span></span> <span data-ttu-id="4c7d4-199">有关详细信息，请参阅 [`events`](events-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-199">For more information, see [`events`](events-overview.md).</span></span> <span data-ttu-id="4c7d4-200">此示例还使用新的 `nameof` 运算符将属性名称符号转换为其文本表示形式。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-200">This example also uses the new `nameof` operator to convert from the property name symbol to its text representation.</span></span>
<span data-ttu-id="4c7d4-201">使用 `nameof` 可以减少输错属性名称这样的错误。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-201">Using `nameof` can reduce errors where you have mistyped the name of the property.</span></span>

<span data-ttu-id="4c7d4-202">再次说明，实现 <xref:System.ComponentModel.INotifyPropertyChanged> 是可以在访问器中编写代码以支持所需方案的情况的示例。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-202">Again, implementing <xref:System.ComponentModel.INotifyPropertyChanged> is an example of a case where you can write code in your accessors to support the scenarios you need.</span></span>

## <a name="summing-up"></a><span data-ttu-id="4c7d4-203">总结</span><span class="sxs-lookup"><span data-stu-id="4c7d4-203">Summing up</span></span>

<span data-ttu-id="4c7d4-204">属性是类或对象中的一种智能字段形式。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-204">Properties are a form of smart fields in a class or object.</span></span> <span data-ttu-id="4c7d4-205">从对象外部，它们看起来像对象中的字段。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-205">From outside the object, they appear like fields in the object.</span></span> <span data-ttu-id="4c7d4-206">但是，属性可以通过丰富的 C# 功能来实现。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-206">However, properties can be implemented using the full palette of C# functionality.</span></span>
<span data-ttu-id="4c7d4-207">你可以提供验证、不同的可访问性、迟缓计算或方案所需的任何要求。</span><span class="sxs-lookup"><span data-stu-id="4c7d4-207">You can provide validation, different accessibility, lazy evaluation, or any requirements your scenarios need.</span></span>
