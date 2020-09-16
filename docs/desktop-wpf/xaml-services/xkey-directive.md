---
title: x:Key 指令
ms.date: 03/30/2017
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
ms.openlocfilehash: 7e4e9cbded01297818f9f01df01e95e94d7dc4af
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548268"
---
# <a name="xkey-directive"></a><span data-ttu-id="3a06d-102">x:Key 指令</span><span class="sxs-lookup"><span data-stu-id="3a06d-102">x:Key Directive</span></span>
<span data-ttu-id="3a06d-103">唯一标识在 XAML 定义的字典中创建和引用的元素。</span><span class="sxs-lookup"><span data-stu-id="3a06d-103">Uniquely identifies elements that are created and referenced in a XAML-defined dictionary.</span></span> <span data-ttu-id="3a06d-104">`x:Key`在 XAML 对象元素中添加值是在资源字典中标识资源的最常见方法，例如在 WPF 中 <xref:System.Windows.ResourceDictionary> 。</span><span class="sxs-lookup"><span data-stu-id="3a06d-104">Adding an `x:Key` value to a XAML object element is the most common way to identify a resource in a resource dictionary, for example in a WPF <xref:System.Windows.ResourceDictionary>.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="3a06d-105">XAML 属性用法</span><span class="sxs-lookup"><span data-stu-id="3a06d-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a><span data-ttu-id="3a06d-106">XAML 特性用法 (特定于 WPF 的) </span><span class="sxs-lookup"><span data-stu-id="3a06d-106">XAML Attribute Usage (WPF-specific)</span></span>  
  
