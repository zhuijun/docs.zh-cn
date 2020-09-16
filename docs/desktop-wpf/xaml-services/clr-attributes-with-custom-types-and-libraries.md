---
title: 自定义类型和库的 XAML 相关 CLR 特性
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: a4b8a58ea2c7d9de2b59ed78dc37e4ce1c434b79
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535392"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a><span data-ttu-id="205b9-102">自定义类型和库的 XAML 相关 CLR 特性</span><span class="sxs-lookup"><span data-stu-id="205b9-102">XAML-related CLR attributes for custom types and libraries</span></span>

<span data-ttu-id="205b9-103">本主题介绍了公共语言运行时 (CLR) 由 .NET XAML 服务定义的属性。</span><span class="sxs-lookup"><span data-stu-id="205b9-103">This topic describes the common language runtime (CLR) attributes that are defined by .NET XAML Services.</span></span> <span data-ttu-id="205b9-104">它还介绍了在 .NET 中定义的、具有应用程序程序集或类型的 XAML 相关方案的其他 CLR 特性。</span><span class="sxs-lookup"><span data-stu-id="205b9-104">It also describes other CLR attributes that are defined in .NET that have a XAML-related scenario for application to assemblies or types.</span></span> <span data-ttu-id="205b9-105">将程序集、类型或成员与这些 CLR 特性相关联可提供与类型相关的 XAML 类型系统信息。</span><span class="sxs-lookup"><span data-stu-id="205b9-105">Attributing assemblies, types, or members with these CLR attributes provides XAML type system information related to your types.</span></span> <span data-ttu-id="205b9-106">向使用 .NET XAML 服务的任何 XAML 使用者提供信息，以便直接或通过专用的 XAML 读取器和 XAML 编写器处理 XAML 节点流。</span><span class="sxs-lookup"><span data-stu-id="205b9-106">Information is provided to any XAML consumer that uses .NET XAML Services for processing the XAML node stream directly or through the dedicated XAML readers and XAML writers.</span></span>

## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a><span data-ttu-id="205b9-107">自定义类型和自定义成员的 XAML 相关 CLR 特性</span><span class="sxs-lookup"><span data-stu-id="205b9-107">XAML-Related CLR Attributes for Custom Types and Custom Members</span></span>

<span data-ttu-id="205b9-108">使用 CLR 特性时，需要使用整个 CLR 来定义类型，否则此类属性将不可用。</span><span class="sxs-lookup"><span data-stu-id="205b9-108">Using CLR attributes entails that you are using the overall CLR to define your types, otherwise such attributes are not available.</span></span> <span data-ttu-id="205b9-109">如果你使用 CLR 定义类型支持，则 .NET XAML 服务 XAML 编写器使用的默认 XAML 架构上下文可以通过反射针对支持程序集读取 CLR 特性。</span><span class="sxs-lookup"><span data-stu-id="205b9-109">If you use the CLR to define type backing, then the default XAML schema context used by .NET XAML Services XAML writers can read CLR attribution through reflection against backing assemblies.</span></span>

<span data-ttu-id="205b9-110">以下各节介绍可应用于自定义类型或自定义成员的与 XAML 相关的属性。</span><span class="sxs-lookup"><span data-stu-id="205b9-110">The following sections describe the XAML-related attributes that you can apply to custom types or custom members.</span></span> <span data-ttu-id="205b9-111">每个 CLR 特性都传达与 XAML 类型系统相关的信息。</span><span class="sxs-lookup"><span data-stu-id="205b9-111">Each CLR attribute communicates information that is relevant to a XAML type system.</span></span> <span data-ttu-id="205b9-112">在加载路径中，特性化信息要么有助于 XAML 读取器构成有效的 XAML 节点流，要么有助于 XAML 编写器生成有效的对象图。</span><span class="sxs-lookup"><span data-stu-id="205b9-112">In the load path, the attributed information either helps the XAML reader form a valid XAML node stream, or it helps the XAML writer produce a valid object graph.</span></span> <span data-ttu-id="205b9-113">在保存路径中，特性化信息可以帮助 XAML 读取器形成重构 XAML 类型系统信息的有效 XAML 节点流;或声明 XAML 编写器或其他 XAML 使用者的序列化提示或要求。</span><span class="sxs-lookup"><span data-stu-id="205b9-113">In the save path, the attributed information either helps the XAML reader form a valid XAML node stream that reconstitutes XAML type system information; or it declares serialization hints or requirements for the XAML writer or other XAML consumers.</span></span>

### <a name="ambientattribute"></a><span data-ttu-id="205b9-114">AmbientAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-114">AmbientAttribute</span></span>

<span data-ttu-id="205b9-115">**参考文档：**<xref:System.Windows.Markup.AmbientAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-115">**Reference Documentation:** <xref:System.Windows.Markup.AmbientAttribute></span></span>

<span data-ttu-id="205b9-116">**适用于：**`get`支持可附加属性的类、属性或访问器成员。</span><span class="sxs-lookup"><span data-stu-id="205b9-116">**Applies to:** Class, property, or `get` accessor members that support attachable properties.</span></span>

<span data-ttu-id="205b9-117">**参数：** 内容</span><span class="sxs-lookup"><span data-stu-id="205b9-117">**Arguments:** None</span></span>

<span data-ttu-id="205b9-118"><xref:System.Windows.Markup.AmbientAttribute> 指示应在 XAML 中的环境属性概念下解释属性或采用特性化类型的所有属性。</span><span class="sxs-lookup"><span data-stu-id="205b9-118"><xref:System.Windows.Markup.AmbientAttribute> indicates that the property, or all properties that take the attributed type, should be interpreted under the ambient property concept in XAML.</span></span> <span data-ttu-id="205b9-119">环境概念涉及 XAML 处理器如何确定成员的类型所有者。</span><span class="sxs-lookup"><span data-stu-id="205b9-119">The ambient concept relates to how XAML processors determine type owners of members.</span></span> <span data-ttu-id="205b9-120">环境属性是一个属性，其中的值应在创建对象图时在分析器上下文中可用，但在此情况下，将为正在创建的即时 XAML 节点挂起典型类型成员查找。</span><span class="sxs-lookup"><span data-stu-id="205b9-120">An ambient property is a property where the value is expected to be available in the parser context when creating an object graph, but where typical type-member lookup is suspended for the immediate XAML node set being created.</span></span>

<span data-ttu-id="205b9-121">环境概念可以应用于可附加成员，这些成员不会以 CLR 特性定义的方式表示为属性 <xref:System.AttributeTargets> 。</span><span class="sxs-lookup"><span data-stu-id="205b9-121">The ambient concept can be applied to attachable members, which are not represented as properties in terms of how CLR attribution defines <xref:System.AttributeTargets>.</span></span> <span data-ttu-id="205b9-122">方法归属用法仅适用于 `get` 支持 XAML 的可附加用法的访问器。</span><span class="sxs-lookup"><span data-stu-id="205b9-122">The method attribution usage should be applied only for a `get` accessor that supports attachable usage for XAML.</span></span>

### <a name="constructorargumentattribute"></a><span data-ttu-id="205b9-123">ConstructorArgumentAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-123">ConstructorArgumentAttribute</span></span>

