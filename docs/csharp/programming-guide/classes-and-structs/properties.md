---
title: 属性 - C# 编程指南
description: C# 中的属性是一种成员，它使用访问器方法来读、写或计算私有字段的值，就像它是公共数据成员一样。
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: 231e8e6a11f2655ccdea5489f054910a1ecf2586
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863937"
---
# <a name="properties-c-programming-guide"></a><span data-ttu-id="9ed33-103">属性（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="9ed33-103">Properties (C# Programming Guide)</span></span>

<span data-ttu-id="9ed33-104">属性是一种成员，它提供灵活的机制来读取、写入或计算私有字段的值。</span><span class="sxs-lookup"><span data-stu-id="9ed33-104">A property is a member that provides a flexible mechanism to read, write, or compute the value of a private field.</span></span> <span data-ttu-id="9ed33-105">属性可用作公共数据成员，但它们实际上是称为*访问器*的特殊方法。</span><span class="sxs-lookup"><span data-stu-id="9ed33-105">Properties can be used as if they are public data members, but they are actually special methods called *accessors*.</span></span> <span data-ttu-id="9ed33-106">这使得可以轻松访问数据，还有助于提高方法的安全性和灵活性。</span><span class="sxs-lookup"><span data-stu-id="9ed33-106">This enables data to be accessed easily and still helps promote the safety and flexibility of methods.</span></span>  

## <a name="properties-overview"></a><span data-ttu-id="9ed33-107">属性概述</span><span class="sxs-lookup"><span data-stu-id="9ed33-107">Properties overview</span></span>  
  
- <span data-ttu-id="9ed33-108">属性允许类公开获取和设置值的公共方法，而隐藏实现或验证代码。</span><span class="sxs-lookup"><span data-stu-id="9ed33-108">Properties enable a class to expose a public way of getting and setting values, while hiding implementation or verification code.</span></span>  
  
