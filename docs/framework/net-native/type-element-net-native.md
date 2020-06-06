---
title: <Type>元素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
ms.openlocfilehash: 4e88b49b82513079ddcf6f0bafe02d44235a406a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73091856"
---
# <a name="type-element-net-native"></a><span data-ttu-id="ef880-102">\<Type>元素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="ef880-102">\<Type> Element (.NET Native)</span></span>

<span data-ttu-id="ef880-103">将运行时策略应用到一个特定类型，例如一个类或结构。</span><span class="sxs-lookup"><span data-stu-id="ef880-103">Applies runtime policy to a particular type, such as a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef880-104">语法</span><span class="sxs-lookup"><span data-stu-id="ef880-104">Syntax</span></span>

```xml
<Type Name="type_name"
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

## <a name="attributes-and-elements"></a><span data-ttu-id="ef880-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ef880-105">Attributes and Elements</span></span>

<span data-ttu-id="ef880-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ef880-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef880-107">特性</span><span class="sxs-lookup"><span data-stu-id="ef880-107">Attributes</span></span>

|<span data-ttu-id="ef880-108">属性</span><span class="sxs-lookup"><span data-stu-id="ef880-108">Attribute</span></span>|<span data-ttu-id="ef880-109">属性类型</span><span class="sxs-lookup"><span data-stu-id="ef880-109">Attribute type</span></span>|<span data-ttu-id="ef880-110">说明</span><span class="sxs-lookup"><span data-stu-id="ef880-110">Description</span></span>|
|---------------|--------------------|-----------------|
|`Name`|<span data-ttu-id="ef880-111">常规</span><span class="sxs-lookup"><span data-stu-id="ef880-111">General</span></span>|<span data-ttu-id="ef880-112">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="ef880-112">Required attribute.</span></span> <span data-ttu-id="ef880-113">指定类型名称。</span><span class="sxs-lookup"><span data-stu-id="ef880-113">Specifies the type name.</span></span>|
|`Activate`|<span data-ttu-id="ef880-114">反射</span><span class="sxs-lookup"><span data-stu-id="ef880-114">Reflection</span></span>|<span data-ttu-id="ef880-115">可选特性。</span><span class="sxs-lookup"><span data-stu-id="ef880-115">Optional attribute.</span></span> <span data-ttu-id="ef880-116">控制运行时对构造函数的访问，以启用实例激活。</span><span class="sxs-lookup"><span data-stu-id="ef880-116">Controls runtime access to constructors to enable activation of instances.</span></span>|
|`Browse`|<span data-ttu-id="ef880-117">反射</span><span class="sxs-lookup"><span data-stu-id="ef880-117">Reflection</span></span>|<span data-ttu-id="ef880-118">可选特性。</span><span class="sxs-lookup"><span data-stu-id="ef880-118">Optional attribute.</span></span> <span data-ttu-id="ef880-119">控制对有关程序元素信息的查询，但并不启用任何运行时访问。</span><span class="sxs-lookup"><span data-stu-id="ef880-119">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|
|`Dynamic`|<span data-ttu-id="ef880-120">反射</span><span class="sxs-lookup"><span data-stu-id="ef880-120">Reflection</span></span>|<span data-ttu-id="ef880-121">可选特性。</span><span class="sxs-lookup"><span data-stu-id="ef880-121">Optional attribute.</span></span> <span data-ttu-id="ef880-122">控制运行时对所有类型成员的访问，包括构造函数、方法、字段、属性和事件，以启用动态编程。</span><span class="sxs-lookup"><span data-stu-id="ef880-122">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|
|`Serialize`|<span data-ttu-id="ef880-123">序列化</span><span class="sxs-lookup"><span data-stu-id="ef880-123">Serialization</span></span>|<span data-ttu-id="ef880-124">可选特性。</span><span class="sxs-lookup"><span data-stu-id="ef880-124">Optional attribute.</span></span> <span data-ttu-id="ef880-125">控制运行时对构造函数、字段和属性的访问，使类型实例得到序列化和反序列化处理，这是通过库进行的，例如 Newtonsoft JSON 序列化程序。</span><span class="sxs-lookup"><span data-stu-id="ef880-125">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|
|`DataContractSerializer`|<span data-ttu-id="ef880-126">序列化</span><span class="sxs-lookup"><span data-stu-id="ef880-126">Serialization</span></span>|<span data-ttu-id="ef880-127">可选特性。</span><span class="sxs-lookup"><span data-stu-id="ef880-127">Optional attribute.</span></span> <span data-ttu-id="ef880-128">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 类的序列化策略。</span><span class="sxs-lookup"><span data-stu-id="ef880-128">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|
|`DataContractJsonSerializer`|<span data-ttu-id="ef880-129">序列化</span><span class="sxs-lookup"><span data-stu-id="ef880-129">Serialization</span></span>|<span data-ttu-id="ef880-130">可选特性。</span><span class="sxs-lookup"><span data-stu-id="ef880-130">Optional attribute.</span></span> <span data-ttu-id="ef880-131">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 类的 JSON 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="ef880-131">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|
|`XmlSerializer`|<span data-ttu-id="ef880-132">序列化</span><span class="sxs-lookup"><span data-stu-id="ef880-132">Serialization</span></span>|<span data-ttu-id="ef880-133">可选特性。</span><span class="sxs-lookup"><span data-stu-id="ef880-133">Optional attribute.</span></span> <span data-ttu-id="ef880-134">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 类的 XML 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="ef880-134">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|
|`MarshalObject`|<span data-ttu-id="ef880-135">Interop</span><span class="sxs-lookup"><span data-stu-id="ef880-135">Interop</span></span>|<span data-ttu-id="ef880-136">可选特性。</span><span class="sxs-lookup"><span data-stu-id="ef880-136">Optional attribute.</span></span> <span data-ttu-id="ef880-137">控制封送引用类型到 Windows 运行时和 COM 的策略。</span><span class="sxs-lookup"><span data-stu-id="ef880-137">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|
|`MarshalDelegate`|<span data-ttu-id="ef880-138">Interop</span><span class="sxs-lookup"><span data-stu-id="ef880-138">Interop</span></span>|<span data-ttu-id="ef880-139">可选特性。</span><span class="sxs-lookup"><span data-stu-id="ef880-139">Optional attribute.</span></span> <span data-ttu-id="ef880-140">控制将委托类型作为函数指针封送到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="ef880-140">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|
|`MarshalStructure`|<span data-ttu-id="ef880-141">Interop</span><span class="sxs-lookup"><span data-stu-id="ef880-141">Interop</span></span>|<span data-ttu-id="ef880-142">可选特性。</span><span class="sxs-lookup"><span data-stu-id="ef880-142">Optional attribute.</span></span> <span data-ttu-id="ef880-143">控制封送处理值类型到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="ef880-143">Controls policy for marshaling value types to native code.</span></span>|

## <a name="name-attribute"></a><span data-ttu-id="ef880-144">Name 特性</span><span class="sxs-lookup"><span data-stu-id="ef880-144">Name attribute</span></span>

|<span data-ttu-id="ef880-145">值</span><span class="sxs-lookup"><span data-stu-id="ef880-145">Value</span></span>|<span data-ttu-id="ef880-146">说明</span><span class="sxs-lookup"><span data-stu-id="ef880-146">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="ef880-147">*type_name*</span><span class="sxs-lookup"><span data-stu-id="ef880-147">*type_name*</span></span>|<span data-ttu-id="ef880-148">类型名称。</span><span class="sxs-lookup"><span data-stu-id="ef880-148">The type name.</span></span> <span data-ttu-id="ef880-149">如果此 `<Type>` 元素是 [\<Namespace>](namespace-element-net-native.md) 元素或另一个元素的子元素 `<Type>` ， *type_name*可以包括该类型的名称，而无需命名空间。</span><span class="sxs-lookup"><span data-stu-id="ef880-149">If this `<Type>` element is the child of either a [\<Namespace>](namespace-element-net-native.md) element or another `<Type>` element, *type_name* can include the name of the type without its namespace.</span></span> <span data-ttu-id="ef880-150">否则，type_name\*\* 必须包含完全限定的类型名称。</span><span class="sxs-lookup"><span data-stu-id="ef880-150">Otherwise, *type_name* must include the fully qualified type name.</span></span>|

## <a name="all-other-attributes"></a><span data-ttu-id="ef880-151">所有其他特性</span><span class="sxs-lookup"><span data-stu-id="ef880-151">All other attributes</span></span>

|<span data-ttu-id="ef880-152">值</span><span class="sxs-lookup"><span data-stu-id="ef880-152">Value</span></span>|<span data-ttu-id="ef880-153">说明</span><span class="sxs-lookup"><span data-stu-id="ef880-153">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="ef880-154">*策略_设置*</span><span class="sxs-lookup"><span data-stu-id="ef880-154">*policy_setting*</span></span>|<span data-ttu-id="ef880-155">该设置将应用到这种策略类型。</span><span class="sxs-lookup"><span data-stu-id="ef880-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="ef880-156">可能值为 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 以及 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="ef880-156">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="ef880-157">有关详细信息，请参阅[运行时指令策略设置](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="ef880-157">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ef880-158">子元素</span><span class="sxs-lookup"><span data-stu-id="ef880-158">Child Elements</span></span>

|<span data-ttu-id="ef880-159">元素</span><span class="sxs-lookup"><span data-stu-id="ef880-159">Element</span></span>|<span data-ttu-id="ef880-160">说明</span><span class="sxs-lookup"><span data-stu-id="ef880-160">Description</span></span>|
|-------------|-----------------|
|[\<AttributeImplies>](attributeimplies-element-net-native.md)|<span data-ttu-id="ef880-161">如果包含类型是一个特性，为该特性所应用到的代码元素定义一个运行时策略。</span><span class="sxs-lookup"><span data-stu-id="ef880-161">If the containing type is an attribute, defines runtime policy for code elements to which the attribute is applied.</span></span>|
|[\<Event>](event-element-net-native.md)|<span data-ttu-id="ef880-162">将反射策略应用到属于这种类型的一个事件。</span><span class="sxs-lookup"><span data-stu-id="ef880-162">Applies reflection policy to an event belonging to this type.</span></span>|
|[\<Field>](field-element-net-native.md)|<span data-ttu-id="ef880-163">将反射策略应用到属于这种类型的一个字段。</span><span class="sxs-lookup"><span data-stu-id="ef880-163">Applies reflection policy to a field belonging to this type.</span></span>|
|[\<GenericParameter>](genericparameter-element-net-native.md)|<span data-ttu-id="ef880-164">将策略应用到一个泛型类型的参数类型。</span><span class="sxs-lookup"><span data-stu-id="ef880-164">Applies policy to the parameter type of a generic type.</span></span>|
|[\<ImpliesType>](impliestype-element-net-native.md)|<span data-ttu-id="ef880-165">如果该策略已应用到以包含 `<Type>` 元素为代表的类型，将该策略应用到一个类型。</span><span class="sxs-lookup"><span data-stu-id="ef880-165">Applies policy to a type, if that policy has been applied to the type represented by the containing `<Type>` element.</span></span>|
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="ef880-166">将反射策略应用到属于这种类型的一个方法。</span><span class="sxs-lookup"><span data-stu-id="ef880-166">Applies reflection policy to a method belonging to this type.</span></span>|
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|<span data-ttu-id="ef880-167">将反射策略应用到属于这种类型的一个构造泛型方法。</span><span class="sxs-lookup"><span data-stu-id="ef880-167">Applies reflection policy to a constructed generic method belonging to this type.</span></span>|
|[\<Property>](property-element-net-native.md)|<span data-ttu-id="ef880-168">将反射策略应用到属于这种类型的一个属性。</span><span class="sxs-lookup"><span data-stu-id="ef880-168">Applies reflection policy to a property belonging to this type.</span></span>|
|[\<Subtypes>](subtypes-element-net-native.md)|<span data-ttu-id="ef880-169">将运行时策略应用到从包含类型继承的所有类。</span><span class="sxs-lookup"><span data-stu-id="ef880-169">Applies runtime policy to all classes inherited from the containing type.</span></span>|
|`<Type>`|<span data-ttu-id="ef880-170">将反射策略应用到一个嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="ef880-170">Applies reflection policy to a nested type.</span></span>|
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="ef880-171">将反射策略应用到一个构造泛型类型。</span><span class="sxs-lookup"><span data-stu-id="ef880-171">Applies reflection policy to a constructed generic type.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ef880-172">父元素</span><span class="sxs-lookup"><span data-stu-id="ef880-172">Parent Elements</span></span>

|<span data-ttu-id="ef880-173">元素</span><span class="sxs-lookup"><span data-stu-id="ef880-173">Element</span></span>|<span data-ttu-id="ef880-174">说明</span><span class="sxs-lookup"><span data-stu-id="ef880-174">Description</span></span>|
|-------------|-----------------|
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="ef880-175">作为应用程序范围内的类型和元数据可以反应在运行时间的类型成员的容器而服务。</span><span class="sxs-lookup"><span data-stu-id="ef880-175">Serves as a container for application-wide types and type members whose metadata is available for reflection at run time.</span></span>|
|[\<Assembly>](assembly-element-net-native.md)|<span data-ttu-id="ef880-176">将反射策略应用到指定程序集中的所有类型。</span><span class="sxs-lookup"><span data-stu-id="ef880-176">Applies reflection policy to all the types in a specified assembly.</span></span>|
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="ef880-177">定义包含元数据在运行时间可以用于反射的类型和类型成员的程序集。</span><span class="sxs-lookup"><span data-stu-id="ef880-177">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>|
|[\<Namespace>](namespace-element-net-native.md)|<span data-ttu-id="ef880-178">将反射策略应用到命名空间中的所有类型。</span><span class="sxs-lookup"><span data-stu-id="ef880-178">Applies reflection policy to all the types in a namespace.</span></span>|
|`<Type>`|<span data-ttu-id="ef880-179">将反射策略应用到一种类型及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="ef880-179">Applies reflection policy to a type and all its members.</span></span>|
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="ef880-180">将反射策略应用到一种构造泛型类型及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="ef880-180">Applies reflection policy to a constructed generic type and all its members.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ef880-181">注解</span><span class="sxs-lookup"><span data-stu-id="ef880-181">Remarks</span></span>

<span data-ttu-id="ef880-182">反射、序列化和互操作特性都是可选项。</span><span class="sxs-lookup"><span data-stu-id="ef880-182">The reflection, serialization, and interop attributes are all optional.</span></span> <span data-ttu-id="ef880-183">如果这些都不存在，`<Type>` 元素会充当容器，其子类型为独立成员定义策略。</span><span class="sxs-lookup"><span data-stu-id="ef880-183">If none are present, the `<Type>` element serves as a container whose child types define policy for individual members.</span></span>

<span data-ttu-id="ef880-184">如果 `<Type>` 元素是、、或元素的子元素 [\<Assembly>](assembly-element-net-native.md) [\<Namespace>](namespace-element-net-native.md) `<Type>` [\<TypeInstantiation>](typeinstantiation-element-net-native.md) ，则它会重写由父元素定义的策略设置。</span><span class="sxs-lookup"><span data-stu-id="ef880-184">If a `<Type>` element is the child of an [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), `<Type>`, or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element, it overrides the policy settings defined by the parent element.</span></span>

<span data-ttu-id="ef880-185">一个泛型类型的 `<Type>` 元素会将其策略应用到所有不具有自身策略的实例化。</span><span class="sxs-lookup"><span data-stu-id="ef880-185">A `<Type>` element of a generic type applies its policy to all instantiations that do not have their own policy.</span></span> <span data-ttu-id="ef880-186">构造的泛型类型的策略是由元素定义的 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 。</span><span class="sxs-lookup"><span data-stu-id="ef880-186">The policy of constructed generic types is defined by the [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>

<span data-ttu-id="ef880-187">如果该类型是一个泛型类型，其名称包含一个重读音符 (\`)，后面还跟着其泛型参数的编号。</span><span class="sxs-lookup"><span data-stu-id="ef880-187">If the type is a generic type, its name is decorated by a grave accent symbol (\`) followed by its number of generic parameters.</span></span> <span data-ttu-id="ef880-188">例如，`Name` 的 `<Type>` 元素 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 特性为 ``Name="System.Collections.Generic.List`1"``。</span><span class="sxs-lookup"><span data-stu-id="ef880-188">For example, the `Name` attribute of a `<Type>` element for the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> class appears as ``Name="System.Collections.Generic.List`1"``.</span></span>

## <a name="example"></a><span data-ttu-id="ef880-189">示例</span><span class="sxs-lookup"><span data-stu-id="ef880-189">Example</span></span>

<span data-ttu-id="ef880-190">以下实例使用反射来展示 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 类的字段、属性和方法。</span><span class="sxs-lookup"><span data-stu-id="ef880-190">The following example uses reflection to display information about the fields, properties, and methods of the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ef880-191">`b`示例中的变量是一个 <xref:Windows.UI.Xaml.Controls.TextBlock> 控件。</span><span class="sxs-lookup"><span data-stu-id="ef880-191">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span> <span data-ttu-id="ef880-192">因为实例仅仅检索了类型信息，元数据的可用性是由 `Browse` 策略设置控制的。</span><span class="sxs-lookup"><span data-stu-id="ef880-192">Because the example simply retrieves type information, the availability of metadata is controlled by the `Browse` policy setting.</span></span>

 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]

 <span data-ttu-id="ef880-193">由于类的元数据 <xref:System.Collections.Generic.List%601> 不会由 .NET Native 工具链自动包含，因此该示例在运行时无法显示请求的成员信息。</span><span class="sxs-lookup"><span data-stu-id="ef880-193">Because metadata for the <xref:System.Collections.Generic.List%601> class isn't automatically included by the .NET Native tool chain, the example fails to display the requested member information at run time.</span></span> <span data-ttu-id="ef880-194">为提供所需的元数据，将以下 `<Type>` 元素添加到运行时指令文件。</span><span class="sxs-lookup"><span data-stu-id="ef880-194">To provide the necessary metadata, add the following `<Type>` element to the runtime directives file.</span></span> <span data-ttu-id="ef880-195">注意，因为我们已经提供了父 [<Namespace\>](namespace-element-net-native.md) 元素，因此不必在 `<Type>` 元素中提供完全限定的类型名称。</span><span class="sxs-lookup"><span data-stu-id="ef880-195">Note that, because we've provided a parent [<Namespace\>](namespace-element-net-native.md) element, we don't have to provide a fully qualified type name in the `<Type>` element.</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="*Application*" Dynamic="Required All" />
      <Namespace Name ="System.Collections.Generic" >
        <Type Name="List`1" Browse="Required All" />
     </Namespace>
   </Application>