<span data-ttu-id="205b9-124">**参考文档：**  <xref:System.Windows.Markup.ConstructorArgumentAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-124">**Reference Documentation:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute></span></span>

<span data-ttu-id="205b9-125">**适用于：** 班级</span><span class="sxs-lookup"><span data-stu-id="205b9-125">**Applies to:** Class</span></span>

<span data-ttu-id="205b9-126">**参数：** 一个字符串，指定与单个构造函数参数匹配的属性的名称。</span><span class="sxs-lookup"><span data-stu-id="205b9-126">**Arguments:** A string that specifies the name of the property that matches a single constructor argument.</span></span>

<span data-ttu-id="205b9-127"><xref:System.Windows.Markup.ConstructorArgumentAttribute> 指定可以通过使用非参数构造函数语法来初始化对象，指定名称的属性提供构造信息。</span><span class="sxs-lookup"><span data-stu-id="205b9-127"><xref:System.Windows.Markup.ConstructorArgumentAttribute> specifies that an object can be initialized by using a non-parameterless constructor syntax, and that a property of the specified name supplies construction information.</span></span> <span data-ttu-id="205b9-128">此信息主要用于 XAML 序列化。</span><span class="sxs-lookup"><span data-stu-id="205b9-128">This information is primarily for XAML serialization.</span></span> <span data-ttu-id="205b9-129">有关详细信息，请参阅 <xref:System.Windows.Markup.ConstructorArgumentAttribute>。</span><span class="sxs-lookup"><span data-stu-id="205b9-129">For more information, see <xref:System.Windows.Markup.ConstructorArgumentAttribute>.</span></span>

### <a name="contentpropertyattribute"></a><span data-ttu-id="205b9-130">ContentPropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-130">ContentPropertyAttribute</span></span>

<span data-ttu-id="205b9-131">**参考文档：**  <xref:System.Windows.Markup.ContentPropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-131">**Reference Documentation:**  <xref:System.Windows.Markup.ContentPropertyAttribute></span></span>

<span data-ttu-id="205b9-132">**适用于：** 班级</span><span class="sxs-lookup"><span data-stu-id="205b9-132">**Applies to:** Class</span></span>

<span data-ttu-id="205b9-133">**参数：** 一个字符串，指定特性化类型的成员的名称。</span><span class="sxs-lookup"><span data-stu-id="205b9-133">**Arguments:** A string that specifies the name of a member of the attributed type.</span></span>

<span data-ttu-id="205b9-134"><xref:System.Windows.Markup.ContentPropertyAttribute> 指示由参数命名的属性应作为该类型的 XAML 内容属性。</span><span class="sxs-lookup"><span data-stu-id="205b9-134"><xref:System.Windows.Markup.ContentPropertyAttribute> indicates that the property as named by the argument should serve as the XAML content property for that type.</span></span> <span data-ttu-id="205b9-135">XAML 内容属性定义继承到可分配给定义类型的所有派生类型。</span><span class="sxs-lookup"><span data-stu-id="205b9-135">The XAML content property definition inherits to all derived types that are assignable to the defining type.</span></span> <span data-ttu-id="205b9-136">您可以通过 <xref:System.Windows.Markup.ContentPropertyAttribute> 对特定派生类型应用，来重写特定派生类型的定义。</span><span class="sxs-lookup"><span data-stu-id="205b9-136">You can override the definition on a specific derived type by applying <xref:System.Windows.Markup.ContentPropertyAttribute> on the specific derived type.</span></span>

<span data-ttu-id="205b9-137">对于用作 XAML 内容属性的属性，可在 XAML 用法中省略属性的属性元素标记。</span><span class="sxs-lookup"><span data-stu-id="205b9-137">For the property that serves as the XAML content property, property element tagging for the property can be omitted in the XAML usage.</span></span> <span data-ttu-id="205b9-138">通常，可以指定 XAML 内容属性，这些属性可为内容和包含模型升级简化的 XAML 标记。</span><span class="sxs-lookup"><span data-stu-id="205b9-138">Typically, you designate XAML content properties that promote a streamlined XAML markup for your content and containment models.</span></span> <span data-ttu-id="205b9-139">由于只能将一个成员指定为 XAML 内容属性，因此，有时需要对类型的多个容器属性中的哪个容器属性指定为 XAML 内容属性。</span><span class="sxs-lookup"><span data-stu-id="205b9-139">Because only one member can be designated as the XAML content property, you sometimes have design choices to make regarding which of several container properties of a type should be designated as the XAML content property.</span></span> <span data-ttu-id="205b9-140">其他容器属性必须与显式属性元素一起使用。</span><span class="sxs-lookup"><span data-stu-id="205b9-140">The other container properties must be used with explicit property elements.</span></span>

<span data-ttu-id="205b9-141">在 XAML 节点流中，XAML 内容属性仍生成， `StartMember` 并 `EndMember` 使用属性的名称作为节点 <xref:System.Xaml.XamlMember> 。</span><span class="sxs-lookup"><span data-stu-id="205b9-141">In the XAML node stream, XAML content properties still produce `StartMember` and `EndMember` nodes, using the name of the property for the <xref:System.Xaml.XamlMember>.</span></span> <span data-ttu-id="205b9-142">若要确定成员是否为 XAML 内容属性，请检查 <xref:System.Xaml.XamlType> 位置的值 `StartObject` 并获取的值 <xref:System.Xaml.XamlType.ContentProperty%2A> 。</span><span class="sxs-lookup"><span data-stu-id="205b9-142">To determine whether a member is the XAML content property, examine the <xref:System.Xaml.XamlType> value from the `StartObject` position and obtain the value of <xref:System.Xaml.XamlType.ContentProperty%2A>.</span></span>

### <a name="contentwrapperattribute"></a><span data-ttu-id="205b9-143">ContentWrapperAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-143">ContentWrapperAttribute</span></span>

<span data-ttu-id="205b9-144">**参考文档：**  <xref:System.Windows.Markup.ContentWrapperAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-144">**Reference Documentation:**  <xref:System.Windows.Markup.ContentWrapperAttribute></span></span>

<span data-ttu-id="205b9-145">**适用于：** 类，特别是集合类型。</span><span class="sxs-lookup"><span data-stu-id="205b9-145">**Applies to:** Class, specifically collection types.</span></span>

<span data-ttu-id="205b9-146">**参数：** 一个 <xref:System.Type> ，指定要用作外部内容的内容包装类型的类型。</span><span class="sxs-lookup"><span data-stu-id="205b9-146">**Arguments:** A <xref:System.Type> that specifies the type to use as the content wrapper type for foreign content.</span></span>

