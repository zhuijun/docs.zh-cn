---
title: 绑定声明概述
description: 了解如何在 XAML 中声明用于应用程序开发 Windows Presentation Foundation （WPF）中的绑定。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- markup extensions [WPF]
- data binding [WPF], declarations
- object element syntax [WPF]
- binding data [WPF], declarations
- syntax [WPF], object elements
- binding declarations [WPF]
ms.assetid: b97fd626-4c0d-4761-872a-2bca5820da2c
ms.openlocfilehash: 8d4943de0cacb5fe0b5a0c37a5a68f15243ad528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619632"
---
# <a name="binding-declarations-overview"></a><span data-ttu-id="adc57-103">绑定声明概述</span><span class="sxs-lookup"><span data-stu-id="adc57-103">Binding Declarations Overview</span></span>

<span data-ttu-id="adc57-104">本主题讨论声明绑定的不同方法。</span><span class="sxs-lookup"><span data-stu-id="adc57-104">This topic discusses the different ways you can declare a binding.</span></span>

<a name="Prereq"></a>

## <a name="prerequisites"></a><span data-ttu-id="adc57-105">先决条件</span><span class="sxs-lookup"><span data-stu-id="adc57-105">Prerequisites</span></span>

<span data-ttu-id="adc57-106">在阅读本主题之前，请务必熟悉标记扩展的概念和使用。</span><span class="sxs-lookup"><span data-stu-id="adc57-106">Before reading this topic, it is important that you are familiar with the concept and usage of markup extensions.</span></span> <span data-ttu-id="adc57-107">有关标记扩展的详细信息，请参阅[标记扩展和 WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="adc57-107">For more information about markup extensions, see [Markup Extensions and WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md).</span></span>

<span data-ttu-id="adc57-108">本主题未涉及数据绑定概念。</span><span class="sxs-lookup"><span data-stu-id="adc57-108">This topic does not cover data binding concepts.</span></span> <span data-ttu-id="adc57-109">有关数据绑定概念的讨论，请参阅[数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="adc57-109">For a discussion of data binding concepts, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<a name="BindinginXAML"></a>

## <a name="declaring-a-binding-in-xaml"></a><span data-ttu-id="adc57-110">在 XAML 中声明绑定</span><span class="sxs-lookup"><span data-stu-id="adc57-110">Declaring a Binding in XAML</span></span>

<span data-ttu-id="adc57-111">本部分介绍如何在 XAML 中声明绑定。</span><span class="sxs-lookup"><span data-stu-id="adc57-111">This section discusses how to declare a binding in XAML.</span></span>

<a name="MarkupExtensionSyntax"></a>

### <a name="markup-extension-usage"></a><span data-ttu-id="adc57-112">标记扩展使用</span><span class="sxs-lookup"><span data-stu-id="adc57-112">Markup Extension Usage</span></span>

<span data-ttu-id="adc57-113"><xref:System.Windows.Data.Binding> 是标记扩展。</span><span class="sxs-lookup"><span data-stu-id="adc57-113"><xref:System.Windows.Data.Binding> is a markup extension.</span></span> <span data-ttu-id="adc57-114">使用绑定扩展声明绑定时，声明包含一系列子句，这些子句跟在 `Binding` 关键字后面，并由逗号 (,) 分隔。</span><span class="sxs-lookup"><span data-stu-id="adc57-114">When you use the binding extension to declare a binding, the declaration consists of a series of clauses following the `Binding` keyword and separated by commas (,).</span></span> <span data-ttu-id="adc57-115">绑定声明中的子句可以按任意顺序排列，有多种可能的组合。</span><span class="sxs-lookup"><span data-stu-id="adc57-115">The clauses in the binding declaration can be in any order and there are many possible combinations.</span></span> <span data-ttu-id="adc57-116">子句*是名称* = *值*对，其中*name*是属性的名称 <xref:System.Windows.Data.Binding> ，*值*是要为属性设置的值。</span><span class="sxs-lookup"><span data-stu-id="adc57-116">The clauses are *Name*=*Value* pairs where *Name* is the name of the <xref:System.Windows.Data.Binding> property and *Value* is the value you are setting for the property.</span></span>

<span data-ttu-id="adc57-117">在标记中创建绑定声明字符串时，必须将这些字符串附加到目标对象的特定依赖属性。</span><span class="sxs-lookup"><span data-stu-id="adc57-117">When creating binding declaration strings in markup, they must be attached to the specific dependency property of a target object.</span></span> <span data-ttu-id="adc57-118">下面的示例演示如何 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> 使用绑定扩展绑定属性，指定 <xref:System.Windows.Data.Binding.Source%2A> 和 <xref:System.Windows.Data.Binding.Path%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="adc57-118">The following example shows how to bind the <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> property using the binding extension, specifying the <xref:System.Windows.Data.Binding.Source%2A> and <xref:System.Windows.Data.Binding.Path%2A> properties.</span></span>

[!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]

<span data-ttu-id="adc57-119">可以通过 <xref:System.Windows.Data.Binding> 这种方式指定类的大多数属性。</span><span class="sxs-lookup"><span data-stu-id="adc57-119">You can specify most of the properties of the <xref:System.Windows.Data.Binding> class this way.</span></span> <span data-ttu-id="adc57-120">有关绑定扩展以及 <xref:System.Windows.Data.Binding> 无法使用绑定扩展进行设置的属性列表的详细信息，请参阅[绑定标记扩展](../advanced/binding-markup-extension.md)概述。</span><span class="sxs-lookup"><span data-stu-id="adc57-120">For more information about the binding extension as well as for a list of <xref:System.Windows.Data.Binding> properties that cannot be set using the binding extension, see the [Binding Markup Extension](../advanced/binding-markup-extension.md) overview.</span></span>

<a name="ObjectElementSyntax"></a>

### <a name="object-element-syntax"></a><span data-ttu-id="adc57-121">对象元素语法</span><span class="sxs-lookup"><span data-stu-id="adc57-121">Object Element Syntax</span></span>

<span data-ttu-id="adc57-122">对象元素语法是创建绑定声明的替代方法。</span><span class="sxs-lookup"><span data-stu-id="adc57-122">Object element syntax is an alternative to creating the binding declaration.</span></span> <span data-ttu-id="adc57-123">在大多数情况下，使用标记扩展或对象元素语法没有特定的优势。</span><span class="sxs-lookup"><span data-stu-id="adc57-123">In most cases, there is no particular advantage to using either the markup extension or the object element syntax.</span></span> <span data-ttu-id="adc57-124">不过，如果标记扩展不支持你的方案，例如，当属性值是不存在任何类型转换的非字符串类型时，需要使用对象元素语法。</span><span class="sxs-lookup"><span data-stu-id="adc57-124">However, in cases which the markup extension does not support your scenario, such as when your property value is of a non-string type for which no type conversion exists, you need to use the object element syntax.</span></span>

<span data-ttu-id="adc57-125">下面是对象元素语法和标记扩展使用的示例：</span><span class="sxs-lookup"><span data-stu-id="adc57-125">The following is an example of both the object element syntax and the markup extension usage:</span></span>

[!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]

<span data-ttu-id="adc57-126">该示例 <xref:System.Windows.Controls.TextBlock.Foreground%2A> 通过使用扩展语法声明绑定来绑定属性。</span><span class="sxs-lookup"><span data-stu-id="adc57-126">The example binds the <xref:System.Windows.Controls.TextBlock.Foreground%2A> property by declaring a binding using the extension syntax.</span></span> <span data-ttu-id="adc57-127">属性的绑定声明 <xref:System.Windows.Controls.TextBlock.Text%2A> 使用对象元素语法。</span><span class="sxs-lookup"><span data-stu-id="adc57-127">The binding declaration for the <xref:System.Windows.Controls.TextBlock.Text%2A> property uses the object element syntax.</span></span>

<span data-ttu-id="adc57-128">有关其他术语的详细信息，请参阅 [XAML 语法详述](../advanced/xaml-syntax-in-detail.md)。</span><span class="sxs-lookup"><span data-stu-id="adc57-128">For more information about the different terms, see [XAML Syntax In Detail](../advanced/xaml-syntax-in-detail.md).</span></span>

<a name="MBandPB"></a>

### <a name="multibinding-and-prioritybinding"></a><span data-ttu-id="adc57-129">MultiBinding 和 PriorityBinding</span><span class="sxs-lookup"><span data-stu-id="adc57-129">MultiBinding and PriorityBinding</span></span>

<span data-ttu-id="adc57-130"><xref:System.Windows.Data.MultiBinding>和 <xref:System.Windows.Data.PriorityBinding> 不支持 XAML 扩展语法。</span><span class="sxs-lookup"><span data-stu-id="adc57-130"><xref:System.Windows.Data.MultiBinding> and <xref:System.Windows.Data.PriorityBinding> do not support the XAML extension syntax.</span></span> <span data-ttu-id="adc57-131">因此，如果在 XAML 中声明或，则必须使用对象元素语法 <xref:System.Windows.Data.MultiBinding> <xref:System.Windows.Data.PriorityBinding> 。</span><span class="sxs-lookup"><span data-stu-id="adc57-131">Therefore, you must use the object element syntax if you are declaring a <xref:System.Windows.Data.MultiBinding> or a <xref:System.Windows.Data.PriorityBinding> in XAML.</span></span>

<a name="BindinginCode"></a>

## <a name="creating-a-binding-in-code"></a><span data-ttu-id="adc57-132">在代码中创建绑定</span><span class="sxs-lookup"><span data-stu-id="adc57-132">Creating a Binding in Code</span></span>

<span data-ttu-id="adc57-133">指定绑定的另一种方法是直接在代码中的对象上设置属性 <xref:System.Windows.Data.Binding> 。</span><span class="sxs-lookup"><span data-stu-id="adc57-133">Another way to specify a binding is to set properties directly on a <xref:System.Windows.Data.Binding> object in code.</span></span> <span data-ttu-id="adc57-134">下面的示例演示如何创建 <xref:System.Windows.Data.Binding> 对象并在代码中指定属性。</span><span class="sxs-lookup"><span data-stu-id="adc57-134">The following example shows how to create a <xref:System.Windows.Data.Binding> object and specify the properties in code.</span></span>  <span data-ttu-id="adc57-135">在此示例中， `TheConverter` 是一个实现接口的对象 <xref:System.Windows.Data.IValueConverter> 。</span><span class="sxs-lookup"><span data-stu-id="adc57-135">In this example, `TheConverter` is an object that implements the <xref:System.Windows.Data.IValueConverter> interface.</span></span>

[!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
[!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]

<span data-ttu-id="adc57-136">如果要绑定的对象是或， <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> 则可以直接对对象调用 `SetBinding` 方法，而不是使用 <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="adc57-136">If the object you are binding is a <xref:System.Windows.FrameworkElement> or a <xref:System.Windows.FrameworkContentElement> you can call the `SetBinding` method on your object directly instead of using <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="adc57-137">有关示例，请参阅[在代码中创建绑定](how-to-create-a-binding-in-code.md)。</span><span class="sxs-lookup"><span data-stu-id="adc57-137">For an example, see [Create a Binding in Code](how-to-create-a-binding-in-code.md).</span></span>

<a name="Path_Syntax"></a>

## <a name="binding-path-syntax"></a><span data-ttu-id="adc57-138">绑定路径语法</span><span class="sxs-lookup"><span data-stu-id="adc57-138">Binding Path Syntax</span></span>

<span data-ttu-id="adc57-139">使用 <xref:System.Windows.Data.Binding.Path%2A> 属性指定要绑定到的源值：</span><span class="sxs-lookup"><span data-stu-id="adc57-139">Use the <xref:System.Windows.Data.Binding.Path%2A> property to specify the source value you want to bind to:</span></span>

- <span data-ttu-id="adc57-140">在最简单的情况下， <xref:System.Windows.Data.Binding.Path%2A> 属性值是要用于绑定的源对象的属性的名称，例如 `Path=PropertyName` 。</span><span class="sxs-lookup"><span data-stu-id="adc57-140">In the simplest case, the <xref:System.Windows.Data.Binding.Path%2A> property value is the name of the property of the source object to use for the binding, such as `Path=PropertyName`.</span></span>

- <span data-ttu-id="adc57-141">可以通过类似于 c # 中的类似语法来指定属性的子属性。</span><span class="sxs-lookup"><span data-stu-id="adc57-141">Subproperties of a property can be specified by a similar syntax as in C#.</span></span> <span data-ttu-id="adc57-142">例如，子句 `Path=ShoppingCart.Order` 设置与对象或属性 `ShoppingCart` 的子属性 `Order` 的绑定。</span><span class="sxs-lookup"><span data-stu-id="adc57-142">For instance, the clause `Path=ShoppingCart.Order` sets the binding to the subproperty `Order` of the object or property `ShoppingCart`.</span></span>

- <span data-ttu-id="adc57-143">若要绑定到附加属性，请将附加属性置于括号中。</span><span class="sxs-lookup"><span data-stu-id="adc57-143">To bind to an attached property, place parentheses around the attached property.</span></span> <span data-ttu-id="adc57-144">例如，若要绑定到附加属性 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> ，语法为 `Path=(DockPanel.Dock)` 。</span><span class="sxs-lookup"><span data-stu-id="adc57-144">For example, to bind to the attached property <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, the syntax is `Path=(DockPanel.Dock)`.</span></span>

- <span data-ttu-id="adc57-145">可以在已应用索引器的属性名后面的方括号内指定属性的索引器。</span><span class="sxs-lookup"><span data-stu-id="adc57-145">Indexers of a property can be specified within square brackets following the property name where the indexer is applied.</span></span> <span data-ttu-id="adc57-146">例如，子句 `Path=ShoppingCart[0]` 将绑定设置为与属性的内部索引处理文本字符串“0”的方式对应的索引。</span><span class="sxs-lookup"><span data-stu-id="adc57-146">For instance, the clause `Path=ShoppingCart[0]` sets the binding to the index that corresponds to how your property's internal indexing handles the literal string "0".</span></span> <span data-ttu-id="adc57-147">还支持嵌套索引器。</span><span class="sxs-lookup"><span data-stu-id="adc57-147">Nested indexers are also supported.</span></span>

- <span data-ttu-id="adc57-148">可以在 `Path` 子句中混用索引器和子属性，例如 `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`</span><span class="sxs-lookup"><span data-stu-id="adc57-148">Indexers and subproperties can be mixed in a `Path` clause; for example, `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`</span></span>

- <span data-ttu-id="adc57-149">可以在索引器内使用多个由逗号 (,) 分隔的索引器参数。</span><span class="sxs-lookup"><span data-stu-id="adc57-149">Inside indexers you can have multiple indexer parameters separated by commas (,).</span></span> <span data-ttu-id="adc57-150">可以使用括号指定每个参数的类型。</span><span class="sxs-lookup"><span data-stu-id="adc57-150">The type of each parameter can be specified with parentheses.</span></span> <span data-ttu-id="adc57-151">例如，可以使用 `Path="[(sys:Int32)42,(sys:Int32)24]"`，其中 `sys` 将映射到 `System` 命名空间。</span><span class="sxs-lookup"><span data-stu-id="adc57-151">For example, you can have `Path="[(sys:Int32)42,(sys:Int32)24]"`, where `sys` is mapped to the `System` namespace.</span></span>

- <span data-ttu-id="adc57-152">如果源是集合视图，则可以使用斜杠 (/) 指定当前项。</span><span class="sxs-lookup"><span data-stu-id="adc57-152">When the source is a collection view, the current item can be specified with a slash (/).</span></span> <span data-ttu-id="adc57-153">例如，子句 `Path=/` 设置与视图中当前项的绑定。</span><span class="sxs-lookup"><span data-stu-id="adc57-153">For example, the clause `Path=/` sets the binding to the current item in the view.</span></span> <span data-ttu-id="adc57-154">如果源是集合，则此语法指定默认集合视图的当前项。</span><span class="sxs-lookup"><span data-stu-id="adc57-154">When the source is a collection, this syntax specifies the current item of the default collection view.</span></span>

- <span data-ttu-id="adc57-155">可以组合使用属性名和斜杠，以遍历作为集合的属性。</span><span class="sxs-lookup"><span data-stu-id="adc57-155">Property names and slashes can be combined to traverse properties that are collections.</span></span> <span data-ttu-id="adc57-156">例如，`Path=/Offices/ManagerName` 指定源集合的当前项，源集合中包含的 `Offices` 属性也是一个集合。</span><span class="sxs-lookup"><span data-stu-id="adc57-156">For example, `Path=/Offices/ManagerName` specifies the current item of the source collection, which contains an `Offices` property that is also a collection.</span></span> <span data-ttu-id="adc57-157">它的当前项是一个包含 `ManagerName` 属性的对象。</span><span class="sxs-lookup"><span data-stu-id="adc57-157">Its current item is an object that contains a `ManagerName` property.</span></span>

- <span data-ttu-id="adc57-158">句点 (.) 路径也可以用于绑定到当前源。</span><span class="sxs-lookup"><span data-stu-id="adc57-158">Optionally, a period (.) path can be used to bind to the current source.</span></span> <span data-ttu-id="adc57-159">例如，`Text="{Binding}"` 与 `Text="{Binding Path=.}"` 等效。</span><span class="sxs-lookup"><span data-stu-id="adc57-159">For example, `Text="{Binding}"` is equivalent to `Text="{Binding Path=.}"`.</span></span>

### <a name="escaping-mechanism"></a><span data-ttu-id="adc57-160">转义机制</span><span class="sxs-lookup"><span data-stu-id="adc57-160">Escaping Mechanism</span></span>

- <span data-ttu-id="adc57-161">在索引器 ([ ]) 内部，脱字符号 (^) 用于对下一个字符进行转义。</span><span class="sxs-lookup"><span data-stu-id="adc57-161">Inside indexers ([ ]), the caret character (^) escapes the next character.</span></span>

- <span data-ttu-id="adc57-162">如果 <xref:System.Windows.Data.Binding.Path%2A> 在 XAML 中设置，还需要对 xml 语言定义的特殊字符进行转义（使用 xml 实体）：</span><span class="sxs-lookup"><span data-stu-id="adc57-162">If you set <xref:System.Windows.Data.Binding.Path%2A> in XAML, you also need to escape (using XML entities) certain characters that are special to the XML language definition:</span></span>

  - <span data-ttu-id="adc57-163">使用 `&amp;` 对字符“&”进行转义。</span><span class="sxs-lookup"><span data-stu-id="adc57-163">Use `&amp;` to escape the character "&".</span></span>

  - <span data-ttu-id="adc57-164">使用 `&gt;` 对结束标记“>”进行转义。</span><span class="sxs-lookup"><span data-stu-id="adc57-164">Use `&gt;` to escape the end tag ">".</span></span>

- <span data-ttu-id="adc57-165">此外，如果在属性中使用标记扩展语法描述整个绑定，需要（使用反斜杠 \\）对 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 标记扩展分析器专用的字符进行转义：</span><span class="sxs-lookup"><span data-stu-id="adc57-165">Additionally, if you describe the entire binding in an attribute using the markup extension syntax, you need to escape (using backslash \\) characters that are special to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] markup extension parser:</span></span>

  - <span data-ttu-id="adc57-166">反斜杠 (\\) 本身是转义字符。</span><span class="sxs-lookup"><span data-stu-id="adc57-166">Backslash (\\) is the escape character itself.</span></span>

  - <span data-ttu-id="adc57-167">等号 (=) 将属性名与属性值分隔开。</span><span class="sxs-lookup"><span data-stu-id="adc57-167">The equal sign (=) separates property name from property value.</span></span>

  - <span data-ttu-id="adc57-168">逗号 (,) 用于分隔属性。</span><span class="sxs-lookup"><span data-stu-id="adc57-168">Comma (,) separates properties.</span></span>

  - <span data-ttu-id="adc57-169">右大括号 (}) 是标记扩展的结尾。</span><span class="sxs-lookup"><span data-stu-id="adc57-169">The right curly brace (}) is the end of a markup extension.</span></span>

