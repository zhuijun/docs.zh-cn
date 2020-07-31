---
title: 动态类型生成的可回收程序集
description: 开始在 .NET 中使用动态类型生成的可回收程序集。 了解可回收程序集的生存期和限制。
ms.date: 08/29/2017
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
ms.openlocfilehash: 4981b93dbd49a6da96740bebed0f2ed7b89036c8
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475120"
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a><span data-ttu-id="833e2-104">动态类型生成的可回收程序集</span><span class="sxs-lookup"><span data-stu-id="833e2-104">Collectible assemblies for dynamic type generation</span></span>

<span data-ttu-id="833e2-105">可回收程序集  是一个动态程序集，卸载该程序集时，无需卸载在其中创建了该程序集的应用程序域。</span><span class="sxs-lookup"><span data-stu-id="833e2-105">*Collectible assemblies* are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span> <span data-ttu-id="833e2-106">可回收程序集使用的所有托管和非托管内存及其包含的类型都是可回收的。</span><span class="sxs-lookup"><span data-stu-id="833e2-106">All managed and unmanaged memory used by a collectible assembly and the types it contains can be reclaimed.</span></span> <span data-ttu-id="833e2-107">从内部表中删除了程序集名称等信息。</span><span class="sxs-lookup"><span data-stu-id="833e2-107">Information such as the assembly name is removed from internal tables.</span></span>

