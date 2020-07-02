---
title: 如何：绑定到集合并基于选择显示信息
description: 按照以下示例，了解如何绑定到集合并基于 Windows Presentation Foundation （WPF）中的选定内容显示信息。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
ms.openlocfilehash: fb8757ee6818a2812308a0a132fa9d06951ad52e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619606"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="7155c-103">如何：绑定到集合并基于选择显示信息</span><span class="sxs-lookup"><span data-stu-id="7155c-103">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="7155c-104">在简单的主-从方案中，有一个数据绑定， <xref:System.Windows.Controls.ItemsControl> 如 <xref:System.Windows.Controls.ListBox> 。</span><span class="sxs-lookup"><span data-stu-id="7155c-104">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="7155c-105">根据用户选择，将显示有关所选项目的详细信息。</span><span class="sxs-lookup"><span data-stu-id="7155c-105">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="7155c-106">此示例演示如何实现此方案。</span><span class="sxs-lookup"><span data-stu-id="7155c-106">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7155c-107">示例</span><span class="sxs-lookup"><span data-stu-id="7155c-107">Example</span></span>  
 <span data-ttu-id="7155c-108">在此示例中， `People` 是 <xref:System.Collections.ObjectModel.ObservableCollection%601> `Person` 类的。</span><span class="sxs-lookup"><span data-stu-id="7155c-108">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="7155c-109">此 `Person` 类包含三个属性： `FirstName` 、 `LastName` 和 `HomeTown` ，均为类型 `string` 。</span><span class="sxs-lookup"><span data-stu-id="7155c-109">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="7155c-110"><xref:System.Windows.Controls.ContentControl>使用以下 <xref:System.Windows.DataTemplate> 内容来定义信息的 `Person` 显示方式：</span><span class="sxs-lookup"><span data-stu-id="7155c-110">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="7155c-111">下面是此示例生成内容的屏幕截图。</span><span class="sxs-lookup"><span data-stu-id="7155c-111">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="7155c-112"><xref:System.Windows.Controls.ContentControl>显示选定人员的其他属性。</span><span class="sxs-lookup"><span data-stu-id="7155c-112">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="7155c-113">![绑定到集合](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="7155c-113">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="7155c-114">在此示例中，需要注意以下两个事项：</span><span class="sxs-lookup"><span data-stu-id="7155c-114">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="7155c-115"><xref:System.Windows.Controls.ListBox>和 <xref:System.Windows.Controls.ContentControl> 绑定到同一个源。</span><span class="sxs-lookup"><span data-stu-id="7155c-115">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="7155c-116"><xref:System.Windows.Data.Binding.Path%2A>未指定这两个绑定的属性，因为这两个控件都绑定到整个集合对象。</span><span class="sxs-lookup"><span data-stu-id="7155c-116">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2. <span data-ttu-id="7155c-117">必须将属性设置 <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> 为，才能 `true` 使此操作生效。</span><span class="sxs-lookup"><span data-stu-id="7155c-117">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="7155c-118">设置此属性可确保所选项始终设置为 <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A> 。</span><span class="sxs-lookup"><span data-stu-id="7155c-118">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="7155c-119">或者，如果 <xref:System.Windows.Controls.ListBox> 从获取数据 <xref:System.Windows.Data.CollectionViewSource> ，则会自动同步选定内容和货币。</span><span class="sxs-lookup"><span data-stu-id="7155c-119">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="7155c-120">请注意， `Person` 类 `ToString` 将按以下方式重写方法。</span><span class="sxs-lookup"><span data-stu-id="7155c-120">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="7155c-121">默认情况下， <xref:System.Windows.Controls.ListBox> 调用 `ToString` 并显示绑定集合中每个对象的字符串表示形式。</span><span class="sxs-lookup"><span data-stu-id="7155c-121">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="7155c-122">这就是为什么每个都 `Person` 显示为中的 <xref:System.Windows.Controls.ListBox> 名字。</span><span class="sxs-lookup"><span data-stu-id="7155c-122">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="7155c-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="7155c-123">See also</span></span>

- [<span data-ttu-id="7155c-124">对分层数据使用主-从模式</span><span class="sxs-lookup"><span data-stu-id="7155c-124">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="7155c-125">对分层 XML 数据使用主-从模式</span><span class="sxs-lookup"><span data-stu-id="7155c-125">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="7155c-126">数据绑定概述</span><span class="sxs-lookup"><span data-stu-id="7155c-126">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="7155c-127">数据模板化概述</span><span class="sxs-lookup"><span data-stu-id="7155c-127">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="7155c-128">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="7155c-128">How-to Topics</span></span>](data-binding-how-to-topics.md)
