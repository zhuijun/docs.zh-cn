---
title: RelativeSource MarkupExtension
description: 指定 RelativeSource 绑定源的属性、绑定标记扩展中的属性，或在 XAML 中设置绑定的 RelativeSource 属性时。
ms.date: 03/30/2017
f1_keywords:
- RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
ms.openlocfilehash: 2da702d23413651a85b45404e088f6708546cc25
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165935"
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="a72eb-103">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="a72eb-103">RelativeSource MarkupExtension</span></span>

<span data-ttu-id="a72eb-104">指定 <xref:System.Windows.Data.RelativeSource> 绑定源的属性，以便在[绑定标记扩展](binding-markup-extension.md)中使用，或在设置 <xref:System.Windows.Data.Binding.RelativeSource%2A> <xref:System.Windows.Data.Binding> 在 XAML 中建立的元素的属性时使用。</span><span class="sxs-lookup"><span data-stu-id="a72eb-104">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="a72eb-105">XAML 属性用法</span><span class="sxs-lookup"><span data-stu-id="a72eb-105">XAML Attribute Usage</span></span>

```xml
<Binding RelativeSource="{RelativeSource modeEnumValue}" ... />
```

## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="a72eb-106">XAML 属性用法（嵌套在 Binding 扩展内）</span><span class="sxs-lookup"><span data-stu-id="a72eb-106">XAML Attribute Usage (nested within Binding extension)</span></span>

```xml
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" ... />
```

## <a name="xaml-object-element-usage"></a><span data-ttu-id="a72eb-107">XAML 对象元素用法</span><span class="sxs-lookup"><span data-stu-id="a72eb-107">XAML Object Element Usage</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource Mode="modeEnumValue"/>
  </Binding.RelativeSource>
</Binding>
```

<span data-ttu-id="a72eb-108">-或-</span><span class="sxs-lookup"><span data-stu-id="a72eb-108">-or-</span></span>

```xml
<Binding>
  <Binding.RelativeSource>
    <RelativeSource
      Mode="FindAncestor"
      AncestorType="{x:Type typeName}"
      AncestorLevel="intLevel"
    />
  </Binding.RelativeSource>