```xaml  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="3a06d-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="3a06d-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`stringKeyValue`|<span data-ttu-id="3a06d-108">要用作键的文本字符串。</span><span class="sxs-lookup"><span data-stu-id="3a06d-108">A text string to use as a key.</span></span> <span data-ttu-id="3a06d-109">文本字符串必须符合 [XamlName 语法](xamlname-grammar.md)。</span><span class="sxs-lookup"><span data-stu-id="3a06d-109">The text string must conform to the [XamlName Grammar](xamlname-grammar.md).</span></span>|  
|`markupExtensionUsage`|<span data-ttu-id="3a06d-110">标记扩展分隔符中的 {} 标记扩展用法，提供要用作键的对象。</span><span class="sxs-lookup"><span data-stu-id="3a06d-110">Within the markup extension delimiters {}, a markup extension usage that provides an object to use as a key.</span></span> <span data-ttu-id="3a06d-111">请参阅“备注”。</span><span class="sxs-lookup"><span data-stu-id="3a06d-111">See Remarks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a06d-112">备注</span><span class="sxs-lookup"><span data-stu-id="3a06d-112">Remarks</span></span>  
 <span data-ttu-id="3a06d-113">`x:Key` 支持 XAML 资源字典概念。</span><span class="sxs-lookup"><span data-stu-id="3a06d-113">`x:Key` supports the XAML resource dictionary concept.</span></span> <span data-ttu-id="3a06d-114">作为语言的 XAML 不会定义资源字典实现，该实现留给特定的 UI 框架。</span><span class="sxs-lookup"><span data-stu-id="3a06d-114">XAML as a language doesn't define a resource dictionary implementation, that is left to specific UI frameworks.</span></span> <span data-ttu-id="3a06d-115">若要了解有关如何在 WPF 中实现 XAML 资源字典的详细信息，请参阅 [Xaml 资源](../fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="3a06d-115">To learn more about how XAML resource dictionaries are implemented in WPF, see [XAML Resources](../fundamentals/xaml-resources-define.md).</span></span>  
  
 <span data-ttu-id="3a06d-116">在 XAML 2006 和 WPF 中， `x:Key` 必须作为属性提供。</span><span class="sxs-lookup"><span data-stu-id="3a06d-116">In XAML 2006 and WPF, `x:Key` must be provided as an attribute.</span></span> <span data-ttu-id="3a06d-117">你仍可以使用非字符串键，但这需要使用标记扩展用法来提供属性窗体中的非字符串值。</span><span class="sxs-lookup"><span data-stu-id="3a06d-117">You can still use nonstring keys, but this requires a markup extension usage in order to provide the nonstring value in attribute form.</span></span> <span data-ttu-id="3a06d-118">如果你使用的是 XAML 2009，则 `x:Key` 可将指定为元素，以显式支持由对象类型（而非字符串）键控的字典，而不需要标记扩展中间。</span><span class="sxs-lookup"><span data-stu-id="3a06d-118">If you are using XAML 2009, `x:Key` can be specified as an element, to explicitly support dictionaries keyed by object types other than strings without requiring a markup extension intermediate.</span></span> <span data-ttu-id="3a06d-119">请参阅本主题中的 "XAML 2009" 部分。</span><span class="sxs-lookup"><span data-stu-id="3a06d-119">See the "XAML 2009" section in this topic.</span></span> <span data-ttu-id="3a06d-120">备注部分的剩余部分专门适用于 XAML 2006 实现。</span><span class="sxs-lookup"><span data-stu-id="3a06d-120">The remainder of the Remarks section applies specifically to the XAML 2006 implementation.</span></span>  
  
 <span data-ttu-id="3a06d-121">的属性值 `x:Key` 可以是 [XamlName 语法](xamlname-grammar.md) 中定义的任何字符串，也可以是通过标记扩展进行计算的对象。</span><span class="sxs-lookup"><span data-stu-id="3a06d-121">The attribute value of `x:Key` can be any string defined in the [XamlName Grammar](xamlname-grammar.md) or can be an object evaluated through a markup extension.</span></span> <span data-ttu-id="3a06d-122">有关 WPF 的示例，请参阅 "WPF 使用说明"。</span><span class="sxs-lookup"><span data-stu-id="3a06d-122">See "WPF Usage Notes" for an example from WPF.</span></span>  
  
 <span data-ttu-id="3a06d-123">作为实现的父元素的子元素 <xref:System.Collections.IDictionary> 通常必须包括一个 `x:Key` 属性，该属性指定字典中的唯一键值。</span><span class="sxs-lookup"><span data-stu-id="3a06d-123">Child elements of a parent element that is an <xref:System.Collections.IDictionary> implementation must typically include an `x:Key` attribute that specifies a unique key value within that dictionary.</span></span> <span data-ttu-id="3a06d-124">框架可能实现用别名替换特定类型的键属性 `x:Key` ; 定义此类属性的类型应采用特性化 <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="3a06d-124">Frameworks might implement aliased key properties to substitute for `x:Key` on particular types; types that define such properties should be attributed with <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.</span></span>  
  
 <span data-ttu-id="3a06d-125">等效于指定的代码 `x:Key` 是用于基础的键 <xref:System.Collections.IDictionary> 。</span><span class="sxs-lookup"><span data-stu-id="3a06d-125">The code equivalent of specifying `x:Key` is the key that is used for the underlying <xref:System.Collections.IDictionary>.</span></span> <span data-ttu-id="3a06d-126">例如， `x:Key` `key` <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> 当你在代码中将资源添加到 wpf 时，适用于 wpf 中某个资源的标记的将与的参数的值等效 <xref:System.Windows.ResourceDictionary> 。</span><span class="sxs-lookup"><span data-stu-id="3a06d-126">For example, an `x:Key` that is applied in markup for a resource in WPF is equivalent to the value of the `key` parameter of <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> when you add the resource to a WPF <xref:System.Windows.ResourceDictionary> in code.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="3a06d-127">WPF 用法说明</span><span class="sxs-lookup"><span data-stu-id="3a06d-127">WPF Usage Notes</span></span>  
 <span data-ttu-id="3a06d-128"><xref:System.Collections.IDictionary>作为实现（如 WPF）的父对象的子对象 <xref:System.Windows.ResourceDictionary> 通常必须包含 `x:Key` 特性，并且键值在该字典中必须是唯一的。</span><span class="sxs-lookup"><span data-stu-id="3a06d-128">Child objects of a parent object that is an <xref:System.Collections.IDictionary> implementation, such as the WPF <xref:System.Windows.ResourceDictionary>, must typically include an `x:Key` attribute, and the key value must be unique within that dictionary.</span></span> <span data-ttu-id="3a06d-129">有两个值得注意的异常：</span><span class="sxs-lookup"><span data-stu-id="3a06d-129">There are two notable exceptions:</span></span>  
  
- <span data-ttu-id="3a06d-130">一些 WPF 类型声明了字典使用的隐式键。</span><span class="sxs-lookup"><span data-stu-id="3a06d-130">Some WPF types declare an implicit key for dictionary usage.</span></span> <span data-ttu-id="3a06d-131">例如， <xref:System.Windows.Style> 具有 <xref:System.Windows.Style.TargetType%2A> 、或的 <xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate.DataType%2A> 可以位于， <xref:System.Windows.ResourceDictionary> 并使用隐式键。</span><span class="sxs-lookup"><span data-stu-id="3a06d-131">For example, a <xref:System.Windows.Style> with a <xref:System.Windows.Style.TargetType%2A>, or a <xref:System.Windows.DataTemplate> with a <xref:System.Windows.DataTemplate.DataType%2A>, can be  in a <xref:System.Windows.ResourceDictionary> and use the implicit key.</span></span>  
  
- <span data-ttu-id="3a06d-132">WPF 支持合并资源字典概念。</span><span class="sxs-lookup"><span data-stu-id="3a06d-132">WPF supports a merged resource dictionary concept.</span></span> <span data-ttu-id="3a06d-133">可以在合并字典之间共享密钥，并可以使用访问共享密钥行为 <xref:System.Windows.FrameworkContentElement.FindResource%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3a06d-133">Keys can be shared between the merged dictionaries, and the shared key behavior can be accessed using <xref:System.Windows.FrameworkContentElement.FindResource%2A>.</span></span> <span data-ttu-id="3a06d-134">有关详细信息，请参阅 [合并资源字典](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries)。</span><span class="sxs-lookup"><span data-stu-id="3a06d-134">For more information, see [Merged Resource Dictionaries](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries).</span></span>  
  
 <span data-ttu-id="3a06d-135">在整个 WPF XAML 实现和应用程序模型中，XAML 标记编译器不会检查密钥的唯一性。</span><span class="sxs-lookup"><span data-stu-id="3a06d-135">In the overall WPF XAML implementation and application model, key uniqueness is not checked by the XAML markup compiler.</span></span> <span data-ttu-id="3a06d-136">相反，缺少值或非唯一 `x:Key` 值会导致加载时 XAML 分析器错误。</span><span class="sxs-lookup"><span data-stu-id="3a06d-136">Instead, missing or nonunique `x:Key` values cause load-time XAML parser errors.</span></span> <span data-ttu-id="3a06d-137">但是，Visual Studio for WPF 字典处理通常会在设计阶段记录此类错误。</span><span class="sxs-lookup"><span data-stu-id="3a06d-137">However, Visual Studio handling of dictionaries for WPF can often note such errors in the design phase.</span></span>  
  
 <span data-ttu-id="3a06d-138">请注意，在显示的语法中， <xref:System.Windows.ResourceDictionary> 对象是隐式的，因为 WPF XAML 处理器如何生成用于填充 <xref:System.Windows.FrameworkElement.Resources%2A> 集合的集合。</span><span class="sxs-lookup"><span data-stu-id="3a06d-138">Note that in the syntax shown, the <xref:System.Windows.ResourceDictionary> object is implicit in how the WPF XAML processor produces a collection to populate a <xref:System.Windows.FrameworkElement.Resources%2A> collection.</span></span> <span data-ttu-id="3a06d-139"><xref:System.Windows.ResourceDictionary>通常不会在标记中显式提供为元素，但在某些情况下，如果需要清楚起见，它可能是在属性元素和内的项之间 (集合对象元素， <xref:System.Windows.FrameworkElement.Resources%2A> 该元素) 填充字典。</span><span class="sxs-lookup"><span data-stu-id="3a06d-139">A <xref:System.Windows.ResourceDictionary> is not typically provided explicitly as an element in markup, although it can be in some cases if wanted for clarity (it would be a collection object element between the <xref:System.Windows.FrameworkElement.Resources%2A> property element and the items within that populate the dictionary).</span></span> <span data-ttu-id="3a06d-140">有关集合对象在标记中几乎始终为隐式元素的原因的信息，请参阅 [XAML 语法（详细](/dotnet/desktop/wpf/advanced/xaml-syntax-in-detail)）。</span><span class="sxs-lookup"><span data-stu-id="3a06d-140">For information about why a collection object is almost always an implicit element in markup, see [XAML Syntax In Detail](/dotnet/desktop/wpf/advanced/xaml-syntax-in-detail).</span></span>  
  
 <span data-ttu-id="3a06d-141">在 WPF XAML 实现中，资源字典键的处理由 <xref:System.Windows.ResourceKey> 抽象类定义。</span><span class="sxs-lookup"><span data-stu-id="3a06d-141">In the WPF XAML implementation, the handling for resource dictionary keys is defined by the <xref:System.Windows.ResourceKey> abstract class.</span></span> <span data-ttu-id="3a06d-142">不过，WPF XAML 处理器基于它们的用法为密钥生成不同的基础扩展类型。</span><span class="sxs-lookup"><span data-stu-id="3a06d-142">However the WPF XAML processor produces different underlying extension types for keys based on their usages.</span></span> <span data-ttu-id="3a06d-143">例如， <xref:System.Windows.DataTemplate> 或任何派生类的键单独处理，并生成一个不同的 <xref:System.Windows.DataTemplateKey> 对象。</span><span class="sxs-lookup"><span data-stu-id="3a06d-143">For example, the key for a <xref:System.Windows.DataTemplate> or any derived class is handled separately, and produces a distinct <xref:System.Windows.DataTemplateKey> object.</span></span>  
  
 <span data-ttu-id="3a06d-144">键和名称 `x:Key` `x:Name` 在基本 XAML 定义 (与) 使用不同的指令和语言元素。</span><span class="sxs-lookup"><span data-stu-id="3a06d-144">Keys and names use different directives and language elements (`x:Key` versus `x:Name`) in the basic XAML definition.</span></span> <span data-ttu-id="3a06d-145">键和名称还可用于 WPF 定义和应用这些概念的不同情况。</span><span class="sxs-lookup"><span data-stu-id="3a06d-145">Keys and names are also used in different situations by the WPF definition and application of these concepts.</span></span> <span data-ttu-id="3a06d-146">有关详细信息，请参阅 [WPF XAML 名称范围](/dotnet/desktop/wpf/advanced/wpf-xaml-namescopes)。</span><span class="sxs-lookup"><span data-stu-id="3a06d-146">For details, see [WPF XAML Namescopes](/dotnet/desktop/wpf/advanced/wpf-xaml-namescopes).</span></span>  
  
 <span data-ttu-id="3a06d-147">如前所述，密钥的值可以通过标记扩展提供，也可以是字符串值以外的值。</span><span class="sxs-lookup"><span data-stu-id="3a06d-147">As stated previously, the value of a key can be supplied through a markup extension and can be other than a string value.</span></span> <span data-ttu-id="3a06d-148">WPF 方案的一个示例是，的值 `x:Key` 可以是 [ComponentResourceKey](/dotnet/desktop/wpf/advanced/componentresourcekey-markup-extension)。</span><span class="sxs-lookup"><span data-stu-id="3a06d-148">An example WPF scenario is that the value of `x:Key` may be a [ComponentResourceKey](/dotnet/desktop/wpf/advanced/componentresourcekey-markup-extension).</span></span> <span data-ttu-id="3a06d-149">某些控件为自定义样式资源公开该类型的样式键，该资源会影响该控件的外观和行为的一部分，而不会完全替换样式。</span><span class="sxs-lookup"><span data-stu-id="3a06d-149">Certain controls expose a style key of that type for a custom style resource that influences part of the appearance and behavior of that control without totally replacing the style.</span></span> <span data-ttu-id="3a06d-150">此类键的一个示例是 <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3a06d-150">An example of such a key is <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.</span></span>  
  
 <span data-ttu-id="3a06d-151">WPF 合并字典功能引入了有关密钥唯一性和键查找行为的其他注意事项。</span><span class="sxs-lookup"><span data-stu-id="3a06d-151">The WPF merged dictionary feature introduces additional considerations for key uniqueness and key lookup behavior.</span></span> <span data-ttu-id="3a06d-152">有关详细信息，请参阅 [合并资源字典](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries)。</span><span class="sxs-lookup"><span data-stu-id="3a06d-152">For more information, see [Merged Resource Dictionaries](/dotnet/desktop/wpf/advanced/merged-resource-dictionaries).</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="3a06d-153">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="3a06d-153">XAML 2009</span></span>  
 <span data-ttu-id="3a06d-154">XAML 2009 放宽 `x:Key` 属性形式始终提供的限制。</span><span class="sxs-lookup"><span data-stu-id="3a06d-154">XAML 2009 relaxes the restriction that `x:Key` always be provided in attribute form.</span></span>  
  
 <span data-ttu-id="3a06d-155">在 WPF 中，可以使用 XAML 2009 功能，但仅针对未进行标记编译的 XAML。</span><span class="sxs-lookup"><span data-stu-id="3a06d-155">In WPF, you can use XAML 2009 features, but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="3a06d-156">WPF 的已编译标记的 XAML 以及 XAML 的 BAML 形式当前不支持 XAML 2009 关键字和功能。</span><span class="sxs-lookup"><span data-stu-id="3a06d-156">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="3a06d-157">在 XAML 2009 下，可以 `x:Key` 通过以下用法指定元素：</span><span class="sxs-lookup"><span data-stu-id="3a06d-157">Under XAML 2009, you can specify `x:Key` elements through the following usage:</span></span>  
  
### <a name="xaml-element-usage-xaml-2009-only"></a><span data-ttu-id="3a06d-158">XAML 元素用法 (仅限 XAML 2009) </span><span class="sxs-lookup"><span data-stu-id="3a06d-158">XAML Element Usage (XAML 2009 only)</span></span>  
  
```xaml  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a><span data-ttu-id="3a06d-159">XAML 值</span><span class="sxs-lookup"><span data-stu-id="3a06d-159">XAML Values</span></span>  
  
