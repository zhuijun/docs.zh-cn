---
title: StaticResource 标记扩展
description: 通过查找对已定义资源的引用来为任何 XAML 属性特性提供一个值。
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: 77396c1867dcbe279d7ba158ed9e6f5f833f17b5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164672"
---
# <a name="staticresource-markup-extension"></a><span data-ttu-id="775f9-103">StaticResource 标记扩展</span><span class="sxs-lookup"><span data-stu-id="775f9-103">StaticResource Markup Extension</span></span>
<span data-ttu-id="775f9-104">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]通过查找对已定义资源的引用为任何属性属性提供一个值。</span><span class="sxs-lookup"><span data-stu-id="775f9-104">Provides a value for any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] property attribute by looking up a reference to an already defined resource.</span></span> <span data-ttu-id="775f9-105">该资源的查找行为类似于加载时查找，它将查找以前从当前页面的标记加载的资源以及 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 其他应用程序源，并将该资源值生成为运行时对象中的属性值。</span><span class="sxs-lookup"><span data-stu-id="775f9-105">Lookup behavior for that resource is analogous to load-time lookup, which will look for resources that were previously loaded from the markup of the current [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page as well as other application sources, and will generate that resource value as the property value in the run-time objects.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="775f9-106">XAML 属性用法</span><span class="sxs-lookup"><span data-stu-id="775f9-106">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{StaticResource key}" ... />  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="775f9-107">XAML 对象元素用法</span><span class="sxs-lookup"><span data-stu-id="775f9-107">XAML Object Element Usage</span></span>  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" ... />  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="775f9-108">XAML 值</span><span class="sxs-lookup"><span data-stu-id="775f9-108">XAML Values</span></span>  
  
|||  
|-|-|  
|`key`|<span data-ttu-id="775f9-109">所请求资源的密钥。</span><span class="sxs-lookup"><span data-stu-id="775f9-109">The key for the requested resource.</span></span> <span data-ttu-id="775f9-110">如果在标记中创建了资源，则此密钥最初由[X：Key 指令](../../../desktop-wpf/xaml-services/xkey-directive.md)分配，或在 `key` 调用时作为参数提供（ <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> 如果资源是在代码中创建的）。</span><span class="sxs-lookup"><span data-stu-id="775f9-110">This key was initially assigned by the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) if a resource was created in markup, or was provided as the `key` parameter when calling <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> if the resource was created in code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="775f9-111">注解</span><span class="sxs-lookup"><span data-stu-id="775f9-111">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="775f9-112">不能尝试对在文件中对其进行 `StaticResource` 词法上进一步定义的资源进行前向引用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="775f9-112">A `StaticResource` must not attempt to make a forward reference to a resource that is defined lexically further within the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="775f9-113">尝试执行此操作不受支持，即使此类引用不会失败，在搜索表示的内部哈希表时，尝试转发引用会导致加载时性能下降 <xref:System.Windows.ResourceDictionary> 。</span><span class="sxs-lookup"><span data-stu-id="775f9-113">Attempting to do so is not supported, and even if such a reference does not fail, attempting the forward reference will incur a load time performance penalty when the internal hash tables representing a <xref:System.Windows.ResourceDictionary> are searched.</span></span> <span data-ttu-id="775f9-114">为了获得最佳结果，请调整资源字典的组合，以便可以避免转发引用。</span><span class="sxs-lookup"><span data-stu-id="775f9-114">For best results, adjust the composition of your resource dictionaries such that forward references can be avoided.</span></span> <span data-ttu-id="775f9-115">如果无法避免正向引用，请改用[DynamicResource 标记扩展](dynamicresource-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="775f9-115">If you cannot avoid a forward reference, use [DynamicResource Markup Extension](dynamicresource-markup-extension.md) instead.</span></span>  
  
 <span data-ttu-id="775f9-116">指定的 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 应与现有资源相对应，该资源在页面、应用程序、可用控件主题和外部资源或系统资源的某一级别以[x：Key 指令](../../../desktop-wpf/xaml-services/xkey-directive.md)标识。</span><span class="sxs-lookup"><span data-stu-id="775f9-116">The specified <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> should correspond to an existing resource, identified with an [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) at some level in your page, application, the available control themes and external resources, or system resources.</span></span> <span data-ttu-id="775f9-117">资源查找按顺序进行。</span><span class="sxs-lookup"><span data-stu-id="775f9-117">The resource lookup occurs in that order.</span></span> <span data-ttu-id="775f9-118">有关静态和动态资源的资源查找行为的详细信息，请参阅[XAML 资源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)。</span><span class="sxs-lookup"><span data-stu-id="775f9-118">For more information about resource lookup behavior for static and dynamic resources, see [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
 <span data-ttu-id="775f9-119">资源键可以是[XamlName 语法](../../../desktop-wpf/xaml-services/xamlname-grammar.md)中定义的任意字符串。</span><span class="sxs-lookup"><span data-stu-id="775f9-119">A resource key can be any string defined in the [XamlName Grammar](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span></span> <span data-ttu-id="775f9-120">资源键还可以是其他对象类型，如 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="775f9-120">A resource key can also be other object types, such as a <xref:System.Type>.</span></span> <span data-ttu-id="775f9-121"><xref:System.Type>关键是通过隐式样式键来设计控件的样式。</span><span class="sxs-lookup"><span data-stu-id="775f9-121">A <xref:System.Type> key is fundamental to how controls can be styled by themes, through an implicit style key.</span></span> <span data-ttu-id="775f9-122">有关详细信息，请参阅[控件创作概述](../controls/control-authoring-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="775f9-122">For more information, see [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="775f9-123">引用资源的替代声明方法是作为[DynamicResource 标记扩展](dynamicresource-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="775f9-123">The alternative declarative means of referencing a resource is as a [DynamicResource Markup Extension](dynamicresource-markup-extension.md).</span></span>  
  
 <span data-ttu-id="775f9-124">特性语法是最常用于该标记扩展的语法。</span><span class="sxs-lookup"><span data-stu-id="775f9-124">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="775f9-125">在 `StaticResource` 标识符字符串之后提供的字符串标记被指定为基础 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 扩展类的 <xref:System.Windows.StaticResourceExtension> 值。</span><span class="sxs-lookup"><span data-stu-id="775f9-125">The string token provided after the `StaticResource` identifier string is assigned as the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> value of the underlying <xref:System.Windows.StaticResourceExtension> extension class.</span></span>  
  
 <span data-ttu-id="775f9-126">`StaticResource`可以在对象元素语法中使用。</span><span class="sxs-lookup"><span data-stu-id="775f9-126">`StaticResource` can be used in object element syntax.</span></span> <span data-ttu-id="775f9-127">在这种情况下，需要指定属性的值 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 。</span><span class="sxs-lookup"><span data-stu-id="775f9-127">In this case, specifying the value of the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property is required.</span></span>  
  
 <span data-ttu-id="775f9-128">`StaticResource` 还可以在详细特性用法中使用，以便将 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 属性指定为一个 property=value 对：</span><span class="sxs-lookup"><span data-stu-id="775f9-128">`StaticResource` can also be used in a verbose attribute usage that specifies the <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> property as a property=value pair:</span></span>  
  
```xml  
<object property="{StaticResource ResourceKey=key}" ... />  
```  
  
 <span data-ttu-id="775f9-129">如果扩展具有一个以上的可设置属性，或者某些属性是可选的，则详细用法通常会很有用。</span><span class="sxs-lookup"><span data-stu-id="775f9-129">The verbose usage is often useful for extensions that have more than one settable property, or if some properties are optional.</span></span> <span data-ttu-id="775f9-130">由于 `StaticResource` 仅有一个可设置的属性，并且此属性是必需的，因此该详细用法不具有典型性。</span><span class="sxs-lookup"><span data-stu-id="775f9-130">Because `StaticResource` has only one settable property, which is required, this verbose usage is not typical.</span></span>  
  
 <span data-ttu-id="775f9-131">在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 处理器实现中，对此标记扩展的处理由 <xref:System.Windows.StaticResourceExtension> 类定义。</span><span class="sxs-lookup"><span data-stu-id="775f9-131">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.StaticResourceExtension> class.</span></span>  
  
 <span data-ttu-id="775f9-132">`StaticResource` 是标记扩展。</span><span class="sxs-lookup"><span data-stu-id="775f9-132">`StaticResource` is a markup extension.</span></span> <span data-ttu-id="775f9-133">当要求转义特性值应为非文本值或非处理程序名称时，通常会实现标记扩展，相对于只在某些类型或属性上放置类型转换器而言，此需求更具有全局性。</span><span class="sxs-lookup"><span data-stu-id="775f9-133">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="775f9-134">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有标记扩展在其特性语法中都使用 { 和 } 字符，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 处理器通过这一约定确认标记扩展必须处理该特性。</span><span class="sxs-lookup"><span data-stu-id="775f9-134">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="775f9-135">有关详细信息，请参阅[标记扩展和 WPF XAML](markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="775f9-135">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="775f9-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="775f9-136">See also</span></span>

- [<span data-ttu-id="775f9-137">样式设置和模板化</span><span class="sxs-lookup"><span data-stu-id="775f9-137">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="775f9-138">XAML 概述 (WPF)</span><span class="sxs-lookup"><span data-stu-id="775f9-138">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="775f9-139">标记扩展和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="775f9-139">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="775f9-140">XAML 资源</span><span class="sxs-lookup"><span data-stu-id="775f9-140">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="775f9-141">资源和代码</span><span class="sxs-lookup"><span data-stu-id="775f9-141">Resources and Code</span></span>](resources-and-code.md)
