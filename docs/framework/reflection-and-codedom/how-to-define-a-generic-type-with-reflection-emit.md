---
title: 如何：使用反射发出定义泛型类型
description: 了解如何使用反射发出定义泛型类型。 创建具有两种类型参数的泛型类型、应用类约束、接口约束等。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- generics [.NET Framework], dynamic types
- reflection emit, generic types
ms.assetid: 07d5f01a-7b5b-40ea-9b15-f21561098fe4
ms.openlocfilehash: bf308b07bf4b2a863b9825e7c8d9f412bdb6d1b8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559208"
---
# <a name="how-to-define-a-generic-type-with-reflection-emit"></a><span data-ttu-id="110c8-104">如何：使用反射发出定义泛型类型</span><span class="sxs-lookup"><span data-stu-id="110c8-104">How to: Define a Generic Type with Reflection Emit</span></span>
<span data-ttu-id="110c8-105">此主题说明如何创建具有两个参数的简单泛型类型、如何对类型参数应用类约束、接口约束和特殊约束，以及如何创建使用类的类型参数作为参数类型和返回类型的成员。</span><span class="sxs-lookup"><span data-stu-id="110c8-105">This topic shows how to create a simple generic type with two type parameters, how to apply class constraints, interface constraints, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="110c8-106">某方法只要属于泛型类型，且使用该类型的类型参数，就不是泛型方法。</span><span class="sxs-lookup"><span data-stu-id="110c8-106">A method is not generic just because it belongs to a generic type and uses the type parameters of that type.</span></span> <span data-ttu-id="110c8-107">只有当方法有属于自己的类型参数列表时才是泛型方法。</span><span class="sxs-lookup"><span data-stu-id="110c8-107">A method is generic only if it has its own type parameter list.</span></span> <span data-ttu-id="110c8-108">多数泛型类型上的方法都不是泛型方法，如本示例所示。</span><span class="sxs-lookup"><span data-stu-id="110c8-108">Most methods on generic types are not generic, as in this example.</span></span> <span data-ttu-id="110c8-109">有关发出泛型方法的示例，请参阅[如何：使用反射发出定义泛型方法](how-to-define-a-generic-method-with-reflection-emit.md)。</span><span class="sxs-lookup"><span data-stu-id="110c8-109">For an example of emitting a generic method, see [How to: Define a Generic Method with Reflection Emit](how-to-define-a-generic-method-with-reflection-emit.md).</span></span>  
  
### <a name="to-define-a-generic-type"></a><span data-ttu-id="110c8-110">定义泛型类型</span><span class="sxs-lookup"><span data-stu-id="110c8-110">To define a generic type</span></span>  
  