- <span data-ttu-id="9ed33-109">[get](../../language-reference/keywords/get.md) 属性访问器用于返回属性值，而 [set](../../language-reference/keywords/set.md) 属性访问器用于分配新值。</span><span class="sxs-lookup"><span data-stu-id="9ed33-109">A [get](../../language-reference/keywords/get.md) property accessor is used to return the property value, and a [set](../../language-reference/keywords/set.md) property accessor is used to assign a new value.</span></span> <span data-ttu-id="9ed33-110">这些访问器可以具有不同的访问级别。</span><span class="sxs-lookup"><span data-stu-id="9ed33-110">These accessors can have different access levels.</span></span> <span data-ttu-id="9ed33-111">有关详细信息，请参阅[限制访问器可访问性](./restricting-accessor-accessibility.md)。</span><span class="sxs-lookup"><span data-stu-id="9ed33-111">For more information, see [Restricting Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
- <span data-ttu-id="9ed33-112">[value](../../language-reference/keywords/value.md) 关键字用于定义由 `set` 访问器分配的值。</span><span class="sxs-lookup"><span data-stu-id="9ed33-112">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` accessor.</span></span>  
- <span data-ttu-id="9ed33-113">属性可以是*读-写*属性（既有 `get` 访问器又有 `set` 访问器）、*只读*属性（有 `get` 访问器，但没有 `set` 访问器）或*只写*访问器（有 `set` 访问器，但没有 `get` 访问器）。</span><span class="sxs-lookup"><span data-stu-id="9ed33-113">Properties can be *read-write* (they have both a `get` and a `set` accessor), *read-only* (they have a `get` accessor but no `set` accessor), or *write-only* (they have a `set` accessor, but no `get` accessor).</span></span> <span data-ttu-id="9ed33-114">只写属性很少出现，常用于限制对敏感数据的访问。</span><span class="sxs-lookup"><span data-stu-id="9ed33-114">Write-only properties are rare and are most commonly used to restrict access to sensitive data.</span></span>

- <span data-ttu-id="9ed33-115">不需要自定义访问器代码的简单属性可以作为表达式主体定义或[自动实现的属性](./auto-implemented-properties.md)来实现。</span><span class="sxs-lookup"><span data-stu-id="9ed33-115">Simple properties that require no custom accessor code can be implemented either as expression body definitions or as [auto-implemented properties](./auto-implemented-properties.md).</span></span>

## <a name="properties-with-backing-fields"></a><span data-ttu-id="9ed33-116">具有支持字段的属性</span><span class="sxs-lookup"><span data-stu-id="9ed33-116">Properties with backing fields</span></span>

<span data-ttu-id="9ed33-117">有一个实现属性的基本模式，该模式使用私有支持字段来设置和检索属性值。</span><span class="sxs-lookup"><span data-stu-id="9ed33-117">One basic pattern for implementing a property involves using a private backing field for setting and retrieving the property value.</span></span> <span data-ttu-id="9ed33-118">`get` 访问器返回私有字段的值，`set` 访问器在向私有字段赋值之前可能会执行一些数据验证。</span><span class="sxs-lookup"><span data-stu-id="9ed33-118">The `get` accessor returns the value of the private field, and the `set` accessor may perform some data validation before assigning a value to the private field.</span></span> <span data-ttu-id="9ed33-119">这两个访问器还可以在存储或返回数据之前对其执行某些转换或计算。</span><span class="sxs-lookup"><span data-stu-id="9ed33-119">Both accessors may also perform some conversion or computation on the data before it is stored or returned.</span></span>

<span data-ttu-id="9ed33-120">下面的示例阐释了此模式。</span><span class="sxs-lookup"><span data-stu-id="9ed33-120">The following example illustrates this pattern.</span></span> <span data-ttu-id="9ed33-121">在此示例中，`TimePeriod` 类表示时间间隔。</span><span class="sxs-lookup"><span data-stu-id="9ed33-121">In this example, the `TimePeriod` class represents an interval of time.</span></span> <span data-ttu-id="9ed33-122">在内部，该类将时间间隔以秒为单位存储在名为 `_seconds` 的私有字段中。</span><span class="sxs-lookup"><span data-stu-id="9ed33-122">Internally, the class stores the time interval in seconds in a private field named `_seconds`.</span></span> <span data-ttu-id="9ed33-123">名为 `Hours` 的读-写属性允许客户以小时为单位指定时间间隔。</span><span class="sxs-lookup"><span data-stu-id="9ed33-123">A read-write property named `Hours` allows the customer to specify the time interval in hours.</span></span> <span data-ttu-id="9ed33-124">`get` 和 `set` 访问器都会执行小时与秒之间的必要转换。</span><span class="sxs-lookup"><span data-stu-id="9ed33-124">Both the `get` and the `set` accessors perform the necessary conversion between hours and seconds.</span></span> <span data-ttu-id="9ed33-125">此外，`set` 访问器还会验证数据，如果小时数无效，则引发 <xref:System.ArgumentOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="9ed33-125">In addition, the `set` accessor validates the data and throws an <xref:System.ArgumentOutOfRangeException> if the number of hours is invalid.</span></span>

 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="9ed33-126">表达式主体定义</span><span class="sxs-lookup"><span data-stu-id="9ed33-126">Expression body definitions</span></span>  

 <span data-ttu-id="9ed33-127">属性访问器通常由单行语句组成，这些语句只分配或只返回表达式的结果。</span><span class="sxs-lookup"><span data-stu-id="9ed33-127">Property accessors often consist of single-line statements that just assign or return the result of an expression.</span></span> <span data-ttu-id="9ed33-128">可以将这些属性作为 expression-bodied 成员来实现。</span><span class="sxs-lookup"><span data-stu-id="9ed33-128">You can implement these properties as expression-bodied members.</span></span> <span data-ttu-id="9ed33-129">`=>` 符号后跟用于为属性赋值或从属性中检索值的表达式，即组成了表达式主体定义。</span><span class="sxs-lookup"><span data-stu-id="9ed33-129">Expression body definitions consist of the `=>` symbol followed by the expression to assign to or retrieve from the property.</span></span>

 <span data-ttu-id="9ed33-130">从 C# 6 开始，只读属性可以将 `get` 访问器作为 expression-bodied 成员实现。</span><span class="sxs-lookup"><span data-stu-id="9ed33-130">Starting with C# 6, read-only properties can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="9ed33-131">在这种情况下，既不使用 `get` 访问器关键字，也不使用 `return` 关键字。</span><span class="sxs-lookup"><span data-stu-id="9ed33-131">In this case, neither the `get` accessor keyword nor the `return` keyword is used.</span></span> <span data-ttu-id="9ed33-132">下面的示例将只读 `Name` 属性作为 expression-bodied 成员实现。</span><span class="sxs-lookup"><span data-stu-id="9ed33-132">The following example implements the read-only `Name` property as an expression-bodied member.</span></span>

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 <span data-ttu-id="9ed33-133">从 C# 7.0 开始，`get` 和 `set` 访问器都可以作为 expression-bodied 成员实现。</span><span class="sxs-lookup"><span data-stu-id="9ed33-133">Starting with C# 7.0, both the `get` and the `set` accessor can be implemented as expression-bodied members.</span></span> <span data-ttu-id="9ed33-134">在这种情况下，必须使用 `get` 和 `set` 关键字。</span><span class="sxs-lookup"><span data-stu-id="9ed33-134">In this case, the `get` and `set` keywords must be present.</span></span> <span data-ttu-id="9ed33-135">下面的示例阐释如何为这两个访问器使用表达式主体定义。</span><span class="sxs-lookup"><span data-stu-id="9ed33-135">The following example illustrates the use of expression body definitions for both accessors.</span></span> <span data-ttu-id="9ed33-136">请注意，`return` 关键字不与 `get` 访问器搭配使用。</span><span class="sxs-lookup"><span data-stu-id="9ed33-136">Note that the `return` keyword is not used with the `get` accessor.</span></span>

  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a><span data-ttu-id="9ed33-137">自动实现的属性</span><span class="sxs-lookup"><span data-stu-id="9ed33-137">Auto-implemented properties</span></span>

<span data-ttu-id="9ed33-138">在某些情况下，属性 `get` 和 `set` 访问器仅向支持字段赋值或仅从其中检索值，而不包括任何附加逻辑。</span><span class="sxs-lookup"><span data-stu-id="9ed33-138">In some cases, property `get` and `set` accessors just assign a value to or retrieve a value from a backing field without including any additional logic.</span></span> <span data-ttu-id="9ed33-139">通过使用自动实现的属性，既能简化代码，还能让 C# 编译器透明地提供支持字段。</span><span class="sxs-lookup"><span data-stu-id="9ed33-139">By using auto-implemented properties, you can simplify your code while having the C# compiler transparently provide the backing field for you.</span></span>

<span data-ttu-id="9ed33-140">如果属性具有 `get` 和 `set` 访问器，则必须自动实现这两个访问器。</span><span class="sxs-lookup"><span data-stu-id="9ed33-140">If a property has both a `get` and a `set` accessor, both must be auto-implemented.</span></span> <span data-ttu-id="9ed33-141">自动实现的属性通过以下方式定义：使用 `get` 和 `set` 关键字，但不提供任何实现。</span><span class="sxs-lookup"><span data-stu-id="9ed33-141">You define an auto-implemented property by using the `get` and `set` keywords without providing any implementation.</span></span> <span data-ttu-id="9ed33-142">下面的示例与上一个示例基本相同，只不过 `Name` 和 `Price` 是自动实现的属性。</span><span class="sxs-lookup"><span data-stu-id="9ed33-142">The following example repeats the previous one, except that `Name` and `Price` are auto-implemented properties.</span></span> <span data-ttu-id="9ed33-143">请注意，该示例还删除了参数化构造函数，以便通过调用无参数构造函数和[对象初始值设定项](object-and-collection-initializers.md)立即初始化 `SaleItem` 对象。</span><span class="sxs-lookup"><span data-stu-id="9ed33-143">Note that the example also removes the parameterized constructor, so that `SaleItem` objects are now initialized with a call to the parameterless constructor and an [object initializer](object-and-collection-initializers.md).</span></span>

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a><span data-ttu-id="9ed33-144">相关章节</span><span class="sxs-lookup"><span data-stu-id="9ed33-144">Related sections</span></span>  
  
- [<span data-ttu-id="9ed33-145">使用属性</span><span class="sxs-lookup"><span data-stu-id="9ed33-145">Using Properties</span></span>](./using-properties.md)  
  
- [<span data-ttu-id="9ed33-146">接口属性</span><span class="sxs-lookup"><span data-stu-id="9ed33-146">Interface Properties</span></span>](./interface-properties.md)  
  
- [<span data-ttu-id="9ed33-147">属性与索引器之间的比较</span><span class="sxs-lookup"><span data-stu-id="9ed33-147">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="9ed33-148">限制访问器可访问性</span><span class="sxs-lookup"><span data-stu-id="9ed33-148">Restricting Accessor Accessibility</span></span>](./restricting-accessor-accessibility.md)  
  
- [<span data-ttu-id="9ed33-149">自动实现的属性</span><span class="sxs-lookup"><span data-stu-id="9ed33-149">Auto-Implemented Properties</span></span>](./auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="9ed33-150">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="9ed33-150">C# Language Specification</span></span>  

<span data-ttu-id="9ed33-151">有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的[属性](~/_csharplang/spec/classes.md#properties)。</span><span class="sxs-lookup"><span data-stu-id="9ed33-151">For more information, see [Properties](~/_csharplang/spec/classes.md#properties) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="9ed33-152">该语言规范是 C# 语法和用法的权威资料。</span><span class="sxs-lookup"><span data-stu-id="9ed33-152">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9ed33-153">请参阅</span><span class="sxs-lookup"><span data-stu-id="9ed33-153">See also</span></span>

- [<span data-ttu-id="9ed33-154">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="9ed33-154">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9ed33-155">使用属性</span><span class="sxs-lookup"><span data-stu-id="9ed33-155">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="9ed33-156">索引器</span><span class="sxs-lookup"><span data-stu-id="9ed33-156">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="9ed33-157">get 关键字</span><span class="sxs-lookup"><span data-stu-id="9ed33-157">get keyword</span></span>](../../language-reference/keywords/get.md)
- [<span data-ttu-id="9ed33-158">set 关键字</span><span class="sxs-lookup"><span data-stu-id="9ed33-158">set keyword</span></span>](../../language-reference/keywords/set.md)
