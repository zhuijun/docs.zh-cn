---
title: 表达式主体定义的成员 - C# 编程指南
description: 了解 expression-bodied 成员。 查看使用属性、构造函数、终结器等的表达式主体定义的代码示例。
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: e68e96e4aa3ff6a64590459a7197da1833e1a275
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381653"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="6f181-104">Expression-bodied 成员（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="6f181-104">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="6f181-105">通过表达式主体定义，可采用非常简洁的可读形式提供成员的实现。</span><span class="sxs-lookup"><span data-stu-id="6f181-105">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="6f181-106">只要任何支持的成员（如方法或属性）的逻辑包含单个表达式，就可以使用表达式主体定义。</span><span class="sxs-lookup"><span data-stu-id="6f181-106">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="6f181-107">表达式主体定义具有下列常规语法：</span><span class="sxs-lookup"><span data-stu-id="6f181-107">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="6f181-108">其中“expression”是有效的表达式。</span><span class="sxs-lookup"><span data-stu-id="6f181-108">where *expression* is a valid expression.</span></span>

<span data-ttu-id="6f181-109">C# 6 中引入了针对方法和只读属性的表达式主体定义支持，并在 C# 7.0 中进行了扩展。</span><span class="sxs-lookup"><span data-stu-id="6f181-109">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="6f181-110">表达式主体定义可用于下表列出的类型成员：</span><span class="sxs-lookup"><span data-stu-id="6f181-110">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="6f181-111">成员</span><span class="sxs-lookup"><span data-stu-id="6f181-111">Member</span></span>  |<span data-ttu-id="6f181-112">开始提供支持的版本</span><span class="sxs-lookup"><span data-stu-id="6f181-112">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="6f181-113">方法</span><span class="sxs-lookup"><span data-stu-id="6f181-113">Method</span></span>](#methods)  |<span data-ttu-id="6f181-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="6f181-114">C# 6</span></span> |
|[<span data-ttu-id="6f181-115">只读属性</span><span class="sxs-lookup"><span data-stu-id="6f181-115">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="6f181-116">C# 6</span><span class="sxs-lookup"><span data-stu-id="6f181-116">C# 6</span></span>  |
|[<span data-ttu-id="6f181-117">Property</span><span class="sxs-lookup"><span data-stu-id="6f181-117">Property</span></span>](#properties)  |<span data-ttu-id="6f181-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="6f181-118">C# 7.0</span></span> |
|[<span data-ttu-id="6f181-119">构造函数</span><span class="sxs-lookup"><span data-stu-id="6f181-119">Constructor</span></span>](#constructors)   |<span data-ttu-id="6f181-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="6f181-120">C# 7.0</span></span> |
|[<span data-ttu-id="6f181-121">终结器</span><span class="sxs-lookup"><span data-stu-id="6f181-121">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="6f181-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="6f181-122">C# 7.0</span></span> |
|[<span data-ttu-id="6f181-123">索引器</span><span class="sxs-lookup"><span data-stu-id="6f181-123">Indexer</span></span>](#indexers)       |<span data-ttu-id="6f181-124">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="6f181-124">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="6f181-125">方法</span><span class="sxs-lookup"><span data-stu-id="6f181-125">Methods</span></span>

<span data-ttu-id="6f181-126">expression-bodied 方法包含单个表达式，它返回的值的类型与方法的返回类型匹配；或者，对于返回 `void` 的方法，其表达式则执行某些操作。</span><span class="sxs-lookup"><span data-stu-id="6f181-126">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="6f181-127">例如，替代 <xref:System.Object.ToString%2A> 方法的类型通常包含单个表达式，该表达式返回当前对象的字符串表示形式。</span><span class="sxs-lookup"><span data-stu-id="6f181-127">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="6f181-128">下面的示例定义 `Person` 类，该类通过表达式主体定义替代 <xref:System.Object.ToString%2A>。</span><span class="sxs-lookup"><span data-stu-id="6f181-128">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="6f181-129">它还定义向控制台显示名称的 `DisplayName` 方法。</span><span class="sxs-lookup"><span data-stu-id="6f181-129">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="6f181-130">请注意，`ToString` 表达式主体定义中未使用 `return` 关键字。</span><span class="sxs-lookup"><span data-stu-id="6f181-130">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="6f181-131">有关详细信息，请参阅[方法（C# 编程指南）](../classes-and-structs/methods.md)。</span><span class="sxs-lookup"><span data-stu-id="6f181-131">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="6f181-132">只读属性</span><span class="sxs-lookup"><span data-stu-id="6f181-132">Read-only properties</span></span>

<span data-ttu-id="6f181-133">从 C# 6 开始，可以使用表达式主体定义来实现只读属性。</span><span class="sxs-lookup"><span data-stu-id="6f181-133">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="6f181-134">为此，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="6f181-134">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="6f181-135">下面的示例定义 `Location` 类，其只读 `Name` 属性以表达式主体定义的形式实现，该表达式主体定义返回私有 `locationName` 字段值：</span><span class="sxs-lookup"><span data-stu-id="6f181-135">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="6f181-136">有关属性的详细信息，请参阅[属性（C# 编程指南）](../classes-and-structs/properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6f181-136">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="6f181-137">属性</span><span class="sxs-lookup"><span data-stu-id="6f181-137">Properties</span></span>

<span data-ttu-id="6f181-138">从 C# 7.0 开始，可以使用表达式主体定义来实现属性 `get` 和 `set` 访问器。</span><span class="sxs-lookup"><span data-stu-id="6f181-138">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="6f181-139">下面的示例演示其实现方法：</span><span class="sxs-lookup"><span data-stu-id="6f181-139">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="6f181-140">有关属性的详细信息，请参阅[属性（C# 编程指南）](../classes-and-structs/properties.md)。</span><span class="sxs-lookup"><span data-stu-id="6f181-140">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="6f181-141">构造函数</span><span class="sxs-lookup"><span data-stu-id="6f181-141">Constructors</span></span>

<span data-ttu-id="6f181-142">构造函数的表达式主体定义通常包含单个赋值表达式或一个方法调用，该方法调用可处理构造函数的参数，也可初始化实例状态。</span><span class="sxs-lookup"><span data-stu-id="6f181-142">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="6f181-143">以下示例定义 `Location` 类，其构造函数具有一个名为“name”的字符串参数。</span><span class="sxs-lookup"><span data-stu-id="6f181-143">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="6f181-144">表达式主体定义向 `Name` 属性分配参数。</span><span class="sxs-lookup"><span data-stu-id="6f181-144">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="6f181-145">有关详细信息，请参阅[构造函数（C# 编程指南）](../classes-and-structs/constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="6f181-145">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="6f181-146">终结器</span><span class="sxs-lookup"><span data-stu-id="6f181-146">Finalizers</span></span>

<span data-ttu-id="6f181-147">终结器的表达式主体定义通常包含清理语句，例如释放非托管资源的语句。</span><span class="sxs-lookup"><span data-stu-id="6f181-147">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="6f181-148">下面的示例定义了一个终结器，该终结器使用表达式主体定义来指示已调用该终结器。</span><span class="sxs-lookup"><span data-stu-id="6f181-148">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="6f181-149">有关详细信息，请参阅[终结器（C# 编程指南）](../classes-and-structs/destructors.md)。</span><span class="sxs-lookup"><span data-stu-id="6f181-149">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="6f181-150">索引器</span><span class="sxs-lookup"><span data-stu-id="6f181-150">Indexers</span></span>

<span data-ttu-id="6f181-151">与使用属性一样，如果 `get` 访问器包含返回值的单个表达式或 `set` 访问器执行简单的赋值，则索引器 `get` 和 `set` 访问器包含表达式主体定义。</span><span class="sxs-lookup"><span data-stu-id="6f181-151">Like with properties, indexer `get` and `set` accessors consist of expression body definitions if the `get` accessor consists of a single expression that returns a value or the `set` accessor performs a simple assignment.</span></span>

<span data-ttu-id="6f181-152">下面的示例定义名为 `Sports` 的类，其中包含一个内部 <xref:System.String> 数组，该数组包含大量体育运动的名称。</span><span class="sxs-lookup"><span data-stu-id="6f181-152">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="6f181-153">索引器的 `get` 和 `set` 访问器都以表达式主体定义的形式实现。</span><span class="sxs-lookup"><span data-stu-id="6f181-153">Both the indexer `get` and `set` accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="6f181-154">有关详细信息，请参阅[索引器（C# 编程指南）](../indexers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="6f181-154">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