1. <span data-ttu-id="110c8-111">定义名为 `GenericEmitExample1` 的动态程序集。</span><span class="sxs-lookup"><span data-stu-id="110c8-111">Define a dynamic assembly named `GenericEmitExample1`.</span></span> <span data-ttu-id="110c8-112">在此示例中，执行了程序集并将其保存到磁盘中，所以指定了 <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="110c8-112">In this example, the assembly is executed and saved to disk, so <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> is specified.</span></span>  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2. <span data-ttu-id="110c8-113">定义动态模块。</span><span class="sxs-lookup"><span data-stu-id="110c8-113">Define a dynamic module.</span></span> <span data-ttu-id="110c8-114">程序集由可执行模块组成。</span><span class="sxs-lookup"><span data-stu-id="110c8-114">An assembly is made up of executable modules.</span></span> <span data-ttu-id="110c8-115">对于单模块程序集，模块名称与程序集名称相同，文件名为模块名称加上扩展名。</span><span class="sxs-lookup"><span data-stu-id="110c8-115">For a single-module assembly, the module name is the same as the assembly name, and the file name is the module name plus an extension.</span></span>  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3. <span data-ttu-id="110c8-116">定义类。</span><span class="sxs-lookup"><span data-stu-id="110c8-116">Define a class.</span></span> <span data-ttu-id="110c8-117">在此示例中，类命名为 `Sample`。</span><span class="sxs-lookup"><span data-stu-id="110c8-117">In this example, the class is named `Sample`.</span></span>  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4. <span data-ttu-id="110c8-118">通过将包含参数名称的字符串数组传递给 <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> 方法来定义 `Sample` 的泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="110c8-118">Define the generic type parameters of `Sample` by passing an array of strings containing the names of the parameters to the <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="110c8-119">这将使该类成为泛型类型。</span><span class="sxs-lookup"><span data-stu-id="110c8-119">This makes the class a generic type.</span></span> <span data-ttu-id="110c8-120">返回值是表示类型参数的 <xref:System.Reflection.Emit.GenericTypeParameterBuilder> 对象数组，可用于发出的代码。</span><span class="sxs-lookup"><span data-stu-id="110c8-120">The return value is an array of <xref:System.Reflection.Emit.GenericTypeParameterBuilder> objects representing the type parameters, which can be used in your emitted code.</span></span>  
  
     <span data-ttu-id="110c8-121">在以下代码中，`Sample` 将成为具有类型参数 `TFirst` 和 `TSecond` 的泛型类型。</span><span class="sxs-lookup"><span data-stu-id="110c8-121">In the following code, `Sample` becomes a generic type with type parameters `TFirst` and `TSecond`.</span></span> <span data-ttu-id="110c8-122">为了使代码更易于阅读，每个 <xref:System.Reflection.Emit.GenericTypeParameterBuilder> 都将放置在与类型参数同名的变量中。</span><span class="sxs-lookup"><span data-stu-id="110c8-122">To make the code easier to read, each <xref:System.Reflection.Emit.GenericTypeParameterBuilder> is placed in a variable with the same name as the type parameter.</span></span>  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5. <span data-ttu-id="110c8-123">向类型参数添加特殊约束。</span><span class="sxs-lookup"><span data-stu-id="110c8-123">Add special constraints to the type parameters.</span></span> <span data-ttu-id="110c8-124">在此示例中，类型参数 `TFirst` 被限制为具有无参数构造函数的类型以及引用类型。</span><span class="sxs-lookup"><span data-stu-id="110c8-124">In this example, type parameter `TFirst` is constrained to types that have parameterless constructors, and to reference types.</span></span>  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6. <span data-ttu-id="110c8-125">可以选择向类型参数添加类约束和接口约束。</span><span class="sxs-lookup"><span data-stu-id="110c8-125">Optionally add class and interface constraints to the type parameters.</span></span> <span data-ttu-id="110c8-126">在此示例中，类型参数 `TFirst` 被限制为从 `baseType` 变量包含的 <xref:System.Type> 对象所表示的基类中派生的类型，以及实现接口类型包含在变量 `interfaceA` 和 `interfaceB` 中的接口的类型。</span><span class="sxs-lookup"><span data-stu-id="110c8-126">In this example, type parameter `TFirst` is constrained to types that derive from the base class represented by the <xref:System.Type> object contained in the variable `baseType`, and that implement the interfaces whose types are contained in the variables `interfaceA` and `interfaceB`.</span></span> <span data-ttu-id="110c8-127">有关这些变量的声明和分配，请参阅代码示例。</span><span class="sxs-lookup"><span data-stu-id="110c8-127">See the code example for the declaration and assignment of these variables.</span></span>  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7. <span data-ttu-id="110c8-128">定义字段。</span><span class="sxs-lookup"><span data-stu-id="110c8-128">Define a field.</span></span> <span data-ttu-id="110c8-129">在此示例中，该字段的类型由类型参数 `TFirst` 指定。</span><span class="sxs-lookup"><span data-stu-id="110c8-129">In this example, the type of the field is specified by type parameter `TFirst`.</span></span> <span data-ttu-id="110c8-130"><xref:System.Reflection.Emit.GenericTypeParameterBuilder> 派生自 <xref:System.Type>，因此可在任何能够使用类型的位置使用泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="110c8-130"><xref:System.Reflection.Emit.GenericTypeParameterBuilder> derives from <xref:System.Type>, so you can use generic type parameters anywhere a type can be used.</span></span>  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8. <span data-ttu-id="110c8-131">定义使用泛型类型的类型参数的方法。</span><span class="sxs-lookup"><span data-stu-id="110c8-131">Define a method that uses the type parameters of the generic type.</span></span> <span data-ttu-id="110c8-132">请注意，此类方法不是泛型方法，除非它们具有自己的类型参数列表。</span><span class="sxs-lookup"><span data-stu-id="110c8-132">Note that such methods are not generic unless they have their own type parameter lists.</span></span> <span data-ttu-id="110c8-133">以下代码定义一个 `static` 方法（在 Visual Basic 中为 `Shared`），该方法接收一个 `TFirst` 数组并返回包含该数组所有元素的 `List<TFirst>`（在 Visual Basic 中为 `List(Of TFirst)`）。</span><span class="sxs-lookup"><span data-stu-id="110c8-133">The following code defines a `static` method (`Shared` in Visual Basic) that takes an array of `TFirst` and returns a `List<TFirst>` (`List(Of TFirst)` in Visual Basic) containing all the elements of the array.</span></span> <span data-ttu-id="110c8-134">若要定义此方法，需要通过调用泛型类型定义 `List<T>` 上的 <xref:System.Type.MakeGenericType%2A> 来创建类型 `List<TFirst>`。</span><span class="sxs-lookup"><span data-stu-id="110c8-134">To define this method, it is necessary to create the type `List<TFirst>` by calling <xref:System.Type.MakeGenericType%2A> on the generic type definition, `List<T>`.</span></span> <span data-ttu-id="110c8-135">（使用 `typeof` 运算符（在 Visual Basic 中为 `GetType`）获取泛型类型定义时，将忽略 `T`。）通过使用 <xref:System.Type.MakeArrayType%2A> 方法创建参数类型。</span><span class="sxs-lookup"><span data-stu-id="110c8-135">(The `T` is omitted when you use the `typeof` operator (`GetType` in Visual Basic) to get the generic type definition.) The parameter type is created by using the <xref:System.Type.MakeArrayType%2A> method.</span></span>  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. <span data-ttu-id="110c8-136">发出方法主体。</span><span class="sxs-lookup"><span data-stu-id="110c8-136">Emit the method body.</span></span> <span data-ttu-id="110c8-137">方法主体由三个操作码组成，这些操作码将输入数组加载到堆栈，调用接收 `IEnumerable<TFirst>` 的 `List<TFirst>` 构造函数（该函数完成将输入元素放入列表的所有工作）并返回（将新的 <xref:System.Collections.Generic.List%601> 对象留在堆栈中）。</span><span class="sxs-lookup"><span data-stu-id="110c8-137">The method body consists of three opcodes that load the input array onto the stack, call the `List<TFirst>` constructor that takes `IEnumerable<TFirst>` (which does all the work of putting the input elements into the list), and return (leaving the new <xref:System.Collections.Generic.List%601> object on the stack).</span></span> <span data-ttu-id="110c8-138">发出此代码的难点在于获取构造函数。</span><span class="sxs-lookup"><span data-stu-id="110c8-138">The difficult part of emitting this code is getting the constructor.</span></span>  
  
     <span data-ttu-id="110c8-139"><xref:System.Reflection.Emit.GenericTypeParameterBuilder> 中不支持 <xref:System.Type.GetConstructor%2A> 方法，所以不可能直接获取 `List<TFirst>` 的构造函数。</span><span class="sxs-lookup"><span data-stu-id="110c8-139">The <xref:System.Type.GetConstructor%2A> method is not supported on a <xref:System.Reflection.Emit.GenericTypeParameterBuilder>, so it is not possible to get the constructor of `List<TFirst>` directly.</span></span> <span data-ttu-id="110c8-140">首先，必须获取泛型类型定义 `List<T>` 的构造函数，然后调用一种可将其转换为 `List<TFirst>` 的对应构造函数的方法。</span><span class="sxs-lookup"><span data-stu-id="110c8-140">First, it is necessary to get the constructor of the generic type definition `List<T>` and then to call a method that converts it to the corresponding constructor of `List<TFirst>`.</span></span>  
  
     <span data-ttu-id="110c8-141">用于此代码示例的构造函数接收 `IEnumerable<T>`。</span><span class="sxs-lookup"><span data-stu-id="110c8-141">The constructor used for this code example takes an `IEnumerable<T>`.</span></span> <span data-ttu-id="110c8-142">但请注意，这不是 <xref:System.Collections.Generic.IEnumerable%601> 泛型接口的泛型类型定义；相反，必须将 `List<T>` 的类型参数 `T` 替代为 `IEnumerable<T>` 的类型参数 `T`。</span><span class="sxs-lookup"><span data-stu-id="110c8-142">Note, however, that this is not the generic type definition of the <xref:System.Collections.Generic.IEnumerable%601> generic interface; instead, the type parameter `T` from `List<T>` must be substituted for the type parameter `T` of `IEnumerable<T>`.</span></span> <span data-ttu-id="110c8-143">（这似乎容易混淆，因为这两个类型都具有名为 `T` 的类型参数。</span><span class="sxs-lookup"><span data-stu-id="110c8-143">(This seems confusing only because both types have type parameters named `T`.</span></span> <span data-ttu-id="110c8-144">这就是此代码示例使用名称 `TFirst` 和 `TSecond` 的原因。）若要获取构造函数的参数类型，请从泛型类型定义 `IEnumerable<T>` 开始并使用 `List<T>` 的第一个泛型类型参数调用 <xref:System.Type.MakeGenericType%2A>。</span><span class="sxs-lookup"><span data-stu-id="110c8-144">That is why this code example uses the names `TFirst` and `TSecond`.) To get the type of the constructor argument, start with the generic type definition `IEnumerable<T>` and call <xref:System.Type.MakeGenericType%2A> with the first generic type parameter of `List<T>`.</span></span> <span data-ttu-id="110c8-145">构造函数参数列表必须作为数组进行传递，在本例中只有一个参数。</span><span class="sxs-lookup"><span data-stu-id="110c8-145">The constructor argument list must be passed as an array, with just one argument in this case.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="110c8-146">在 C# 中使用 `typeof` 运算符时，泛型类型定义将表达为 `IEnumerable<>`；在 Visual Basic 中使用 `GetType` 运算符时，泛型类型定义将表达为 `IEnumerable(Of )`。</span><span class="sxs-lookup"><span data-stu-id="110c8-146">The generic type definition is expressed as `IEnumerable<>` when you use the `typeof` operator in C#, or `IEnumerable(Of )` when you use the `GetType` operator in Visual Basic.</span></span>  
  
     <span data-ttu-id="110c8-147">现在，可以通过调用泛型类型定义上的 <xref:System.Type.GetConstructor%2A> 来获取 `List<T>` 的构造函数。</span><span class="sxs-lookup"><span data-stu-id="110c8-147">Now it is possible to get the constructor of `List<T>` by calling <xref:System.Type.GetConstructor%2A> on the generic type definition.</span></span> <span data-ttu-id="110c8-148">若要将此构造函数转换为 `List<TFirst>` 对应的构造函数，请将 `List<TFirst>` 和 `List<T>` 的构造函数传递给静态 <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="110c8-148">To convert this constructor to the corresponding constructor of `List<TFirst>`, pass `List<TFirst>` and the constructor from `List<T>` to the static <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=nameWithType> method.</span></span>  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. <span data-ttu-id="110c8-149">创建类型，并保存文件。</span><span class="sxs-lookup"><span data-stu-id="110c8-149">Create the type and save the file.</span></span>  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. <span data-ttu-id="110c8-150">调用方法。</span><span class="sxs-lookup"><span data-stu-id="110c8-150">Invoke the method.</span></span> <span data-ttu-id="110c8-151">`ExampleMethod` 不是泛型，但它所属的类型为泛型，因此，为了获取可以调用的 <xref:System.Reflection.MethodInfo>，需要从 `Sample` 的类型定义创建一个构造类型。</span><span class="sxs-lookup"><span data-stu-id="110c8-151">`ExampleMethod` is not generic, but the type it belongs to is generic, so in order to get a <xref:System.Reflection.MethodInfo> that can be invoked it is necessary to create a constructed type from the type definition for `Sample`.</span></span> <span data-ttu-id="110c8-152">该构造类型使用 `Example` 类和 `ExampleDerived` 类，前者满足 `TFirst` 上的约束，因为它是引用类型并且具有默认的无参数构造函数，后者满足 `TSecond` 上的约束。</span><span class="sxs-lookup"><span data-stu-id="110c8-152">The constructed type uses the `Example` class, which satisfies the constraints on `TFirst` because it is a reference type and has a default parameterless constructor, and the `ExampleDerived` class which satisfies the constraints on `TSecond`.</span></span> <span data-ttu-id="110c8-153">（示例代码部分提供了 `ExampleDerived` 的代码。）将这两个类型传递给 <xref:System.Type.MakeGenericType%2A> 以创建构造类型。</span><span class="sxs-lookup"><span data-stu-id="110c8-153">(The code for `ExampleDerived` can be found in the example code section.) These two types are passed to <xref:System.Type.MakeGenericType%2A> to create the constructed type.</span></span> <span data-ttu-id="110c8-154">然后使用 <xref:System.Type.GetMethod%2A> 方法获取 <xref:System.Reflection.MethodInfo>。</span><span class="sxs-lookup"><span data-stu-id="110c8-154">The <xref:System.Reflection.MethodInfo> is then obtained using the <xref:System.Type.GetMethod%2A> method.</span></span>  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. <span data-ttu-id="110c8-155">以下代码将创建一个 `Example` 对象数组，将该数组放在类型为 <xref:System.Object>，表示要调用的方法的参数的数组中，然后将创建的数组传递给 <xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="110c8-155">The following code creates an array of `Example` objects, places that array in an array of type <xref:System.Object> representing the arguments of the method to be invoked, and passes them to the <xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> method.</span></span> <span data-ttu-id="110c8-156"><xref:System.Reflection.MethodBase.Invoke%2A> 方法的第一个参数是空引用，因为该方法为 `static`。</span><span class="sxs-lookup"><span data-stu-id="110c8-156">The first argument of the <xref:System.Reflection.MethodBase.Invoke%2A> method is a null reference because the method is `static`.</span></span>  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="110c8-157">示例</span><span class="sxs-lookup"><span data-stu-id="110c8-157">Example</span></span>  
 <span data-ttu-id="110c8-158">以下代码示例定义一个名为 `Sample` 的类，还定义一个基类和两个接口。</span><span class="sxs-lookup"><span data-stu-id="110c8-158">The following code example defines a class named `Sample`, along with a base class and two interfaces.</span></span> <span data-ttu-id="110c8-159">该程序可为 `Sample` 定义两个泛型类型参数，使其成为泛型类型。</span><span class="sxs-lookup"><span data-stu-id="110c8-159">The program defines two generic type parameters for `Sample`, turning it into a generic type.</span></span> <span data-ttu-id="110c8-160">只有类型参数能使一个类型成为泛型类型。</span><span class="sxs-lookup"><span data-stu-id="110c8-160">Type parameters are the only thing that makes a type generic.</span></span> <span data-ttu-id="110c8-161">该程序通过显示定义类型参数前后的测试消息来对此进行演示。</span><span class="sxs-lookup"><span data-stu-id="110c8-161">The program shows this by displaying a test message before and after the definition of the type parameters.</span></span>  
  
 <span data-ttu-id="110c8-162">类型参数 `TSecond` 用于通过基类和接口来演示类和接口约束，类型参数 `TFirst` 用于演示特殊约束。</span><span class="sxs-lookup"><span data-stu-id="110c8-162">The type parameter `TSecond` is used to demonstrate class and interface constraints, using the base class and interfaces, and the type parameter `TFirst` is used to demonstrate special constraints.</span></span>  
  
 <span data-ttu-id="110c8-163">此代码示例针对字段类型以及方法的参数和返回类型，通过使用该类的类型参数定义字段和方法。</span><span class="sxs-lookup"><span data-stu-id="110c8-163">The code example defines a field and a method using the class's type parameters for the field type and for the parameter and return type of the method.</span></span>  
  
 <span data-ttu-id="110c8-164">创建 `Sample` 类后，调用该方法。</span><span class="sxs-lookup"><span data-stu-id="110c8-164">After the `Sample` class has been created, the method is invoked.</span></span>  
  
 <span data-ttu-id="110c8-165">该程序中包括一个可列出泛型类型信息的方法，和一个可列出类型参数上的特殊约束的方法。</span><span class="sxs-lookup"><span data-stu-id="110c8-165">The program includes a method that lists information about a generic type, and a method that lists the special constraints on a type parameter.</span></span> <span data-ttu-id="110c8-166">这些方法用于显示有关已完成的 `Sample` 类的信息。</span><span class="sxs-lookup"><span data-stu-id="110c8-166">These methods are used to display information about the finished `Sample` class.</span></span>  
  
 <span data-ttu-id="110c8-167">程序将完成的模块以 `GenericEmitExample1.dll` 的形式保存到磁盘中，所以可以使用 [Ildasm.exe（IL 反汇编程序）](../tools/ildasm-exe-il-disassembler.md)将其打开，并检查 `Sample` 类的 MSIL。</span><span class="sxs-lookup"><span data-stu-id="110c8-167">The program saves the finished module to disk as `GenericEmitExample1.dll`, so you can open it with the [Ildasm.exe (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) and examine the MSIL for the `Sample` class.</span></span>  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="110c8-168">请参阅</span><span class="sxs-lookup"><span data-stu-id="110c8-168">See also</span></span>

- <xref:System.Reflection.Emit.GenericTypeParameterBuilder>
- <span data-ttu-id="110c8-169">[使用反射发出](/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="110c8-169">[Using Reflection Emit](/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))</span></span>
- <span data-ttu-id="110c8-170">[反射发出动态程序集应用场景](/previous-versions/dotnet/netframework-4.0/tt9483fk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="110c8-170">[Reflection Emit Dynamic Assembly Scenarios](/previous-versions/dotnet/netframework-4.0/tt9483fk(v=vs.100))</span></span>