<span data-ttu-id="205b9-147"><xref:System.Windows.Markup.ContentWrapperAttribute> 指定将用于包装外部内容的关联集合类型上的一个或多个类型。</span><span class="sxs-lookup"><span data-stu-id="205b9-147"><xref:System.Windows.Markup.ContentWrapperAttribute> specifies one or more types on the associated collection type that will be used to wrap foreign content.</span></span> <span data-ttu-id="205b9-148">"外部内容" 指的是对内容属性类型的类型系统约束不会捕获所属类型的 XAML 使用情况支持的所有可能的内容事例。</span><span class="sxs-lookup"><span data-stu-id="205b9-148">Foreign content refers to cases where the type system constraints on the type of the content property do not capture all of the possible content cases that XAML usage for the owning type would support.</span></span> <span data-ttu-id="205b9-149">例如，XAML 支持特定类型的内容可能支持强类型化泛型中的字符串 <xref:System.Collections.ObjectModel.Collection%601> 。</span><span class="sxs-lookup"><span data-stu-id="205b9-149">For example, XAML support for content of a particular type might support strings in a strongly typed generic <xref:System.Collections.ObjectModel.Collection%601>.</span></span> <span data-ttu-id="205b9-150">内容包装适用于将预先存在的标记约定迁移到用于集合的可赋值值的 XAML 概念，如迁移与文本相关的内容模型。</span><span class="sxs-lookup"><span data-stu-id="205b9-150">Content wrappers are useful for migrating pre-existing markup conventions into XAML's conception of assignable values for collections, such as migrating text-related content models.</span></span>

<span data-ttu-id="205b9-151">若要指定多个内容包装类型，请多次应用该属性。</span><span class="sxs-lookup"><span data-stu-id="205b9-151">To specify more than one content wrapper type, apply the attribute multiple times.</span></span>

### <a name="dependsonattribute"></a><span data-ttu-id="205b9-152">DependsOnAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-152">DependsOnAttribute</span></span>

<span data-ttu-id="205b9-153">**参考文档：**  <xref:System.Windows.Markup.DependsOnAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-153">**Reference Documentation:**  <xref:System.Windows.Markup.DependsOnAttribute></span></span>

<span data-ttu-id="205b9-154">**适用于：** 知识产权</span><span class="sxs-lookup"><span data-stu-id="205b9-154">**Applies to:** Property</span></span>

<span data-ttu-id="205b9-155">**参数：** 一个字符串，指定特性化类型的另一个成员的名称。</span><span class="sxs-lookup"><span data-stu-id="205b9-155">**Arguments:** A string that specifies the name of another member of the attributed type.</span></span>

<span data-ttu-id="205b9-156"><xref:System.Windows.Markup.DependsOnAttribute> 指示特性化属性依赖于另一个属性的值。</span><span class="sxs-lookup"><span data-stu-id="205b9-156"><xref:System.Windows.Markup.DependsOnAttribute> indicates that the attributed property depends on the value of another property.</span></span> <span data-ttu-id="205b9-157">将此特性应用于属性定义可确保先在 XAML 对象写入中处理依赖属性。</span><span class="sxs-lookup"><span data-stu-id="205b9-157">Applying this attribute to a property definition ensures that the dependent properties are processed first in XAML object writing.</span></span> <span data-ttu-id="205b9-158">使用 <xref:System.Windows.Markup.DependsOnAttribute> 情况：指定类型的异常事例，必须遵循特定的分析顺序才能实现有效的对象创建。</span><span class="sxs-lookup"><span data-stu-id="205b9-158">Usages of <xref:System.Windows.Markup.DependsOnAttribute> specify the exceptional cases of properties on types where a specific order of parsing must be followed for valid object creation.</span></span>

<span data-ttu-id="205b9-159">可以将多个 <xref:System.Windows.Markup.DependsOnAttribute> 事例应用于一个属性定义。</span><span class="sxs-lookup"><span data-stu-id="205b9-159">You can apply multiple <xref:System.Windows.Markup.DependsOnAttribute> cases to a property definition.</span></span>

### <a name="markupextensionreturntypeattribute"></a><span data-ttu-id="205b9-160">MarkupExtensionReturnTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-160">MarkupExtensionReturnTypeAttribute</span></span>

<span data-ttu-id="205b9-161">**参考文档：**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-161">**Reference Documentation:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute></span></span>

<span data-ttu-id="205b9-162">**适用于：** 类，它应为 <xref:System.Windows.Markup.MarkupExtension> 派生类型。</span><span class="sxs-lookup"><span data-stu-id="205b9-162">**Applies to:** Class, which is expected to be a <xref:System.Windows.Markup.MarkupExtension> derived type.</span></span>

<span data-ttu-id="205b9-163">**参数：** 一个 <xref:System.Type> ，指定要作为 `ProvideValue` 特性化结果的最精确类型 <xref:System.Windows.Markup.MarkupExtension> 。</span><span class="sxs-lookup"><span data-stu-id="205b9-163">**Arguments:** A <xref:System.Type> that specifies the most precise type to expect as the `ProvideValue` result of the attributed <xref:System.Windows.Markup.MarkupExtension>.</span></span>