<span data-ttu-id="833e2-108">要启用卸载，请在创建动态程序集时使用 <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> 标志。</span><span class="sxs-lookup"><span data-stu-id="833e2-108">To enable unloading, use the <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType> flag when you create a dynamic assembly.</span></span> <span data-ttu-id="833e2-109">程序集是瞬态程序集（即无法保存），并受到[可回收程序集限制](#restrictions-on-collectible-assemblies)部分中所述的限制。</span><span class="sxs-lookup"><span data-stu-id="833e2-109">The assembly is transient (that is, it cannot be saved) and is subject to limitations described in the [Restrictions on Collectible Assemblies](#restrictions-on-collectible-assemblies) section.</span></span> <span data-ttu-id="833e2-110">释放与程序集关联的所有对象时，公共语言运行时 (CLR) 会自动卸载可回收程序集。</span><span class="sxs-lookup"><span data-stu-id="833e2-110">The common language runtime (CLR) unloads a collectible assembly automatically when you release all objects associated with the assembly.</span></span> <span data-ttu-id="833e2-111">在所有其他方面，可回收程序集的创建和使用方法与其他动态程序集相同。</span><span class="sxs-lookup"><span data-stu-id="833e2-111">In all other respects, collectible assemblies are created and used in the same way as other dynamic assemblies.</span></span>

## <a name="lifetime-of-collectible-assemblies"></a><span data-ttu-id="833e2-112">可回收程序集的生存期</span><span class="sxs-lookup"><span data-stu-id="833e2-112">Lifetime of collectible assemblies</span></span>

<span data-ttu-id="833e2-113">可回收程序集的生存期受控于是否存在对其包含的类型和从这些类型创建的对象的引用。</span><span class="sxs-lookup"><span data-stu-id="833e2-113">The lifetime of a collectible assembly is controlled by the existence of references to the types it contains and the objects that are created from those types.</span></span> <span data-ttu-id="833e2-114">只要存在以下一项或多项（`T` 是程序集中定义的任何类型），公共语言运行时就不会卸载程序集：</span><span class="sxs-lookup"><span data-stu-id="833e2-114">The common language runtime does not unload an assembly as long as one or more of the following exist (`T` is any type that is defined in the assembly):</span></span>

- <span data-ttu-id="833e2-115">`T` 的一个实例。</span><span class="sxs-lookup"><span data-stu-id="833e2-115">An instance of `T`.</span></span>

- <span data-ttu-id="833e2-116">`T` 数组的一个实例。</span><span class="sxs-lookup"><span data-stu-id="833e2-116">An instance of an array of `T`.</span></span>

- <span data-ttu-id="833e2-117">使用 `T` 作为其类型参数的一个泛型类型实例。</span><span class="sxs-lookup"><span data-stu-id="833e2-117">An instance of a generic type that has `T` as one of its type arguments.</span></span> <span data-ttu-id="833e2-118">这包括 `T` 的泛型集合，即使该集合为空。</span><span class="sxs-lookup"><span data-stu-id="833e2-118">This includes generic collections of `T`, even if that collection is empty.</span></span>

- <span data-ttu-id="833e2-119"><xref:System.Type> 或 <xref:System.Reflection.Emit.TypeBuilder> 的一个实例，表示 `T`。</span><span class="sxs-lookup"><span data-stu-id="833e2-119">An instance of <xref:System.Type> or <xref:System.Reflection.Emit.TypeBuilder> that represents `T`.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="833e2-120">必须释放表示部分程序集的所有对象。</span><span class="sxs-lookup"><span data-stu-id="833e2-120">You must release all objects that represent parts of the assembly.</span></span> <span data-ttu-id="833e2-121">定义 `T` 的 <xref:System.Reflection.Emit.ModuleBuilder> 保持对 <xref:System.Reflection.Emit.TypeBuilder> 的引用，<xref:System.Reflection.Emit.AssemblyBuilder> 对象保持对 <xref:System.Reflection.Emit.ModuleBuilder> 的引用，因此必须释放对这些对象的引用。</span><span class="sxs-lookup"><span data-stu-id="833e2-121">The <xref:System.Reflection.Emit.ModuleBuilder> that defines `T` keeps a reference to the <xref:System.Reflection.Emit.TypeBuilder>, and the <xref:System.Reflection.Emit.AssemblyBuilder> object keeps a reference to the <xref:System.Reflection.Emit.ModuleBuilder>, so references to these objects must be released.</span></span> <span data-ttu-id="833e2-122">即使是存在 `T` 的构造中使用的 <xref:System.Reflection.Emit.LocalBuilder> 或 <xref:System.Reflection.Emit.ILGenerator>，也会阻止卸载。</span><span class="sxs-lookup"><span data-stu-id="833e2-122">Even the existence of a <xref:System.Reflection.Emit.LocalBuilder> or an <xref:System.Reflection.Emit.ILGenerator> used in the construction of `T` prevents unloading.</span></span>

- <span data-ttu-id="833e2-123">仍可供执行代码访问的另一动态定义类型 `T1` 对 `T` 的静态引用。</span><span class="sxs-lookup"><span data-stu-id="833e2-123">A static reference to `T` by another dynamically defined type `T1` that is still reachable by executing code.</span></span> <span data-ttu-id="833e2-124">例如，`T1` 可能派生自 `T`，或 `T` 可能为 `T1` 的方法中的参数类型。</span><span class="sxs-lookup"><span data-stu-id="833e2-124">For example, `T1` might derive from `T`, or `T` might be the type of a parameter in a method of `T1`.</span></span>

- <span data-ttu-id="833e2-125">属于 `T` 的静态字段的 ByRef  。</span><span class="sxs-lookup"><span data-stu-id="833e2-125">A **ByRef** to a static field that belongs to `T`.</span></span>

- <span data-ttu-id="833e2-126">引用 `T` 或 `T` 的组件的 <xref:System.RuntimeTypeHandle>、<xref:System.RuntimeFieldHandle>、<xref:System.RuntimeMethodHandle>。</span><span class="sxs-lookup"><span data-stu-id="833e2-126">A <xref:System.RuntimeTypeHandle>, <xref:System.RuntimeFieldHandle>, or <xref:System.RuntimeMethodHandle> that refers to `T` or to a component of `T`.</span></span>

- <span data-ttu-id="833e2-127">可直接或间接用于访问表示 `T` 的 <xref:System.Type> 对象的任何反射对象的实例。</span><span class="sxs-lookup"><span data-stu-id="833e2-127">An instance of any reflection object that could be used indirectly or directly to access the <xref:System.Type> object that represents `T`.</span></span> <span data-ttu-id="833e2-128">例如，可从其元素类型为 `T` 的任意数组类型，或类型参数为 `T` 的泛型类型获取 `T` 的 <xref:System.Type> 对象。</span><span class="sxs-lookup"><span data-stu-id="833e2-128">For example, the <xref:System.Type> object for `T` can be obtained from an array type whose element type is `T`, or from a generic type that has `T` as a type argument.</span></span>

- <span data-ttu-id="833e2-129">任何线程的调用堆栈上的方法 `M`，其中 `M` 是 `T` 的一种方法，或程序集中定义的模块级方法。</span><span class="sxs-lookup"><span data-stu-id="833e2-129">A method `M` on the call stack of any thread, where `M` is a method of `T` or a module-level method that is defined in the assembly.</span></span>

- <span data-ttu-id="833e2-130">对程序集模块中定义的静态方法的委托。</span><span class="sxs-lookup"><span data-stu-id="833e2-130">A delegate to a static method that is defined in a module of the assembly.</span></span>

<span data-ttu-id="833e2-131">对于程序集中的唯一类型或唯一方法，如果列表中仅存在一个项，则运行时无法卸载程序集。</span><span class="sxs-lookup"><span data-stu-id="833e2-131">If only one item from this list exists for only one type or one method in the assembly, the runtime cannot unload the assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="833e2-132">终结器针对列表中的所有项运行前，运行时实际上不会卸载程序集。</span><span class="sxs-lookup"><span data-stu-id="833e2-132">The runtime does not actually unload the assembly until finalizers have run for all items in the list.</span></span>

<span data-ttu-id="833e2-133">为了跟踪生存期，在生成可回收程序集时创建和使用的构造泛型类型（如 `List<int>` (C#) 或 `List(Of Integer)` (Visual Basic)）被视为在包含泛型类型定义的程序集中定义，或在包含其类型参数之一的程序集中定义。</span><span class="sxs-lookup"><span data-stu-id="833e2-133">For purposes of tracking lifetime, a constructed generic type such as `List<int>` (in C#) or `List(Of Integer)` (in Visual Basic) that is created and used in the generation of a collectible assembly is considered to have been defined either in the assembly that contains the generic type definition or in an assembly that contains the definition of one of its type arguments.</span></span> <span data-ttu-id="833e2-134">使用的具体程序集是实现详细信息，并且可能会有所更改。</span><span class="sxs-lookup"><span data-stu-id="833e2-134">The exact assembly that is used is an implementation detail and subject to change.</span></span>

## <a name="restrictions-on-collectible-assemblies"></a><span data-ttu-id="833e2-135">对可回收程序集的限制</span><span class="sxs-lookup"><span data-stu-id="833e2-135">Restrictions on collectible assemblies</span></span>

<span data-ttu-id="833e2-136">对可回收程序集有以下限制：</span><span class="sxs-lookup"><span data-stu-id="833e2-136">The following restrictions apply to collectible assemblies:</span></span>

- <span data-ttu-id="833e2-137">静态引用  ：普通动态程序集中的类型不能具有对可回收程序集中定义的类型的静态引用。</span><span class="sxs-lookup"><span data-stu-id="833e2-137">**Static references** Types in an ordinary dynamic assembly cannot have static references to types that are defined in a collectible assembly.</span></span> <span data-ttu-id="833e2-138">例如，如果定义了普通类型，且该类型继承自可回收程序集中的类型，则会引发 <xref:System.NotSupportedException> 异常。</span><span class="sxs-lookup"><span data-stu-id="833e2-138">For example, if you define an ordinary type that inherits from a type in a collectible assembly, a <xref:System.NotSupportedException> exception is thrown.</span></span> <span data-ttu-id="833e2-139">可回收程序集中的类型可具有对另一可回收程序集中的类型的引用，但这可将引用程序集的生存期延长至引用的程序集的生存期。</span><span class="sxs-lookup"><span data-stu-id="833e2-139">A type in a collectible assembly can have static references to a type in another collectible assembly, but this extends the lifetime of the referenced assembly to the lifetime of the referencing assembly.</span></span>

- <span data-ttu-id="833e2-140">COM 互操作  ：任何 COM 接口都不可在可回收程序集中定义，并且可回收程序集内的任何类型实例都不可转换为 COM 对象。</span><span class="sxs-lookup"><span data-stu-id="833e2-140">**COM interop** No COM interfaces can be defined within a collectible assembly, and no instances of types within a collectible assembly can be converted into COM objects.</span></span> <span data-ttu-id="833e2-141">可回收程序集中的类型不可用作 COM 可调用包装器 (CCW) 或运行时可调用包装器 (RCW)。</span><span class="sxs-lookup"><span data-stu-id="833e2-141">A type in a collectible assembly cannot serve as a COM callable wrapper (CCW) or runtime callable wrapper (RCW).</span></span> <span data-ttu-id="833e2-142">但是，可回收程序集中的类型可以使用实现 COM 接口的对象。</span><span class="sxs-lookup"><span data-stu-id="833e2-142">However, types in collectible assemblies can use objects that implement COM interfaces.</span></span>

- <span data-ttu-id="833e2-143">平台调用  ：在可回收程序集中声明具有 <xref:System.Runtime.InteropServices.DllImportAttribute> 属性的方法时，该方法不会进行编译。</span><span class="sxs-lookup"><span data-stu-id="833e2-143">**Platform invoke** Methods that have the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute will not compile when they are declared in a collectible assembly.</span></span> <span data-ttu-id="833e2-144"><xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> 指令不能用于可回收程序集中类型的实现，并且不可将此类类型封送到非托管代码。</span><span class="sxs-lookup"><span data-stu-id="833e2-144">The <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType> instruction cannot be used in the implementation of a type in a collectible assembly, and such types cannot be marshaled to unmanaged code.</span></span> <span data-ttu-id="833e2-145">但是，仍可使用非可回收程序集中声明的入口点调入本机代码。</span><span class="sxs-lookup"><span data-stu-id="833e2-145">However, you can call into native code by using an entry point that is declared in a non-collectible assembly.</span></span>

- <span data-ttu-id="833e2-146">封送  ：无法封送可回收程序集中定义的对象（尤其是委托）。</span><span class="sxs-lookup"><span data-stu-id="833e2-146">**Marshaling** Objects (in particular, delegates) that are defined in collectible assemblies cannot be marshaled.</span></span> <span data-ttu-id="833e2-147">这是对所有暂时性发出的类型的限制。</span><span class="sxs-lookup"><span data-stu-id="833e2-147">This is a restriction on all transient emitted types.</span></span>

- <span data-ttu-id="833e2-148">程序集加载  ：对于加载可回收程序集，反射发出是支持的唯一机制。</span><span class="sxs-lookup"><span data-stu-id="833e2-148">**Assembly loading** Reflection emit is the only mechanism that is supported for loading collectible assemblies.</span></span> <span data-ttu-id="833e2-149">使用任何其他形式的程序集加载机制加载的程序集无法卸载。</span><span class="sxs-lookup"><span data-stu-id="833e2-149">Assemblies that are loaded by using any other form of assembly loading cannot be unloaded.</span></span>

- <span data-ttu-id="833e2-150">上下文绑定对象  ：不支持上下文静态变量。</span><span class="sxs-lookup"><span data-stu-id="833e2-150">**Context-bound objects** Context-static variables are not supported.</span></span> <span data-ttu-id="833e2-151">可回收程序集中的类型无法扩展 <xref:System.ContextBoundObject>。</span><span class="sxs-lookup"><span data-stu-id="833e2-151">Types in a collectible assembly cannot extend <xref:System.ContextBoundObject>.</span></span> <span data-ttu-id="833e2-152">但是，可回收程序集中的代码可使用在其他位置定义的上下文绑定对象。</span><span class="sxs-lookup"><span data-stu-id="833e2-152">However, code in collectible assemblies can use context-bound objects that are defined elsewhere.</span></span>

- <span data-ttu-id="833e2-153">线程静态数据  ：不支持线程静态变量。</span><span class="sxs-lookup"><span data-stu-id="833e2-153">**Thread-static data** Thread-static variables are not supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="833e2-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="833e2-154">See also</span></span>

- [<span data-ttu-id="833e2-155">发出动态方法和程序集</span><span class="sxs-lookup"><span data-stu-id="833e2-155">Emitting Dynamic Methods and Assemblies</span></span>](emitting-dynamic-methods-and-assemblies.md)
