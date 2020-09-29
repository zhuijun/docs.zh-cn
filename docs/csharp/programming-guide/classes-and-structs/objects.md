---
title: 对象 - C# 编程指南
description: C# 使用类或结构定义来定义对象的类型。 在 C# 等面向对象的语言中，程序由动态交互的对象组成。
ms.date: 07/20/2015
helpviewer_keywords:
- objects [C#], about objects
- variables [C#]
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
ms.openlocfilehash: 61d79f5647fa05edade9aef90653544b08c20c83
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181825"
---
# <a name="objects-c-programming-guide"></a><span data-ttu-id="7db88-104">对象（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="7db88-104">Objects (C# Programming Guide)</span></span>

<span data-ttu-id="7db88-105">类或结构定义的作用类似于蓝图，指定该类型可以进行哪些操作。</span><span class="sxs-lookup"><span data-stu-id="7db88-105">A class or struct definition is like a blueprint that specifies what the type can do.</span></span> <span data-ttu-id="7db88-106">从本质上说，对象是按照此蓝图分配和配置的内存块。</span><span class="sxs-lookup"><span data-stu-id="7db88-106">An object is basically a block of memory that has been allocated and configured according to the blueprint.</span></span> <span data-ttu-id="7db88-107">程序可以创建同一个类的多个对象。</span><span class="sxs-lookup"><span data-stu-id="7db88-107">A program may create many objects of the same class.</span></span> <span data-ttu-id="7db88-108">对象也称为实例，可以存储在命名变量中，也可以存储在数组或集合中。</span><span class="sxs-lookup"><span data-stu-id="7db88-108">Objects are also called instances, and they can be stored in either a named variable or in an array or collection.</span></span> <span data-ttu-id="7db88-109">使用这些变量来调用对象方法及访问对象公共属性的代码称为客户端代码。</span><span class="sxs-lookup"><span data-stu-id="7db88-109">Client code is the code that uses these variables to call the methods and access the public properties of the object.</span></span> <span data-ttu-id="7db88-110">在 C# 等面向对象的语言中，典型的程序由动态交互的多个对象组成。</span><span class="sxs-lookup"><span data-stu-id="7db88-110">In an object-oriented language such as C#, a typical program consists of multiple objects interacting dynamically.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7db88-111">静态类型的行为与此处介绍的不同。</span><span class="sxs-lookup"><span data-stu-id="7db88-111">Static types behave differently than what is described here.</span></span> <span data-ttu-id="7db88-112">有关详细信息，请参阅[静态类和静态类成员](./static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="7db88-112">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>
  
## <a name="struct-instances-vs-class-instances"></a><span data-ttu-id="7db88-113">结构实例与类实例</span><span class="sxs-lookup"><span data-stu-id="7db88-113">Struct Instances vs. Class Instances</span></span>  

 <span data-ttu-id="7db88-114">由于类是引用类型，因此类对象的变量引用该对象在托管堆上的地址。</span><span class="sxs-lookup"><span data-stu-id="7db88-114">Because classes are reference types, a variable of a class object holds a reference to the address of the object on the managed heap.</span></span> <span data-ttu-id="7db88-115">如果将同一类型的第二个对象分配给第一个对象，则两个变量都引用该地址的对象。</span><span class="sxs-lookup"><span data-stu-id="7db88-115">If a second object of the same type is assigned to the first object, then both variables refer to the object at that address.</span></span> <span data-ttu-id="7db88-116">这一点将在本主题后面部分进行更详细的讨论。</span><span class="sxs-lookup"><span data-stu-id="7db88-116">This point is discussed in more detail later in this topic.</span></span>  
  
 <span data-ttu-id="7db88-117">类的实例是使用 [new 运算符](../../language-reference/operators/new-operator.md)创建的。</span><span class="sxs-lookup"><span data-stu-id="7db88-117">Instances of classes are created by using the [new operator](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="7db88-118">在下面的示例中，`Person` 为类型，`person1` 和 `person 2` 为该类型的实例（即对象）。</span><span class="sxs-lookup"><span data-stu-id="7db88-118">In the following example, `Person` is the type and `person1` and `person 2` are instances, or objects, of that type.</span></span>  
  
 [!code-csharp[csProgGuideStatements#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#30)]  
  
 <span data-ttu-id="7db88-119">由于结构是值类型，因此结构对象的变量具有整个对象的副本。</span><span class="sxs-lookup"><span data-stu-id="7db88-119">Because structs are value types, a variable of a struct object holds a copy of the entire object.</span></span> <span data-ttu-id="7db88-120">结构的实例也可以使用 `new` 运算符来创建，但这不是必需的，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="7db88-120">Instances of structs can also be created by using the `new` operator, but this is not required, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideStatements#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#31)]  
  
 <span data-ttu-id="7db88-121">`p1` 和 `p2` 的内存在线程堆栈上进行分配。</span><span class="sxs-lookup"><span data-stu-id="7db88-121">The memory for both `p1` and `p2` is allocated on the thread stack.</span></span> <span data-ttu-id="7db88-122">该内存随声明它的类型或方法一起回收。</span><span class="sxs-lookup"><span data-stu-id="7db88-122">That memory is reclaimed along with the type or method in which it is declared.</span></span> <span data-ttu-id="7db88-123">这就是在赋值时复制结构的一个原因。</span><span class="sxs-lookup"><span data-stu-id="7db88-123">This is one reason why structs are copied on assignment.</span></span> <span data-ttu-id="7db88-124">相比之下，当对类实例对象的所有引用都超出范围时，为该类实例分配的内存将由公共语言运行时自动回收（垃圾回收）。</span><span class="sxs-lookup"><span data-stu-id="7db88-124">By contrast, the memory that is allocated for a class instance is automatically reclaimed (garbage collected) by the common language runtime when all references to the object have gone out of scope.</span></span> <span data-ttu-id="7db88-125">无法像在 C++ 中那样明确地销毁类对象。</span><span class="sxs-lookup"><span data-stu-id="7db88-125">It is not possible to deterministically destroy a class object like you can in C++.</span></span> <span data-ttu-id="7db88-126">有关 .NET 中的垃圾回收的详细信息，请参阅[垃圾回收](../../../standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="7db88-126">For more information about garbage collection in .NET, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7db88-127">公共语言运行时中高度优化了托管堆上内存的分配和释放。</span><span class="sxs-lookup"><span data-stu-id="7db88-127">The allocation and deallocation of memory on the managed heap is highly optimized in the common language runtime.</span></span> <span data-ttu-id="7db88-128">在大多数情况下，在堆上分配类实例与在堆栈上分配结构实例在性能成本上没有显著的差别。</span><span class="sxs-lookup"><span data-stu-id="7db88-128">In most cases there is no significant difference in the performance cost of allocating a class instance on the heap versus allocating a struct instance on the stack.</span></span>
  
## <a name="object-identity-vs-value-equality"></a><span data-ttu-id="7db88-129">对象标识与值相等性</span><span class="sxs-lookup"><span data-stu-id="7db88-129">Object Identity vs. Value Equality</span></span>  

 <span data-ttu-id="7db88-130">在比较两个对象是否相等时，首先必须明确是想知道两个变量是否表示内存中的同一对象，还是想知道这两个对象的一个或多个字段的值是否相等。</span><span class="sxs-lookup"><span data-stu-id="7db88-130">When you compare two objects for equality, you must first distinguish whether you want to know whether the two variables represent the same object in memory, or whether the values of one or more of their fields are equivalent.</span></span> <span data-ttu-id="7db88-131">如果要对值进行比较，则必须考虑这两个对象是值类型（结构）的实例，还是引用类型（类、委托、数组）的实例。</span><span class="sxs-lookup"><span data-stu-id="7db88-131">If you are intending to compare values, you must consider whether the objects are instances of value types (structs) or reference types (classes, delegates, arrays).</span></span>  
  
- <span data-ttu-id="7db88-132">若要确定两个类实例是否引用内存中的同一位置（这意味着它们具有相同的标识），可使用静态 <xref:System.Object.Equals%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="7db88-132">To determine whether two class instances refer to the same location in memory (which means that they have the same *identity*), use the static <xref:System.Object.Equals%2A> method.</span></span> <span data-ttu-id="7db88-133">（<xref:System.Object?displayProperty=nameWithType> 是所有值类型和引用类型的隐式基类，其中包括用户定义的结构和类。）</span><span class="sxs-lookup"><span data-stu-id="7db88-133">(<xref:System.Object?displayProperty=nameWithType> is the implicit base class for all value types and reference types, including user-defined structs and classes.)</span></span>  
  
- <span data-ttu-id="7db88-134">若要确定两个结构实例中的实例字段是否具有相同的值，可使用 <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="7db88-134">To determine whether the instance fields in two struct instances have the same values, use the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7db88-135">由于所有结构都隐式继承自 <xref:System.ValueType?displayProperty=nameWithType>，因此可以直接在对象上调用该方法，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="7db88-135">Because all structs implicitly inherit from <xref:System.ValueType?displayProperty=nameWithType>, you call the method directly on your object as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideStatements#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#32)]  
  
 <span data-ttu-id="7db88-136">`Equals` 的 <xref:System.ValueType?displayProperty=nameWithType> 实现使用反射，因为它必须能够确定任何结构中有哪些字段。</span><span class="sxs-lookup"><span data-stu-id="7db88-136">The <xref:System.ValueType?displayProperty=nameWithType> implementation of `Equals` uses reflection because it must be able to determine what the fields are in any struct.</span></span> <span data-ttu-id="7db88-137">在创建自己的结构时，重写 `Equals` 方法可以提供特定于你的类型的高效求等算法。</span><span class="sxs-lookup"><span data-stu-id="7db88-137">When creating your own structs, override the `Equals` method to provide an efficient equality algorithm that is specific to your type.</span></span>  
  
- <span data-ttu-id="7db88-138">若要确定两个类实例中字段的值是否相等，可以使用 <xref:System.Object.Equals%2A> 方法或 [== 运算符](../../language-reference/operators/equality-operators.md#equality-operator-)。</span><span class="sxs-lookup"><span data-stu-id="7db88-138">To determine whether the values of the fields in two class instances are equal, you might be able to use the <xref:System.Object.Equals%2A> method or the [== operator](../../language-reference/operators/equality-operators.md#equality-operator-).</span></span> <span data-ttu-id="7db88-139">但是，只有类通过重写或重载提供关于那种类型对象的“相等”含义的自定义时，才能使用它们。</span><span class="sxs-lookup"><span data-stu-id="7db88-139">However, only use them if the class has overridden or overloaded them to provide a custom definition of what "equality" means for objects of that type.</span></span> <span data-ttu-id="7db88-140">类也可能实现 <xref:System.IEquatable%601> 接口或 <xref:System.Collections.Generic.IEqualityComparer%601> 接口。</span><span class="sxs-lookup"><span data-stu-id="7db88-140">The class might also implement the <xref:System.IEquatable%601> interface or the <xref:System.Collections.Generic.IEqualityComparer%601> interface.</span></span> <span data-ttu-id="7db88-141">这两个接口都提供可用于测试值相等性的方法。</span><span class="sxs-lookup"><span data-stu-id="7db88-141">Both interfaces provide methods that can be used to test value equality.</span></span> <span data-ttu-id="7db88-142">设计好替代 `Equals` 的类后，请务必遵循[如何为类型定义值相等性](../statements-expressions-operators/how-to-define-value-equality-for-a-type.md)和 <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> 中介绍的准则。</span><span class="sxs-lookup"><span data-stu-id="7db88-142">When designing your own classes that override `Equals`, make sure to follow the guidelines stated in [How to define value equality for a type](../statements-expressions-operators/how-to-define-value-equality-for-a-type.md) and <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="7db88-143">相关章节</span><span class="sxs-lookup"><span data-stu-id="7db88-143">Related Sections</span></span>  

 <span data-ttu-id="7db88-144">更多相关信息：</span><span class="sxs-lookup"><span data-stu-id="7db88-144">For more information:</span></span>  
  
- [<span data-ttu-id="7db88-145">类</span><span class="sxs-lookup"><span data-stu-id="7db88-145">Classes</span></span>](./classes.md)  
  
- [<span data-ttu-id="7db88-146">构造函数</span><span class="sxs-lookup"><span data-stu-id="7db88-146">Constructors</span></span>](./constructors.md)  
  
- [<span data-ttu-id="7db88-147">终结器</span><span class="sxs-lookup"><span data-stu-id="7db88-147">Finalizers</span></span>](./destructors.md)  
  
- [<span data-ttu-id="7db88-148">事件</span><span class="sxs-lookup"><span data-stu-id="7db88-148">Events</span></span>](../events/index.md)  
  
## <a name="see-also"></a><span data-ttu-id="7db88-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="7db88-149">See also</span></span>

- [<span data-ttu-id="7db88-150">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="7db88-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7db88-151">object</span><span class="sxs-lookup"><span data-stu-id="7db88-151">object</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="7db88-152">继承</span><span class="sxs-lookup"><span data-stu-id="7db88-152">Inheritance</span></span>](./inheritance.md)
- [<span data-ttu-id="7db88-153">class</span><span class="sxs-lookup"><span data-stu-id="7db88-153">class</span></span>](../../language-reference/keywords/class.md)
- [<span data-ttu-id="7db88-154">结构类型</span><span class="sxs-lookup"><span data-stu-id="7db88-154">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="7db88-155">new 运算符</span><span class="sxs-lookup"><span data-stu-id="7db88-155">new Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="7db88-156">常规类型系统</span><span class="sxs-lookup"><span data-stu-id="7db88-156">Common Type System</span></span>](../../../standard/base-types/common-type-system.md)
