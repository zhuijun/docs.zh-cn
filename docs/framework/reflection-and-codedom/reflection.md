---
title: .NET 中的反射
description: 查看 .NET 中的反射。 获取有关加载的程序集和其中定义的类型的信息，如类、接口、结构和枚举。
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET], reflection
- EventInfo class, reflection
- common language runtime, reflection
- FieldInfo class, reflection
- ParameterInfo class, reflection
- ConstructorInfo class, reflection
- Assembly class, reflection
- value types, reflection
- reflection, about reflection
- modules, reflection
- runtime, reflection
- Module class, reflection
- MethodInfo class, reflection
- PropertyInfo class, reflection
- type browsers
- reflection
- discovering type information at run time
- type system, reflection
ms.assetid: d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775
ms.openlocfilehash: 46c67595126af2c62b28d29983775943586a0b90
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865276"
---
# <a name="reflection-in-net"></a><span data-ttu-id="b726d-104">.NET 中的反射</span><span class="sxs-lookup"><span data-stu-id="b726d-104">Reflection in .NET</span></span>

<span data-ttu-id="b726d-105"><xref:System.Reflection> 命名空间中的类与 <xref:System.Type?displayProperty=nameWithType> 使你能够获取有关加载的[程序集](../../standard/assembly/index.md)和其中定义的类型的信息，如[类](../../standard/base-types/common-type-system.md#classes)、[接口](../../standard/base-types/common-type-system.md#interfaces)和值类型（即[结构](../../standard/base-types/common-type-system.md#structures)和[枚举](../../standard/base-types/common-type-system.md#enumerations)）。</span><span class="sxs-lookup"><span data-stu-id="b726d-105">The classes in the <xref:System.Reflection> namespace, together with <xref:System.Type?displayProperty=nameWithType>, enable you to obtain information about loaded [assemblies](../../standard/assembly/index.md) and the types defined within them, such as [classes](../../standard/base-types/common-type-system.md#classes), [interfaces](../../standard/base-types/common-type-system.md#interfaces), and value types (that is, [structures](../../standard/base-types/common-type-system.md#structures) and [enumerations](../../standard/base-types/common-type-system.md#enumerations)).</span></span> <span data-ttu-id="b726d-106">可以使用反射在运行时创建、调用和访问类型实例。</span><span class="sxs-lookup"><span data-stu-id="b726d-106">You can also use reflection to create type instances at run time, and to invoke and access them.</span></span> <span data-ttu-id="b726d-107">有关反射的特定方面的主题，请参见本概述末的[相关主题](#related_topics)。</span><span class="sxs-lookup"><span data-stu-id="b726d-107">For topics about specific aspects of reflection, see [Related Topics](#related_topics) at the end of this overview.</span></span>
  
<span data-ttu-id="b726d-108">[公共语言运行时](../../standard/clr.md)加载程序管理[应用程序域](../app-domains/application-domains.md)，应用程序域构成具有相同应用程序范围的对象周围定义的边界。</span><span class="sxs-lookup"><span data-stu-id="b726d-108">The [common language runtime](../../standard/clr.md) loader manages [application domains](../app-domains/application-domains.md), which constitute defined boundaries around objects that have the same application scope.</span></span> <span data-ttu-id="b726d-109">此管理包括将每个程序集加载到相应的应用程序域中和控制每个程序集内的类型层次结构的内存布局。</span><span class="sxs-lookup"><span data-stu-id="b726d-109">This management includes loading each assembly into the appropriate application domain and controlling the memory layout of the type hierarchy within each assembly.</span></span>  
  
<span data-ttu-id="b726d-110">[程序集](../app-domains/index.md)包含模块、模块包含类型，而类型包含成员。</span><span class="sxs-lookup"><span data-stu-id="b726d-110">[Assemblies](../app-domains/index.md) contain modules, modules contain types, and types contain members.</span></span> <span data-ttu-id="b726d-111">反射提供封装程序集、模块和类型的对象。</span><span class="sxs-lookup"><span data-stu-id="b726d-111">Reflection provides objects that encapsulate assemblies, modules, and types.</span></span> <span data-ttu-id="b726d-112">可以使用反射动态地创建类型的实例，将类型绑定到现有对象，或从现有对象中获取类型。</span><span class="sxs-lookup"><span data-stu-id="b726d-112">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object.</span></span> <span data-ttu-id="b726d-113">然后，可以调用类型的方法或访问其字段和属性。</span><span class="sxs-lookup"><span data-stu-id="b726d-113">You can then invoke the type's methods or access its fields and properties.</span></span> <span data-ttu-id="b726d-114">反射的典型用法如下所示：</span><span class="sxs-lookup"><span data-stu-id="b726d-114">Typical uses of reflection include the following:</span></span>  
  
- <span data-ttu-id="b726d-115">使用 <xref:System.Reflection.Assembly> 来定义和加载程序集，加载程序集清单中列出的模块，以及在此程序集中定位一个类型并创建一个它的实例。</span><span class="sxs-lookup"><span data-stu-id="b726d-115">Use <xref:System.Reflection.Assembly> to define and load assemblies, load modules that are listed in the assembly manifest, and locate a type from this assembly and create an instance of it.</span></span>  
  
- <span data-ttu-id="b726d-116">使用 <xref:System.Reflection.Module> 发现信息，如包含模块的程序集和模块中的类。</span><span class="sxs-lookup"><span data-stu-id="b726d-116">Use <xref:System.Reflection.Module> to discover information such as the assembly that contains the module and the classes in the module.</span></span> <span data-ttu-id="b726d-117">还可以获取所有全局方法或模块上定义的其它特定的非全局方法。</span><span class="sxs-lookup"><span data-stu-id="b726d-117">You can also get all global methods or other specific, nonglobal methods defined on the module.</span></span>  
  
- <span data-ttu-id="b726d-118">使用 <xref:System.Reflection.ConstructorInfo> 发现信息，如名称、参数、访问修饰符（如 `public` 或 `private`）和构造函数的实现详细信息（如 `abstract` 或 `virtual`）。</span><span class="sxs-lookup"><span data-stu-id="b726d-118">Use <xref:System.Reflection.ConstructorInfo> to discover information such as the name, parameters, access modifiers (such as `public` or `private`), and implementation details (such as `abstract` or `virtual`) of a constructor.</span></span> <span data-ttu-id="b726d-119">使用 <xref:System.Type> 的 <xref:System.Type.GetConstructors%2A> 或 <xref:System.Type.GetConstructor%2A> 方法来调用特定构造函数。</span><span class="sxs-lookup"><span data-stu-id="b726d-119">Use the <xref:System.Type.GetConstructors%2A> or <xref:System.Type.GetConstructor%2A> method of a <xref:System.Type> to invoke a specific constructor.</span></span>  
  
- <span data-ttu-id="b726d-120">使用 <xref:System.Reflection.MethodInfo> 发现信息，如名称、返回类型、参数、访问修饰符（如 `public` 或 `private`）和方法的实现详细信息（如 `abstract` 或 `virtual`）。</span><span class="sxs-lookup"><span data-stu-id="b726d-120">Use <xref:System.Reflection.MethodInfo> to discover information such as the name, return type, parameters, access modifiers (such as `public` or `private`), and implementation details (such as `abstract` or `virtual`) of a method.</span></span> <span data-ttu-id="b726d-121">使用 <xref:System.Type> 的 <xref:System.Type.GetMethods%2A> 或 <xref:System.Type.GetMethod%2A> 方法来调用特定方法。</span><span class="sxs-lookup"><span data-stu-id="b726d-121">Use the <xref:System.Type.GetMethods%2A> or <xref:System.Type.GetMethod%2A> method of a <xref:System.Type> to invoke a specific method.</span></span>  
  
- <span data-ttu-id="b726d-122">使用 <xref:System.Reflection.FieldInfo> 发现信息，如名称、访问修饰符（如 `public` 或 `private`）和一个字段的实现详细信息 （如 `static`）；并获取或设置字段值。</span><span class="sxs-lookup"><span data-stu-id="b726d-122">Use <xref:System.Reflection.FieldInfo> to discover information such as the name, access modifiers (such as `public` or `private`) and implementation details (such as `static`) of a field, and to get or set field values.</span></span>  
  
- <span data-ttu-id="b726d-123">使用 <xref:System.Reflection.EventInfo> 发现信息（如名称、事件处理程序的数据类型、自定义特性、声明类型以及事件的反射的类型），并添加或删除事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="b726d-123">Use <xref:System.Reflection.EventInfo> to discover information such as the name, event-handler data type, custom attributes, declaring type, and reflected type of an event, and to add or remove event handlers.</span></span>  
  
- <span data-ttu-id="b726d-124">使用 <xref:System.Reflection.PropertyInfo> 发现信息（如名称、数据类型、声明类型，反射的类型和属性的只读或可写状态），并获取或设置属性值。</span><span class="sxs-lookup"><span data-stu-id="b726d-124">Use <xref:System.Reflection.PropertyInfo> to discover information such as the name, data type, declaring type, reflected type, and read-only or writable status of a property, and to get or set property values.</span></span>  
  
- <span data-ttu-id="b726d-125">使用 <xref:System.Reflection.ParameterInfo> 发现信息，如参数的名称、数据类型、参数是输入参数还是输出参数以及参数在方法签名中的位置。</span><span class="sxs-lookup"><span data-stu-id="b726d-125">Use <xref:System.Reflection.ParameterInfo> to discover information such as a parameter's name, data type, whether a parameter is an input or output parameter, and the position of the parameter in a method signature.</span></span>  
  
- <span data-ttu-id="b726d-126">使用 <xref:System.Reflection.CustomAttributeData> 在于应用程序域的仅反射上下文中工作时发现有关自定义特性的信息。</span><span class="sxs-lookup"><span data-stu-id="b726d-126">Use <xref:System.Reflection.CustomAttributeData> to discover information about custom attributes when you are working in the reflection-only context of an application domain.</span></span> <span data-ttu-id="b726d-127"><xref:System.Reflection.CustomAttributeData> 使你能够检查特性，而无需创建它们的实例。</span><span class="sxs-lookup"><span data-stu-id="b726d-127"><xref:System.Reflection.CustomAttributeData> allows you to examine attributes without creating instances of them.</span></span>  
  
<span data-ttu-id="b726d-128"><xref:System.Reflection.Emit> 命名空间的类提供一种专用形式的反射，使你能够在运行时生成类型。</span><span class="sxs-lookup"><span data-stu-id="b726d-128">The classes of the <xref:System.Reflection.Emit> namespace provide a specialized form of reflection that enables you to build types at run time.</span></span>  
  
<span data-ttu-id="b726d-129">还可以使用反射来创建称为类型浏览器的应用程序，它使用户能够选择类型，然后查看有关这些类型的信息。</span><span class="sxs-lookup"><span data-stu-id="b726d-129">Reflection can also be used to create applications called type browsers, which enable users to select types and then view the information about those types.</span></span>  
  
<span data-ttu-id="b726d-130">反射还有其它用途。</span><span class="sxs-lookup"><span data-stu-id="b726d-130">There are other uses for reflection.</span></span> <span data-ttu-id="b726d-131">JScript 等语言的编译器使用反射来构造符号表。</span><span class="sxs-lookup"><span data-stu-id="b726d-131">Compilers for languages such as JScript use reflection to construct symbol tables.</span></span> <span data-ttu-id="b726d-132"><xref:System.Runtime.Serialization> 命名空间中的类使用反射来访问数据并确定要保存哪些字段。</span><span class="sxs-lookup"><span data-stu-id="b726d-132">The classes in the <xref:System.Runtime.Serialization> namespace use reflection to access data and to determine which fields to persist.</span></span> <span data-ttu-id="b726d-133"><xref:System.Runtime.Remoting> 命名空间中的类通过序列化间接使用反射。</span><span class="sxs-lookup"><span data-stu-id="b726d-133">The classes in the <xref:System.Runtime.Remoting> namespace use reflection indirectly through serialization.</span></span>  
  
## <a name="runtime-types-in-reflection"></a><span data-ttu-id="b726d-134">反射中的运行时类型</span><span class="sxs-lookup"><span data-stu-id="b726d-134">Runtime Types in Reflection</span></span>  
<span data-ttu-id="b726d-135">反射提供类（如 <xref:System.Type> 和 <xref:System.Reflection.MethodInfo>），用于表示类型、成员、参数和其它代码实体。</span><span class="sxs-lookup"><span data-stu-id="b726d-135">Reflection provides classes, such as <xref:System.Type> and <xref:System.Reflection.MethodInfo>, to represent types, members, parameters, and other code entities.</span></span> <span data-ttu-id="b726d-136">但使用反射时，你并不直接使用这些类，其中大部分类均是抽象的（Visual Basic 中为 `MustInherit`）。</span><span class="sxs-lookup"><span data-stu-id="b726d-136">However, when you use reflection, you don't work directly with these classes, most of which are abstract (`MustInherit` in Visual Basic).</span></span> <span data-ttu-id="b726d-137">相反，你使用由公共语言运行时 (CLR) 提供的类型。</span><span class="sxs-lookup"><span data-stu-id="b726d-137">Instead, you work with types provided by the common language runtime (CLR).</span></span>  
  
<span data-ttu-id="b726d-138">例如，使用 C# `typeof` 运算符（Visual Basic 中为 `GetType`）获取 <xref:System.Type> 对象时，该对象实际上是 `RuntimeType`。</span><span class="sxs-lookup"><span data-stu-id="b726d-138">For example, when you use the C# `typeof` operator (`GetType` in Visual Basic) to obtain a <xref:System.Type> object, the object is really a `RuntimeType`.</span></span> <span data-ttu-id="b726d-139">`RuntimeType` 派生自 <xref:System.Type>，并提供所有抽象方法的实现。</span><span class="sxs-lookup"><span data-stu-id="b726d-139">`RuntimeType` derives from <xref:System.Type> and provides implementations of all the abstract methods.</span></span>  
  
<span data-ttu-id="b726d-140">这些运行时类是 `internal`（Visual Basic 中为 `Friend`）。</span><span class="sxs-lookup"><span data-stu-id="b726d-140">These runtime classes are `internal` (`Friend` in Visual Basic).</span></span> <span data-ttu-id="b726d-141">它们没有与其基类分开记录，因为它们的行为由基类文档来描述。</span><span class="sxs-lookup"><span data-stu-id="b726d-141">They are not documented separately from their base classes, because their behavior is described by the base class documentation.</span></span>  
  
<a name="related_topics"></a>

## <a name="related-topics"></a><span data-ttu-id="b726d-142">相关主题</span><span class="sxs-lookup"><span data-stu-id="b726d-142">Related Topics</span></span>  
  
|<span data-ttu-id="b726d-143">Title</span><span class="sxs-lookup"><span data-stu-id="b726d-143">Title</span></span>|<span data-ttu-id="b726d-144">描述</span><span class="sxs-lookup"><span data-stu-id="b726d-144">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b726d-145">查看类型信息</span><span class="sxs-lookup"><span data-stu-id="b726d-145">Viewing Type Information</span></span>](viewing-type-information.md)|<span data-ttu-id="b726d-146">介绍 <xref:System.Type> 类，并提供演示如何使用具有几个反射类的 <xref:System.Type> 来获取有关构造函数、方法、字段、属性和事件的信息的代码示例。</span><span class="sxs-lookup"><span data-stu-id="b726d-146">Describes the <xref:System.Type> class and provides code examples that illustrate how to use <xref:System.Type> with several reflection classes to obtain information about constructors, methods, fields, properties, and events.</span></span>|  
|[<span data-ttu-id="b726d-147">反射类型和泛型类型</span><span class="sxs-lookup"><span data-stu-id="b726d-147">Reflection and Generic Types</span></span>](reflection-and-generic-types.md)|<span data-ttu-id="b726d-148">说明反射如何处理泛型类型和泛型方法的类型参数和类型自变量。</span><span class="sxs-lookup"><span data-stu-id="b726d-148">Explains how reflection handles the type parameters and type arguments of generic types and generic methods.</span></span>|  
|[<span data-ttu-id="b726d-149">反射的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="b726d-149">Security Considerations for Reflection</span></span>](security-considerations-for-reflection.md)|<span data-ttu-id="b726d-150">描述确定可以在何种程度上使用反射来发现类型信息和访问类型的规则。</span><span class="sxs-lookup"><span data-stu-id="b726d-150">Describes the rules that determine to what degree reflection can be used to discover type information and access types.</span></span>|  
|[<span data-ttu-id="b726d-151">动态加载和使用类型</span><span class="sxs-lookup"><span data-stu-id="b726d-151">Dynamically Loading and Using Types</span></span>](dynamically-loading-and-using-types.md)|<span data-ttu-id="b726d-152">描述支持后期绑定的反射自定义绑定接口。</span><span class="sxs-lookup"><span data-stu-id="b726d-152">Describes the reflection custom-binding interface that supports late binding.</span></span>|  
|[<span data-ttu-id="b726d-153">如何：将程序集加载到仅反射上下文中</span><span class="sxs-lookup"><span data-stu-id="b726d-153">How to: Load Assemblies into the Reflection-Only Context</span></span>](how-to-load-assemblies-into-the-reflection-only-context.md)|<span data-ttu-id="b726d-154">描述仅反射的加载上下文。</span><span class="sxs-lookup"><span data-stu-id="b726d-154">Describes the reflection-only load context.</span></span> <span data-ttu-id="b726d-155">显示如何加载程序集、如何测试上下文以及如何检查应用到仅反射上下文中的程序集。</span><span class="sxs-lookup"><span data-stu-id="b726d-155">Shows how to load an assembly, how to test the context, and how to examine attributes applied to an assembly in the reflection-only context.</span></span>|  
|[<span data-ttu-id="b726d-156">访问自定义属性</span><span class="sxs-lookup"><span data-stu-id="b726d-156">Accessing Custom Attributes</span></span>](accessing-custom-attributes.md)|<span data-ttu-id="b726d-157">演示如何使用反射来查询特性的存在和值。</span><span class="sxs-lookup"><span data-stu-id="b726d-157">Demonstrates using reflection to query attribute existence and values.</span></span>|  
|[<span data-ttu-id="b726d-158">指定完全限定的类型名称</span><span class="sxs-lookup"><span data-stu-id="b726d-158">Specifying Fully Qualified Type Names</span></span>](specifying-fully-qualified-type-names.md)|<span data-ttu-id="b726d-159">描述 Backus-Naur 形式 (BNF) 的完全限定类型名称的格式，以及指定特殊字符、程序集名称、指针、引用和数组所需的语法。</span><span class="sxs-lookup"><span data-stu-id="b726d-159">Describes the format of fully qualified type names in terms of the Backus-Naur form (BNF), and the syntax required for specifying special characters, assembly names, pointers, references, and arrays.</span></span>|  
|[<span data-ttu-id="b726d-160">如何：使用反射将委托挂钩</span><span class="sxs-lookup"><span data-stu-id="b726d-160">How to: Hook Up a Delegate Using Reflection</span></span>](how-to-hook-up-a-delegate-using-reflection.md)|<span data-ttu-id="b726d-161">说明如何创建方法的委托并将委托挂钩到事件。</span><span class="sxs-lookup"><span data-stu-id="b726d-161">Explains how to create a delegate for a method and hook the delegate up to an event.</span></span> <span data-ttu-id="b726d-162">说明如何使用 <xref:System.Reflection.Emit.DynamicMethod> 在运行时创建事件处理方法。</span><span class="sxs-lookup"><span data-stu-id="b726d-162">Explains how to create an event-handling method at run time using <xref:System.Reflection.Emit.DynamicMethod>.</span></span>|  
|[<span data-ttu-id="b726d-163">发出动态方法和程序集</span><span class="sxs-lookup"><span data-stu-id="b726d-163">Emitting Dynamic Methods and Assemblies</span></span>](emitting-dynamic-methods-and-assemblies.md)|<span data-ttu-id="b726d-164">说明如何生成动态程序集和动态方法。</span><span class="sxs-lookup"><span data-stu-id="b726d-164">Explains how to generate dynamic assemblies and dynamic methods.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="b726d-165">参考</span><span class="sxs-lookup"><span data-stu-id="b726d-165">Reference</span></span>  

<xref:System.Type?displayProperty=nameWithType>  
  
<xref:System.Reflection>  
  
<xref:System.Reflection.Emit>  
