---
title: 如何：使用反射将委托挂钩
description: 了解如何在 .NET 中使用反射将委托挂钩。 通过反射获取所需的类型将现有的方法连接到事件。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
ms.openlocfilehash: b5d93efd278a53a4e6382f2321918e58ead55899
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865081"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="aa849-104">如何：使用反射将委托挂钩</span><span class="sxs-lookup"><span data-stu-id="aa849-104">How to: Hook Up a Delegate Using Reflection</span></span>
<span data-ttu-id="aa849-105">使用反射加载和运行程序集时，不能使用 C# `+=` 运算符或 Visual Basic [AddHandler 语句](../../visual-basic/language-reference/statements/addhandler-statement.md)等语言功能将事件挂钩。</span><span class="sxs-lookup"><span data-stu-id="aa849-105">When you use reflection to load and run assemblies, you cannot use language features like the C# `+=` operator or the Visual Basic [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md) to hook up events.</span></span> <span data-ttu-id="aa849-106">以下过程介绍如何通过反射获取所需的全部类型来将现有方法挂钩到事件，以及如何使用反射发出以创建动态方法并将其挂钩到事件。</span><span class="sxs-lookup"><span data-stu-id="aa849-106">The following procedures show how to hook up an existing method to an event by getting all the necessary types through reflection, and how to create a dynamic method using reflection emit and hook it up to an event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aa849-107">有关事件处理委托的其他挂钩方式，请参阅 <xref:System.Reflection.EventInfo> 类的 <xref:System.Reflection.EventInfo.AddEventHandler%2A> 方法的代码示例。</span><span class="sxs-lookup"><span data-stu-id="aa849-107">For another way to hook up an event-handling delegate, see the code example for the <xref:System.Reflection.EventInfo.AddEventHandler%2A> method of the <xref:System.Reflection.EventInfo> class.</span></span>  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a><span data-ttu-id="aa849-108">使用反射挂钩委托</span><span class="sxs-lookup"><span data-stu-id="aa849-108">To hook up a delegate using reflection</span></span>  
  