|||  
|-|-|  
|`keyObject`|<span data-ttu-id="3a06d-160">对象的对象元素，该对象用作专用字典中给定的的键 `object` 。</span><span class="sxs-lookup"><span data-stu-id="3a06d-160">Object element for the object that is used as the key for a given `object` in a specialized dictionary.</span></span>|  
  
- <span data-ttu-id="3a06d-161">此类用途的容器/父项未在此处显示。</span><span class="sxs-lookup"><span data-stu-id="3a06d-161">The container/parent for this kind of use is not shown here.</span></span> <span data-ttu-id="3a06d-162">`object` 应为表示专用字典实现的对象元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="3a06d-162">`object` is expected to be a child of an object element that represents a specialized dictionary implementation.</span></span> <span data-ttu-id="3a06d-163">`keyObject` 应为对象实例 (或值类型的值) ，此值适合作为特定专用字典实现的键。</span><span class="sxs-lookup"><span data-stu-id="3a06d-163">`keyObject` is expected to be an object instance (or a value of a value type) that is appropriate as the key for that particular specialized dictionary implementation.</span></span>  
  
- <span data-ttu-id="3a06d-164">WPF 不实现需要此用法的字典。</span><span class="sxs-lookup"><span data-stu-id="3a06d-164">WPF does not implement dictionaries that require this usage.</span></span> <span data-ttu-id="3a06d-165">对象键是 XAML 语言的常规功能，对于在 XAML 中创建字典的某些自定义字典方案可能很有用。</span><span class="sxs-lookup"><span data-stu-id="3a06d-165">Object keys is more a general feature of the XAML language, possibly useful for certain custom dictionary scenarios where creating the dictionary in XAML is desirable.</span></span> <span data-ttu-id="3a06d-166">对于使用资源的非字符串密钥的隐式样式等 WPF 功能，存在用于建立或指定密钥的其他方法，因此不需要使用对象密钥。</span><span class="sxs-lookup"><span data-stu-id="3a06d-166">For WPF features such as implicit styles that use non-string keys for resources, other techniques for establishing or specifying the keys exist, so using an object key is not necessary.</span></span>  
  
