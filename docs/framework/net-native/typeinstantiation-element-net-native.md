---
title: <TypeInstantiation>元素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
ms.openlocfilehash: 9069856b3d8739724d148b5eea5d4188c8b8b9e1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128679"
---
# <a name="typeinstantiation-element-net-native"></a><span data-ttu-id="c1ea3-102">\<TypeInstantiation>元素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="c1ea3-102">\<TypeInstantiation> Element (.NET Native)</span></span>
<span data-ttu-id="c1ea3-103">将运行时反射策略应用到一个构造泛型类型。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-103">Applies runtime reflection policy to a constructed generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1ea3-104">语法</span><span class="sxs-lookup"><span data-stu-id="c1ea3-104">Syntax</span></span>  
  
```xml  
<TypeInstantiation Name="type_name"  
                   Arguments="type_arguments"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1ea3-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c1ea3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c1ea3-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1ea3-107">特性</span><span class="sxs-lookup"><span data-stu-id="c1ea3-107">Attributes</span></span>  
  
|<span data-ttu-id="c1ea3-108">属性</span><span class="sxs-lookup"><span data-stu-id="c1ea3-108">Attribute</span></span>|<span data-ttu-id="c1ea3-109">属性类型</span><span class="sxs-lookup"><span data-stu-id="c1ea3-109">Attribute type</span></span>|<span data-ttu-id="c1ea3-110">说明</span><span class="sxs-lookup"><span data-stu-id="c1ea3-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="c1ea3-111">常规</span><span class="sxs-lookup"><span data-stu-id="c1ea3-111">General</span></span>|<span data-ttu-id="c1ea3-112">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-112">Required attribute.</span></span> <span data-ttu-id="c1ea3-113">指定类型名称。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-113">Specifies the type name.</span></span>|  
|`Arguments`|<span data-ttu-id="c1ea3-114">常规</span><span class="sxs-lookup"><span data-stu-id="c1ea3-114">General</span></span>|<span data-ttu-id="c1ea3-115">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-115">Required attribute.</span></span> <span data-ttu-id="c1ea3-116">指定泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-116">Specifies the generic type arguments.</span></span> <span data-ttu-id="c1ea3-117">如果存在多个自变量，它们之间用逗号分割。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-117">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Activate`|<span data-ttu-id="c1ea3-118">反射</span><span class="sxs-lookup"><span data-stu-id="c1ea3-118">Reflection</span></span>|<span data-ttu-id="c1ea3-119">可选特性。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-119">Optional attribute.</span></span> <span data-ttu-id="c1ea3-120">控制运行时对构造函数的访问，以启用实例激活。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-120">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="c1ea3-121">反射</span><span class="sxs-lookup"><span data-stu-id="c1ea3-121">Reflection</span></span>|<span data-ttu-id="c1ea3-122">可选特性。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-122">Optional attribute.</span></span> <span data-ttu-id="c1ea3-123">控制对有关程序元素信息的查询，但并不启用任何运行时访问。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-123">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="c1ea3-124">反射</span><span class="sxs-lookup"><span data-stu-id="c1ea3-124">Reflection</span></span>|<span data-ttu-id="c1ea3-125">可选特性。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-125">Optional attribute.</span></span> <span data-ttu-id="c1ea3-126">控制运行时对所有类型成员的访问，包括构造函数、方法、字段、属性和事件，以启用动态编程。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-126">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="c1ea3-127">序列化</span><span class="sxs-lookup"><span data-stu-id="c1ea3-127">Serialization</span></span>|<span data-ttu-id="c1ea3-128">可选特性。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-128">Optional attribute.</span></span> <span data-ttu-id="c1ea3-129">控制运行时对构造函数、字段和属性的访问，使类型实例得到序列化和反序列化处理，这是通过库进行的，例如 Newtonsoft JSON 序列化程序。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-129">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="c1ea3-130">序列化</span><span class="sxs-lookup"><span data-stu-id="c1ea3-130">Serialization</span></span>|<span data-ttu-id="c1ea3-131">可选特性。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-131">Optional attribute.</span></span> <span data-ttu-id="c1ea3-132">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 类的序列化策略。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-132">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="c1ea3-133">序列化</span><span class="sxs-lookup"><span data-stu-id="c1ea3-133">Serialization</span></span>|<span data-ttu-id="c1ea3-134">可选特性。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-134">Optional attribute.</span></span> <span data-ttu-id="c1ea3-135">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 类的 JSON 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-135">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="c1ea3-136">序列化</span><span class="sxs-lookup"><span data-stu-id="c1ea3-136">Serialization</span></span>|<span data-ttu-id="c1ea3-137">可选特性。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-137">Optional attribute.</span></span> <span data-ttu-id="c1ea3-138">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 类的 XML 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-138">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="c1ea3-139">Interop</span><span class="sxs-lookup"><span data-stu-id="c1ea3-139">Interop</span></span>|<span data-ttu-id="c1ea3-140">可选特性。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-140">Optional attribute.</span></span> <span data-ttu-id="c1ea3-141">控制封送引用类型到 Windows 运行时和 COM 的策略。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-141">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="c1ea3-142">Interop</span><span class="sxs-lookup"><span data-stu-id="c1ea3-142">Interop</span></span>|<span data-ttu-id="c1ea3-143">可选特性。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-143">Optional attribute.</span></span> <span data-ttu-id="c1ea3-144">控制将委托类型作为函数指针封送到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-144">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="c1ea3-145">Interop</span><span class="sxs-lookup"><span data-stu-id="c1ea3-145">Interop</span></span>|<span data-ttu-id="c1ea3-146">可选特性。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-146">Optional attribute.</span></span> <span data-ttu-id="c1ea3-147">控制封送结构到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-147">Controls policy for marshaling structures to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="c1ea3-148">Name 特性</span><span class="sxs-lookup"><span data-stu-id="c1ea3-148">Name attribute</span></span>  
  
