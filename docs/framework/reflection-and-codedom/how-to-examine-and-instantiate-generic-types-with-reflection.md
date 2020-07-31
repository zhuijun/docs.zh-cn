---
title: 如何：使用反射检查和实例化泛型类型
description: 了解如何使用反射检查和实例化泛型类型。 使用 IsGenericType、IsGenericParameter 和 GenericParameterPosition 属性。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
ms.openlocfilehash: b57a0ed0c809da442dc9fcf202ad364060971f80
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865094"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a><span data-ttu-id="20c87-104">如何：使用反射检查和实例化泛型类型</span><span class="sxs-lookup"><span data-stu-id="20c87-104">How to: Examine and Instantiate Generic Types with Reflection</span></span>
<span data-ttu-id="20c87-105">获取泛型类型信息的方式与获取其他类型信息的方式相同：检查表示泛型类型的 <xref:System.Type> 对象。</span><span class="sxs-lookup"><span data-stu-id="20c87-105">Information about generic types is obtained in the same way as information about other types: by examining a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="20c87-106">主要的差异在于，泛型类型具有表示其泛型类型参数的 <xref:System.Type> 对象列表。</span><span class="sxs-lookup"><span data-stu-id="20c87-106">The principle difference is that a generic type has a list of <xref:System.Type> objects representing its generic type parameters.</span></span> <span data-ttu-id="20c87-107">本部分的第一个过程是检查泛型类型。</span><span class="sxs-lookup"><span data-stu-id="20c87-107">The first procedure in this section examines generic types.</span></span>  
  
 <span data-ttu-id="20c87-108">通过将类型实参绑定到泛型类型定义的类型形参，可以创建表示构造类型的 <xref:System.Type> 对象。</span><span class="sxs-lookup"><span data-stu-id="20c87-108">You can create a <xref:System.Type> object that represents a constructed type by binding type arguments to the type parameters of a generic type definition.</span></span> <span data-ttu-id="20c87-109">第二个过程对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="20c87-109">The second procedure demonstrates this.</span></span>  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a><span data-ttu-id="20c87-110">检查泛型类型及其类型参数</span><span class="sxs-lookup"><span data-stu-id="20c87-110">To examine a generic type and its type parameters</span></span>  
  