</Directives>
```

## <a name="example"></a><span data-ttu-id="ef880-196">示例</span><span class="sxs-lookup"><span data-stu-id="ef880-196">Example</span></span>
 <span data-ttu-id="ef880-197">以下实例使用了反射来检索一个代表 <xref:System.Reflection.PropertyInfo> 属性的 <xref:System.String.Chars%2A?displayProperty=nameWithType> 对象。</span><span class="sxs-lookup"><span data-stu-id="ef880-197">The following example uses reflection to retrieve a <xref:System.Reflection.PropertyInfo> object that represents the <xref:System.String.Chars%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ef880-198">它使用 <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> 方法来检索一个字符串中的七个字符的值，并在该字符串中显示所有字符。</span><span class="sxs-lookup"><span data-stu-id="ef880-198">It then uses the <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> method to retrieve the value of the seventh character in a string, and to display all the characters in the string.</span></span> <span data-ttu-id="ef880-199">`b`示例中的变量是一个 <xref:Windows.UI.Xaml.Controls.TextBlock> 控件。</span><span class="sxs-lookup"><span data-stu-id="ef880-199">The variable `b` in the example is a <xref:Windows.UI.Xaml.Controls.TextBlock> control.</span></span>

 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]

 <span data-ttu-id="ef880-200">由于对象的元数据 <xref:System.String> 不可用，因此在 <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> <xref:System.NullReferenceException> 使用 .NET Native 工具链编译时，对方法的调用会在运行时引发异常。</span><span class="sxs-lookup"><span data-stu-id="ef880-200">Because metadata for the <xref:System.String> object isn't available, the call to the <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> method throws a <xref:System.NullReferenceException> exception at run time when compiled with the .NET Native tool chain.</span></span> <span data-ttu-id="ef880-201">要消除异常并提供必需的元数据，请将以下 `<Type>` 元素添加到运行时指令文件：</span><span class="sxs-lookup"><span data-stu-id="ef880-201">To eliminate the exception and provide the necessary metadata, add the following `<Type>` element to the runtime directives file:</span></span>

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
    <Assembly Name="*Application*" Dynamic="Required All" />
    <Type Name="System.String" Dynamic="Required Public"/> -->
  </Application>
</Directives>
```

## <a name="see-also"></a><span data-ttu-id="ef880-202">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ef880-202">See also</span></span>

- [<span data-ttu-id="ef880-203">运行时指令 (rd.xml) 配置文件引用</span><span class="sxs-lookup"><span data-stu-id="ef880-203">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="ef880-204">运行时指令元素</span><span class="sxs-lookup"><span data-stu-id="ef880-204">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="ef880-205">运行时指令策略设置</span><span class="sxs-lookup"><span data-stu-id="ef880-205">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