|<span data-ttu-id="c1ea3-149">值</span><span class="sxs-lookup"><span data-stu-id="c1ea3-149">Value</span></span>|<span data-ttu-id="c1ea3-150">说明</span><span class="sxs-lookup"><span data-stu-id="c1ea3-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c1ea3-151">*type_name*</span><span class="sxs-lookup"><span data-stu-id="c1ea3-151">*type_name*</span></span>|<span data-ttu-id="c1ea3-152">类型名称。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-152">The type name.</span></span> <span data-ttu-id="c1ea3-153">如果此 `<TypeInstantiation>` 元素是 [\<Namespace>](namespace-element-net-native.md) 元素、元素或另一个元素的子元素，则 [\<Type>](type-element-net-native.md) `<TypeInstantiation>` *type_name*可以指定该类型的名称，而无需命名空间。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-153">If this `<TypeInstantiation>` element is the child of a [\<Namespace>](namespace-element-net-native.md) element, a [\<Type>](type-element-net-native.md) element, or another `<TypeInstantiation>` element, *type_name* can specify the name of the type without its namespace.</span></span> <span data-ttu-id="c1ea3-154">否则，type_name\*\* 必须包含完全限定的类型名称。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-154">Otherwise, *type_name* must include the fully qualified type name.</span></span> <span data-ttu-id="c1ea3-155">该类型名称没有经过修饰。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-155">The type name isn't decorated.</span></span> <span data-ttu-id="c1ea3-156">例如，对于一个 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 对象，`<TypeInstantiation>` 元素可能显示如下：</span><span class="sxs-lookup"><span data-stu-id="c1ea3-156">For example, for a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> object, the `<TypeInstantiation>` element might appear as follows:</span></span><br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="c1ea3-157">自变量特性</span><span class="sxs-lookup"><span data-stu-id="c1ea3-157">Arguments attribute</span></span>  
  