- <span data-ttu-id="3a06d-167">`keyObject` 也可以是对象元素窗体中的标记扩展用法，而不是直接对象实例。</span><span class="sxs-lookup"><span data-stu-id="3a06d-167">`keyObject` could also be a markup extension usage in object element form, rather than a direct object instance.</span></span>  
  
## <a name="silverlight-usage-notes"></a><span data-ttu-id="3a06d-168">Silverlight 使用说明</span><span class="sxs-lookup"><span data-stu-id="3a06d-168">Silverlight Usage Notes</span></span>  
 <span data-ttu-id="3a06d-169">`x:Key` 对于 Silverlight，单独记录。</span><span class="sxs-lookup"><span data-stu-id="3a06d-169">`x:Key` for Silverlight is documented separately.</span></span> <span data-ttu-id="3a06d-170">有关详细信息，请参阅 [XAML 命名空间 (x： ) 语言功能 (Silverlight) ](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95))。</span><span class="sxs-lookup"><span data-stu-id="3a06d-170">For more information, see [XAML Namespace (x:) Language Features (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a06d-171">请参阅</span><span class="sxs-lookup"><span data-stu-id="3a06d-171">See also</span></span>

- [<span data-ttu-id="3a06d-172">XAML 资源</span><span class="sxs-lookup"><span data-stu-id="3a06d-172">XAML Resources</span></span>](../fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="3a06d-173">资源和代码</span><span class="sxs-lookup"><span data-stu-id="3a06d-173">Resources and Code</span></span>](/dotnet/desktop/wpf/advanced/resources-and-code)
- [<span data-ttu-id="3a06d-174">StaticResource 标记扩展</span><span class="sxs-lookup"><span data-stu-id="3a06d-174">StaticResource Markup Extension</span></span>](/dotnet/desktop/wpf/advanced/staticresource-markup-extension)