1. <span data-ttu-id="aa849-109">加载包含引发事件的类型的程序集。</span><span class="sxs-lookup"><span data-stu-id="aa849-109">Load an assembly that contains a type that raises events.</span></span> <span data-ttu-id="aa849-110">程序集通常使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法加载。</span><span class="sxs-lookup"><span data-stu-id="aa849-110">Assemblies are usually loaded with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="aa849-111">为了简化本示例，当前程序集中使用了派生窗体，因此使用 <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> 方法加载当前程序集。</span><span class="sxs-lookup"><span data-stu-id="aa849-111">To keep this example simple, a derived form in the current assembly is used, so the <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> method is used to load the current assembly.</span></span>  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. <span data-ttu-id="aa849-112">获取表示类型的 <xref:System.Type> 对象，并创建一个该类型的实例。</span><span class="sxs-lookup"><span data-stu-id="aa849-112">Get a <xref:System.Type> object representing the type, and create an instance of the type.</span></span> <span data-ttu-id="aa849-113">由于窗体具有无参数构造函数，因此下面的代码中使用了 <xref:System.Activator.CreateInstance%28System.Type%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="aa849-113">The <xref:System.Activator.CreateInstance%28System.Type%29> method is used in the following code because the form has a parameterless constructor.</span></span> <span data-ttu-id="aa849-114">如果要创建的类型没有无参数构造函数，<xref:System.Activator.CreateInstance%2A> 方法还有其他几种重载可供使用。</span><span class="sxs-lookup"><span data-stu-id="aa849-114">There are several other overloads of the <xref:System.Activator.CreateInstance%2A> method that you can use if the type you are creating does not have a parameterless constructor.</span></span> <span data-ttu-id="aa849-115">新实例存储为类型 <xref:System.Object>，以保持对程序集一无所知的假定。</span><span class="sxs-lookup"><span data-stu-id="aa849-115">The new instance is stored as type <xref:System.Object> to maintain the fiction that nothing is known about the assembly.</span></span> <span data-ttu-id="aa849-116">（通过反射可获取程序集中的类型，无需事先知悉其名称。）</span><span class="sxs-lookup"><span data-stu-id="aa849-116">(Reflection allows you to get the types in an assembly without knowing their names in advance.)</span></span>  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. <span data-ttu-id="aa849-117">获取表示该事件的 <xref:System.Reflection.EventInfo> 对象，并使用 <xref:System.Reflection.EventInfo.EventHandlerType%2A> 属性来获取用于处理事件的委托类型。</span><span class="sxs-lookup"><span data-stu-id="aa849-117">Get an <xref:System.Reflection.EventInfo> object representing the event, and use the <xref:System.Reflection.EventInfo.EventHandlerType%2A> property to get the type of delegate used to handle the event.</span></span> <span data-ttu-id="aa849-118">在以下代码中，获取了 <xref:System.Windows.Forms.Control.Click> 事件的 <xref:System.Reflection.EventInfo>。</span><span class="sxs-lookup"><span data-stu-id="aa849-118">In the following code, an <xref:System.Reflection.EventInfo> for the <xref:System.Windows.Forms.Control.Click> event is obtained.</span></span>  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. <span data-ttu-id="aa849-119">获取表示处理事件的方法的 <xref:System.Reflection.MethodInfo> 对象。</span><span class="sxs-lookup"><span data-stu-id="aa849-119">Get a <xref:System.Reflection.MethodInfo> object representing the method that handles the event.</span></span> <span data-ttu-id="aa849-120">本主题后面“示例”部分中的完整程序代码包含一个与 <xref:System.EventHandler> 委托的签名匹配的方法，该方法处理 <xref:System.Windows.Forms.Control.Click> 事件，但您也可以在运行时生成动态方法。</span><span class="sxs-lookup"><span data-stu-id="aa849-120">The complete program code in the Example section later in this topic contains a method that matches the signature of the <xref:System.EventHandler> delegate, which handles the <xref:System.Windows.Forms.Control.Click> event, but you can also generate dynamic methods at run time.</span></span> <span data-ttu-id="aa849-121">有关详细信息，请参阅附带的使用动态方法在运行时生成事件处理程序的过程。</span><span class="sxs-lookup"><span data-stu-id="aa849-121">For details, see the accompanying procedure, for generating an event handler at run time by using a dynamic method.</span></span>  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. <span data-ttu-id="aa849-122">使用 <xref:System.Delegate.CreateDelegate%2A> 方法创建委托的实例。</span><span class="sxs-lookup"><span data-stu-id="aa849-122">Create an instance of the delegate, using the <xref:System.Delegate.CreateDelegate%2A> method.</span></span> <span data-ttu-id="aa849-123">此方法是静态的（在 Visual Basic 中为 `Shared`），因此必须提供委托类型。</span><span class="sxs-lookup"><span data-stu-id="aa849-123">This method is static (`Shared` in Visual Basic), so the delegate type must be supplied.</span></span> <span data-ttu-id="aa849-124">建议使用带有 <xref:System.Reflection.MethodInfo> 的 <xref:System.Delegate.CreateDelegate%2A> 重载。</span><span class="sxs-lookup"><span data-stu-id="aa849-124">Using the overloads of <xref:System.Delegate.CreateDelegate%2A> that take a <xref:System.Reflection.MethodInfo> is recommended.</span></span>  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. <span data-ttu-id="aa849-125">获取 `add` 访问器方法，并调用该方法以将事件挂钩。</span><span class="sxs-lookup"><span data-stu-id="aa849-125">Get the `add` accessor method and invoke it to hook up the event.</span></span> <span data-ttu-id="aa849-126">所有事件都有一个 `add` 访问器和一个 `remove` 访问器，这些访问器由高级语言的语法隐藏。</span><span class="sxs-lookup"><span data-stu-id="aa849-126">All events have an `add` accessor and a `remove` accessor, which are hidden by the syntax of high-level languages.</span></span> <span data-ttu-id="aa849-127">例如，C# 使用 `+=` 运算符将事件挂钩，Visual Basic 则使用 [AddHandler 语句](../../visual-basic/language-reference/statements/addhandler-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="aa849-127">For example, C# uses the `+=` operator to hook up events, and Visual Basic uses the [AddHandler statement](../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="aa849-128">以下代码获取 <xref:System.Windows.Forms.Control.Click> 事件的 `add` 访问器，然后以后期绑定方式对其进行调用，并在委托实例中传递。</span><span class="sxs-lookup"><span data-stu-id="aa849-128">The following code gets the `add` accessor of the <xref:System.Windows.Forms.Control.Click> event and invokes it late-bound, passing in the delegate instance.</span></span> <span data-ttu-id="aa849-129">参数必须作为数组传递。</span><span class="sxs-lookup"><span data-stu-id="aa849-129">The arguments must be passed as an array.</span></span>  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. <span data-ttu-id="aa849-130">测试事件。</span><span class="sxs-lookup"><span data-stu-id="aa849-130">Test the event.</span></span> <span data-ttu-id="aa849-131">以下代码显示在代码示例中定义的窗体。</span><span class="sxs-lookup"><span data-stu-id="aa849-131">The following code shows the form defined in the code example.</span></span> <span data-ttu-id="aa849-132">单击窗体可调用事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="aa849-132">Clicking the form invokes the event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a><span data-ttu-id="aa849-133">使用动态方法在运行时生成事件处理程序</span><span class="sxs-lookup"><span data-stu-id="aa849-133">To generate an event handler at run time by using a dynamic method</span></span>  
  