1. <span data-ttu-id="20c87-111">获取表示泛型类型的 <xref:System.Type> 实例。</span><span class="sxs-lookup"><span data-stu-id="20c87-111">Get an instance of <xref:System.Type> that represents the generic type.</span></span> <span data-ttu-id="20c87-112">在下面的代码中，使用 C# 的 `typeof` 运算符（在 Visual Basic 中为 `GetType`，在 Visual C++ 中为 `typeid`）获取类型。</span><span class="sxs-lookup"><span data-stu-id="20c87-112">In the following code, the type is obtained using the C# `typeof` operator (`GetType` in Visual Basic, `typeid` in Visual C++).</span></span> <span data-ttu-id="20c87-113">有关获取 <xref:System.Type> 对象的其他方法，请参阅 <xref:System.Type> 类主题。</span><span class="sxs-lookup"><span data-stu-id="20c87-113">See the <xref:System.Type> class topic for other ways to get a <xref:System.Type> object.</span></span> <span data-ttu-id="20c87-114">请注意，在余下的过程中，类型包含在名为 `t` 的方法参数中。</span><span class="sxs-lookup"><span data-stu-id="20c87-114">Note that in the rest of this procedure, the type is contained in a method parameter named `t`.</span></span>  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. <span data-ttu-id="20c87-115">使用 <xref:System.Type.IsGenericType%2A> 属性确定类型是否为泛型，然后使用 <xref:System.Type.IsGenericTypeDefinition%2A> 属性确定类型是否为泛型类型定义。</span><span class="sxs-lookup"><span data-stu-id="20c87-115">Use the <xref:System.Type.IsGenericType%2A> property to determine whether the type is generic, and use the <xref:System.Type.IsGenericTypeDefinition%2A> property to determine whether the type is a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. <span data-ttu-id="20c87-116">使用 <xref:System.Type.GetGenericArguments%2A> 方法获取包含泛型类型参数的数组。</span><span class="sxs-lookup"><span data-stu-id="20c87-116">Get an array that contains the generic type arguments, using the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. <span data-ttu-id="20c87-117">对于每个类型实参，使用 <xref:System.Type.IsGenericParameter%2A> 属性确定它是类型形参（例如，在泛型类型定义中），还是为类型形参指定的类型（例如，在构造类型中）。</span><span class="sxs-lookup"><span data-stu-id="20c87-117">For each type argument, determine whether it is a type parameter (for example, in a generic type definition) or a type that has been specified for a type parameter (for example, in a constructed type), using the <xref:System.Type.IsGenericParameter%2A> property.</span></span>  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. <span data-ttu-id="20c87-118">在类型系统中，和普通类型一样，泛型类型参数由 <xref:System.Type> 实例表示。</span><span class="sxs-lookup"><span data-stu-id="20c87-118">In the type system, a generic type parameter is represented by an instance of <xref:System.Type>, just as ordinary types are.</span></span> <span data-ttu-id="20c87-119">以下代码显示表示泛型类型参数的 <xref:System.Type> 对象的名称和参数位置。</span><span class="sxs-lookup"><span data-stu-id="20c87-119">The following code displays the name and parameter position of a <xref:System.Type> object that represents a generic type parameter.</span></span> <span data-ttu-id="20c87-120">此处，参数位置无足轻重；它在用户检查已用作其他泛型类型的类型实参的类型形参时更有价值。</span><span class="sxs-lookup"><span data-stu-id="20c87-120">The parameter position is trivial information here; it is of more interest when you are examining a type parameter that has been used as a type argument of another generic type.</span></span>  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. <span data-ttu-id="20c87-121">通过使用 <xref:System.Type.GetGenericParameterConstraints%2A> 方法获取单个数组中的所有约束，确定泛型类型参数的基类型约束和接口约束。</span><span class="sxs-lookup"><span data-stu-id="20c87-121">Determine the base type constraint and the interface constraints of a generic type parameter by using the <xref:System.Type.GetGenericParameterConstraints%2A> method to obtain all the constraints in a single array.</span></span> <span data-ttu-id="20c87-122">不保证约束以任何特定顺序排列。</span><span class="sxs-lookup"><span data-stu-id="20c87-122">Constraints are not guaranteed to be in any particular order.</span></span>  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. <span data-ttu-id="20c87-123">使用 <xref:System.Type.GenericParameterAttributes%2A> 属性发现类型参数的特殊约束，如要求其作为引用类型。</span><span class="sxs-lookup"><span data-stu-id="20c87-123">Use the <xref:System.Type.GenericParameterAttributes%2A> property to discover the special constraints on a type parameter, such as requiring that it be a reference type.</span></span> <span data-ttu-id="20c87-124">该属性还包含表示方差的值，该值可屏蔽，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="20c87-124">The property also includes values that represent variance, which you can mask off as shown in the following code.</span></span>  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. <span data-ttu-id="20c87-125">特殊约束属性为标志，表示没有任何特殊约束的相同标志 (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) 还表示没有协变或逆变。</span><span class="sxs-lookup"><span data-stu-id="20c87-125">The special constraint attributes are flags, and the same flag (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) that represents no special constraints also represents no covariance or contravariance.</span></span> <span data-ttu-id="20c87-126">因此，若要测试其中一项条件，则必须使用适当的掩码。</span><span class="sxs-lookup"><span data-stu-id="20c87-126">Thus, to test for either of these conditions you must use the appropriate mask.</span></span> <span data-ttu-id="20c87-127">在这种情况下，请使用 <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> 隔离特殊约束标志。</span><span class="sxs-lookup"><span data-stu-id="20c87-127">In this case, use <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> to isolate the special constraint flags.</span></span>  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a><span data-ttu-id="20c87-128">构造泛型类型的实例</span><span class="sxs-lookup"><span data-stu-id="20c87-128">Constructing an Instance of a Generic Type</span></span>  
 <span data-ttu-id="20c87-129">泛型类型和模板类似。</span><span class="sxs-lookup"><span data-stu-id="20c87-129">A generic type is like a template.</span></span> <span data-ttu-id="20c87-130">除非指定其泛型类型参数的实际类型，否则不能创建泛型类型的实例。</span><span class="sxs-lookup"><span data-stu-id="20c87-130">You cannot create instances of it unless you specify real types for its generic type parameters.</span></span> <span data-ttu-id="20c87-131">若要在运行时执行此操作，则需要使用 <xref:System.Type.MakeGenericType%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="20c87-131">To do this at run time, using reflection, requires the <xref:System.Type.MakeGenericType%2A> method.</span></span>  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a><span data-ttu-id="20c87-132">构造泛型类型的实例</span><span class="sxs-lookup"><span data-stu-id="20c87-132">To construct an instance of a generic type</span></span>  
  
