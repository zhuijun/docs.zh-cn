---
title: 如何：定义和执行动态方法
description: 了解如何在 .NET. 中定义和执行动态方法。 查看简单的动态方法和绑定到类实例的动态方法的示例。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
ms.openlocfilehash: d1ccf3d3ac966e35e1708f0639785a2760eb8287
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559182"
---
# <a name="how-to-define-and-execute-dynamic-methods"></a><span data-ttu-id="69f5b-104">如何：定义和执行动态方法</span><span class="sxs-lookup"><span data-stu-id="69f5b-104">How to: Define and Execute Dynamic Methods</span></span>
<span data-ttu-id="69f5b-105">以下过程介绍如何定义和执行简单的动态方法和绑定到类实例的动态方法。</span><span class="sxs-lookup"><span data-stu-id="69f5b-105">The following procedures show how to define and execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span> <span data-ttu-id="69f5b-106">有关动态方法的更多信息，请参阅 <xref:System.Reflection.Emit.DynamicMethod> 类和[反射发出动态方法应用场景](/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="69f5b-106">For more information on dynamic methods, see the <xref:System.Reflection.Emit.DynamicMethod> class and [Reflection Emit Dynamic Method Scenarios](/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100)).</span></span>  
  
### <a name="to-define-and-execute-a-dynamic-method"></a><span data-ttu-id="69f5b-107">定义和执行动态方法</span><span class="sxs-lookup"><span data-stu-id="69f5b-107">To define and execute a dynamic method</span></span>  
  
