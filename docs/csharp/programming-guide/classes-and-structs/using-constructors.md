---
title: 使用构造函数 - C# 编程指南
description: 此示例演示如何使用 C# 中的 new 运算符实例化类。 在为 new 对象分配内存后调用简单构造函数。
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
ms.openlocfilehash: 6b441b04bd6bfcb5564f40a90718e822f56ac21e
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863950"
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="836a6-104">使用构造函数（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="836a6-104">Using Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="836a6-105">创建[类](../../language-reference/keywords/class.md)或[结构](../../language-reference/builtin-types/struct.md)时，将会调用其构造函数。</span><span class="sxs-lookup"><span data-stu-id="836a6-105">When a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="836a6-106">构造函数与该类或结构具有相同名称，并且通常初始化新对象的数据成员。</span><span class="sxs-lookup"><span data-stu-id="836a6-106">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="836a6-107">在下面的示例中，通过使用简单构造函数定义了一个名为 `Taxi` 的类。</span><span class="sxs-lookup"><span data-stu-id="836a6-107">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="836a6-108">然后使用 [new](../../language-reference/operators/new-operator.md) 运算符对该类进行实例化。</span><span class="sxs-lookup"><span data-stu-id="836a6-108">This class is then instantiated with the [new](../../language-reference/operators/new-operator.md) operator.</span></span> <span data-ttu-id="836a6-109">在为新对象分配内存之后，`new` 运算符立即调用 `Taxi` 构造函数。</span><span class="sxs-lookup"><span data-stu-id="836a6-109">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#53)]  
  
 <span data-ttu-id="836a6-110">不带任何参数的构造函数称为“无参数构造函数”。</span><span class="sxs-lookup"><span data-stu-id="836a6-110">A constructor that takes no parameters is called a *parameterless constructor*.</span></span> <span data-ttu-id="836a6-111">每当使用 `new` 运算符实例化对象且不为 `new` 提供任何参数时，会调用无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="836a6-111">Parameterless constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="836a6-112">有关详细信息，请参阅[实例构造函数](./instance-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="836a6-112">For more information, see [Instance Constructors](./instance-constructors.md).</span></span>  
  
 <span data-ttu-id="836a6-113">除非类是[静态](../../language-reference/keywords/static.md)的，否则 C# 编译器将为无构造函数的类提供一个公共的无参数构造函数，以便该类可以实例化。</span><span class="sxs-lookup"><span data-stu-id="836a6-113">Unless the class is [static](../../language-reference/keywords/static.md), classes without constructors are given a public parameterless constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="836a6-114">有关详细信息，请参阅[静态类和静态类成员](./static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="836a6-114">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="836a6-115">通过将构造函数设置为私有构造函数，可以阻止类被实例化，如下所示：</span><span class="sxs-lookup"><span data-stu-id="836a6-115">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="836a6-116">有关详细信息，请参阅[私有构造函数](./private-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="836a6-116">For more information, see [Private Constructors](./private-constructors.md).</span></span>  
  
 <span data-ttu-id="836a6-117">[结构](../../language-reference/builtin-types/struct.md)类型的构造函数与类的构造函数类似，但是 `structs` 不包含显式无参数构造函数，因为编译器将自动提供一个显式无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="836a6-117">Constructors for [struct](../../language-reference/builtin-types/struct.md) types resemble class constructors, but `structs` cannot contain an explicit parameterless constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="836a6-118">此构造函数会将 `struct` 中的每个字段初始化为[默认值](../../language-reference/builtin-types/default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="836a6-118">This constructor initializes each field in the `struct` to the [default value](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="836a6-119">但是，只有使用 `new` 实例化 `struct` 时，才会调用此无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="836a6-119">However, this parameterless constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="836a6-120">例如，此代码使用 <xref:System.Int32> 的无参数构造函数，因此可确保整数已初始化：</span><span class="sxs-lookup"><span data-stu-id="836a6-120">For example, this code uses the parameterless constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```csharp  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="836a6-121">但是，下面的代码会导致编译器错误，因为它不使用 `new`，而且尝试使用尚未初始化的对象：</span><span class="sxs-lookup"><span data-stu-id="836a6-121">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```csharp  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="836a6-122">或者，可将基于 `structs` 的对象（包括所有内置数值类型）初始化或赋值后使用，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="836a6-122">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```csharp  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="836a6-123">因此无需调用值类型的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="836a6-123">So calling the parameterless constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="836a6-124">两个类和 `structs` 都可以定义带参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="836a6-124">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="836a6-125">必须通过 `new` 语句或 [base](../../language-reference/keywords/base.md) 语句调用带参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="836a6-125">Constructors that take parameters must be called through a `new` statement or a [base](../../language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="836a6-126">类和 `structs` 还可以定义多个构造函数，并且二者均无需定义无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="836a6-126">Classes and `structs` can also define multiple constructors, and neither is required to define a parameterless constructor.</span></span> <span data-ttu-id="836a6-127">例如：</span><span class="sxs-lookup"><span data-stu-id="836a6-127">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#54)]  
  
 <span data-ttu-id="836a6-128">可使用下面任一语句创建此类：</span><span class="sxs-lookup"><span data-stu-id="836a6-128">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#55)]  
  
 <span data-ttu-id="836a6-129">构造函数可以使用 `base` 关键字调用基类的构造函数。</span><span class="sxs-lookup"><span data-stu-id="836a6-129">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="836a6-130">例如：</span><span class="sxs-lookup"><span data-stu-id="836a6-130">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#56)]  
  
 <span data-ttu-id="836a6-131">在此示例中，在执行构造函数块之前调用基类的构造函数。</span><span class="sxs-lookup"><span data-stu-id="836a6-131">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="836a6-132">`base` 关键字可带参数使用，也可不带参数使用。</span><span class="sxs-lookup"><span data-stu-id="836a6-132">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="836a6-133">构造函数的任何参数都可用作 `base` 的参数，或用作表达式的一部分。</span><span class="sxs-lookup"><span data-stu-id="836a6-133">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="836a6-134">有关详细信息，请参阅 [base](../../language-reference/keywords/base.md)。</span><span class="sxs-lookup"><span data-stu-id="836a6-134">For more information, see [base](../../language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="836a6-135">在派生类中，如果不使用 `base` 关键字来显式调用基类构造函数，则将隐式调用无参数构造函数（若有）。</span><span class="sxs-lookup"><span data-stu-id="836a6-135">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the parameterless constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="836a6-136">这意味着下面的构造函数声明等效：</span><span class="sxs-lookup"><span data-stu-id="836a6-136">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#58)]  
  
 [!code-csharp[csProgGuideObjects#57](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#57)]  
  
 <span data-ttu-id="836a6-137">如果基类没有提供无参数构造函数，派生类必须使用 `base` 显式调用基类构造函数。</span><span class="sxs-lookup"><span data-stu-id="836a6-137">If a base class does not offer a parameterless constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="836a6-138">构造函数可以使用 [this](../../language-reference/keywords/this.md) 关键字调用同一对象中的另一构造函数。</span><span class="sxs-lookup"><span data-stu-id="836a6-138">A constructor can invoke another constructor in the same object by using the [this](../../language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="836a6-139">和 `base` 一样，`this` 可带参数使用也可不带参数使用，构造函数中的任何参数都可用作 `this` 的参数，或者用作表达式的一部分。</span><span class="sxs-lookup"><span data-stu-id="836a6-139">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="836a6-140">例如，可以使用 `this` 重写前一示例中的第二个构造函数：</span><span class="sxs-lookup"><span data-stu-id="836a6-140">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#59)]  
  
 <span data-ttu-id="836a6-141">上一示例中使用 `this` 关键字会导致此构造函数被调用：</span><span class="sxs-lookup"><span data-stu-id="836a6-141">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#60)]  
  
 <span data-ttu-id="836a6-142">可以将构造函数标记为[public](../../language-reference/keywords/public.md)、[private](../../language-reference/keywords/private.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md) 或 [private protected](../../language-reference/keywords/private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="836a6-142">Constructors can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="836a6-143">这些访问修饰符定义类的用户构造该类的方式。</span><span class="sxs-lookup"><span data-stu-id="836a6-143">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="836a6-144">有关详细信息，请参阅[访问修饰符](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="836a6-144">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="836a6-145">可使用 [static](../../language-reference/keywords/static.md) 关键字将构造函数声明为静态构造函数。</span><span class="sxs-lookup"><span data-stu-id="836a6-145">A constructor can be declared static by using the [static](../../language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="836a6-146">在访问任何静态字段之前，都将自动调用静态构造函数，它们通常用于初始化静态类成员。</span><span class="sxs-lookup"><span data-stu-id="836a6-146">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="836a6-147">有关详细信息，请参阅[静态构造函数](./static-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="836a6-147">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="836a6-148">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="836a6-148">C# Language Specification</span></span>  

<span data-ttu-id="836a6-149">有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的[实例构造函数](~/_csharplang/spec/classes.md#instance-constructors)和[静态构造函数](~/_csharplang/spec/classes.md#static-constructors)。</span><span class="sxs-lookup"><span data-stu-id="836a6-149">For more information, see [Instance constructors](~/_csharplang/spec/classes.md#instance-constructors) and [Static constructors](~/_csharplang/spec/classes.md#static-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="836a6-150">该语言规范是 C# 语法和用法的权威资料。</span><span class="sxs-lookup"><span data-stu-id="836a6-150">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="836a6-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="836a6-151">See also</span></span>

- [<span data-ttu-id="836a6-152">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="836a6-152">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="836a6-153">类和结构</span><span class="sxs-lookup"><span data-stu-id="836a6-153">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="836a6-154">构造函数</span><span class="sxs-lookup"><span data-stu-id="836a6-154">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="836a6-155">终结器</span><span class="sxs-lookup"><span data-stu-id="836a6-155">Finalizers</span></span>](./destructors.md)