</Binding>
```

## <a name="xaml-values"></a><span data-ttu-id="a72eb-109">XAML 值</span><span class="sxs-lookup"><span data-stu-id="a72eb-109">XAML Values</span></span>

|||
|-|-|
|`modeEnumValue`|<span data-ttu-id="a72eb-110">下列类型作之一：</span><span class="sxs-lookup"><span data-stu-id="a72eb-110">One of the following:</span></span><br /><br /> <span data-ttu-id="a72eb-111">-字符串标记 `Self` ; 对应于创建的， <xref:System.Windows.Data.RelativeSource> 其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 属性设置为 <xref:System.Windows.Data.RelativeSourceMode.Self> 。</span><span class="sxs-lookup"><span data-stu-id="a72eb-111">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="a72eb-112">-字符串标记 `TemplatedParent` ; 对应于创建的， <xref:System.Windows.Data.RelativeSource> 其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 属性设置为 <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent> 。</span><span class="sxs-lookup"><span data-stu-id="a72eb-112">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="a72eb-113">-字符串标记 `PreviousData` ; 对应于创建的， <xref:System.Windows.Data.RelativeSource> 其 <xref:System.Windows.Data.RelativeSource.Mode%2A> 属性设置为 <xref:System.Windows.Data.RelativeSourceMode.PreviousData> 。</span><span class="sxs-lookup"><span data-stu-id="a72eb-113">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="a72eb-114">-有关模式的信息，请参阅下文 `FindAncestor` 。</span><span class="sxs-lookup"><span data-stu-id="a72eb-114">-   See below for information on `FindAncestor` mode.</span></span>|
|`FindAncestor`|<span data-ttu-id="a72eb-115">字符串标记 `FindAncestor`。</span><span class="sxs-lookup"><span data-stu-id="a72eb-115">The string token `FindAncestor`.</span></span> <span data-ttu-id="a72eb-116">使用此标记可输入一个模式，以便 `RelativeSource` 指定上级类型和可选的上级级别。</span><span class="sxs-lookup"><span data-stu-id="a72eb-116">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="a72eb-117">它对应于通过将 <xref:System.Windows.Data.RelativeSource> 属性设置为 <xref:System.Windows.Data.RelativeSource.Mode%2A> 而创建的 <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>。</span><span class="sxs-lookup"><span data-stu-id="a72eb-117">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|
|`typeName`|<span data-ttu-id="a72eb-118">对于 `FindAncestor` 模式是必需的。</span><span class="sxs-lookup"><span data-stu-id="a72eb-118">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="a72eb-119">类型的名称，用于填充 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="a72eb-119">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|
|`intLevel`|<span data-ttu-id="a72eb-120">对于 `FindAncestor` 模式是可选的。</span><span class="sxs-lookup"><span data-stu-id="a72eb-120">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="a72eb-121">上级级别（在逻辑树中向父级方向计算）。</span><span class="sxs-lookup"><span data-stu-id="a72eb-121">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|

## <a name="remarks"></a><span data-ttu-id="a72eb-122">注解</span><span class="sxs-lookup"><span data-stu-id="a72eb-122">Remarks</span></span>

<span data-ttu-id="a72eb-123">`{RelativeSource TemplatedParent}`绑定使用情况是一项关键技术，可解决控件的 UI 与控件的逻辑之间的更大分离。</span><span class="sxs-lookup"><span data-stu-id="a72eb-123">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="a72eb-124">这可以实现从模板定义内绑定到模板化父级（在其中应用模板的运行时对象实例）。</span><span class="sxs-lookup"><span data-stu-id="a72eb-124">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="a72eb-125">对于这种情况， [TemplateBinding 标记扩展](templatebinding-markup-extension.md)实际上是以下绑定表达式的简写形式： `{Binding RelativeSource={RelativeSource TemplatedParent}}` 。</span><span class="sxs-lookup"><span data-stu-id="a72eb-125">For this case, the [TemplateBinding Markup Extension](templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="a72eb-126">`TemplateBinding`或 `{RelativeSource TemplatedParent}` 用法仅在定义模板的 XAML 中相关。</span><span class="sxs-lookup"><span data-stu-id="a72eb-126">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="a72eb-127">有关详细信息，请参阅[TemplateBinding 标记扩展](templatebinding-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="a72eb-127">For more information, see [TemplateBinding Markup Extension](templatebinding-markup-extension.md).</span></span>

<span data-ttu-id="a72eb-128">`{RelativeSource FindAncestor}`主要用于控件模板或可预测的自包含 UI 组合，适用于控件始终应位于特定上级类型的可视化树中的情况。</span><span class="sxs-lookup"><span data-stu-id="a72eb-128">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="a72eb-129">例如，项控件的项可能使用 `FindAncestor` 用法绑定到其项控件父级/祖先级。</span><span class="sxs-lookup"><span data-stu-id="a72eb-129">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="a72eb-130">或者，属于模板中控件组合一部分的元素可使用 `FindAncestor` 绑定到同一组合结构中的父元素。</span><span class="sxs-lookup"><span data-stu-id="a72eb-130">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>

<span data-ttu-id="a72eb-131">在 XAML 语法章节显示的 `FindAncestor` 模式的对象元素语法中，第二个对象元素语法专门用于 `FindAncestor` 模式。</span><span class="sxs-lookup"><span data-stu-id="a72eb-131">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="a72eb-132">`FindAncestor` 模式需要 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="a72eb-132">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="a72eb-133">必须 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 使用对要查找的上级类型的[X:Type 标记扩展](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)引用将设置为属性。</span><span class="sxs-lookup"><span data-stu-id="a72eb-133">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../../desktop-wpf/xaml-services/xtype-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="a72eb-134">当在运行时处理绑定请求时，将会用到 <xref:System.Windows.Data.RelativeSource.AncestorType%2A> 值。</span><span class="sxs-lookup"><span data-stu-id="a72eb-134">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>

<span data-ttu-id="a72eb-135">对于 `FindAncestor` 模式，当元素树中可能存在多个该类型的上级时，可以使用可选属性 <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> 帮助消除上级查找的歧义。</span><span class="sxs-lookup"><span data-stu-id="a72eb-135">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>

<span data-ttu-id="a72eb-136">有关如何使用 `FindAncestor` 模式的详细信息，请参阅 <xref:System.Windows.Data.RelativeSource>。</span><span class="sxs-lookup"><span data-stu-id="a72eb-136">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>

<span data-ttu-id="a72eb-137">`{RelativeSource Self}`对于以下情况非常有用：实例的一个属性应依赖于同一个实例的另一个属性的值，并且这两个属性之间已存在一般的依赖属性关系（如强制）。</span><span class="sxs-lookup"><span data-stu-id="a72eb-137">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="a72eb-138">尽管对象很少存在两个属性，以便这些值按原义相同（并且类型相同），但也可以将 `Converter` 参数应用到具有的绑定 `{RelativeSource Self}` ，并使用转换器在源和目标类型之间转换。</span><span class="sxs-lookup"><span data-stu-id="a72eb-138">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="a72eb-139">的另一个方案 `{RelativeSource Self}` 作为的一部分 <xref:System.Windows.MultiDataTrigger> 。</span><span class="sxs-lookup"><span data-stu-id="a72eb-139">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>

<span data-ttu-id="a72eb-140">例如，以下 XAML 定义了一个 <xref:System.Windows.Shapes.Rectangle> 元素，以便无论为 <xref:System.Windows.FrameworkElement.Width%2A> 输入什么值，都确保 <xref:System.Windows.Shapes.Rectangle> 始终是一个方形：`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="a72eb-140">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>