<a name="Default"></a>

## <a name="default-behaviors"></a><span data-ttu-id="adc57-170">默认行为</span><span class="sxs-lookup"><span data-stu-id="adc57-170">Default Behaviors</span></span>

<span data-ttu-id="adc57-171">如果未在声明中指定默认行为，则默认行为如下所示。</span><span class="sxs-lookup"><span data-stu-id="adc57-171">The default behavior is as follows if not specified in the declaration.</span></span>

- <span data-ttu-id="adc57-172">创建一个默认转换器，尝试在绑定源值和绑定目标值之间执行类型转换。</span><span class="sxs-lookup"><span data-stu-id="adc57-172">A default converter is created that tries to do a type conversion between the binding source value and the binding target value.</span></span> <span data-ttu-id="adc57-173">如果不能进行转换，默认转换器会返回 `null`。</span><span class="sxs-lookup"><span data-stu-id="adc57-173">If a conversion cannot be made, the default converter returns `null`.</span></span>

- <span data-ttu-id="adc57-174">如果未设置，则 <xref:System.Windows.Data.Binding.ConverterCulture%2A> 绑定引擎将使用 `Language` 绑定目标对象的属性。</span><span class="sxs-lookup"><span data-stu-id="adc57-174">If you do not set <xref:System.Windows.Data.Binding.ConverterCulture%2A>, the binding engine uses the `Language` property of the binding target object.</span></span> <span data-ttu-id="adc57-175">在 XAML 中，此属性默认为“en-US”，如果已显式设置了一个值，则从页面的根元素（或任何元素）继承该值。</span><span class="sxs-lookup"><span data-stu-id="adc57-175">In XAML, this defaults to "en-US" or inherits the value from the root element (or any element) of the page, if one has been explicitly set.</span></span>

