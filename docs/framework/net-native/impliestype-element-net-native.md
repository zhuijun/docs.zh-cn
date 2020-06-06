---
title: <ImpliesType>元素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 3abd2071-0f28-40ba-b9a0-d52bd94cd2f6
ms.openlocfilehash: 57f4208233cd5e8544b4f1c254e3b0e0eaacd508
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79181005"
---
# <a name="impliestype-element-net-native"></a><span data-ttu-id="db4a5-102">\<ImpliesType>元素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="db4a5-102">\<ImpliesType> Element (.NET Native)</span></span>
<span data-ttu-id="db4a5-103">如果该策略已应用到该包含类型或方法，将该策略应用到一个类型。</span><span class="sxs-lookup"><span data-stu-id="db4a5-103">Applies policy to a type, if that policy has been applied to the containing type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db4a5-104">语法</span><span class="sxs-lookup"><span data-stu-id="db4a5-104">Syntax</span></span>  
  
```xml
<ImpliesType Name="type_name"  
             Activate="policy_type"  
             Browse="policy_type"  
             Dynamic="policy_type"  
             Serialize="policy_type"
             DataContractSerializer="policy_setting"  
             DataContractJsonSerializer="policy_setting"  
             XmlSerializer="policy_setting"  
             MarshalObject="policy_setting"  
             MarshalDelegate="policy_setting"  
             MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db4a5-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="db4a5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="db4a5-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="db4a5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db4a5-107">特性</span><span class="sxs-lookup"><span data-stu-id="db4a5-107">Attributes</span></span>  
  
|<span data-ttu-id="db4a5-108">属性</span><span class="sxs-lookup"><span data-stu-id="db4a5-108">Attribute</span></span>|<span data-ttu-id="db4a5-109">属性类型</span><span class="sxs-lookup"><span data-stu-id="db4a5-109">Attribute type</span></span>|<span data-ttu-id="db4a5-110">说明</span><span class="sxs-lookup"><span data-stu-id="db4a5-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="db4a5-111">常规</span><span class="sxs-lookup"><span data-stu-id="db4a5-111">General</span></span>|<span data-ttu-id="db4a5-112">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="db4a5-112">Required attribute.</span></span> <span data-ttu-id="db4a5-113">指定类型名称。</span><span class="sxs-lookup"><span data-stu-id="db4a5-113">Specifies the type name.</span></span>|  
|`Activate`|<span data-ttu-id="db4a5-114">反射</span><span class="sxs-lookup"><span data-stu-id="db4a5-114">Reflection</span></span>|<span data-ttu-id="db4a5-115">可选特性。</span><span class="sxs-lookup"><span data-stu-id="db4a5-115">Optional attribute.</span></span> <span data-ttu-id="db4a5-116">控制运行时对构造函数的访问，以启用实例激活。</span><span class="sxs-lookup"><span data-stu-id="db4a5-116">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="db4a5-117">反射</span><span class="sxs-lookup"><span data-stu-id="db4a5-117">Reflection</span></span>|<span data-ttu-id="db4a5-118">可选特性。</span><span class="sxs-lookup"><span data-stu-id="db4a5-118">Optional attribute.</span></span> <span data-ttu-id="db4a5-119">控制对有关程序元素信息的查询，但并不启用任何运行时访问。</span><span class="sxs-lookup"><span data-stu-id="db4a5-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="db4a5-120">反射</span><span class="sxs-lookup"><span data-stu-id="db4a5-120">Reflection</span></span>|<span data-ttu-id="db4a5-121">可选特性。</span><span class="sxs-lookup"><span data-stu-id="db4a5-121">Optional attribute.</span></span> <span data-ttu-id="db4a5-122">控制运行时对所有类型成员的访问，包括构造函数、方法、字段、属性和事件，以启用动态编程。</span><span class="sxs-lookup"><span data-stu-id="db4a5-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="db4a5-123">序列化</span><span class="sxs-lookup"><span data-stu-id="db4a5-123">Serialization</span></span>|<span data-ttu-id="db4a5-124">可选特性。</span><span class="sxs-lookup"><span data-stu-id="db4a5-124">Optional attribute.</span></span> <span data-ttu-id="db4a5-125">控制运行时对构造函数、字段和属性的访问，使类型实例得到序列化和反序列化处理，这是通过库进行的，例如 Newtonsoft JSON 序列化程序。</span><span class="sxs-lookup"><span data-stu-id="db4a5-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="db4a5-126">序列化</span><span class="sxs-lookup"><span data-stu-id="db4a5-126">Serialization</span></span>|<span data-ttu-id="db4a5-127">可选特性。</span><span class="sxs-lookup"><span data-stu-id="db4a5-127">Optional attribute.</span></span> <span data-ttu-id="db4a5-128">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 类的序列化策略。</span><span class="sxs-lookup"><span data-stu-id="db4a5-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="db4a5-129">序列化</span><span class="sxs-lookup"><span data-stu-id="db4a5-129">Serialization</span></span>|<span data-ttu-id="db4a5-130">可选特性。</span><span class="sxs-lookup"><span data-stu-id="db4a5-130">Optional attribute.</span></span> <span data-ttu-id="db4a5-131">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 类的 JSON 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="db4a5-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="db4a5-132">序列化</span><span class="sxs-lookup"><span data-stu-id="db4a5-132">Serialization</span></span>|<span data-ttu-id="db4a5-133">可选特性。</span><span class="sxs-lookup"><span data-stu-id="db4a5-133">Optional attribute.</span></span> <span data-ttu-id="db4a5-134">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 类的 XML 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="db4a5-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="db4a5-135">Interop</span><span class="sxs-lookup"><span data-stu-id="db4a5-135">Interop</span></span>|<span data-ttu-id="db4a5-136">可选特性。</span><span class="sxs-lookup"><span data-stu-id="db4a5-136">Optional attribute.</span></span> <span data-ttu-id="db4a5-137">控制封送引用类型到 Windows 运行时和 COM 的策略。</span><span class="sxs-lookup"><span data-stu-id="db4a5-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="db4a5-138">Interop</span><span class="sxs-lookup"><span data-stu-id="db4a5-138">Interop</span></span>|<span data-ttu-id="db4a5-139">可选特性。</span><span class="sxs-lookup"><span data-stu-id="db4a5-139">Optional attribute.</span></span> <span data-ttu-id="db4a5-140">控制将委托类型作为函数指针封送到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="db4a5-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="db4a5-141">Interop</span><span class="sxs-lookup"><span data-stu-id="db4a5-141">Interop</span></span>|<span data-ttu-id="db4a5-142">可选特性。</span><span class="sxs-lookup"><span data-stu-id="db4a5-142">Optional attribute.</span></span> <span data-ttu-id="db4a5-143">控制封送处理值类型到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="db4a5-143">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="db4a5-144">Name 特性</span><span class="sxs-lookup"><span data-stu-id="db4a5-144">Name attribute</span></span>  
  
|<span data-ttu-id="db4a5-145">值</span><span class="sxs-lookup"><span data-stu-id="db4a5-145">Value</span></span>|<span data-ttu-id="db4a5-146">说明</span><span class="sxs-lookup"><span data-stu-id="db4a5-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db4a5-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="db4a5-147">*type_name*</span></span>|<span data-ttu-id="db4a5-148">类型名称。</span><span class="sxs-lookup"><span data-stu-id="db4a5-148">The type name.</span></span> <span data-ttu-id="db4a5-149">如果此 `<ImpliesType>` 元素代表的类型同其包含的 `<Type>` 元素位于相同的命名空间，type_name\*\* 可能会包括类型名称而不包括其命名空间。</span><span class="sxs-lookup"><span data-stu-id="db4a5-149">If the type represented by this `<ImpliesType>` element is located in the same namespace as its containing `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="db4a5-150">否则，type_name\*\* 必须包含完全限定的类型名称。</span><span class="sxs-lookup"><span data-stu-id="db4a5-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="db4a5-151">所有其他特性</span><span class="sxs-lookup"><span data-stu-id="db4a5-151">All other attributes</span></span>  
  