|<span data-ttu-id="c1ea3-158">值</span><span class="sxs-lookup"><span data-stu-id="c1ea3-158">Value</span></span>|<span data-ttu-id="c1ea3-159">说明</span><span class="sxs-lookup"><span data-stu-id="c1ea3-159">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c1ea3-160">type_argument\*\*</span><span class="sxs-lookup"><span data-stu-id="c1ea3-160">*type_argument*</span></span>|<span data-ttu-id="c1ea3-161">指定泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-161">Specifies the generic type arguments.</span></span> <span data-ttu-id="c1ea3-162">如果存在多个自变量，它们之间用逗号分割。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-162">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="c1ea3-163">每个自变量必须包含一个完全限定的类型名称。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-163">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="c1ea3-164">所有其他特性</span><span class="sxs-lookup"><span data-stu-id="c1ea3-164">All other attributes</span></span>  
  
|<span data-ttu-id="c1ea3-165">值</span><span class="sxs-lookup"><span data-stu-id="c1ea3-165">Value</span></span>|<span data-ttu-id="c1ea3-166">说明</span><span class="sxs-lookup"><span data-stu-id="c1ea3-166">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c1ea3-167">*策略_设置*</span><span class="sxs-lookup"><span data-stu-id="c1ea3-167">*policy_setting*</span></span>|<span data-ttu-id="c1ea3-168">该设置将应用到这个构造泛型类型的策略类型。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-168">The setting to apply to this policy type for the constructed generic type.</span></span> <span data-ttu-id="c1ea3-169">可能值为 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 以及 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-169">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="c1ea3-170">有关详细信息，请参阅[运行时指令策略设置](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-170">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1ea3-171">子元素</span><span class="sxs-lookup"><span data-stu-id="c1ea3-171">Child Elements</span></span>  
  
|<span data-ttu-id="c1ea3-172">元素</span><span class="sxs-lookup"><span data-stu-id="c1ea3-172">Element</span></span>|<span data-ttu-id="c1ea3-173">说明</span><span class="sxs-lookup"><span data-stu-id="c1ea3-173">Description</span></span>|  
|-------------|-----------------|  
|[\<Event>](event-element-net-native.md)|<span data-ttu-id="c1ea3-174">将反射策略应用到属于这种类型的一个事件。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-174">Applies reflection policy to an event belonging to this type.</span></span>|  
|[\<Field>](field-element-net-native.md)|<span data-ttu-id="c1ea3-175">将反射策略应用到属于这种类型的一个字段。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-175">Applies reflection policy to a field belonging to this type.</span></span>|  
|[\<ImpliesType>](impliestype-element-net-native.md)|<span data-ttu-id="c1ea3-176">如果该策略已应用到以包含 `<TypeInstantiation>` 元素为代表的类型，将该策略应用到一个类型。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-176">Applies policy to a type, if that policy has been applied to the type represented by the containing `<TypeInstantiation>` element.</span></span>|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="c1ea3-177">将反射策略应用到属于这种类型的一个方法。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-177">Applies reflection policy to a method belonging to this type.</span></span>|  
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|<span data-ttu-id="c1ea3-178">将反射策略应用到属于这种类型的一个构造泛型方法。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-178">Applies reflection policy to a constructed generic method belonging to this type.</span></span>|  
|[\<Property>](property-element-net-native.md)|<span data-ttu-id="c1ea3-179">将反射策略应用到属于这种类型的一个属性。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-179">Applies reflection policy to a property belonging to this type.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="c1ea3-180">将反射策略应用到一个嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-180">Applies reflection policy to a nested type.</span></span>|  
|`<TypeInstantiation>`|<span data-ttu-id="c1ea3-181">将反射策略应用到一个嵌套的构造泛型类型。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-181">Applies reflection policy to a nested constructed generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c1ea3-182">父元素</span><span class="sxs-lookup"><span data-stu-id="c1ea3-182">Parent Elements</span></span>  
  