- <span data-ttu-id="adc57-176">只要绑定已具有数据上下文（例如，来自父元素的继承数据上下文），并且该上下文返回的任何项或集合无需进一步修改路径即适用于绑定，则绑定声明可以不必使用任何子句：`{Binding}`。这通常是为数据样式指定绑定所用的方法，其中该绑定作用于某个集合。</span><span class="sxs-lookup"><span data-stu-id="adc57-176">As long as the binding already has a data context (for instance, the inherited data context coming from a parent element), and whatever item or collection being returned by that context is appropriate for binding without requiring further path modification, a binding declaration can have no clauses at all: `{Binding}` This is often the way a binding is specified for data styling, where the binding acts upon a collection.</span></span> <span data-ttu-id="adc57-177">有关详细信息，请参阅[绑定源概述](binding-sources-overview.md)中的“整个对象用作绑定源”一节。</span><span class="sxs-lookup"><span data-stu-id="adc57-177">For more information, see the "Entire Objects Used as a Binding Source" section in the [Binding Sources Overview](binding-sources-overview.md).</span></span>

- <span data-ttu-id="adc57-178">根据所 <xref:System.Windows.Data.Binding.Mode%2A> 绑定的依赖属性，默认值不同于单向和双向。</span><span class="sxs-lookup"><span data-stu-id="adc57-178">The default <xref:System.Windows.Data.Binding.Mode%2A> varies between one-way and two-way depending on the dependency property that is being bound.</span></span> <span data-ttu-id="adc57-179">始终可以显式声明绑定模式，以确保绑定具有所需行为。</span><span class="sxs-lookup"><span data-stu-id="adc57-179">You can always declare the binding mode explicitly to ensure that your binding has the desired behavior.</span></span> <span data-ttu-id="adc57-180">通常，用户可编辑的控件属性（如 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType> ）默认为双向绑定，而其他大多数属性默认为单向绑定。</span><span class="sxs-lookup"><span data-stu-id="adc57-180">In general, user-editable control properties, such as <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>, default to two-way bindings, whereas most other properties default to one-way bindings.</span></span>

