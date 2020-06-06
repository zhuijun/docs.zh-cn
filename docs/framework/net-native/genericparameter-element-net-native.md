---
title: <GenericParameter>元素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
ms.openlocfilehash: d0b18211206a8f9d4365ab3affe6d1c376003348
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128436"
---
# <a name="genericparameter-element-net-native"></a><span data-ttu-id="cef41-102">\<GenericParameter>元素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="cef41-102">\<GenericParameter> Element (.NET Native)</span></span>
<span data-ttu-id="cef41-103">将策略应用到一个泛型类型或方法的参数类型。</span><span class="sxs-lookup"><span data-stu-id="cef41-103">Applies policy to the parameter type of a generic type or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cef41-104">语法</span><span class="sxs-lookup"><span data-stu-id="cef41-104">Syntax</span></span>  
  
```xml  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cef41-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cef41-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cef41-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cef41-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cef41-107">特性</span><span class="sxs-lookup"><span data-stu-id="cef41-107">Attributes</span></span>  
  
|<span data-ttu-id="cef41-108">属性</span><span class="sxs-lookup"><span data-stu-id="cef41-108">Attribute</span></span>|<span data-ttu-id="cef41-109">属性类型</span><span class="sxs-lookup"><span data-stu-id="cef41-109">Attribute type</span></span>|<span data-ttu-id="cef41-110">说明</span><span class="sxs-lookup"><span data-stu-id="cef41-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="cef41-111">常规</span><span class="sxs-lookup"><span data-stu-id="cef41-111">General</span></span>|<span data-ttu-id="cef41-112">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="cef41-112">Required attribute.</span></span> <span data-ttu-id="cef41-113">泛型参数的名称。</span><span class="sxs-lookup"><span data-stu-id="cef41-113">The name of the generic parameter.</span></span> <span data-ttu-id="cef41-114">例如，对于泛型委托 <xref:System.Func%603>，`Name` 特性的值为“TResult”，从而将运行时策略应用到该委托的返回值。</span><span class="sxs-lookup"><span data-stu-id="cef41-114">For example, for the generic delegate <xref:System.Func%603>, the value of the `Name` attribute is "TResult" to apply runtime policy to the delegate's return value.</span></span>|  
|`Activate`|<span data-ttu-id="cef41-115">反射</span><span class="sxs-lookup"><span data-stu-id="cef41-115">Reflection</span></span>|<span data-ttu-id="cef41-116">可选特性。</span><span class="sxs-lookup"><span data-stu-id="cef41-116">Optional attribute.</span></span> <span data-ttu-id="cef41-117">控制运行时对构造函数的访问，以启用实例激活。</span><span class="sxs-lookup"><span data-stu-id="cef41-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="cef41-118">反射</span><span class="sxs-lookup"><span data-stu-id="cef41-118">Reflection</span></span>|<span data-ttu-id="cef41-119">可选特性。</span><span class="sxs-lookup"><span data-stu-id="cef41-119">Optional attribute.</span></span> <span data-ttu-id="cef41-120">控制对有关程序元素信息的查询，但并不启用任何运行时访问。</span><span class="sxs-lookup"><span data-stu-id="cef41-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="cef41-121">反射</span><span class="sxs-lookup"><span data-stu-id="cef41-121">Reflection</span></span>|<span data-ttu-id="cef41-122">可选特性。</span><span class="sxs-lookup"><span data-stu-id="cef41-122">Optional attribute.</span></span> <span data-ttu-id="cef41-123">控制运行时对所有类型成员的访问，包括构造函数、方法、字段、属性和事件，以启用动态编程。</span><span class="sxs-lookup"><span data-stu-id="cef41-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="cef41-124">序列化</span><span class="sxs-lookup"><span data-stu-id="cef41-124">Serialization</span></span>|<span data-ttu-id="cef41-125">可选特性。</span><span class="sxs-lookup"><span data-stu-id="cef41-125">Optional attribute.</span></span> <span data-ttu-id="cef41-126">控制运行时对构造函数、字段和属性的访问，使类型实例得到序列化和反序列化处理，这是通过库进行的，例如 Newtonsoft JSON 序列化程序。</span><span class="sxs-lookup"><span data-stu-id="cef41-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="cef41-127">序列化</span><span class="sxs-lookup"><span data-stu-id="cef41-127">Serialization</span></span>|<span data-ttu-id="cef41-128">可选特性。</span><span class="sxs-lookup"><span data-stu-id="cef41-128">Optional attribute.</span></span> <span data-ttu-id="cef41-129">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 类的序列化策略。</span><span class="sxs-lookup"><span data-stu-id="cef41-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="cef41-130">序列化</span><span class="sxs-lookup"><span data-stu-id="cef41-130">Serialization</span></span>|<span data-ttu-id="cef41-131">可选特性。</span><span class="sxs-lookup"><span data-stu-id="cef41-131">Optional attribute.</span></span> <span data-ttu-id="cef41-132">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 类的 JSON 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="cef41-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="cef41-133">序列化</span><span class="sxs-lookup"><span data-stu-id="cef41-133">Serialization</span></span>|<span data-ttu-id="cef41-134">可选特性。</span><span class="sxs-lookup"><span data-stu-id="cef41-134">Optional attribute.</span></span> <span data-ttu-id="cef41-135">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 类的 XML 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="cef41-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="cef41-136">Interop</span><span class="sxs-lookup"><span data-stu-id="cef41-136">Interop</span></span>|<span data-ttu-id="cef41-137">可选特性。</span><span class="sxs-lookup"><span data-stu-id="cef41-137">Optional attribute.</span></span> <span data-ttu-id="cef41-138">控制封送引用类型到 Windows 运行时和 COM 的策略。</span><span class="sxs-lookup"><span data-stu-id="cef41-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="cef41-139">Interop</span><span class="sxs-lookup"><span data-stu-id="cef41-139">Interop</span></span>|<span data-ttu-id="cef41-140">可选特性。</span><span class="sxs-lookup"><span data-stu-id="cef41-140">Optional attribute.</span></span> <span data-ttu-id="cef41-141">控制将委托类型作为函数指针封送到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="cef41-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="cef41-142">Interop</span><span class="sxs-lookup"><span data-stu-id="cef41-142">Interop</span></span>|<span data-ttu-id="cef41-143">可选特性。</span><span class="sxs-lookup"><span data-stu-id="cef41-143">Optional attribute.</span></span> <span data-ttu-id="cef41-144">控制封送处理值类型到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="cef41-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="cef41-145">Name 特性</span><span class="sxs-lookup"><span data-stu-id="cef41-145">Name attribute</span></span>  
  
|<span data-ttu-id="cef41-146">值</span><span class="sxs-lookup"><span data-stu-id="cef41-146">Value</span></span>|<span data-ttu-id="cef41-147">说明</span><span class="sxs-lookup"><span data-stu-id="cef41-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cef41-148">generic_parameter_name\*\*</span><span class="sxs-lookup"><span data-stu-id="cef41-148">*generic_parameter_name*</span></span>|<span data-ttu-id="cef41-149">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="cef41-149">Required attribute.</span></span> <span data-ttu-id="cef41-150">泛型类型参数的名称。</span><span class="sxs-lookup"><span data-stu-id="cef41-150">The name of the generic type parameter.</span></span> <span data-ttu-id="cef41-151">例如，对于泛型委托 <xref:System.Func%603>，“TResult”的一个 generic_parameter_name 值将运行时策略应用到该委托的返回值\*\*。</span><span class="sxs-lookup"><span data-stu-id="cef41-151">For example, for the generic delegate <xref:System.Func%603>, a *generic_parameter_name* value of "TResult" applies runtime policy to the delegate's return value.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="cef41-152">所有其他特性</span><span class="sxs-lookup"><span data-stu-id="cef41-152">All other attributes</span></span>  
  
|<span data-ttu-id="cef41-153">值</span><span class="sxs-lookup"><span data-stu-id="cef41-153">Value</span></span>|<span data-ttu-id="cef41-154">说明</span><span class="sxs-lookup"><span data-stu-id="cef41-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cef41-155">*策略_设置*</span><span class="sxs-lookup"><span data-stu-id="cef41-155">*policy_setting*</span></span>|<span data-ttu-id="cef41-156">该设置将应用到这种策略类型。</span><span class="sxs-lookup"><span data-stu-id="cef41-156">The setting to apply to this policy type.</span></span> <span data-ttu-id="cef41-157">可能值为 `All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 以及 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="cef41-157">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="cef41-158">有关详细信息，请参阅[运行时指令策略设置](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="cef41-158">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cef41-159">子元素</span><span class="sxs-lookup"><span data-stu-id="cef41-159">Child Elements</span></span>  
 <span data-ttu-id="cef41-160">无。</span><span class="sxs-lookup"><span data-stu-id="cef41-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cef41-161">父元素</span><span class="sxs-lookup"><span data-stu-id="cef41-161">Parent Elements</span></span>  
  
|<span data-ttu-id="cef41-162">元素</span><span class="sxs-lookup"><span data-stu-id="cef41-162">Element</span></span>|<span data-ttu-id="cef41-163">说明</span><span class="sxs-lookup"><span data-stu-id="cef41-163">Description</span></span>|  
|-------------|-----------------|  
|[\<Method>](method-element-net-native.md)|<span data-ttu-id="cef41-164">将运行时反射策略应用到一个构造函数或方法。</span><span class="sxs-lookup"><span data-stu-id="cef41-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="cef41-165">将运行时反射策略应用到一个特定类型，例如一个类或结构。</span><span class="sxs-lookup"><span data-stu-id="cef41-165">Applies runtime reflection policy to a particular type, such as a class or structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cef41-166">注解</span><span class="sxs-lookup"><span data-stu-id="cef41-166">Remarks</span></span>  
 <span data-ttu-id="cef41-167">`<GenericParameter>`元素是或元素的子元素 [\<Method>](method-element-net-native.md) [\<Type>](type-element-net-native.md) ，用于将策略应用于特定的泛型类型参数，该参数由泛型类型或方法签名中的名称指定。</span><span class="sxs-lookup"><span data-stu-id="cef41-167">The `<GenericParameter>` element is a child of either the [\<Method>](method-element-net-native.md) or [\<Type>](type-element-net-native.md) element and is used to apply policy to a particular generic type parameter, which is specified by its name in the generic type or method signature.</span></span>  
  
 <span data-ttu-id="cef41-168">`<GenericParameter>` 元素在同序列化程序一起使用时非常有用。</span><span class="sxs-lookup"><span data-stu-id="cef41-168">The `<GenericParameter>` element is most useful when used with serializers.</span></span> <span data-ttu-id="cef41-169">下面的示例使用 `<GenericParameter>` 元素， `T` 在对 newtonsoft.json JSON 序列化程序的[JsonConvert \<T> （String）](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm)方法重载的调用中，将策略应用于该类型。</span><span class="sxs-lookup"><span data-stu-id="cef41-169">The following example uses the `<GenericParameter>` element to apply policy to the type `T` in calls to the NewtonSoft JSON serializer's [JsonConvert.DeserializeObject\<T>(String)](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonConvert_DeserializeObject__1.htm) method overloads.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cef41-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cef41-170">See also</span></span>

- [<span data-ttu-id="cef41-171">\<Method>Element</span><span class="sxs-lookup"><span data-stu-id="cef41-171">\<Method> Element</span></span>](method-element-net-native.md)
- [<span data-ttu-id="cef41-172">\<Type>Element</span><span class="sxs-lookup"><span data-stu-id="cef41-172">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="cef41-173">运行时指令 (rd.xml) 配置文件引用</span><span class="sxs-lookup"><span data-stu-id="cef41-173">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="cef41-174">运行时指令策略设置</span><span class="sxs-lookup"><span data-stu-id="cef41-174">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="cef41-175">运行时指令元素</span><span class="sxs-lookup"><span data-stu-id="cef41-175">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
