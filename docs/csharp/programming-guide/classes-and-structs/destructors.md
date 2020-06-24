---
title: 终结器 - C# 编程指南
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 62fc531a8064a8a5cb144a89aa9975b3199db976
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990113"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="5bc40-102">终结器（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="5bc40-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="5bc40-103">终结器（也称为\*\*\*\* 析构函数）用于在垃圾回收器收集类实例时执行任何必要的最终清理操作。</span><span class="sxs-lookup"><span data-stu-id="5bc40-103">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bc40-104">备注</span><span class="sxs-lookup"><span data-stu-id="5bc40-104">Remarks</span></span>  
  
- <span data-ttu-id="5bc40-105">无法在结构中定义终结器。</span><span class="sxs-lookup"><span data-stu-id="5bc40-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="5bc40-106">它们仅用于类。</span><span class="sxs-lookup"><span data-stu-id="5bc40-106">They are only used with classes.</span></span>  
  
- <span data-ttu-id="5bc40-107">一个类只能有一个终结器。</span><span class="sxs-lookup"><span data-stu-id="5bc40-107">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="5bc40-108">不能继承或重载终结器。</span><span class="sxs-lookup"><span data-stu-id="5bc40-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="5bc40-109">不能手动调用终结器。</span><span class="sxs-lookup"><span data-stu-id="5bc40-109">Finalizers cannot be called.</span></span> <span data-ttu-id="5bc40-110">可以自动调用它们。</span><span class="sxs-lookup"><span data-stu-id="5bc40-110">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="5bc40-111">终结器不使用修饰符或参数。</span><span class="sxs-lookup"><span data-stu-id="5bc40-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="5bc40-112">例如，以下是类 `Car` 的终结器声明。</span><span class="sxs-lookup"><span data-stu-id="5bc40-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="5bc40-113">终结器也可以作为表达式主体定义实现，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="5bc40-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="5bc40-114">终结器隐式调用对象基类上的 <xref:System.Object.Finalize%2A>。</span><span class="sxs-lookup"><span data-stu-id="5bc40-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="5bc40-115">因此，对终结器的调用会隐式转换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="5bc40-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 <span data-ttu-id="5bc40-116">这种设计意味着，对继承链（从派生程度最高到派生程度最低）中的所有实例以递归方式调用 `Finalize` 方法。</span><span class="sxs-lookup"><span data-stu-id="5bc40-116">This design means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5bc40-117">不应使用空终结器。</span><span class="sxs-lookup"><span data-stu-id="5bc40-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="5bc40-118">如果类包含终结器，会在 `Finalize` 队列中创建一个条目。</span><span class="sxs-lookup"><span data-stu-id="5bc40-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="5bc40-119">调用终结器时，会调用垃圾回收器来处理该队列。</span><span class="sxs-lookup"><span data-stu-id="5bc40-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="5bc40-120">空终结器只会导致不必要的性能损失。</span><span class="sxs-lookup"><span data-stu-id="5bc40-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="5bc40-121">程序员无法控制何时调用终结器，因为这由垃圾回收器决定。</span><span class="sxs-lookup"><span data-stu-id="5bc40-121">The programmer has no control over when the finalizer is called; the garbage collector decides when to call it.</span></span> <span data-ttu-id="5bc40-122">垃圾回收器检查应用程序不再使用的对象。</span><span class="sxs-lookup"><span data-stu-id="5bc40-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="5bc40-123">如果它认为某个对象符合终止条件，则调用终结器（如果有），并回收用来存储此对象的内存。</span><span class="sxs-lookup"><span data-stu-id="5bc40-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span>

 <span data-ttu-id="5bc40-124">在 .NET Framework 应用程序中（但不在 .NET Core 应用程序中），程序退出时也会调用终结器。</span><span class="sxs-lookup"><span data-stu-id="5bc40-124">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span>
  
 <span data-ttu-id="5bc40-125">可以通过调用 <xref:System.GC.Collect%2A> 强制进行垃圾回收，但多数情况下应避免此调用，因为它可能会造成性能问题。</span><span class="sxs-lookup"><span data-stu-id="5bc40-125">It's possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this call should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="5bc40-126">使用终结器释放资源</span><span class="sxs-lookup"><span data-stu-id="5bc40-126">Using finalizers to release resources</span></span>  
 <span data-ttu-id="5bc40-127">一般来说，对于开发人员，C# 所需的内存管理比不面向带垃圾回收的运行时的语言要少。</span><span class="sxs-lookup"><span data-stu-id="5bc40-127">In general, C# does not require as much memory management on the part of the developer as languages that don't target a runtime with garbage collection.</span></span> <span data-ttu-id="5bc40-128">这是因为 .NET 垃圾回收器会隐式管理对象的内存分配和释放。</span><span class="sxs-lookup"><span data-stu-id="5bc40-128">This is because the .NET garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="5bc40-129">但是，如果应用程序封装非托管的资源，例如窗口、文件和网络连接，则应使用终结器释放这些资源。</span><span class="sxs-lookup"><span data-stu-id="5bc40-129">However, when your application encapsulates unmanaged resources, such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="5bc40-130">当对象符合终止条件时，垃圾回收器会运行对象的 `Finalize` 方法。</span><span class="sxs-lookup"><span data-stu-id="5bc40-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="5bc40-131">显式释放资源</span><span class="sxs-lookup"><span data-stu-id="5bc40-131">Explicit release of resources</span></span>  
 <span data-ttu-id="5bc40-132">如果应用程序正在使用昂贵的外部资源，我们还建议在垃圾回收器释放对象前显式释放资源。</span><span class="sxs-lookup"><span data-stu-id="5bc40-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="5bc40-133">若要释放资源，请从 <xref:System.IDisposable> 接口实现 `Dispose` 方法，对对象执行必要的清理。</span><span class="sxs-lookup"><span data-stu-id="5bc40-133">To release the resource, implement a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="5bc40-134">这样可大大提高应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="5bc40-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="5bc40-135">如果调用 `Dispose` 方法失败，那么即使拥有对资源的显式控制，终结器也会成为清除资源的一个保障。</span><span class="sxs-lookup"><span data-stu-id="5bc40-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method fails.</span></span>  
  
 <span data-ttu-id="5bc40-136">有关清除资源的详细信息，请参阅以下文章：</span><span class="sxs-lookup"><span data-stu-id="5bc40-136">For more information about cleaning up resources, see the following articles:</span></span>  
  