|<span data-ttu-id="db4a5-152">值</span><span class="sxs-lookup"><span data-stu-id="db4a5-152">Value</span></span>|<span data-ttu-id="db4a5-153">说明</span><span class="sxs-lookup"><span data-stu-id="db4a5-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="db4a5-154">*策略_设置*</span><span class="sxs-lookup"><span data-stu-id="db4a5-154">*policy_setting*</span></span>|<span data-ttu-id="db4a5-155">该设置将应用到这种策略类型。</span><span class="sxs-lookup"><span data-stu-id="db4a5-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="db4a5-156">可能值为 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 以及 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="db4a5-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="db4a5-157">有关详细信息，请参阅[运行时指令策略设置](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="db4a5-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db4a5-158">子元素</span><span class="sxs-lookup"><span data-stu-id="db4a5-158">Child Elements</span></span>  
 <span data-ttu-id="db4a5-159">无。</span><span class="sxs-lookup"><span data-stu-id="db4a5-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db4a5-160">父元素</span><span class="sxs-lookup"><span data-stu-id="db4a5-160">Parent Elements</span></span>  
  
|<span data-ttu-id="db4a5-161">元素</span><span class="sxs-lookup"><span data-stu-id="db4a5-161">Element</span></span>|<span data-ttu-id="db4a5-162">说明</span><span class="sxs-lookup"><span data-stu-id="db4a5-162">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="db4a5-163">将反射策略应用到一种类型及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="db4a5-163">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="db4a5-164">将反射策略应用到一种构造泛型类型及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="db4a5-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="db4a5-165">将反射策略应用到一个方法。</span><span class="sxs-lookup"><span data-stu-id="db4a5-165">Applies reflection policy to a method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db4a5-166">注解</span><span class="sxs-lookup"><span data-stu-id="db4a5-166">Remarks</span></span>  
 <span data-ttu-id="db4a5-167">该 `<ImpliesType>` 元素主要是供库使用的。</span><span class="sxs-lookup"><span data-stu-id="db4a5-167">The `<ImpliesType>` element is primarily intended for use by libraries.</span></span> <span data-ttu-id="db4a5-168">它讨论的是以下情景：</span><span class="sxs-lookup"><span data-stu-id="db4a5-168">It addresses the following scenario:</span></span>  
  