|<span data-ttu-id="c1ea3-183">元素</span><span class="sxs-lookup"><span data-stu-id="c1ea3-183">Element</span></span>|<span data-ttu-id="c1ea3-184">说明</span><span class="sxs-lookup"><span data-stu-id="c1ea3-184">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="c1ea3-185">作为应用程序范围内的类型和元数据可以反应在运行时间的类型成员的容器而服务。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-185">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span>|  
|[\<Assembly>](assembly-element-net-native.md)|<span data-ttu-id="c1ea3-186">将反射策略应用到指定程序集中的所有类型。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-186">Applies reflection policy to all the types in a specified assembly.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="c1ea3-187">定义包含元数据在运行时间可以用于反射的类型和类型成员的程序集。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-187">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>|  
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="c1ea3-188">将反射策略应用到命名空间中的所有类型。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-188">Applies reflection policy to all the types in a namespace.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="c1ea3-189">将反射策略应用到一种类型及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-189">Applies reflection policy to a type and all its members.</span></span>|  
|`<TypeInstantiation>`|<span data-ttu-id="c1ea3-190">将反射策略应用到一种构造泛型类型及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-190">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1ea3-191">注解</span><span class="sxs-lookup"><span data-stu-id="c1ea3-191">Remarks</span></span>  
 <span data-ttu-id="c1ea3-192">反射、序列化和互操作特性都是可选项。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-192">The reflection, serialization, and interop attributes are all optional.</span></span> <span data-ttu-id="c1ea3-193">然而，至少一个特性必须存在。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-193">However, at least one must be present.</span></span>  
  
 <span data-ttu-id="c1ea3-194">如果 `<TypeInstantiation>` 元素是 [\<Assembly>](assembly-element-net-native.md) 、 [\<Namespace>](namespace-element-net-native.md) 、或元素的子元素 [\<Type>](type-element-net-native.md) ，则它会重写由父元素定义的策略设置。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-194">If a `<TypeInstantiation>` element is the child of an [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), or [\<Type>](type-element-net-native.md), element, it overrides the policy settings defined by the parent element.</span></span> <span data-ttu-id="c1ea3-195">如果 [\<Type>](type-element-net-native.md) 元素定义了一个相应的泛型类型定义，则 `<TypeInstantiation>` 元素只会重写指定的构造泛型类型的实例化的运行时反射策略。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-195">If a [\<Type>](type-element-net-native.md) element defines a corresponding generic type definition, the `<TypeInstantiation>` element overrides runtime reflection policy only for instantiations of the specified constructed generic type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1ea3-196">示例</span><span class="sxs-lookup"><span data-stu-id="c1ea3-196">Example</span></span>  
 <span data-ttu-id="c1ea3-197">以下实例使用反射从一个构造的 <xref:System.Collections.Generic.Dictionary%602> 对象取回了泛型类型定义。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-197">The following example uses reflection to retrieve the generic type definition from a constructed <xref:System.Collections.Generic.Dictionary%602> object.</span></span> <span data-ttu-id="c1ea3-198">它还使用反射显示了代表构造泛型类型和构造类型定义的有关 <xref:System.Type> 对象的信息。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-198">It also uses reflection to display information about <xref:System.Type> objects that represent constructed generic types and generic type definitions.</span></span> <span data-ttu-id="c1ea3-199">`b`示例中的变量是一个 <xref:Windows.UI.Xaml.Controls.TextBlock> 控件。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-199">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 <span data-ttu-id="c1ea3-200">使用 .NET Native 工具链进行编译之后，该示例在调用方法的行上引发[MissingMetadataException](missingmetadataexception-class-net-native.md)异常 <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="c1ea3-200">After compilation with the .NET Native tool chain, the example throws a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception on the line that calls the <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c1ea3-201">你可通过将以下 `<TypeInstantiation>` 元素添加到运行时指令文件来消除异常并提供必需的元数据：</span><span class="sxs-lookup"><span data-stu-id="c1ea3-201">You can eliminate the exception and provide the necessary metadata by adding the following `<TypeInstantiation>` element to the runtime directives file:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
     <TypeInstantiation Name="System.Collections.Generic.Dictionary"  
                        Arguments="System.String,GenericType.Example"  
                        Dynamic="Required Public" />  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1ea3-202">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c1ea3-202">See also</span></span>

- [<span data-ttu-id="c1ea3-203">运行时指令 (rd.xml) 配置文件引用</span><span class="sxs-lookup"><span data-stu-id="c1ea3-203">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="c1ea3-204">运行时指令元素</span><span class="sxs-lookup"><span data-stu-id="c1ea3-204">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="c1ea3-205">运行时指令策略设置</span><span class="sxs-lookup"><span data-stu-id="c1ea3-205">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