- <span data-ttu-id="5bc40-137">[清理未托管资源](../../../standard/garbage-collection/unmanaged.md)（清理未托管资源）</span><span class="sxs-lookup"><span data-stu-id="5bc40-137">[Cleaning Up Unmanaged Resources](../../../standard/garbage-collection/unmanaged.md)</span></span>  
  
- [<span data-ttu-id="5bc40-138">实现 Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="5bc40-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="5bc40-139">using 语句</span><span class="sxs-lookup"><span data-stu-id="5bc40-139">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="5bc40-140">示例</span><span class="sxs-lookup"><span data-stu-id="5bc40-140">Example</span></span>  
 <span data-ttu-id="5bc40-141">以下示例创建了三个类，并且这三个类构成了一个继承链。</span><span class="sxs-lookup"><span data-stu-id="5bc40-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="5bc40-142">类 `First` 是基类，`Second` 派生自 `First`，`Third` 派生自 `Second`。</span><span class="sxs-lookup"><span data-stu-id="5bc40-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="5bc40-143">这三个类都具有终结器。</span><span class="sxs-lookup"><span data-stu-id="5bc40-143">All three have finalizers.</span></span> <span data-ttu-id="5bc40-144">在 `Main` 中，已创建派生程度最高的类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="5bc40-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="5bc40-145">程序运行时，请注意，将按顺序（从派生程度最高到派生程度最低）自动调用这三个类的终结器。</span><span class="sxs-lookup"><span data-stu-id="5bc40-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="5bc40-146">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="5bc40-146">C# language specification</span></span>  

<span data-ttu-id="5bc40-147">有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的[析构函数](~/_csharplang/spec/classes.md#destructors)部分。</span><span class="sxs-lookup"><span data-stu-id="5bc40-147">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5bc40-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="5bc40-148">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="5bc40-149">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="5bc40-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5bc40-150">构造函数</span><span class="sxs-lookup"><span data-stu-id="5bc40-150">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="5bc40-151">垃圾回收</span><span class="sxs-lookup"><span data-stu-id="5bc40-151">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