1. <span data-ttu-id="69f5b-108">声明用于执行方法的委托类型。</span><span class="sxs-lookup"><span data-stu-id="69f5b-108">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="69f5b-109">考虑使用泛型委托，将需要声明的委托类型数降到最低。</span><span class="sxs-lookup"><span data-stu-id="69f5b-109">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="69f5b-110">以下代码声明两种可用于 `SquareIt` 方法的委托类型，其中一个是泛型。</span><span class="sxs-lookup"><span data-stu-id="69f5b-110">The following code declares two delegate types that could be used for the `SquareIt` method, and one of them is generic.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2. <span data-ttu-id="69f5b-111">创建用于为动态方法指定参数类型的数组。</span><span class="sxs-lookup"><span data-stu-id="69f5b-111">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="69f5b-112">在此示例中，唯一的参数为 `int`（在 Visual Basic 中为 `Integer`），所以数组只有一个元素。</span><span class="sxs-lookup"><span data-stu-id="69f5b-112">In this example, the only parameter is an `int` (`Integer` in Visual Basic), so the array has only one element.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3. <span data-ttu-id="69f5b-113">创建 <xref:System.Reflection.Emit.DynamicMethod>。</span><span class="sxs-lookup"><span data-stu-id="69f5b-113">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="69f5b-114">在此示例中，该方法命名为 `SquareIt`。</span><span class="sxs-lookup"><span data-stu-id="69f5b-114">In this example the method is named `SquareIt`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="69f5b-115">不需要为动态方法命名，并且不能通过名称调用它们。</span><span class="sxs-lookup"><span data-stu-id="69f5b-115">It is not necessary to give dynamic methods names, and they cannot be invoked by name.</span></span> <span data-ttu-id="69f5b-116">多个动态方法可以具有相同的名称。</span><span class="sxs-lookup"><span data-stu-id="69f5b-116">Multiple dynamic methods can have the same name.</span></span> <span data-ttu-id="69f5b-117">但是，名称将在调用堆栈中显示并且可用于调试。</span><span class="sxs-lookup"><span data-stu-id="69f5b-117">However, the name appears in call stacks and can be useful for debugging.</span></span>  
  
     <span data-ttu-id="69f5b-118">返回值的类型指定为 `long`。</span><span class="sxs-lookup"><span data-stu-id="69f5b-118">The type of the return value is specified as `long`.</span></span> <span data-ttu-id="69f5b-119">该方法与包含 `Example` 类的模块关联，该类包含代码示例。</span><span class="sxs-lookup"><span data-stu-id="69f5b-119">The method is associated with the module that contains the `Example` class, which contains the example code.</span></span> <span data-ttu-id="69f5b-120">可以指定任何加载的模块。</span><span class="sxs-lookup"><span data-stu-id="69f5b-120">Any loaded module could be specified.</span></span> <span data-ttu-id="69f5b-121">动态方法的行为类似于模块级的 `static` 方法（在 Visual Basic 中为 `Shared`）。</span><span class="sxs-lookup"><span data-stu-id="69f5b-121">The dynamic method acts like a module-level `static` method (`Shared` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4. <span data-ttu-id="69f5b-122">发出方法主体。</span><span class="sxs-lookup"><span data-stu-id="69f5b-122">Emit the method body.</span></span> <span data-ttu-id="69f5b-123">在此示例中，使用 <xref:System.Reflection.Emit.ILGenerator> 对象发出 Microsoft 中间语言 (MSIL)。</span><span class="sxs-lookup"><span data-stu-id="69f5b-123">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="69f5b-124">也可以结合使用 <xref:System.Reflection.Emit.DynamicILInfo> 对象与非托管代码生成器，发出 <xref:System.Reflection.Emit.DynamicMethod> 的方法主体。</span><span class="sxs-lookup"><span data-stu-id="69f5b-124">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="69f5b-125">此示例中的 MSIL 将该参数（一个 `int`）加载到堆栈上，将其转换为 `long`，复制 `long`，然后将这两个数字相乘。</span><span class="sxs-lookup"><span data-stu-id="69f5b-125">The MSIL in this example loads the argument, which is an `int`, onto the stack, converts it to a `long`, duplicates the `long`, and multiplies the two numbers.</span></span> <span data-ttu-id="69f5b-126">这会将平方结果保留在堆栈中，方法只需返回即可。</span><span class="sxs-lookup"><span data-stu-id="69f5b-126">This leaves the squared result on the stack, and all the method has to do is return.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5. <span data-ttu-id="69f5b-127">通过调用 <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> 方法创建表示动态方法的委托（在步骤 1 中声明）的实例。</span><span class="sxs-lookup"><span data-stu-id="69f5b-127">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="69f5b-128">创建委托即完成该方法，任何更改方法的进一步尝试（例如，添加更多 MSIL）都将被忽略。</span><span class="sxs-lookup"><span data-stu-id="69f5b-128">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span> <span data-ttu-id="69f5b-129">以下代码使用泛型委托创建委托并调用它。</span><span class="sxs-lookup"><span data-stu-id="69f5b-129">The following code creates the delegate and invokes it, using a generic delegate.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a><span data-ttu-id="69f5b-130">定义和执行绑定到对象的动态方法</span><span class="sxs-lookup"><span data-stu-id="69f5b-130">To define and execute a dynamic method that is bound to an object</span></span>  
  
1. <span data-ttu-id="69f5b-131">声明用于执行方法的委托类型。</span><span class="sxs-lookup"><span data-stu-id="69f5b-131">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="69f5b-132">考虑使用泛型委托，将需要声明的委托类型数降到最低。</span><span class="sxs-lookup"><span data-stu-id="69f5b-132">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="69f5b-133">以下代码声明一个泛型委托类型，可使用该类型执行任何具有一个参数和一个返回值的方法，如果委托绑定到对象，则该类型也可以执行具有两个参数和一个返回值的方法。</span><span class="sxs-lookup"><span data-stu-id="69f5b-133">The following code declares a generic delegate type that can be used to execute any method with one parameter and a return value, or a method with two parameters and a return value if the delegate is bound to an object.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2. <span data-ttu-id="69f5b-134">创建用于为动态方法指定参数类型的数组。</span><span class="sxs-lookup"><span data-stu-id="69f5b-134">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="69f5b-135">如果表示方法的委托要绑定到对象，则第一个参数必须与委托绑定到的类型相匹配。</span><span class="sxs-lookup"><span data-stu-id="69f5b-135">If the delegate representing the method is to be bound to an object, the first parameter must match the type the delegate is bound to.</span></span> <span data-ttu-id="69f5b-136">在此示例中，存在两个参数，分别属于 `Example` 和 `int`（在 Visual Basic 中为 `Integer`）类型。</span><span class="sxs-lookup"><span data-stu-id="69f5b-136">In this example, there are two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3. <span data-ttu-id="69f5b-137">创建 <xref:System.Reflection.Emit.DynamicMethod>。</span><span class="sxs-lookup"><span data-stu-id="69f5b-137">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="69f5b-138">在此示例中，方法没有名称。</span><span class="sxs-lookup"><span data-stu-id="69f5b-138">In this example the method has no name.</span></span> <span data-ttu-id="69f5b-139">返回值的类型指定为 `int`（在 Visual Basic 中为 `Integer`）。</span><span class="sxs-lookup"><span data-stu-id="69f5b-139">The type of the return value is specified as `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="69f5b-140">该方法可以访问 `Example` 类的私有成员和受保护成员。</span><span class="sxs-lookup"><span data-stu-id="69f5b-140">The method has access to the private and protected members of the `Example` class.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4. <span data-ttu-id="69f5b-141">发出方法主体。</span><span class="sxs-lookup"><span data-stu-id="69f5b-141">Emit the method body.</span></span> <span data-ttu-id="69f5b-142">在此示例中，使用 <xref:System.Reflection.Emit.ILGenerator> 对象发出 Microsoft 中间语言 (MSIL)。</span><span class="sxs-lookup"><span data-stu-id="69f5b-142">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="69f5b-143">也可以结合使用 <xref:System.Reflection.Emit.DynamicILInfo> 对象与非托管代码生成器，发出 <xref:System.Reflection.Emit.DynamicMethod> 的方法主体。</span><span class="sxs-lookup"><span data-stu-id="69f5b-143">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="69f5b-144">此示例中的 MSIL 加载第一个参数（一个 `Example` 类的实例），然后使用该参数加载类型 `int` 的专用实例字段的值。</span><span class="sxs-lookup"><span data-stu-id="69f5b-144">The MSIL in this example loads the first argument, which is an instance of the `Example` class, and uses it to load the value of a private instance field of type `int`.</span></span> <span data-ttu-id="69f5b-145">然后加载第二个参数，并将两个数相乘。</span><span class="sxs-lookup"><span data-stu-id="69f5b-145">The second argument is loaded, and the two numbers are multiplied.</span></span> <span data-ttu-id="69f5b-146">如果结果大于 `int`，将截断该值且丢弃最高有效位。</span><span class="sxs-lookup"><span data-stu-id="69f5b-146">If the result is larger than `int`, the value is truncated and the most significant bits are discarded.</span></span> <span data-ttu-id="69f5b-147">该方法返回，返回值保留在堆栈中。</span><span class="sxs-lookup"><span data-stu-id="69f5b-147">The method returns, with the return value on the stack.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5. <span data-ttu-id="69f5b-148">通过调用 <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> 方法重载创建表示动态方法的委托（在步骤 1 中声明）的实例。</span><span class="sxs-lookup"><span data-stu-id="69f5b-148">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> method overload.</span></span> <span data-ttu-id="69f5b-149">创建委托即完成该方法，任何更改方法的进一步尝试（例如，添加更多 MSIL）都将被忽略。</span><span class="sxs-lookup"><span data-stu-id="69f5b-149">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="69f5b-150">可以多次调用 <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> 方法，创建绑定到目标类型的其他实例的委托。</span><span class="sxs-lookup"><span data-stu-id="69f5b-150">You can call the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method multiple times to create delegates bound to other instances of the target type.</span></span>  
  
     <span data-ttu-id="69f5b-151">以下代码将该方法绑定到 `Example` 类的一个新实例，该类的专用测试字段设置为 42。</span><span class="sxs-lookup"><span data-stu-id="69f5b-151">The following code binds the method to a new instance of the `Example` class whose private test field is set to 42.</span></span> <span data-ttu-id="69f5b-152">也就是说，每次调用委托时，都会将 `Example` 的实例传递给该方法的第一个参数。</span><span class="sxs-lookup"><span data-stu-id="69f5b-152">That is, each time the delegate is invoked the instance of `Example` is passed to the first parameter of the method.</span></span>  
  
     <span data-ttu-id="69f5b-153">使用委托 `OneParameter` 的原因是该方法的第一个参数始终会接收 `Example` 的实例。</span><span class="sxs-lookup"><span data-stu-id="69f5b-153">The delegate `OneParameter` is used because the first parameter of the method always receives the instance of `Example`.</span></span> <span data-ttu-id="69f5b-154">调用委托时，只需要使用第二个参数。</span><span class="sxs-lookup"><span data-stu-id="69f5b-154">When the delegate is invoked, only the second parameter is required.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="69f5b-155">示例</span><span class="sxs-lookup"><span data-stu-id="69f5b-155">Example</span></span>  
 <span data-ttu-id="69f5b-156">以下代码示例演示一个简单的动态方法和一个绑定到类实例的动态方法。</span><span class="sxs-lookup"><span data-stu-id="69f5b-156">The following code example demonstrates a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>  
  
 <span data-ttu-id="69f5b-157">简单动态方法具有一个 32 位整数参数，返回该整数的 64 位平方。</span><span class="sxs-lookup"><span data-stu-id="69f5b-157">The simple dynamic method takes one argument, a 32-bit integer, and returns the 64-bit square of that integer.</span></span> <span data-ttu-id="69f5b-158">使用泛型委托来调用该方法。</span><span class="sxs-lookup"><span data-stu-id="69f5b-158">A generic delegate is used to invoke the method.</span></span>  
  
 <span data-ttu-id="69f5b-159">第二个动态方法有两个参数，分别属于 `Example` 和 `int`（在 Visual Basic 中为 `Integer`）类型。</span><span class="sxs-lookup"><span data-stu-id="69f5b-159">The second dynamic method has two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="69f5b-160">创建动态方法后，将使用具有一个 `int` 类型参数的泛型委托将其绑定到 `Example` 的实例。</span><span class="sxs-lookup"><span data-stu-id="69f5b-160">When the dynamic method has been created, it is bound to an instance of `Example`, using a generic delegate that has one argument of type `int`.</span></span> <span data-ttu-id="69f5b-161">该委托没有 `Example` 类型的参数，因为方法的第一个参数始终接收 `Example` 的绑定实例。</span><span class="sxs-lookup"><span data-stu-id="69f5b-161">The delegate does not have an argument of type `Example` because the first parameter of the method always receives the bound instance of `Example`.</span></span> <span data-ttu-id="69f5b-162">调用委托时，只提供 `int` 参数。</span><span class="sxs-lookup"><span data-stu-id="69f5b-162">When the delegate is invoked, only the `int` argument is supplied.</span></span> <span data-ttu-id="69f5b-163">此动态方法访问 `Example` 类的专用字段，并返回专用字段和 `int` 参数的乘积。</span><span class="sxs-lookup"><span data-stu-id="69f5b-163">This dynamic method accesses a private field of the `Example` class and returns the product of the private field and the `int` argument.</span></span>  
  
 <span data-ttu-id="69f5b-164">该代码示例定义可用于执行方法的委托。</span><span class="sxs-lookup"><span data-stu-id="69f5b-164">The code example defines delegates that can be used to execute the methods.</span></span>  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="69f5b-165">请参阅</span><span class="sxs-lookup"><span data-stu-id="69f5b-165">See also</span></span>

- <xref:System.Reflection.Emit.DynamicMethod>
- <span data-ttu-id="69f5b-166">[使用反射发出](/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="69f5b-166">[Using Reflection Emit](/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))</span></span>
- <span data-ttu-id="69f5b-167">[反射发出动态方法应用场景](/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="69f5b-167">[Reflection Emit Dynamic Method Scenarios](/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100))</span></span>