<span data-ttu-id="205b9-164">有关详细信息，请参阅 [XAML 的标记扩展概述](markup-extensions-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="205b9-164">For more information, see [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span></span>

### <a name="namescopepropertyattribute"></a><span data-ttu-id="205b9-165">NameScopePropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-165">NameScopePropertyAttribute</span></span>

<span data-ttu-id="205b9-166">**参考文档：**  <xref:System.Windows.Markup.NameScopePropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-166">**Reference Documentation:**  <xref:System.Windows.Markup.NameScopePropertyAttribute></span></span>

<span data-ttu-id="205b9-167">**适用于：** 班级</span><span class="sxs-lookup"><span data-stu-id="205b9-167">**Applies to:** Class</span></span>

<span data-ttu-id="205b9-168">**参数：** 支持两种形式的归属：</span><span class="sxs-lookup"><span data-stu-id="205b9-168">**Arguments:** Supports two forms of attribution:</span></span>

- <span data-ttu-id="205b9-169">一个字符串，指定特性化类型上属性的名称。</span><span class="sxs-lookup"><span data-stu-id="205b9-169">A string that specifies the name of a property on the attributed type.</span></span>

- <span data-ttu-id="205b9-170">一个字符串，指定属性的名称，并指定一个 <xref:System.Type> 用于定义命名属性的类型的。</span><span class="sxs-lookup"><span data-stu-id="205b9-170">A string that specifies the name of a property, and a <xref:System.Type> for the type that defines the named property.</span></span> <span data-ttu-id="205b9-171">此窗体用于将可附加成员指定为 XAML 名称范围属性。</span><span class="sxs-lookup"><span data-stu-id="205b9-171">This form is for specifying an attachable member as the XAML namescope property.</span></span>

<span data-ttu-id="205b9-172"><xref:System.Windows.Markup.NameScopePropertyAttribute> 指定为特性化类提供 XAML 名称范围值的属性。</span><span class="sxs-lookup"><span data-stu-id="205b9-172"><xref:System.Windows.Markup.NameScopePropertyAttribute> specifies a property that provides the XAML namescope value for the attributed class.</span></span> <span data-ttu-id="205b9-173">XAML 名称范围属性应引用实现 <xref:System.Windows.Markup.INameScope> 并保存实际 XAML 名称范围、其存储和行为的对象。</span><span class="sxs-lookup"><span data-stu-id="205b9-173">The XAML namescope property is expected to reference an object that implements <xref:System.Windows.Markup.INameScope> and holds the actual XAML namescope, its store, and its behavior.</span></span>

### <a name="runtimenamepropertyattribute"></a><span data-ttu-id="205b9-174">RuntimeNamePropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-174">RuntimeNamePropertyAttribute</span></span>

<span data-ttu-id="205b9-175">**参考文档：**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-175">**Reference Documentation:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute></span></span>

<span data-ttu-id="205b9-176">**适用于：** 班级</span><span class="sxs-lookup"><span data-stu-id="205b9-176">**Applies to:** Class</span></span>

<span data-ttu-id="205b9-177">**参数：** 一个字符串，指定特性化类型上的运行时名称属性的名称。</span><span class="sxs-lookup"><span data-stu-id="205b9-177">**Arguments:** A string that specifies the name of the run-time name property on the attributed type.</span></span>

<span data-ttu-id="205b9-178"><xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 报告映射到 XAML [X：Name 指令](xname-directive.md)的特性化类型的属性。</span><span class="sxs-lookup"><span data-stu-id="205b9-178"><xref:System.Windows.Markup.RuntimeNamePropertyAttribute> reports a property of the attributed type that maps to the XAML [x:Name Directive](xname-directive.md).</span></span> <span data-ttu-id="205b9-179">属性必须为类型 <xref:System.String> ，并且必须是可读/写的。</span><span class="sxs-lookup"><span data-stu-id="205b9-179">The property must be of type <xref:System.String> and must be read/write.</span></span>

<span data-ttu-id="205b9-180">定义继承到可分配给定义类型的所有派生类型。</span><span class="sxs-lookup"><span data-stu-id="205b9-180">The definition inherits to all derived types that are assignable to the defining type.</span></span> <span data-ttu-id="205b9-181">您可以通过 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 对特定派生类型应用，来重写特定派生类型的定义。</span><span class="sxs-lookup"><span data-stu-id="205b9-181">You can override the definition on a specific derived type by applying <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> on the specific derived type.</span></span>

### <a name="trimsurroundingwhitespaceattribute"></a><span data-ttu-id="205b9-182">TrimSurroundingWhitespaceAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-182">TrimSurroundingWhitespaceAttribute</span></span>

<span data-ttu-id="205b9-183">**参考文档：**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-183">**Reference Documentation:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute></span></span>

<span data-ttu-id="205b9-184">**适用于：** 各种</span><span class="sxs-lookup"><span data-stu-id="205b9-184">**Applies to:** Types</span></span>

<span data-ttu-id="205b9-185">**参数：** 内容.</span><span class="sxs-lookup"><span data-stu-id="205b9-185">**Arguments:** None.</span></span>

<span data-ttu-id="205b9-186"><xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> 应用于特定的类型，这些特定类型可能在空白内容中显示为子元素 (具有) 的集合保存的内容 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="205b9-186"><xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> is applied to specific types that might appear as child elements within white-space significant content (content held by a collection that has <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>).</span></span> <span data-ttu-id="205b9-187"><xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> 主要与 save 路径相关，但通过检查，在加载路径的 XAML 类型系统中提供 <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="205b9-187"><xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> is mainly relevant to the save path, but is available in the XAML type system in the load path by examining <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="205b9-188">有关详细信息，请参阅 [XAML 中的空白处理](white-space-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="205b9-188">For more information, see [White-space processing in XAML](white-space-processing.md).</span></span>

### <a name="typeconverterattribute"></a><span data-ttu-id="205b9-189">TypeConverterAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-189">TypeConverterAttribute</span></span>

<span data-ttu-id="205b9-190">**参考文档：**  <xref:System.ComponentModel.TypeConverterAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-190">**Reference Documentation:**  <xref:System.ComponentModel.TypeConverterAttribute></span></span>

<span data-ttu-id="205b9-191">**适用于：** 仅 XAML 有效方法 (的类、属性和方法是 `get` 支持可附加成员) 的访问器。</span><span class="sxs-lookup"><span data-stu-id="205b9-191">**Applies to:** Class, property, method (the only XAML-valid method case is a `get` accessor that supports an attachable member).</span></span>

<span data-ttu-id="205b9-192">**参数：** 的 <xref:System.Type> <xref:System.ComponentModel.TypeConverter> 。</span><span class="sxs-lookup"><span data-stu-id="205b9-192">**Arguments:** The <xref:System.Type> of the <xref:System.ComponentModel.TypeConverter>.</span></span>

<span data-ttu-id="205b9-193"><xref:System.ComponentModel.TypeConverterAttribute> 在 XAML 上下文中引用自定义 <xref:System.ComponentModel.TypeConverter> 。</span><span class="sxs-lookup"><span data-stu-id="205b9-193"><xref:System.ComponentModel.TypeConverterAttribute> in a XAML context references a custom <xref:System.ComponentModel.TypeConverter>.</span></span> <span data-ttu-id="205b9-194">这 <xref:System.ComponentModel.TypeConverter> 为自定义类型或该类型的成员提供类型转换行为。</span><span class="sxs-lookup"><span data-stu-id="205b9-194">This <xref:System.ComponentModel.TypeConverter> provides type conversion behavior for custom types, or members of that type.</span></span>

<span data-ttu-id="205b9-195">将 <xref:System.ComponentModel.TypeConverterAttribute> 特性应用到类型，并引用类型转换器实现。</span><span class="sxs-lookup"><span data-stu-id="205b9-195">Apply the <xref:System.ComponentModel.TypeConverterAttribute> attribute to your type, referencing your type converter implementation.</span></span> <span data-ttu-id="205b9-196">可以在类、结构或接口上定义 XAML 的类型转换器。</span><span class="sxs-lookup"><span data-stu-id="205b9-196">You can define type converters for XAML on classes, structures, or interfaces.</span></span> <span data-ttu-id="205b9-197">不需要为枚举提供类型转换，而是在本机启用该转换。</span><span class="sxs-lookup"><span data-stu-id="205b9-197">You do not need to provide type conversion for enumerations, that conversion is enabled natively.</span></span>

<span data-ttu-id="205b9-198">类型转换器应该能够从用于标记中的属性或初始化文本的字符串转换为所需的目标类型。</span><span class="sxs-lookup"><span data-stu-id="205b9-198">Your type converter should be able to convert from a string that is used for attributes or initialization text in markup, into your intended destination type.</span></span> <span data-ttu-id="205b9-199">有关详细信息，请参阅 [TypeConverters 和 XAML](/dotnet/desktop/wpf/advanced/typeconverters-and-xaml)。</span><span class="sxs-lookup"><span data-stu-id="205b9-199">For more information, see [TypeConverters and XAML](/dotnet/desktop/wpf/advanced/typeconverters-and-xaml).</span></span>

<span data-ttu-id="205b9-200">不是应用于类型的所有值，也可以针对特定属性建立 XAML 的类型转换器行为。</span><span class="sxs-lookup"><span data-stu-id="205b9-200">Rather than applying to all values of a type, a type converter behavior for XAML can also be established on a specific property.</span></span> <span data-ttu-id="205b9-201">在这种情况下，您将应用于 <xref:System.ComponentModel.TypeConverterAttribute> 外部定义 (属性定义，而不是特定 `get` 和 `set` 定义) 。</span><span class="sxs-lookup"><span data-stu-id="205b9-201">In this case, you apply <xref:System.ComponentModel.TypeConverterAttribute> to the property definition (the outer definition, not the specific `get` and `set` definitions).</span></span>

<span data-ttu-id="205b9-202">可通过将应用 <xref:System.ComponentModel.TypeConverterAttribute> 到 `get` 支持 xaml 使用的方法访问器来分配自定义可附加成员的 XAML 用法的类型转换器行为。</span><span class="sxs-lookup"><span data-stu-id="205b9-202">A type converter behavior for XAML usage of a custom attachable member can be assigned by applying <xref:System.ComponentModel.TypeConverterAttribute> to the `get` method accessor that supports the XAML usage.</span></span>

<span data-ttu-id="205b9-203">与类似 <xref:System.ComponentModel.TypeConverter> ， <xref:System.ComponentModel.TypeConverterAttribute> 在存在 XAML 之前存在于 .net 中，类型转换器模型用于其他目的。</span><span class="sxs-lookup"><span data-stu-id="205b9-203">Similar to <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> existed in .NET prior to the existence of XAML, and the type converter model served other purposes.</span></span> <span data-ttu-id="205b9-204">若要引用和使用 <xref:System.ComponentModel.TypeConverterAttribute> ，你必须完全限定它或提供的 `using` 语句 <xref:System.ComponentModel> 。</span><span class="sxs-lookup"><span data-stu-id="205b9-204">In order to reference and use <xref:System.ComponentModel.TypeConverterAttribute>, you must fully qualify it or provide a `using` statement for <xref:System.ComponentModel>.</span></span> <span data-ttu-id="205b9-205">还包括项目中的系统程序集。</span><span class="sxs-lookup"><span data-stu-id="205b9-205">Also include the System assembly in your project.</span></span>

### <a name="uidpropertyattribute"></a><span data-ttu-id="205b9-206">UidPropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-206">UidPropertyAttribute</span></span>

<span data-ttu-id="205b9-207">**参考文档：**  <xref:System.Windows.Markup.UidPropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-207">**Reference Documentation:**  <xref:System.Windows.Markup.UidPropertyAttribute></span></span>

<span data-ttu-id="205b9-208">**适用于：** 班级</span><span class="sxs-lookup"><span data-stu-id="205b9-208">**Applies to:** Class</span></span>

<span data-ttu-id="205b9-209">**参数：** 按名称引用相关属性的字符串。</span><span class="sxs-lookup"><span data-stu-id="205b9-209">**Arguments:** A string that references the relevant property by name.</span></span>

<span data-ttu-id="205b9-210">指示为 [X：Uid 指令](xuid-directive.md)指定别名的类的 CLR 属性。</span><span class="sxs-lookup"><span data-stu-id="205b9-210">Indicates the CLR property of a class that aliases the [x:Uid Directive](xuid-directive.md).</span></span>

### <a name="usableduringinitializationattribute"></a><span data-ttu-id="205b9-211">UsableDuringInitializationAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-211">UsableDuringInitializationAttribute</span></span>

<span data-ttu-id="205b9-212">**参考文档：**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-212">**Reference Documentation:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute></span></span>

<span data-ttu-id="205b9-213">**适用于：** 班级</span><span class="sxs-lookup"><span data-stu-id="205b9-213">**Applies to:** Class</span></span>

<span data-ttu-id="205b9-214">**参数：** 布尔值。</span><span class="sxs-lookup"><span data-stu-id="205b9-214">**Arguments:** A Boolean.</span></span> <span data-ttu-id="205b9-215">如果用于属性的预期目的，则该值应设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="205b9-215">If used for the attribute's intended purpose, the value should be set to `true`.</span></span>

<span data-ttu-id="205b9-216">指示在 XAML 对象图创建期间是否自上而下生成此类型。</span><span class="sxs-lookup"><span data-stu-id="205b9-216">Indicates whether the type is built top-down during XAML object graph creation.</span></span> <span data-ttu-id="205b9-217">这是一个高级概念，可能与编程模型的定义密切相关。</span><span class="sxs-lookup"><span data-stu-id="205b9-217">This is an advanced concept, which is probably closely related to the definition of your programming model.</span></span> <span data-ttu-id="205b9-218">有关详细信息，请参阅 <xref:System.Windows.Markup.UsableDuringInitializationAttribute>。</span><span class="sxs-lookup"><span data-stu-id="205b9-218">For more information, see <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.</span></span>

### <a name="valueserializerattribute"></a><span data-ttu-id="205b9-219">ValueSerializerAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-219">ValueSerializerAttribute</span></span>

<span data-ttu-id="205b9-220">**参考文档：**  <xref:System.Windows.Markup.ValueSerializerAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-220">**Reference Documentation:**  <xref:System.Windows.Markup.ValueSerializerAttribute></span></span>

<span data-ttu-id="205b9-221">**适用于：** 仅 XAML 有效方法 (的类、属性和方法是 `get` 支持可附加成员) 的访问器。</span><span class="sxs-lookup"><span data-stu-id="205b9-221">**Applies to:** Class, property, method (the only XAML-valid method case is a `get` accessor that supports an attachable member).</span></span>

<span data-ttu-id="205b9-222">**参数：** 一个 <xref:System.Type> ，指定序列化程序支持类，以便在序列化特性化类型的所有属性或特定的特性化属性时使用。</span><span class="sxs-lookup"><span data-stu-id="205b9-222">**Arguments:** A <xref:System.Type> that specifies the value serializer support class to use when serializing all properties of the attributed type, or the specific attributed property.</span></span>

<span data-ttu-id="205b9-223"><xref:System.Windows.Markup.ValueSerializer> 指定一个值序列化类，该类需要更多的状态和上下文，而 <xref:System.ComponentModel.TypeConverter> 不是。</span><span class="sxs-lookup"><span data-stu-id="205b9-223"><xref:System.Windows.Markup.ValueSerializer> specifies a value serialization class that requires more state and context than a <xref:System.ComponentModel.TypeConverter> does.</span></span> <span data-ttu-id="205b9-224"><xref:System.Windows.Markup.ValueSerializer> 可以通过对可 <xref:System.Windows.Markup.ValueSerializerAttribute> `get` 附加成员的静态访问器方法应用属性，与可附加成员关联。</span><span class="sxs-lookup"><span data-stu-id="205b9-224"><xref:System.Windows.Markup.ValueSerializer> can be associated with an attachable member by applying the <xref:System.Windows.Markup.ValueSerializerAttribute> attribute on the static `get` accessor method for the attachable member.</span></span> <span data-ttu-id="205b9-225">值序列化还适用于枚举、接口和结构，但不适用于委托。</span><span class="sxs-lookup"><span data-stu-id="205b9-225">Value serialization is also applicable for enumerations, interfaces, and structures, but not for delegates.</span></span>

### <a name="whitespacesignificantcollectionattribute"></a><span data-ttu-id="205b9-226">WhitespaceSignificantCollectionAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-226">WhitespaceSignificantCollectionAttribute</span></span>

<span data-ttu-id="205b9-227">**参考文档：**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-227">**Reference Documentation:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute></span></span>

<span data-ttu-id="205b9-228">**适用于：** 类，特别是应承载混合内容的集合类型，在这种情况下，对象元素周围的空白可能对 UI 表示形式非常重要。</span><span class="sxs-lookup"><span data-stu-id="205b9-228">**Applies to:** Class, specifically collection types that are expected to host mixed content, where white space around object elements might be significant for UI representation.</span></span>

<span data-ttu-id="205b9-229">**参数：** 内容.</span><span class="sxs-lookup"><span data-stu-id="205b9-229">**Arguments:** None.</span></span>

<span data-ttu-id="205b9-230"><xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> 指示应由 XAML 处理器以空白形式处理集合类型，这将影响集合中的 XAML 节点流的值节点的构造。</span><span class="sxs-lookup"><span data-stu-id="205b9-230"><xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> indicates that a collection type should be processed as white-space significant by a XAML processor, which influences the construction of the XAML node stream's value nodes within the collection.</span></span> <span data-ttu-id="205b9-231">有关详细信息，请参阅 [XAML 中的空白处理](white-space-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="205b9-231">For more information, see [White-space processing in XAML](white-space-processing.md).</span></span>

### <a name="xamldeferloadattribute"></a><span data-ttu-id="205b9-232">XamlDeferLoadAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-232">XamlDeferLoadAttribute</span></span>

<span data-ttu-id="205b9-233">**参考文档：**  <xref:System.Windows.Markup.XamlDeferLoadAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-233">**Reference Documentation:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute></span></span>

<span data-ttu-id="205b9-234">**适用于：** 类，属性。</span><span class="sxs-lookup"><span data-stu-id="205b9-234">**Applies to:** Class, property.</span></span>

<span data-ttu-id="205b9-235">**参数：** 支持将两个特性窗体类型作为字符串或类型为 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="205b9-235">**Arguments:** Supports two attribution forms types as strings, or types as <xref:System.Type>.</span></span> <span data-ttu-id="205b9-236">请参阅 <xref:System.Windows.Markup.XamlDeferLoadAttribute>。</span><span class="sxs-lookup"><span data-stu-id="205b9-236">See <xref:System.Windows.Markup.XamlDeferLoadAttribute>.</span></span>

<span data-ttu-id="205b9-237">指示类或属性具有 XAML 的延迟加载用途（如模板行为），并报告启用延迟行为及其目标/内容类型的类。</span><span class="sxs-lookup"><span data-stu-id="205b9-237">Indicates that a class or property has a deferred load usage for XAML (such as a template behavior), and reports the class that enables the deferring behavior and its destination/content type.</span></span>

### <a name="xamlsetmarkupextensionattribute"></a><span data-ttu-id="205b9-238">System.windows.markup.xamlsetmarkupextensionattribute</span><span class="sxs-lookup"><span data-stu-id="205b9-238">XamlSetMarkupExtensionAttribute</span></span>

<span data-ttu-id="205b9-239">**参考文档：**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-239">**Reference Documentation:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute></span></span>

<span data-ttu-id="205b9-240">**适用于：** 班级</span><span class="sxs-lookup"><span data-stu-id="205b9-240">**Applies to:** Class</span></span>

<span data-ttu-id="205b9-241">**参数：** 命名回调。</span><span class="sxs-lookup"><span data-stu-id="205b9-241">**Arguments:** Names the callback.</span></span>

<span data-ttu-id="205b9-242">指示类可以使用标记扩展为其一个或多个属性提供值，并引用 XAML 编写器在对类的任何属性执行标记扩展设置操作之前应调用的处理程序。</span><span class="sxs-lookup"><span data-stu-id="205b9-242">Indicates that a class can use a markup extension to provide a value for one or more of its properties, and references a handler that a XAML writer should call before performing a markup extension set operation on any property of the class.</span></span>

### <a name="xamlsettypeconverterattribute"></a><span data-ttu-id="205b9-243">XamlSetTypeConverterAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-243">XamlSetTypeConverterAttribute</span></span>

<span data-ttu-id="205b9-244">**参考文档：**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-244">**Reference Documentation:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute></span></span>

<span data-ttu-id="205b9-245">**适用于：** 班级</span><span class="sxs-lookup"><span data-stu-id="205b9-245">**Applies to:** Class</span></span>

<span data-ttu-id="205b9-246">**参数：** 命名回调。</span><span class="sxs-lookup"><span data-stu-id="205b9-246">**Arguments:** Names the callback.</span></span>

<span data-ttu-id="205b9-247">指示类可以使用类型转换器为其一个或多个属性提供值，并引用 XAML 编写器在对类的任何属性执行类型转换器设置操作之前应调用的处理程序。</span><span class="sxs-lookup"><span data-stu-id="205b9-247">Indicates that a class can use a type converter to provide a value for one or more of its properties, and references a handler that a XAML writer should call before performing a type converter set operation on any property of the class.</span></span>

### <a name="xmllangpropertyattribute"></a><span data-ttu-id="205b9-248">XmlLangPropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-248">XmlLangPropertyAttribute</span></span>

<span data-ttu-id="205b9-249">**参考文档：**  <xref:System.Windows.Markup.XmlLangPropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-249">**Reference Documentation:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute></span></span>

<span data-ttu-id="205b9-250">**适用于：** 班级</span><span class="sxs-lookup"><span data-stu-id="205b9-250">**Applies to:** Class</span></span>

<span data-ttu-id="205b9-251">**参数：** 一个字符串，指定属性类型的别名属性的名称 `xml:lang` 。</span><span class="sxs-lookup"><span data-stu-id="205b9-251">**Arguments:** A string that specifies the name of the property to alias to `xml:lang` on the attributed type.</span></span>

<span data-ttu-id="205b9-252"><xref:System.Windows.Markup.XmlLangPropertyAttribute> 报告映射到 XML 指令的特性化类型的属性 `lang` 。</span><span class="sxs-lookup"><span data-stu-id="205b9-252"><xref:System.Windows.Markup.XmlLangPropertyAttribute> reports a property of the attributed type that maps to the XML `lang` directive.</span></span> <span data-ttu-id="205b9-253">属性的类型不一定为， <xref:System.String> 但必须可从字符串中赋值 (可以通过将类型转换器与属性的类型或特定属性) 关联来实现。</span><span class="sxs-lookup"><span data-stu-id="205b9-253">The property is not necessarily of type <xref:System.String> but must be assignable from a string (assignment could be accomplished by associating a type converter with the property's type or with the specific property).</span></span> <span data-ttu-id="205b9-254">属性必须是读/写属性。</span><span class="sxs-lookup"><span data-stu-id="205b9-254">The property must be read/write.</span></span>

<span data-ttu-id="205b9-255">映射的应用场景 `xml:lang` 是为了使运行时对象模型可以访问 XML 指定的语言信息，而无需使用 XMLDOM 进行专门处理。</span><span class="sxs-lookup"><span data-stu-id="205b9-255">The scenario for mapping `xml:lang` is so that a runtime object model has access to XML-specified language information without specifically processing with an XMLDOM.</span></span>

<span data-ttu-id="205b9-256">定义继承到可分配给定义类型的所有派生类型。</span><span class="sxs-lookup"><span data-stu-id="205b9-256">The definition inherits to all derived types that are assignable to the defining type.</span></span> <span data-ttu-id="205b9-257">您可以通过在特定派生类型上应用来重写特定派生类型的定义 <xref:System.Windows.Markup.XmlLangPropertyAttribute> ，但这种情况并不常见。</span><span class="sxs-lookup"><span data-stu-id="205b9-257">You can override the definition on a specific derived type by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> on the specific derived type, although that is an uncommon scenario.</span></span>

## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a><span data-ttu-id="205b9-258">程序集级别的 XAML 相关 CLR 特性</span><span class="sxs-lookup"><span data-stu-id="205b9-258">XAML-Related CLR Attributes at the Assembly Level</span></span>

<span data-ttu-id="205b9-259">以下各节介绍了与 XAML 相关的特性，这些特性不应用于类型或成员定义，而是应用于程序集。</span><span class="sxs-lookup"><span data-stu-id="205b9-259">The following sections describe the XAML-related attributes that are not applied to types or member definitions, but are instead applied to assemblies.</span></span> <span data-ttu-id="205b9-260">这些属性与定义包含要在 XAML 中使用的自定义类型的库的整体目标有关。</span><span class="sxs-lookup"><span data-stu-id="205b9-260">These attributes are pertinent to the overall goal of defining a library that contains custom types to use in XAML.</span></span> <span data-ttu-id="205b9-261">有些属性不一定会直接影响 XAML 节点流，而是在节点流中传递，供其他使用者使用。</span><span class="sxs-lookup"><span data-stu-id="205b9-261">Some of the attributes do not necessarily influence the XAML node stream directly, but are passed on in the node stream for other consumers to use.</span></span> <span data-ttu-id="205b9-262">信息的使用者包括需要 XAML 命名空间信息和关联的前缀信息的设计环境或序列化过程。</span><span class="sxs-lookup"><span data-stu-id="205b9-262">Consumers for the information include design environments or serialization processes that need XAML namespace information and associated prefix information.</span></span> <span data-ttu-id="205b9-263">XAML 架构上下文 (包括 .NET XAML 服务默认值) 还使用此信息。</span><span class="sxs-lookup"><span data-stu-id="205b9-263">A XAML schema context (including the .NET XAML Services default) also uses this information.</span></span>

### <a name="xmlnscompatiblewithattribute"></a><span data-ttu-id="205b9-264">XmlnsCompatibleWithAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-264">XmlnsCompatibleWithAttribute</span></span>

<span data-ttu-id="205b9-265">**参考文档：**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-265">**Reference Documentation:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute></span></span>

<span data-ttu-id="205b9-266">**参数：**</span><span class="sxs-lookup"><span data-stu-id="205b9-266">**Arguments:**</span></span>

- <span data-ttu-id="205b9-267">一个字符串，该字符串指定要归类的 XAML 命名空间的标识符。</span><span class="sxs-lookup"><span data-stu-id="205b9-267">A string that specifies the identifier of the XAML namespace to subsume.</span></span>

- <span data-ttu-id="205b9-268">一个字符串，该字符串指定可从上一个参数归类 XAML 命名空间的 XAML 命名空间的标识符。</span><span class="sxs-lookup"><span data-stu-id="205b9-268">A string that specifies the identifier of the XAML namespace that can subsume the XAML namespace from the previous argument.</span></span>

  <span data-ttu-id="205b9-269"><xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> 指定 XAML 命名空间可由另一个 XAML 命名空间归入。</span><span class="sxs-lookup"><span data-stu-id="205b9-269"><xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> specifies that a XAML namespace can be subsumed by another XAML namespace.</span></span> <span data-ttu-id="205b9-270">通常，先前定义的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 中指示了包含 XAML 命令空间。</span><span class="sxs-lookup"><span data-stu-id="205b9-270">Typically, the subsuming XAML namespace is indicated in a previously defined <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.</span></span> <span data-ttu-id="205b9-271">此方法可用于对库中的 XAML 词汇进行版本控制，并使其与先前定义的针对早期版本的词汇的标记兼容。</span><span class="sxs-lookup"><span data-stu-id="205b9-271">This technique can be used for versioning a XAML vocabulary in a library and to make it compatible with previously defined markup against the earlier versioned vocabulary.</span></span>

### <a name="xmlnsdefinitionattribute"></a><span data-ttu-id="205b9-272">System.windows.markup.xmlnsdefinitionattribute></span><span class="sxs-lookup"><span data-stu-id="205b9-272">XmlnsDefinitionAttribute</span></span>

<span data-ttu-id="205b9-273">**参考文档：**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-273">**Reference Documentation:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute></span></span>

<span data-ttu-id="205b9-274">**参数：**</span><span class="sxs-lookup"><span data-stu-id="205b9-274">**Arguments:**</span></span>

- <span data-ttu-id="205b9-275">一个字符串，指定要定义的 XAML 命名空间的标识符。</span><span class="sxs-lookup"><span data-stu-id="205b9-275">A string that specifies the identifier of the XAML namespace to define.</span></span>

- <span data-ttu-id="205b9-276">命名 CLR 命名空间的字符串。</span><span class="sxs-lookup"><span data-stu-id="205b9-276">A string that names a CLR namespace.</span></span> <span data-ttu-id="205b9-277">CLR 命名空间应在程序集中定义公共类型，并且必须至少有一个 CLR 命名空间类型适用于 XAML 用法。</span><span class="sxs-lookup"><span data-stu-id="205b9-277">The CLR namespace should define public types in your assembly, and at least one of the CLR namespace types should be intended for XAML usage.</span></span>

  <span data-ttu-id="205b9-278"><xref:System.Windows.Markup.XmlnsDefinitionAttribute> 指定在 XAML 命名空间和 CLR 命名空间之间按程序集进行的映射，然后 XAML 对象编写器或 XAML 架构上下文使用该命名空间进行类型解析。</span><span class="sxs-lookup"><span data-stu-id="205b9-278"><xref:System.Windows.Markup.XmlnsDefinitionAttribute> specifies a mapping on a per-assembly basis between a XAML namespace and a CLR namespace, which is then used for type resolution by a XAML object writer or XAML schema context.</span></span>

  <span data-ttu-id="205b9-279"><xref:System.Windows.Markup.XmlnsDefinitionAttribute>可以将多个应用程序应用于一个程序集。</span><span class="sxs-lookup"><span data-stu-id="205b9-279">More than one <xref:System.Windows.Markup.XmlnsDefinitionAttribute> can be applied to an assembly.</span></span> <span data-ttu-id="205b9-280">这可能是由于以下原因引起的：</span><span class="sxs-lookup"><span data-stu-id="205b9-280">This might be done for any combination of the following reasons:</span></span>

- <span data-ttu-id="205b9-281">库设计包含多个 CLR 命名空间，适用于运行时 API 访问的逻辑组织;但是，你希望这些命名空间中的所有类型都可以通过引用相同的 XAML 命名空间来使用 XAML。</span><span class="sxs-lookup"><span data-stu-id="205b9-281">The library design contains multiple CLR namespaces for logical organization of run-time API access; however, you want all types in those namespaces to be XAML-usable by referencing the same XAML namespace.</span></span> <span data-ttu-id="205b9-282">在这种情况下，可以 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 使用相同 <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> 值但不同的值来应用多个属性 <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> 。</span><span class="sxs-lookup"><span data-stu-id="205b9-282">In this case, you apply several <xref:System.Windows.Markup.XmlnsDefinitionAttribute> attributes using the same <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> value but different <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> values.</span></span> <span data-ttu-id="205b9-283">如果要为 XAML 命名空间定义映射，而框架或应用程序要将其用作默认的 XAML 命名空间，则此方法特别有用。</span><span class="sxs-lookup"><span data-stu-id="205b9-283">This is especially useful if you are defining mappings for the XAML namespace that your framework or application intends to be the default XAML namespace in common usage.</span></span>

- <span data-ttu-id="205b9-284">库设计包含多个 CLR 命名空间，并且需要在这些 CLR 命名空间中的类型用法之间进行有意的 XAML 命名空间分隔。</span><span class="sxs-lookup"><span data-stu-id="205b9-284">The library design contains multiple CLR namespaces, and you want a deliberate XAML namespace separation between the usages of types in those CLR namespaces.</span></span>

- <span data-ttu-id="205b9-285">在程序集中定义 CLR 命名空间，并希望可通过多个 XAML 命名空间访问该命名空间。</span><span class="sxs-lookup"><span data-stu-id="205b9-285">You define a CLR namespace in the assembly, and you want it to be accessible through more than one XAML namespace.</span></span> <span data-ttu-id="205b9-286">当您支持具有相同基本代码的多个词汇时，会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="205b9-286">This scenario occurs when you are supporting multiple vocabularies with the same codebase.</span></span>

- <span data-ttu-id="205b9-287">在一个或多个 CLR 命名空间中定义 XAML 语言支持。</span><span class="sxs-lookup"><span data-stu-id="205b9-287">You define XAML language support in one or more CLR namespaces.</span></span> <span data-ttu-id="205b9-288">在这种情况下， <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> 该值应为 `http://schemas.microsoft.com/winfx/2006/xaml` 。</span><span class="sxs-lookup"><span data-stu-id="205b9-288">In this case, the <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> value should be `http://schemas.microsoft.com/winfx/2006/xaml`.</span></span>

### <a name="xmlnsprefixattribute"></a><span data-ttu-id="205b9-289">XmlnsPrefixAttribute</span><span class="sxs-lookup"><span data-stu-id="205b9-289">XmlnsPrefixAttribute</span></span>

<span data-ttu-id="205b9-290">**参考文档：**  <xref:System.Windows.Markup.XmlnsPrefixAttribute></span><span class="sxs-lookup"><span data-stu-id="205b9-290">**Reference Documentation:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute></span></span>

<span data-ttu-id="205b9-291">**参数：**</span><span class="sxs-lookup"><span data-stu-id="205b9-291">**Arguments:**</span></span>

- <span data-ttu-id="205b9-292">一个指定 XAML 命名空间的标识符的字符串。</span><span class="sxs-lookup"><span data-stu-id="205b9-292">A string that specifies the identifier of a XAML namespace.</span></span>

- <span data-ttu-id="205b9-293">一个字符串，指定建议的前缀。</span><span class="sxs-lookup"><span data-stu-id="205b9-293">A string that specifies a recommended prefix.</span></span>

  <span data-ttu-id="205b9-294"><xref:System.Windows.Markup.XmlnsDefinitionAttribute> 指定一个建议用于 XAML 命名空间的前缀。</span><span class="sxs-lookup"><span data-stu-id="205b9-294"><xref:System.Windows.Markup.XmlnsDefinitionAttribute> specifies a recommended prefix to use for a XAML namespace.</span></span> <span data-ttu-id="205b9-295">当写入 .NET XAML 服务序列化的 XAML 文件中的元素和属性时 <xref:System.Xaml.XamlXmlWriter> ，或者当 xaml 实现库与具有 XAML 编辑功能的设计环境进行交互时，前缀非常有用。</span><span class="sxs-lookup"><span data-stu-id="205b9-295">The prefix is useful when writing elements and attributes in a XAML file that is serialized by .NET XAML Services <xref:System.Xaml.XamlXmlWriter>, or when a XAML-implementing library interacts with a design environment that has XAML editing features.</span></span>

  <span data-ttu-id="205b9-296"><xref:System.Windows.Markup.XmlnsPrefixAttribute>可以将多个应用程序应用于一个程序集。</span><span class="sxs-lookup"><span data-stu-id="205b9-296">More than one <xref:System.Windows.Markup.XmlnsPrefixAttribute> can be applied to an assembly.</span></span> <span data-ttu-id="205b9-297">这可能是由于以下原因引起的：</span><span class="sxs-lookup"><span data-stu-id="205b9-297">This might be done for any combination of the following reasons:</span></span>

- <span data-ttu-id="205b9-298">程序集定义多个 XAML 命名空间的类型。</span><span class="sxs-lookup"><span data-stu-id="205b9-298">Your assembly defines types for more than one XAML namespace.</span></span> <span data-ttu-id="205b9-299">在这种情况下，为每个 XAML 命名空间定义不同的前缀值。</span><span class="sxs-lookup"><span data-stu-id="205b9-299">In this case, define different prefix values for each XAML namespace.</span></span>

- <span data-ttu-id="205b9-300">支持多个词汇，并为每个词汇和 XAML 命名空间使用不同的前缀。</span><span class="sxs-lookup"><span data-stu-id="205b9-300">You are supporting multiple vocabularies, and you use different prefixes for each vocabulary and XAML namespace.</span></span>

- <span data-ttu-id="205b9-301">在程序集中定义 XAML 语言支持，并为指定 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> `http://schemas.microsoft.com/winfx/2006/xaml` 。</span><span class="sxs-lookup"><span data-stu-id="205b9-301">You define XAML language support in the assembly and have a <xref:System.Windows.Markup.XmlnsDefinitionAttribute> for `http://schemas.microsoft.com/winfx/2006/xaml`.</span></span> <span data-ttu-id="205b9-302">在这种情况下，通常应升级前缀 `x` 。</span><span class="sxs-lookup"><span data-stu-id="205b9-302">In this case, you typically should promote the prefix `x`.</span></span>

> [!NOTE]
> <span data-ttu-id="205b9-303">.NET XAML 服务还定义了与 XAML 相关的属性 <xref:System.Windows.Markup.RootNamespaceAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="205b9-303">.NET XAML Services also defines the XAML-related attribute <xref:System.Windows.Markup.RootNamespaceAttribute>.</span></span> <span data-ttu-id="205b9-304">此属性是项目系统支持的程序集级别特性，它与 XAML 自定义类型无关。</span><span class="sxs-lookup"><span data-stu-id="205b9-304">This attribute is an assembly-level attribute for project system support, and it is not relevant for XAML custom types.</span></span>

## <a name="see-also"></a><span data-ttu-id="205b9-305">请参阅</span><span class="sxs-lookup"><span data-stu-id="205b9-305">See also</span></span>

- <xref:System.Attribute>
- [<span data-ttu-id="205b9-306">定义与 .NET XAML 服务一起使用的自定义类型</span><span class="sxs-lookup"><span data-stu-id="205b9-306">Defining Custom Types for Use with .NET XAML Services</span></span>](define-custom-types.md)
