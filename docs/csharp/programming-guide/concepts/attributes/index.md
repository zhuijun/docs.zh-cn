---
title: 特性 (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 358285a39f72ad3ddf1b265e20b443308375d074
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241573"
---
# <a name="attributes-c"></a><span data-ttu-id="06535-102">特性 (C#)</span><span class="sxs-lookup"><span data-stu-id="06535-102">Attributes (C#)</span></span>

<span data-ttu-id="06535-103">使用特性，可以有效地将元数据或声明性信息与代码（程序集、类型、方法、属性等）相关联。</span><span class="sxs-lookup"><span data-stu-id="06535-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="06535-104">将特性与程序实体相关联后，可以在运行时使用*反射*这项技术查询特性。</span><span class="sxs-lookup"><span data-stu-id="06535-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="06535-105">有关详细信息，请参阅[反射 (C#)](../reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="06535-105">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="06535-106">特性具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="06535-106">Attributes have the following properties:</span></span>

- <span data-ttu-id="06535-107">特性向程序添加元数据。</span><span class="sxs-lookup"><span data-stu-id="06535-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="06535-108">*元数据*是程序中定义的类型的相关信息。</span><span class="sxs-lookup"><span data-stu-id="06535-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="06535-109">所有 .NET 程序集都包含一组指定的元数据，用于描述程序集中定义的类型和类型成员。</span><span class="sxs-lookup"><span data-stu-id="06535-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="06535-110">可以添加自定义特性来指定所需的其他任何信息。</span><span class="sxs-lookup"><span data-stu-id="06535-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="06535-111">有关详细信息，请参阅[创建自定义特性 (C#)](creating-custom-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="06535-111">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="06535-112">可以将一个或多个特性应用于整个程序集、模块或较小的程序元素（如类和属性）。</span><span class="sxs-lookup"><span data-stu-id="06535-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="06535-113">特性可以像方法和属性一样接受自变量。</span><span class="sxs-lookup"><span data-stu-id="06535-113">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="06535-114">程序可使用反射来检查自己的元数据或其他程序中的元数据。</span><span class="sxs-lookup"><span data-stu-id="06535-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="06535-115">有关详细信息，请参阅[使用反射访问特性 (C#)](accessing-attributes-by-using-reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="06535-115">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="06535-116">使用特性</span><span class="sxs-lookup"><span data-stu-id="06535-116">Using attributes</span></span>

<span data-ttu-id="06535-117">可以将特性附加到大多数的声明中，尽管特定特性可能会限制可有效附加到的声明的类型。</span><span class="sxs-lookup"><span data-stu-id="06535-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="06535-118">在 C# 中，通过用方括号 ([]) 将特性名称括起来，并置于应用该特性的实体的声明上方以指定特性。</span><span class="sxs-lookup"><span data-stu-id="06535-118">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="06535-119">在此示例中，<xref:System.SerializableAttribute> 特性用于将具体特征应用于类：</span><span class="sxs-lookup"><span data-stu-id="06535-119">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="06535-120">下方示例声明了一个具有特性 <xref:System.Runtime.InteropServices.DllImportAttribute> 的方法：</span><span class="sxs-lookup"><span data-stu-id="06535-120">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="06535-121">如下方示例所示，可以将多个特性附加到声明中：</span><span class="sxs-lookup"><span data-stu-id="06535-121">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="06535-122">对于给定实体，一些特性可以指定多次。</span><span class="sxs-lookup"><span data-stu-id="06535-122">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="06535-123"><xref:System.Diagnostics.ConditionalAttribute> 便属于此类多用途特性：</span><span class="sxs-lookup"><span data-stu-id="06535-123">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="06535-124">按照约定，所有特性名称均以“Attribute”一词结尾，以便与 .NET 库中的其他项区分开来。</span><span class="sxs-lookup"><span data-stu-id="06535-124">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="06535-125">不过，在代码中使用特性时，无需指定特性后缀。</span><span class="sxs-lookup"><span data-stu-id="06535-125">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="06535-126">例如，`[DllImport]` 等同于 `[DllImportAttribute]`，但 `DllImportAttribute` 是此特性在 .NET 类库中的实际名称。</span><span class="sxs-lookup"><span data-stu-id="06535-126">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="06535-127">特性参数</span><span class="sxs-lookup"><span data-stu-id="06535-127">Attribute parameters</span></span>

<span data-ttu-id="06535-128">许多属性都有参数，可以是位置参数、未命名参数或已命名参数。</span><span class="sxs-lookup"><span data-stu-id="06535-128">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="06535-129">必须以特定顺序指定任何位置参数，且不能省略。</span><span class="sxs-lookup"><span data-stu-id="06535-129">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="06535-130">已命名参数是可选参数，可以通过任何顺序指定。</span><span class="sxs-lookup"><span data-stu-id="06535-130">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="06535-131">首先指定的是位置参数。</span><span class="sxs-lookup"><span data-stu-id="06535-131">Positional parameters are specified first.</span></span> <span data-ttu-id="06535-132">例如，下面这三个特性是等同的：</span><span class="sxs-lookup"><span data-stu-id="06535-132">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="06535-133">第一个参数（DLL 名称）是位置参数，始终第一个出现；其他是已命名参数。</span><span class="sxs-lookup"><span data-stu-id="06535-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="06535-134">在此示例中，两个已命名参数的默认值均为 false，因此可以省略。</span><span class="sxs-lookup"><span data-stu-id="06535-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="06535-135">位置参数与特性构造函数的参数相对应。</span><span class="sxs-lookup"><span data-stu-id="06535-135">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="06535-136">已命名或可选参数与该特性的属性或字段相对应。</span><span class="sxs-lookup"><span data-stu-id="06535-136">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="06535-137">若要了解默认参数值，请参阅各个特性文档。</span><span class="sxs-lookup"><span data-stu-id="06535-137">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="06535-138">特性目标</span><span class="sxs-lookup"><span data-stu-id="06535-138">Attribute targets</span></span>

<span data-ttu-id="06535-139">特性目标是指应用特性的实体。</span><span class="sxs-lookup"><span data-stu-id="06535-139">The *target* of an attribute is the entity which the attribute applies to.</span></span> <span data-ttu-id="06535-140">例如，特性可应用于类、特定方法或整个程序集。</span><span class="sxs-lookup"><span data-stu-id="06535-140">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="06535-141">默认情况下，特性应用于紧跟在它后面的元素。</span><span class="sxs-lookup"><span data-stu-id="06535-141">By default, an attribute applies to the element that follows it.</span></span> <span data-ttu-id="06535-142">不过，还可以进行显式标识。例如，可以标识为将特性应用于方法，还是应用于其参数或返回值。</span><span class="sxs-lookup"><span data-stu-id="06535-142">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="06535-143">若要显式标识特性目标，请使用以下语法：</span><span class="sxs-lookup"><span data-stu-id="06535-143">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="06535-144">下表列出了可能的 `target` 值。</span><span class="sxs-lookup"><span data-stu-id="06535-144">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="06535-145">目标值</span><span class="sxs-lookup"><span data-stu-id="06535-145">Target value</span></span>|<span data-ttu-id="06535-146">适用对象</span><span class="sxs-lookup"><span data-stu-id="06535-146">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="06535-147">整个程序集</span><span class="sxs-lookup"><span data-stu-id="06535-147">Entire assembly</span></span>|
|`module`|<span data-ttu-id="06535-148">当前程序集模块</span><span class="sxs-lookup"><span data-stu-id="06535-148">Current assembly module</span></span>|
|`field`|<span data-ttu-id="06535-149">类或结构中的字段</span><span class="sxs-lookup"><span data-stu-id="06535-149">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="06535-150">事件</span><span class="sxs-lookup"><span data-stu-id="06535-150">Event</span></span>|
|`method`|<span data-ttu-id="06535-151">方法或 `get` 和 `set` 属性访问器</span><span class="sxs-lookup"><span data-stu-id="06535-151">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="06535-152">方法参数或 `set` 属性访问器参数</span><span class="sxs-lookup"><span data-stu-id="06535-152">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="06535-153">Property</span><span class="sxs-lookup"><span data-stu-id="06535-153">Property</span></span>|
|`return`|<span data-ttu-id="06535-154">方法、属性索引器或 `get` 属性访问器的返回值</span><span class="sxs-lookup"><span data-stu-id="06535-154">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="06535-155">结构、类、接口、枚举或委托</span><span class="sxs-lookup"><span data-stu-id="06535-155">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="06535-156">指定 `field` 目标值，将特性应用到为[自动实现的属性](../../../properties.md)创建的支持字段。</span><span class="sxs-lookup"><span data-stu-id="06535-156">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="06535-157">下面的示例展示了如何将特性应用于程序集和模块。</span><span class="sxs-lookup"><span data-stu-id="06535-157">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="06535-158">有关详细信息，请参阅[通用特性 (C#)](../../../language-reference/attributes/global.md)。</span><span class="sxs-lookup"><span data-stu-id="06535-158">For more information, see [Common Attributes (C#)](../../../language-reference/attributes/global.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="06535-159">以下示例演示如何将特性应用于 C# 中的方法、方法参数和方法返回值。</span><span class="sxs-lookup"><span data-stu-id="06535-159">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="06535-160">无论在哪个目标上将 `ValidatedContract` 定义为有效，都必须指定 `return` 目标，即使 `ValidatedContract` 定义为仅应用于返回值也是如此。</span><span class="sxs-lookup"><span data-stu-id="06535-160">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="06535-161">换言之，编译器不会使用 `AttributeUsage` 信息来解析不明确的特性目标。</span><span class="sxs-lookup"><span data-stu-id="06535-161">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="06535-162">有关详细信息，请参阅 [AttributeUsage (C#)](../../../language-reference/attributes/general.md)。</span><span class="sxs-lookup"><span data-stu-id="06535-162">For more information, see [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="06535-163">特性的常见用途</span><span class="sxs-lookup"><span data-stu-id="06535-163">Common uses for attributes</span></span>

<span data-ttu-id="06535-164">下面列出了代码中特性的一些常见用途：</span><span class="sxs-lookup"><span data-stu-id="06535-164">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="06535-165">在 Web 服务中使用 `WebMethod` 特性标记方法，以指明方法应可通过 SOAP 协议进行调用。</span><span class="sxs-lookup"><span data-stu-id="06535-165">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="06535-166">有关详细信息，请参阅 <xref:System.Web.Services.WebMethodAttribute>。</span><span class="sxs-lookup"><span data-stu-id="06535-166">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="06535-167">描述在与本机代码互操作时如何封送方法参数。</span><span class="sxs-lookup"><span data-stu-id="06535-167">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="06535-168">有关详细信息，请参阅 <xref:System.Runtime.InteropServices.MarshalAsAttribute>。</span><span class="sxs-lookup"><span data-stu-id="06535-168">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="06535-169">描述类、方法和接口的 COM 属性。</span><span class="sxs-lookup"><span data-stu-id="06535-169">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="06535-170">使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 类调用非托管代码。</span><span class="sxs-lookup"><span data-stu-id="06535-170">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="06535-171">从标题、版本、说明或商标方面描述程序集。</span><span class="sxs-lookup"><span data-stu-id="06535-171">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="06535-172">描述要序列化并暂留类的哪些成员。</span><span class="sxs-lookup"><span data-stu-id="06535-172">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="06535-173">描述如何为了执行 XML 序列化在类成员和 XML 节点之间进行映射。</span><span class="sxs-lookup"><span data-stu-id="06535-173">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="06535-174">描述的方法的安全要求。</span><span class="sxs-lookup"><span data-stu-id="06535-174">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="06535-175">指定用于强制实施安全规范的特征。</span><span class="sxs-lookup"><span data-stu-id="06535-175">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="06535-176">通过实时 (JIT) 编译器控制优化，这样代码就一直都易于调试。</span><span class="sxs-lookup"><span data-stu-id="06535-176">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="06535-177">获取方法调用方的相关信息。</span><span class="sxs-lookup"><span data-stu-id="06535-177">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="06535-178">相关章节</span><span class="sxs-lookup"><span data-stu-id="06535-178">Related sections</span></span>

<span data-ttu-id="06535-179">有关详细信息，请参见:</span><span class="sxs-lookup"><span data-stu-id="06535-179">For more information, see:</span></span>

- [<span data-ttu-id="06535-180">创建自定义特性 (C#)</span><span class="sxs-lookup"><span data-stu-id="06535-180">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="06535-181">使用反射访问特性 (C#)</span><span class="sxs-lookup"><span data-stu-id="06535-181">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="06535-182">如何使用特性创建 C/C++ 联合 (C#)</span><span class="sxs-lookup"><span data-stu-id="06535-182">How to create a C/C++ union by using attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="06535-183">通用特性 (C#)</span><span class="sxs-lookup"><span data-stu-id="06535-183">Common Attributes (C#)</span></span>](../../../language-reference/attributes/global.md)  
- [<span data-ttu-id="06535-184">调用方信息 (C#)</span><span class="sxs-lookup"><span data-stu-id="06535-184">Caller Information (C#)</span></span>](../../../language-reference/attributes/caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="06535-185">请参阅</span><span class="sxs-lookup"><span data-stu-id="06535-185">See also</span></span>

- [<span data-ttu-id="06535-186">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="06535-186">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="06535-187">反射 (C#)</span><span class="sxs-lookup"><span data-stu-id="06535-187">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="06535-188">特性</span><span class="sxs-lookup"><span data-stu-id="06535-188">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="06535-189">在 C# 中使用特性</span><span class="sxs-lookup"><span data-stu-id="06535-189">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)