- <span data-ttu-id="db4a5-169">如果一个例程需要反射到一个类型，它必然也要反射到另一种类型。</span><span class="sxs-lookup"><span data-stu-id="db4a5-169">If a routine needs to reflect on one type, it necessarily needs to reflect on a second type.</span></span>  
  
- <span data-ttu-id="db4a5-170">否则，第二种类型的暗示的实例化元数据就不可用，因为静态分析没有指示这一步骤是必须的。</span><span class="sxs-lookup"><span data-stu-id="db4a5-170">The metadata for the implied instantiation of the second type is otherwise unavailable, because static analysis doesn't indicate that it's necessary.</span></span>  
  
 <span data-ttu-id="db4a5-171">最常见的两种类型是附带共享类型参数的泛型实例化。</span><span class="sxs-lookup"><span data-stu-id="db4a5-171">Most commonly, the two types are generic instantiations with shared type arguments.</span></span>  
  
 <span data-ttu-id="db4a5-172">对 `<ImpliesType>` 元素的定义是以一个假设为基础的，即如果需要反射到父元素指定的类型上暗示着也需要反射到 `<ImpliesType>` 元素指定的类型上。</span><span class="sxs-lookup"><span data-stu-id="db4a5-172">The `<ImpliesType>` element was defined with the assumption that a need for reflection on the type specified by its parent element implies a need for reflection on the type specified by the `<ImpliesType>` element.</span></span> <span data-ttu-id="db4a5-173">例如，以下反射指令应用到两种类型，`Explicit<T>` 和 `Implicit<T>`。</span><span class="sxs-lookup"><span data-stu-id="db4a5-173">For example, the following reflection directives apply to two types, `Explicit<T>` and `Implicit<T>`.</span></span>  
  