1. <span data-ttu-id="20c87-133">获取表示泛型类型的 <xref:System.Type> 对象。</span><span class="sxs-lookup"><span data-stu-id="20c87-133">Get a <xref:System.Type> object that represents the generic type.</span></span> <span data-ttu-id="20c87-134">以下代码以两种不同方式获取泛型类型 <xref:System.Collections.Generic.Dictionary%602>：一种是使用 <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> 方法重载和描述类型的字符串，另一种是调用构造类型 `Dictionary\<String, Example>`（在 Visual Basic 中为 `Dictionary(Of String, Example)`）的 <xref:System.Type.GetGenericTypeDefinition%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="20c87-134">The following code gets the generic type <xref:System.Collections.Generic.Dictionary%602> in two different ways: by using the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method overload with a string describing the type, and by calling the <xref:System.Type.GetGenericTypeDefinition%2A> method on the constructed type `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` in Visual Basic).</span></span> <span data-ttu-id="20c87-135"><xref:System.Type.MakeGenericType%2A> 方法需要泛型类型定义。</span><span class="sxs-lookup"><span data-stu-id="20c87-135">The <xref:System.Type.MakeGenericType%2A> method requires a generic type definition.</span></span>  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. <span data-ttu-id="20c87-136">构造用于替代类型形参的类型实参数组。</span><span class="sxs-lookup"><span data-stu-id="20c87-136">Construct an array of type arguments to substitute for the type parameters.</span></span> <span data-ttu-id="20c87-137">该数组必须包含正确数目的 <xref:System.Type> 对象，并且顺序和它们在类型形参列表中的顺序相同。</span><span class="sxs-lookup"><span data-stu-id="20c87-137">The array must contain the correct number of <xref:System.Type> objects, in the same order as they appear in the type parameter list.</span></span> <span data-ttu-id="20c87-138">在这种情况下，键（第一个类型形参）的类型为 <xref:System.String>，字典中的值是名为 `Example` 的类的实例。</span><span class="sxs-lookup"><span data-stu-id="20c87-138">In this case, the key (first type parameter) is of type <xref:System.String>, and the values in the dictionary are instances of a class named `Example`.</span></span>  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. <span data-ttu-id="20c87-139">调用 <xref:System.Type.MakeGenericType%2A> 方法，将类型实参绑定到类型形参，然后构造类型。</span><span class="sxs-lookup"><span data-stu-id="20c87-139">Call the <xref:System.Type.MakeGenericType%2A> method to bind the type arguments to the type parameters and construct the type.</span></span>  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. <span data-ttu-id="20c87-140">使用 <xref:System.Activator.CreateInstance%28System.Type%29> 方法重载来创建构造类型的对象。</span><span class="sxs-lookup"><span data-stu-id="20c87-140">Use the <xref:System.Activator.CreateInstance%28System.Type%29> method overload to create an object of the constructed type.</span></span> <span data-ttu-id="20c87-141">以下代码在生成的 `Dictionary<String, Example>` 对象中存储 `Example` 类的两个实例。</span><span class="sxs-lookup"><span data-stu-id="20c87-141">The following code stores two instances of the `Example` class in the resulting `Dictionary<String, Example>` object.</span></span>  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="20c87-142">示例</span><span class="sxs-lookup"><span data-stu-id="20c87-142">Example</span></span>  
 <span data-ttu-id="20c87-143">下面的代码示例定义 `DisplayGenericType` 方法来检查代码中使用的泛型类型定义和构造类型，并显示它们的信息。</span><span class="sxs-lookup"><span data-stu-id="20c87-143">The following code example defines a `DisplayGenericType` method to examine the generic type definitions and constructed types used in the code and display their information.</span></span> <span data-ttu-id="20c87-144">`DisplayGenericType` 方法演示如何使用 <xref:System.Type.IsGenericType%2A>、<xref:System.Type.IsGenericParameter%2A> 和 <xref:System.Type.GenericParameterPosition%2A> 属性以及 <xref:System.Type.GetGenericArguments%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="20c87-144">The `DisplayGenericType` method shows how to use the <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, and <xref:System.Type.GenericParameterPosition%2A> properties and the <xref:System.Type.GetGenericArguments%2A> method.</span></span>  
  
 <span data-ttu-id="20c87-145">该示例还定义 `DisplayGenericParameter` 方法来检查泛型类型参数，并显示其约束。</span><span class="sxs-lookup"><span data-stu-id="20c87-145">The example also defines a `DisplayGenericParameter` method to examine a generic type parameter and display its constraints.</span></span>  
  
 <span data-ttu-id="20c87-146">代码示例定义一组测试类型，包括说明类型参数约束的泛型类型，并演示如何显示这些类型的信息。</span><span class="sxs-lookup"><span data-stu-id="20c87-146">The code example defines a set of test types, including a generic type that illustrates type parameter constraints, and shows how to display information about these types.</span></span>  
  
 <span data-ttu-id="20c87-147">示例通过创建类型参数数组并调用 <xref:System.Type.MakeGenericType%2A> 方法，从 <xref:System.Collections.Generic.Dictionary%602> 类构造类型。</span><span class="sxs-lookup"><span data-stu-id="20c87-147">The example constructs a type from the <xref:System.Collections.Generic.Dictionary%602> class by creating an array of type arguments and calling the <xref:System.Type.MakeGenericType%2A> method.</span></span> <span data-ttu-id="20c87-148">程序将使用 <xref:System.Type.MakeGenericType%2A> 构造的 <xref:System.Type> 对象和使用 `typeof`（在 Visual Basic 中为 `GetType`）获取的 <xref:System.Type> 对象进行比较，演示这两个对象是相同的。</span><span class="sxs-lookup"><span data-stu-id="20c87-148">The program compares the <xref:System.Type> object constructed using <xref:System.Type.MakeGenericType%2A> with a <xref:System.Type> object obtained using `typeof` (`GetType` in Visual Basic), demonstrating that they are the same.</span></span> <span data-ttu-id="20c87-149">类似地，程序使用 <xref:System.Type.GetGenericTypeDefinition%2A> 方法获取构造类型的泛型类型定义，并将其与表示 <xref:System.Collections.Generic.Dictionary%602> 类的 <xref:System.Type> 对象进行比较。</span><span class="sxs-lookup"><span data-stu-id="20c87-149">Similarly, the program uses the <xref:System.Type.GetGenericTypeDefinition%2A> method to obtain the generic type definition of the constructed type, and compares it to the <xref:System.Type> object representing the <xref:System.Collections.Generic.Dictionary%602> class.</span></span>  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="20c87-150">请参阅</span><span class="sxs-lookup"><span data-stu-id="20c87-150">See also</span></span>

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="20c87-151">反射类型和泛型类型</span><span class="sxs-lookup"><span data-stu-id="20c87-151">Reflection and Generic Types</span></span>](reflection-and-generic-types.md)
- [<span data-ttu-id="20c87-152">查看类型信息</span><span class="sxs-lookup"><span data-stu-id="20c87-152">Viewing Type Information</span></span>](viewing-type-information.md)
- [<span data-ttu-id="20c87-153">泛型</span><span class="sxs-lookup"><span data-stu-id="20c87-153">Generics</span></span>](../../standard/generics/index.md)
