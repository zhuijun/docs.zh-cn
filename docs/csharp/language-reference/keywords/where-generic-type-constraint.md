---
title: where（泛型类型约束）- C# 参考
ms.date: 04/15/2020
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 406c710cd884363c32b98336717732a09b3d1fc1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401870"
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="c580f-102">where（泛型类型约束）（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="c580f-102">where (generic type constraint) (C# Reference)</span></span>

<span data-ttu-id="c580f-103">泛型定义中的 `where` 子句指定对用作泛型类型、方法、委托或本地函数中类型参数的参数类型的约束。</span><span class="sxs-lookup"><span data-stu-id="c580f-103">The `where` clause in a generic definition specifies constraints on the types that are used as arguments for type parameters in a generic type, method, delegate, or local function.</span></span> <span data-ttu-id="c580f-104">约束可指定接口、基类或要求泛型类型为引用、值或非托管类型。</span><span class="sxs-lookup"><span data-stu-id="c580f-104">Constraints can specify interfaces, base classes, or require a generic type to be a reference, value, or unmanaged type.</span></span> <span data-ttu-id="c580f-105">它们声明类型参数必须具备的功能。</span><span class="sxs-lookup"><span data-stu-id="c580f-105">They declare capabilities that the type argument must have.</span></span>

<span data-ttu-id="c580f-106">例如，可以声明一个泛型类 `MyGenericClass`，以使类型参数 `T` 实现 <xref:System.IComparable%601> 接口：</span><span class="sxs-lookup"><span data-stu-id="c580f-106">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>

[!code-csharp[using an interface constraint](snippets/GenericWhereConstraints.cs#1)]

> [!NOTE]
> <span data-ttu-id="c580f-107">有关查询表达式中的 where 子句的详细信息，请参阅 [where 子句](where-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="c580f-107">For more information on the where clause in a query expression, see [where clause](where-clause.md).</span></span>

<span data-ttu-id="c580f-108">`where` 子句还可包括基类约束。</span><span class="sxs-lookup"><span data-stu-id="c580f-108">The `where` clause can also include a base class constraint.</span></span> <span data-ttu-id="c580f-109">基类约束表明用作该泛型类型的类型参数的类型具有指定的类作为基类（或者是该基类）。</span><span class="sxs-lookup"><span data-stu-id="c580f-109">The base class constraint states that a type to be used as a type argument for that generic type has the specified class as a base class, or is that base class.</span></span> <span data-ttu-id="c580f-110">该基类约束一经使用，就必须出现在该类型参数的所有其他约束之前。</span><span class="sxs-lookup"><span data-stu-id="c580f-110">If the base class constraint is used, it must appear before any other constraints on that type parameter.</span></span> <span data-ttu-id="c580f-111">某些类型不允许作为基类约束：<xref:System.Object>、<xref:System.Array> 和 <xref:System.ValueType>。</span><span class="sxs-lookup"><span data-stu-id="c580f-111">Some types are disallowed as a base class constraint: <xref:System.Object>, <xref:System.Array>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="c580f-112">在 C# 7.3 之前，<xref:System.Enum>、<xref:System.Delegate> 和 <xref:System.MulticastDelegate> 也不允许作为基类约束。</span><span class="sxs-lookup"><span data-stu-id="c580f-112">Before C# 7.3, <xref:System.Enum>, <xref:System.Delegate>, and <xref:System.MulticastDelegate> were also disallowed as base class constraints.</span></span> <span data-ttu-id="c580f-113">以下示例显示现可指定为基类的类型：</span><span class="sxs-lookup"><span data-stu-id="c580f-113">The following example shows the types that can now be specified as a base class:</span></span>

[!code-csharp[using an interface constraint](snippets/GenericWhereConstraints.cs#2)]

<span data-ttu-id="c580f-114">在 C# 8.0 及更高版本中的可为 null 上下文中，强制执行基类类型的为 null 性。</span><span class="sxs-lookup"><span data-stu-id="c580f-114">In a nullable context in C# 8.0 and later, the nullability of the base class type is enforced.</span></span> <span data-ttu-id="c580f-115">如果基类不可为 null（例如 `Base`），则类型参数必须不可为 null。</span><span class="sxs-lookup"><span data-stu-id="c580f-115">If the base class is non-nullable (for example `Base`), the type argument must be non-nullable.</span></span> <span data-ttu-id="c580f-116">如果基类可为 null（例如 `Base?`），则类型参数可以是可为 null 或不可为 null 的引用类型。</span><span class="sxs-lookup"><span data-stu-id="c580f-116">If the base class is nullable (for example `Base?`), the type argument may be either a nullable or non-nullable reference type.</span></span> <span data-ttu-id="c580f-117">当基类不可为 null 时，如果类型参数是可为 null 的引用类型，编译器将发出警告。</span><span class="sxs-lookup"><span data-stu-id="c580f-117">The compiler issues a warning if the type argument is a nullable reference type when the base class is non-nullable.</span></span>

<span data-ttu-id="c580f-118">`where` 子句可指定类型为 `class` 或 `struct`。</span><span class="sxs-lookup"><span data-stu-id="c580f-118">The `where` clause can specify that the type is a `class` or a `struct`.</span></span> <span data-ttu-id="c580f-119">`struct` 约束不再需要指定 `System.ValueType` 的基类约束。</span><span class="sxs-lookup"><span data-stu-id="c580f-119">The `struct` constraint removes the need to specify a base class constraint of `System.ValueType`.</span></span> <span data-ttu-id="c580f-120">`System.ValueType` 类型可能不用作基类约束。</span><span class="sxs-lookup"><span data-stu-id="c580f-120">The `System.ValueType` type may not be used as a base class constraint.</span></span> <span data-ttu-id="c580f-121">以下示例显示 `class` 和 `struct` 约束：</span><span class="sxs-lookup"><span data-stu-id="c580f-121">The following example shows both the `class` and `struct` constraints:</span></span>

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#3)]

<span data-ttu-id="c580f-122">在 C# 8.0 及更高版本中的可为 null 上下文中，`class` 约束要求类型是不可为 null 的引用类型。</span><span class="sxs-lookup"><span data-stu-id="c580f-122">In a nullable context in C# 8.0 and later, the `class` constraint requires a type to be a non-nullable reference type.</span></span> <span data-ttu-id="c580f-123">若要允许可为 null 的引用类型，请使用 `class?` 约束，该约束允许可为 null 和不可为 null 的引用类型。</span><span class="sxs-lookup"><span data-stu-id="c580f-123">To allow nullable reference types, use the `class?` constraint, which allows both nullable and non-nullable reference types.</span></span>

<span data-ttu-id="c580f-124">`where` 子句可能包含 `notnull` 约束。</span><span class="sxs-lookup"><span data-stu-id="c580f-124">The `where` clause may include the `notnull` constraint.</span></span> <span data-ttu-id="c580f-125">`notnull` 约束将类型参数限制为不可为 null 的类型。</span><span class="sxs-lookup"><span data-stu-id="c580f-125">The `notnull` constraint limits the type parameter to non-nullable types.</span></span> <span data-ttu-id="c580f-126">该类型可以是[值类型](../builtin-types/value-types.md)，也可以是不可为 null 的引用类型。</span><span class="sxs-lookup"><span data-stu-id="c580f-126">That type may be a [value type](../builtin-types/value-types.md) or a non-nullable reference type.</span></span> <span data-ttu-id="c580f-127">对于在 [`nullable enable` 上下文](../../nullable-references.md#nullable-contexts)中编译的代码，从 C# 8.0 开始可以使用 `notnull` 约束。</span><span class="sxs-lookup"><span data-stu-id="c580f-127">The `notnull` constraint is available starting in C# 8.0 for code compiled in a [`nullable enable` context](../../nullable-references.md#nullable-contexts).</span></span> <span data-ttu-id="c580f-128">与其他约束不同，如果类型参数违反 `notnull` 约束，编译器会生成警告而不是错误。</span><span class="sxs-lookup"><span data-stu-id="c580f-128">Unlike other constraints, if a type argument violates the `notnull` constraint, the compiler generates a warning instead of an error.</span></span> <span data-ttu-id="c580f-129">警告仅在 `nullable enable` 上下文中生成。</span><span class="sxs-lookup"><span data-stu-id="c580f-129">Warnings are only generated in a `nullable enable` context.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c580f-130">包含 `notnull` 约束的泛型声明可以在可为 null 的不明显上下文中使用，但编译器不会强制执行约束。</span><span class="sxs-lookup"><span data-stu-id="c580f-130">Generic declarations that include the `notnull` constraint can be used in a nullable oblivious context, but compiler does not enforce the constraint.</span></span>

[!code-csharp[using the nonnull constraint](snippets/GenericWhereConstraints.cs#NotNull)]

<span data-ttu-id="c580f-131">`where` 子句还可包括 `unmanaged` 约束。</span><span class="sxs-lookup"><span data-stu-id="c580f-131">The `where` clause may also include an `unmanaged` constraint.</span></span> <span data-ttu-id="c580f-132">`unmanaged` 约束将类型参数限制为名为[“非托管类型”](../builtin-types/unmanaged-types.md)的类型。</span><span class="sxs-lookup"><span data-stu-id="c580f-132">The `unmanaged` constraint limits the type parameter to types known as [unmanaged types](../builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="c580f-133">`unmanaged` 约束使得在 C# 中编写低级别的互操作代码变得更容易。</span><span class="sxs-lookup"><span data-stu-id="c580f-133">The `unmanaged` constraint makes it easier to write low-level interop code in C#.</span></span> <span data-ttu-id="c580f-134">此约束支持跨所有非托管类型的可重用例程。</span><span class="sxs-lookup"><span data-stu-id="c580f-134">This constraint enables reusable routines across all unmanaged types.</span></span> <span data-ttu-id="c580f-135">`unmanaged` 约束不能与 `class` 或 `struct` 约束结合使用。</span><span class="sxs-lookup"><span data-stu-id="c580f-135">The `unmanaged` constraint can't be combined with the `class` or `struct` constraint.</span></span> <span data-ttu-id="c580f-136">`unmanaged` 约束强制该类型必须为 `struct`：</span><span class="sxs-lookup"><span data-stu-id="c580f-136">The `unmanaged` constraint enforces that the type must be a `struct`:</span></span>

[!code-csharp[using the unmanaged constraint](snippets/GenericWhereConstraints.cs#4)]

<span data-ttu-id="c580f-137">`where` 子句也可能包括构造函数约束 `new()`。</span><span class="sxs-lookup"><span data-stu-id="c580f-137">The `where` clause may also include a constructor constraint, `new()`.</span></span> <span data-ttu-id="c580f-138">该约束使得能够使用 `new` 运算符创建类型参数的实例。</span><span class="sxs-lookup"><span data-stu-id="c580f-138">That constraint makes it possible to create an instance of a type parameter using the `new` operator.</span></span> <span data-ttu-id="c580f-139">[new() 约束](new-constraint.md)可以让编译器知道：提供的任何类型参数都必须具有可访问的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="c580f-139">The [new() Constraint](new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless constructor.</span></span> <span data-ttu-id="c580f-140">例如：</span><span class="sxs-lookup"><span data-stu-id="c580f-140">For example:</span></span>

[!code-csharp[using the new constraint](snippets/GenericWhereConstraints.cs#5)]

<span data-ttu-id="c580f-141">`new()` 约束出现在 `where` 子句的最后。</span><span class="sxs-lookup"><span data-stu-id="c580f-141">The `new()` constraint appears last in the `where` clause.</span></span> <span data-ttu-id="c580f-142">`new()` 约束不能与 `struct` 或 `unmanaged` 约束结合使用。</span><span class="sxs-lookup"><span data-stu-id="c580f-142">The `new()` constraint can't be combined with the `struct` or `unmanaged` constraints.</span></span> <span data-ttu-id="c580f-143">所有满足这些约束的类型必须具有可访问的无参数构造函数，这使得 `new()` 约束冗余。</span><span class="sxs-lookup"><span data-stu-id="c580f-143">All types satisfying those constraints must have an accessible parameterless constructor, making the `new()` constraint redundant.</span></span>

<span data-ttu-id="c580f-144">对于多个类型参数，每个类型参数都使用一个 `where` 子句，例如：</span><span class="sxs-lookup"><span data-stu-id="c580f-144">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>

[!code-csharp[using multiple where constraints](snippets/GenericWhereConstraints.cs#6)]

<span data-ttu-id="c580f-145">还可将约束附加到泛型方法的类型参数，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="c580f-145">You can also attach constraints to type parameters of generic methods, as shown in the following example:</span></span>

[!code-csharp[where constraints with generic methods](snippets/GenericWhereConstraints.cs#7)]

<span data-ttu-id="c580f-146">请注意，对于委托和方法两者来说，描述类型参数约束的语法是一样的：</span><span class="sxs-lookup"><span data-stu-id="c580f-146">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>

[!code-csharp[where constraints with generic methods](snippets/GenericWhereConstraints.cs#8)]

<span data-ttu-id="c580f-147">有关泛型委托的信息，请参阅[泛型委托](../../programming-guide/generics/generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="c580f-147">For information on generic delegates, see [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span>

<span data-ttu-id="c580f-148">有关约束的语法和用法的详细信息，请参阅[类型参数的约束](../../programming-guide/generics/constraints-on-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="c580f-148">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../programming-guide/generics/constraints-on-type-parameters.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c580f-149">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="c580f-149">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c580f-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="c580f-150">See also</span></span>

- [<span data-ttu-id="c580f-151">C# 参考</span><span class="sxs-lookup"><span data-stu-id="c580f-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c580f-152">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="c580f-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c580f-153">泛型介绍</span><span class="sxs-lookup"><span data-stu-id="c580f-153">Introduction to Generics</span></span>](../../programming-guide/generics/index.md)
- [<span data-ttu-id="c580f-154">new 约束</span><span class="sxs-lookup"><span data-stu-id="c580f-154">new Constraint</span></span>](./new-constraint.md)
- [<span data-ttu-id="c580f-155">类型参数的约束</span><span class="sxs-lookup"><span data-stu-id="c580f-155">Constraints on Type Parameters</span></span>](../../programming-guide/generics/constraints-on-type-parameters.md)