<span data-ttu-id="a72eb-141">`{RelativeSource PreviousData}`在数据模板中或在绑定使用集合作为数据源的情况下很有用。</span><span class="sxs-lookup"><span data-stu-id="a72eb-141">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="a72eb-142">您可以使用 `{RelativeSource PreviousData}` 突出显示集合中相邻数据项之间的关系。</span><span class="sxs-lookup"><span data-stu-id="a72eb-142">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="a72eb-143">相关技术是在数据源中的当前项和前一个项之间建立 <xref:System.Windows.Data.MultiBinding>，并使用此绑定上的转换器来确定这两个项及其属性的差异。</span><span class="sxs-lookup"><span data-stu-id="a72eb-143">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>

<span data-ttu-id="a72eb-144">在下面的示例中，项目模板中的第一个 <xref:System.Windows.Controls.TextBlock> 可显示当前编号。</span><span class="sxs-lookup"><span data-stu-id="a72eb-144">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="a72eb-145">第二个 <xref:System.Windows.Controls.TextBlock> 绑定是 <xref:System.Windows.Data.MultiBinding> 通常有两个 <xref:System.Windows.Data.Binding> 要素：当前记录和通过使用有意使用以前的数据记录的绑定 `{RelativeSource PreviousData}` 。</span><span class="sxs-lookup"><span data-stu-id="a72eb-145">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> constituents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="a72eb-146">然后，<xref:System.Windows.Data.MultiBinding> 上的转换器将计算差异，并将其返回到绑定。</span><span class="sxs-lookup"><span data-stu-id="a72eb-146">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>

```xml
<ListBox Name="fibolist">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding}"/>
            <TextBlock>, difference = </TextBlock>
                <TextBlock>
                    <TextBlock.Text>
                        <MultiBinding Converter="{StaticResource DiffConverter}">
                            <Binding/>
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>
                        </MultiBinding>
                    </TextBlock.Text>
                </TextBlock>
            </StackPanel>
        </DataTemplate>
    </ListBox.ItemTemplate>
</ListBox>
```

<span data-ttu-id="a72eb-147">此处未介绍如何将数据绑定描述为概念，请参阅[数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a72eb-147">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<span data-ttu-id="a72eb-148">在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML 处理器实现中，对此标记扩展的处理由 <xref:System.Windows.Data.RelativeSource> 类定义。</span><span class="sxs-lookup"><span data-stu-id="a72eb-148">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>

<span data-ttu-id="a72eb-149">`RelativeSource` 是标记扩展。</span><span class="sxs-lookup"><span data-stu-id="a72eb-149">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="a72eb-150">当要求转义特性值应为非文本值或非处理程序名称时，通常会实现标记扩展，相对于只在某些类型或属性上放置类型转换器而言，此需求更具有全局性。</span><span class="sxs-lookup"><span data-stu-id="a72eb-150">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="a72eb-151">XAML 中的所有标记扩展在 `{` `}` 其特性语法中使用和字符，这是 xaml 处理器识别标记扩展必须处理特性的约定。</span><span class="sxs-lookup"><span data-stu-id="a72eb-151">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="a72eb-152">有关详细信息，请参阅[标记扩展和 WPF XAML](markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="a72eb-152">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a72eb-153">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a72eb-153">See also</span></span>

- <xref:System.Windows.Data.Binding>
- [<span data-ttu-id="a72eb-154">样式设置和模板化</span><span class="sxs-lookup"><span data-stu-id="a72eb-154">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="a72eb-155">XAML 概述 (WPF)</span><span class="sxs-lookup"><span data-stu-id="a72eb-155">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="a72eb-156">标记扩展和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="a72eb-156">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
- [<span data-ttu-id="a72eb-157">数据绑定概述</span><span class="sxs-lookup"><span data-stu-id="a72eb-157">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="a72eb-158">绑定声明概述</span><span class="sxs-lookup"><span data-stu-id="a72eb-158">Binding Declarations Overview</span></span>](../data/binding-declarations-overview.md)
- [<span data-ttu-id="a72eb-159">x:Type 标记扩展</span><span class="sxs-lookup"><span data-stu-id="a72eb-159">x:Type Markup Extension</span></span>](../../../desktop-wpf/xaml-services/xtype-markup-extension.md)
