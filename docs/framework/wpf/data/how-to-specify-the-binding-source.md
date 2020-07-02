---
title: 如何：指定绑定源
description: 了解如何在 Windows Presentation Foundation （WPF）中通过此示例指定绑定源。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 02f27da007ebe8c5985f91b83adfba7d3d00219a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621660"
---
# <a name="how-to-specify-the-binding-source"></a><span data-ttu-id="ded52-103">如何：指定绑定源</span><span class="sxs-lookup"><span data-stu-id="ded52-103">How to: Specify the Binding Source</span></span>
<span data-ttu-id="ded52-104">在数据绑定中，绑定源对象是指从其获取数据的对象。</span><span class="sxs-lookup"><span data-stu-id="ded52-104">In data binding, the binding source object refers to the object you obtain your data from.</span></span> <span data-ttu-id="ded52-105">本主题描述了指定绑定源的不同方法。</span><span class="sxs-lookup"><span data-stu-id="ded52-105">This topic describes the different ways of specifying the binding source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ded52-106">示例</span><span class="sxs-lookup"><span data-stu-id="ded52-106">Example</span></span>  
 <span data-ttu-id="ded52-107">如果要将几个属性绑定到一个通用源，则需要使用 `DataContext` 属性，它能让你方便地建立一个范围，所有数据绑定的属性都在该范围中继承通用源。</span><span class="sxs-lookup"><span data-stu-id="ded52-107">If you are binding several properties to a common source, you want to use the `DataContext` property, which provides a convenient way to establish a scope within which all data-bound properties inherit a common source.</span></span>  
  
 <span data-ttu-id="ded52-108">在下面的示例中，数据上下文建立在应用程序的根元素上。</span><span class="sxs-lookup"><span data-stu-id="ded52-108">In the following example, the data context is established on the root element of the application.</span></span> <span data-ttu-id="ded52-109">这允许所有子元素继承该数据上下文。</span><span class="sxs-lookup"><span data-stu-id="ded52-109">This allows all child elements to inherit that data context.</span></span> <span data-ttu-id="ded52-110">绑定的数据来自自定义数据类 `NetIncome`，可通过映射直接引用该类，已为该类分配了 `incomeDataSource` 资源键。</span><span class="sxs-lookup"><span data-stu-id="ded52-110">Data for the binding comes from a custom data class, `NetIncome`, referenced directly through a mapping and given the resource key of `incomeDataSource`.</span></span>  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 <span data-ttu-id="ded52-111">下面的示例展示了 `NetIncome` 类的定义。</span><span class="sxs-lookup"><span data-stu-id="ded52-111">The following example shows the definition of the `NetIncome` class.</span></span>  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