```xml  
<Type Name="Explicit{ET}">  
    <ImpliesType Name="Implicit{ET}" Dynamic="Required Public" />  
</Type>  
```  
  
 <span data-ttu-id="db4a5-174">这个指令是不起作用的，除非 `Explicit` 的一个实例化具有一个已定义的 `Dynamic` 策略设置。</span><span class="sxs-lookup"><span data-stu-id="db4a5-174">This directive has no effect unless an instantiation of `Explicit` has a defined `Dynamic` policy setting.</span></span> <span data-ttu-id="db4a5-175">例如，如果对于 `Explicit<Int32>` 情况如此，`Implicit<Int32>` 会同其根公共成员一起被实例化，并且它们的元数据就能由动态编程访问。</span><span class="sxs-lookup"><span data-stu-id="db4a5-175">For example, if that's the case for `Explicit<Int32>`, `Implicit<Int32>` is instantiated with its public members rooted, and their metadata is made accessible for dynamic programming.</span></span>  
  
 <span data-ttu-id="db4a5-176">以下是一个至少可以应用到序列化程序的实际实例。</span><span class="sxs-lookup"><span data-stu-id="db4a5-176">The following is a real-world example that applies to at least one serializer.</span></span> <span data-ttu-id="db4a5-177">指令捕获对类型化为内容的内容进行反射的需求， `IList<` *something* `>` `List<` *something* `>` 而不需要每个应用程序的批注就会反映相应的内容类型。</span><span class="sxs-lookup"><span data-stu-id="db4a5-177">The directives capture the requirement that reflecting on something typed as `IList<`*something*`>` also involves reflecting on the corresponding `List<`*something*`>` type without requiring any per-application annotation.</span></span>  
  
```xml  
<Type Name="System.Collections.Generic.IList{T}">  
   <ImpliesType Name="System.Collections.Generic.List{T}" Serialize="Public" />  
</Type>  
```  
  
 <span data-ttu-id="db4a5-178">`<ImpliesType>` 元素也可能出现在 `<Method>` 元素内部，因为在某些情况下泛型方法暗示着反射到了一个类型实例化上。</span><span class="sxs-lookup"><span data-stu-id="db4a5-178">The `<ImpliesType>` element can also appear within a `<Method>` element, because in some cases instantiating a generic method implies reflecting on a type instantiation.</span></span> <span data-ttu-id="db4a5-179">例如，想象一个特定的库可以动态访问的泛型方法 `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` 以及相关的 <xref:System.Collections.Generic.List%601> 和 <xref:System.Array> 类型。</span><span class="sxs-lookup"><span data-stu-id="db4a5-179">For example, imagine a generic method `IEnumerable<T> MakeEnumerable<T>(string spelling, T defaultValue)` that a given library will access dynamically along with the associated <xref:System.Collections.Generic.List%601> and <xref:System.Array> types.</span></span> <span data-ttu-id="db4a5-180">这可以表示为：</span><span class="sxs-lookup"><span data-stu-id="db4a5-180">This can be expressed as:</span></span>  
  
```xml  
<Type Name="MyType">  
    <Method Name="MakeEnumerable{T}" Signature="(System.String, T)" Dynamic="Included">  
        <ImpliesType Name="T[]" Dynamic="Public" />  
        <ImpliesType Name="System.Collections.Generic.List{T}" Dynamic="Public" />  
    </Method>  
</Type>  
```  
  
## <a name="see-also"></a><span data-ttu-id="db4a5-181">另请参阅</span><span class="sxs-lookup"><span data-stu-id="db4a5-181">See also</span></span>

- [<span data-ttu-id="db4a5-182">运行时指令 (rd.xml) 配置文件引用</span><span class="sxs-lookup"><span data-stu-id="db4a5-182">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="db4a5-183">运行时指令元素</span><span class="sxs-lookup"><span data-stu-id="db4a5-183">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="db4a5-184">运行时指令策略设置</span><span class="sxs-lookup"><span data-stu-id="db4a5-184">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