1. <span data-ttu-id="aa849-134">使用轻量动态方法和反射发出可在运行时生成事件处理程序方法。</span><span class="sxs-lookup"><span data-stu-id="aa849-134">Event-handler methods can be generated at run time, using lightweight dynamic methods and reflection emit.</span></span> <span data-ttu-id="aa849-135">若要构造事件处理程序，需要委托的返回类型和参数类型。</span><span class="sxs-lookup"><span data-stu-id="aa849-135">To construct an event handler, you need the return type and parameter types of the delegate.</span></span> <span data-ttu-id="aa849-136">可通过检查委托的 `Invoke` 方法来获取这些类型。</span><span class="sxs-lookup"><span data-stu-id="aa849-136">These can be obtained by examining the delegate's `Invoke` method.</span></span> <span data-ttu-id="aa849-137">以下代码使用 `GetDelegateReturnType` 和 `GetDelegateParameterTypes` 方法获取此信息。</span><span class="sxs-lookup"><span data-stu-id="aa849-137">The following code uses the `GetDelegateReturnType` and `GetDelegateParameterTypes` methods to obtain this information.</span></span> <span data-ttu-id="aa849-138">本主题后面的“示例”部分提供了这些方法的代码。</span><span class="sxs-lookup"><span data-stu-id="aa849-138">The code for these methods can be found in the Example section later in this topic.</span></span>  
  
     <span data-ttu-id="aa849-139">无需命名 <xref:System.Reflection.Emit.DynamicMethod> 即可使用空字符串。</span><span class="sxs-lookup"><span data-stu-id="aa849-139">It is not necessary to name a <xref:System.Reflection.Emit.DynamicMethod>, so the empty string can be used.</span></span> <span data-ttu-id="aa849-140">在以下代码中，最后一个参数将动态方法与当前类型相关联，允许委托访问 `Example` 类的所有公共和私有成员。</span><span class="sxs-lookup"><span data-stu-id="aa849-140">In the following code, the last argument associates the dynamic method with the current type, giving the delegate access to all the public and private members of the `Example` class.</span></span>  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. <span data-ttu-id="aa849-141">生成方法体。</span><span class="sxs-lookup"><span data-stu-id="aa849-141">Generate a method body.</span></span> <span data-ttu-id="aa849-142">此方法加载字符串、调用带有字符串的 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> 方法重载、从堆栈弹出返回值（因为处理程序没有返回类型）并返回这些值。</span><span class="sxs-lookup"><span data-stu-id="aa849-142">This method loads a string, calls the overload of the <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> method that takes a string, pops the return value off the stack (because the handler has no return type), and returns.</span></span> <span data-ttu-id="aa849-143">若要详细了解如何发出动态方法，请参阅[如何：定义和执行动态方法](how-to-define-and-execute-dynamic-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="aa849-143">To learn more about emitting dynamic methods, see [How to: Define and Execute Dynamic Methods](how-to-define-and-execute-dynamic-methods.md).</span></span>  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. <span data-ttu-id="aa849-144">通过调用动态方法的 <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> 方法完成该动态方法。</span><span class="sxs-lookup"><span data-stu-id="aa849-144">Complete the dynamic method by calling its <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="aa849-145">使用 `add` 访问器向事件的调用列表添加委托。</span><span class="sxs-lookup"><span data-stu-id="aa849-145">Use the `add` accessor to add the delegate to the invocation list for the event.</span></span>  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. <span data-ttu-id="aa849-146">测试事件。</span><span class="sxs-lookup"><span data-stu-id="aa849-146">Test the event.</span></span> <span data-ttu-id="aa849-147">以下代码加载在代码示例中定义的窗体。</span><span class="sxs-lookup"><span data-stu-id="aa849-147">The following code loads the form defined in the code example.</span></span> <span data-ttu-id="aa849-148">单击该窗体可同时调用预定义的事件处理程序和发出的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="aa849-148">Clicking the form invokes both the predefined event handler and the emitted event handler.</span></span>  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="aa849-149">示例</span><span class="sxs-lookup"><span data-stu-id="aa849-149">Example</span></span>  
 <span data-ttu-id="aa849-150">以下代码示例介绍如何使用反射将现有方法挂钩到事件，以及如何使用 <xref:System.Reflection.Emit.DynamicMethod> 类在运行时发出方法并将其挂钩到事件。</span><span class="sxs-lookup"><span data-stu-id="aa849-150">The following code example shows how to hook up an existing method to an event using reflection, and also how to use the <xref:System.Reflection.Emit.DynamicMethod> class to emit a method at run time and hook it up to an event.</span></span>  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="aa849-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="aa849-151">See also</span></span>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [<span data-ttu-id="aa849-152">如何：定义和执行动态方法</span><span class="sxs-lookup"><span data-stu-id="aa849-152">How to: Define and Execute Dynamic Methods</span></span>](how-to-define-and-execute-dynamic-methods.md)
- [<span data-ttu-id="aa849-153">反射</span><span class="sxs-lookup"><span data-stu-id="aa849-153">Reflection</span></span>](reflection.md)