> <span data-ttu-id="ded52-112">以上示例实例化标记中的对象，并将其用作资源。</span><span class="sxs-lookup"><span data-stu-id="ded52-112">The above example instantiates the object in markup and uses it as a resource.</span></span> <span data-ttu-id="ded52-113">如果希望绑定到已在代码中实例化的对象，需要通过编程方式设置 `DataContext` 属性。</span><span class="sxs-lookup"><span data-stu-id="ded52-113">If you want to bind to an object that has already been instantiated in code, you need to set the `DataContext` property programmatically.</span></span> <span data-ttu-id="ded52-114">有关示例，请参阅[使数据可用于 XAML 中的绑定](how-to-make-data-available-for-binding-in-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="ded52-114">For an example, see [Make Data Available for Binding in XAML](how-to-make-data-available-for-binding-in-xaml.md).</span></span>  
  
 <span data-ttu-id="ded52-115">另外，如果希望在个别绑定上显式指定源，可以选择以下选项。</span><span class="sxs-lookup"><span data-stu-id="ded52-115">Alternatively, if you want to specify the source on your individual bindings explicitly, you have the following options.</span></span> <span data-ttu-id="ded52-116">这些选项优先于继承的数据上下文。</span><span class="sxs-lookup"><span data-stu-id="ded52-116">These take precedence over the inherited data context.</span></span>  
  
|<span data-ttu-id="ded52-117">Property</span><span class="sxs-lookup"><span data-stu-id="ded52-117">Property</span></span>|<span data-ttu-id="ded52-118">描述</span><span class="sxs-lookup"><span data-stu-id="ded52-118">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|<span data-ttu-id="ded52-119">使用此属性将源设置为对象的实例。</span><span class="sxs-lookup"><span data-stu-id="ded52-119">You use this property to set the source to an instance of an object.</span></span> <span data-ttu-id="ded52-120">如果不需要建立作用域的功能，其中有多个属性继承相同的数据上下文，则可以使用属性， <xref:System.Windows.Data.Binding.Source%2A> 而不是 `DataContext` 属性。</span><span class="sxs-lookup"><span data-stu-id="ded52-120">If you do not need the functionality of establishing a scope in which several properties inherit the same data context, you can use the <xref:System.Windows.Data.Binding.Source%2A> property instead of the `DataContext` property.</span></span> <span data-ttu-id="ded52-121">有关详细信息，请参阅 <xref:System.Windows.Data.Binding.Source%2A>。</span><span class="sxs-lookup"><span data-stu-id="ded52-121">For more information, see <xref:System.Windows.Data.Binding.Source%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|<span data-ttu-id="ded52-122">当希望指定相对于绑定目标位置的源时，这很有用。</span><span class="sxs-lookup"><span data-stu-id="ded52-122">This is useful when you want to specify the source relative to where your binding target is.</span></span> <span data-ttu-id="ded52-123">当想要将元素的一个属性绑定到同一元素的另一个属性时，或者如果要在样式或模板中定义绑定，则可能需要使用此属性。</span><span class="sxs-lookup"><span data-stu-id="ded52-123">Some common scenarios where you may use this property is when you want to bind one property of your element to another property of the same element or if you are defining a binding in a style or a template.</span></span> <span data-ttu-id="ded52-124">有关详细信息，请参阅 <xref:System.Windows.Data.Binding.RelativeSource%2A>。</span><span class="sxs-lookup"><span data-stu-id="ded52-124">For more information, see <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|<span data-ttu-id="ded52-125">指定一个表示希望绑定到的元素的字符串。</span><span class="sxs-lookup"><span data-stu-id="ded52-125">You specify a string that represents the element you want to bind to.</span></span> <span data-ttu-id="ded52-126">当希望绑定到应用程序上另一个元素的属性时，这很有用。</span><span class="sxs-lookup"><span data-stu-id="ded52-126">This is useful when you want to bind to the property of another element on your application.</span></span> <span data-ttu-id="ded52-127">例如，如果想要使用 <xref:System.Windows.Controls.Slider> 控制应用程序中另一个控件的高度，或者要将控件的绑定到控件的属性，则为 <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> <xref:System.Windows.Controls.ListBox> 。</span><span class="sxs-lookup"><span data-stu-id="ded52-127">For example, if you want to use a <xref:System.Windows.Controls.Slider> to control the height of another control in your application, or if you want to bind the <xref:System.Windows.Controls.ContentControl.Content%2A> of your control to the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property of your <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="ded52-128">有关详细信息，请参阅 <xref:System.Windows.Data.Binding.ElementName%2A>。</span><span class="sxs-lookup"><span data-stu-id="ded52-128">For more information, see <xref:System.Windows.Data.Binding.ElementName%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ded52-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="ded52-129">See also</span></span>

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ded52-130">属性值继承</span><span class="sxs-lookup"><span data-stu-id="ded52-130">Property Value Inheritance</span></span>](../advanced/property-value-inheritance.md)
- [<span data-ttu-id="ded52-131">数据绑定概述</span><span class="sxs-lookup"><span data-stu-id="ded52-131">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="ded52-132">绑定声明概述</span><span class="sxs-lookup"><span data-stu-id="ded52-132">Binding Declarations Overview</span></span>](binding-declarations-overview.md)
- [<span data-ttu-id="ded52-133">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="ded52-133">How-to Topics</span></span>](data-binding-how-to-topics.md)
