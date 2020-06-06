---
title: <Subtypes>元素 (.NET Native)
ms.date: 03/30/2017
ms.assetid: fb854070-248b-46cf-9dab-c322e2b4d624
ms.openlocfilehash: bb719449f3769c5dbbde6d05efdb865c18bb4ab2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79180934"
---
# <a name="subtypes-element-net-native"></a><span data-ttu-id="b0c85-102">\<Subtypes>元素 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="b0c85-102">\<Subtypes> Element (.NET Native)</span></span>
<span data-ttu-id="b0c85-103">将运行时策略应用到从包含类型继承的所有类。</span><span class="sxs-lookup"><span data-stu-id="b0c85-103">Applies runtime policy to all classes inherited from the containing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0c85-104">语法</span><span class="sxs-lookup"><span data-stu-id="b0c85-104">Syntax</span></span>  
  
```xml  
<Subtypes Activate="policy_type"  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0c85-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b0c85-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b0c85-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b0c85-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0c85-107">特性</span><span class="sxs-lookup"><span data-stu-id="b0c85-107">Attributes</span></span>  
  
|<span data-ttu-id="b0c85-108">属性</span><span class="sxs-lookup"><span data-stu-id="b0c85-108">Attribute</span></span>|<span data-ttu-id="b0c85-109">属性类型</span><span class="sxs-lookup"><span data-stu-id="b0c85-109">Attribute type</span></span>|<span data-ttu-id="b0c85-110">说明</span><span class="sxs-lookup"><span data-stu-id="b0c85-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="b0c85-111">反射</span><span class="sxs-lookup"><span data-stu-id="b0c85-111">Reflection</span></span>|<span data-ttu-id="b0c85-112">可选特性。</span><span class="sxs-lookup"><span data-stu-id="b0c85-112">Optional attribute.</span></span> <span data-ttu-id="b0c85-113">控制运行时对构造函数的访问，以启用实例激活。</span><span class="sxs-lookup"><span data-stu-id="b0c85-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="b0c85-114">反射</span><span class="sxs-lookup"><span data-stu-id="b0c85-114">Reflection</span></span>|<span data-ttu-id="b0c85-115">可选特性。</span><span class="sxs-lookup"><span data-stu-id="b0c85-115">Optional attribute.</span></span> <span data-ttu-id="b0c85-116">控制对有关程序元素信息的查询，但并不启用任何运行时访问。</span><span class="sxs-lookup"><span data-stu-id="b0c85-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="b0c85-117">反射</span><span class="sxs-lookup"><span data-stu-id="b0c85-117">Reflection</span></span>|<span data-ttu-id="b0c85-118">可选特性。</span><span class="sxs-lookup"><span data-stu-id="b0c85-118">Optional attribute.</span></span> <span data-ttu-id="b0c85-119">控制运行时对所有类型成员的访问，包括构造函数、方法、字段、属性和事件，以启用动态编程。</span><span class="sxs-lookup"><span data-stu-id="b0c85-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="b0c85-120">序列化</span><span class="sxs-lookup"><span data-stu-id="b0c85-120">Serialization</span></span>|<span data-ttu-id="b0c85-121">可选特性。</span><span class="sxs-lookup"><span data-stu-id="b0c85-121">Optional attribute.</span></span> <span data-ttu-id="b0c85-122">控制运行时对构造函数、字段和属性的访问，使类型实例得到序列化和反序列化处理，这是通过库进行的，例如 Newtonsoft JSON 序列化程序。</span><span class="sxs-lookup"><span data-stu-id="b0c85-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="b0c85-123">序列化</span><span class="sxs-lookup"><span data-stu-id="b0c85-123">Serialization</span></span>|<span data-ttu-id="b0c85-124">可选特性。</span><span class="sxs-lookup"><span data-stu-id="b0c85-124">Optional attribute.</span></span> <span data-ttu-id="b0c85-125">控制使用 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> 类的序列化策略。</span><span class="sxs-lookup"><span data-stu-id="b0c85-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="b0c85-126">序列化</span><span class="sxs-lookup"><span data-stu-id="b0c85-126">Serialization</span></span>|<span data-ttu-id="b0c85-127">可选特性。</span><span class="sxs-lookup"><span data-stu-id="b0c85-127">Optional attribute.</span></span> <span data-ttu-id="b0c85-128">控制使用 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> 类的 JSON 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="b0c85-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="b0c85-129">序列化</span><span class="sxs-lookup"><span data-stu-id="b0c85-129">Serialization</span></span>|<span data-ttu-id="b0c85-130">可选特性。</span><span class="sxs-lookup"><span data-stu-id="b0c85-130">Optional attribute.</span></span> <span data-ttu-id="b0c85-131">控制使用 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 类的 XML 序列化策略。</span><span class="sxs-lookup"><span data-stu-id="b0c85-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="b0c85-132">Interop</span><span class="sxs-lookup"><span data-stu-id="b0c85-132">Interop</span></span>|<span data-ttu-id="b0c85-133">可选特性。</span><span class="sxs-lookup"><span data-stu-id="b0c85-133">Optional attribute.</span></span> <span data-ttu-id="b0c85-134">控制封送引用类型到 Windows 运行时和 COM 的策略。</span><span class="sxs-lookup"><span data-stu-id="b0c85-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="b0c85-135">Interop</span><span class="sxs-lookup"><span data-stu-id="b0c85-135">Interop</span></span>|<span data-ttu-id="b0c85-136">可选特性。</span><span class="sxs-lookup"><span data-stu-id="b0c85-136">Optional attribute.</span></span> <span data-ttu-id="b0c85-137">控制将委托类型作为函数指针封送到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="b0c85-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="b0c85-138">Interop</span><span class="sxs-lookup"><span data-stu-id="b0c85-138">Interop</span></span>|<span data-ttu-id="b0c85-139">可选特性。</span><span class="sxs-lookup"><span data-stu-id="b0c85-139">Optional attribute.</span></span> <span data-ttu-id="b0c85-140">控制封送处理值类型到本机代码的策略。</span><span class="sxs-lookup"><span data-stu-id="b0c85-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="b0c85-141">所有特性</span><span class="sxs-lookup"><span data-stu-id="b0c85-141">All attributes</span></span>  
  
|<span data-ttu-id="b0c85-142">值</span><span class="sxs-lookup"><span data-stu-id="b0c85-142">Value</span></span>|<span data-ttu-id="b0c85-143">说明</span><span class="sxs-lookup"><span data-stu-id="b0c85-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b0c85-144">*策略_设置*</span><span class="sxs-lookup"><span data-stu-id="b0c85-144">*policy_setting*</span></span>|<span data-ttu-id="b0c85-145">该设置将应用到这种策略类型。</span><span class="sxs-lookup"><span data-stu-id="b0c85-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="b0c85-146">可能值为 `All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal` 以及 `Required All`。</span><span class="sxs-lookup"><span data-stu-id="b0c85-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="b0c85-147">有关详细信息，请参阅[运行时指令策略设置](runtime-directive-policy-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="b0c85-147">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0c85-148">子元素</span><span class="sxs-lookup"><span data-stu-id="b0c85-148">Child Elements</span></span>  
 <span data-ttu-id="b0c85-149">无。</span><span class="sxs-lookup"><span data-stu-id="b0c85-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0c85-150">父元素</span><span class="sxs-lookup"><span data-stu-id="b0c85-150">Parent Elements</span></span>  
  
|<span data-ttu-id="b0c85-151">元素</span><span class="sxs-lookup"><span data-stu-id="b0c85-151">Element</span></span>|<span data-ttu-id="b0c85-152">说明</span><span class="sxs-lookup"><span data-stu-id="b0c85-152">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="b0c85-153">将反射策略应用到一种类型及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="b0c85-153">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0c85-154">注解</span><span class="sxs-lookup"><span data-stu-id="b0c85-154">Remarks</span></span>  
 <span data-ttu-id="b0c85-155">`<Subtypes>` 元素将策略应用到其包含类型的所有子类型。</span><span class="sxs-lookup"><span data-stu-id="b0c85-155">The `<Subtypes>` element applies policy to all the subtypes of its containing type.</span></span> <span data-ttu-id="b0c85-156">当你想将不同的策略应用到派生类型及其基类时可使用它。</span><span class="sxs-lookup"><span data-stu-id="b0c85-156">You use it when you want to apply different policies to derived types and their base classes.</span></span>  
  
 <span data-ttu-id="b0c85-157">反射、序列化和互操作特性都是可选项，但必须存在至少一项。</span><span class="sxs-lookup"><span data-stu-id="b0c85-157">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0c85-158">示例</span><span class="sxs-lookup"><span data-stu-id="b0c85-158">Example</span></span>  
 <span data-ttu-id="b0c85-159">以下实例定义了一个名为 `BaseClass` 的类和一个名为 `Derived1` 的子类。</span><span class="sxs-lookup"><span data-stu-id="b0c85-159">The following example defines a class named `BaseClass` and a subclass named `Derived1`.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#4)]  
  
 <span data-ttu-id="b0c85-160">如以下代码所示，运行时指令文件为 `Dynamic` 到 `Activate` 显式设置了 `BaseClass` 和 `Excluded` 策略。</span><span class="sxs-lookup"><span data-stu-id="b0c85-160">As shown in the following code, the runtime directives file explicitly sets the `Dynamic` and `Activate` policies for `BaseClass` to `Excluded`.</span></span> <span data-ttu-id="b0c85-161">因此，类型 `BaseClass` 的对象无法得到动态实例化或通过调用 `BaseClass` 类构造函数得到实例化。</span><span class="sxs-lookup"><span data-stu-id="b0c85-161">Because of this, objects of type `BaseClass` cannot be instantiated dynamically or by calls to the `BaseClass` class constructor.</span></span> <span data-ttu-id="b0c85-162">然而，`<Subtypes>` 元素允许从 `BaseClass` 派生的类得到动态实例化并通过对其类构造函数的调用得到实例化。</span><span class="sxs-lookup"><span data-stu-id="b0c85-162">However, the `<Subtypes>` element allows classes derived from `BaseClass` to be instantiated dynamically and through calls to their class constructors.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
   <Assembly Name="*Application*" Dynamic="Required All" />  
     <Type Name="Examples.Libraries.BaseClass" Activate ="Excluded" Dynamic="Excluded" >  
        <Subtypes Activate="Public" Dynamic ="Public"/>  
     </Type>  
  </Application>  
</Directives>  
```  
  
 <span data-ttu-id="b0c85-163">由于 `<Subtypes>` 指令的存在，以下代码通过成功调用 `Derived1` 方法执行动态实例化了一个 <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> 实例。</span><span class="sxs-lookup"><span data-stu-id="b0c85-163">Because of the `<Subtypes>` directive, the following code that instantiates a `Derived1` instance dynamically by calling the <xref:System.Activator.CreateInstance%28System.Type%29?displayProperty=nameWithType> method executes successfully.</span></span>  <span data-ttu-id="b0c85-164">这里的块变量是一个空白 Windows 应用商店应用的一个 <xref:System.Windows.Controls.TextBlock> 对象。</span><span class="sxs-lookup"><span data-stu-id="b0c85-164">The block variable here is a <xref:System.Windows.Controls.TextBlock> object in a blank Windows Store app.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/subtypes.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b0c85-165">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b0c85-165">See also</span></span>

- [<span data-ttu-id="b0c85-166">\<Type>Element</span><span class="sxs-lookup"><span data-stu-id="b0c85-166">\<Type> Element</span></span>](type-element-net-native.md)
- [<span data-ttu-id="b0c85-167">运行时指令 (rd.xml) 配置文件引用</span><span class="sxs-lookup"><span data-stu-id="b0c85-167">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="b0c85-168">运行时指令元素</span><span class="sxs-lookup"><span data-stu-id="b0c85-168">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="b0c85-169">运行时指令策略设置</span><span class="sxs-lookup"><span data-stu-id="b0c85-169">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