- <span data-ttu-id="adc57-181">默认 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> 在和之间也不同， <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> 具体取决于绑定的依赖项属性。</span><span class="sxs-lookup"><span data-stu-id="adc57-181">The default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value varies between <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> and <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> depending on the bound dependency property as well.</span></span> <span data-ttu-id="adc57-182">大多数依赖属性的默认值为 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>，而 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> 属性的默认值为 <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>。</span><span class="sxs-lookup"><span data-stu-id="adc57-182">The default value for most dependency properties is <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, while the <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> property has a default value of <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span></span>

## <a name="see-also"></a><span data-ttu-id="adc57-183">请参阅</span><span class="sxs-lookup"><span data-stu-id="adc57-183">See also</span></span>

- [<span data-ttu-id="adc57-184">数据绑定概述</span><span class="sxs-lookup"><span data-stu-id="adc57-184">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="adc57-185">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="adc57-185">How-to Topics</span></span>](data-binding-how-to-topics.md)
- [<span data-ttu-id="adc57-186">数据绑定</span><span class="sxs-lookup"><span data-stu-id="adc57-186">Data Binding</span></span>](../advanced/optimizing-performance-data-binding.md)
- [<span data-ttu-id="adc57-187">PropertyPath XAML 语法</span><span class="sxs-lookup"><span data-stu-id="adc57-187">PropertyPath XAML Syntax</span></span>](../advanced/propertypath-xaml-syntax.md)
