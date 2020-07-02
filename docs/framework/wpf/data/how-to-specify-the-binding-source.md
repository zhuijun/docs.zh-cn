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
# <a name="how-to-specify-the-binding-source"></a>如何：指定绑定源
在数据绑定中，绑定源对象是指从其获取数据的对象。 本主题描述了指定绑定源的不同方法。  
  
## <a name="example"></a>示例  
 如果要将几个属性绑定到一个通用源，则需要使用 `DataContext` 属性，它能让你方便地建立一个范围，所有数据绑定的属性都在该范围中继承通用源。  
  
 在下面的示例中，数据上下文建立在应用程序的根元素上。 这允许所有子元素继承该数据上下文。 绑定的数据来自自定义数据类 `NetIncome`，可通过映射直接引用该类，已为该类分配了 `incomeDataSource` 资源键。  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 下面的示例展示了 `NetIncome` 类的定义。  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
> 以上示例实例化标记中的对象，并将其用作资源。 如果希望绑定到已在代码中实例化的对象，需要通过编程方式设置 `DataContext` 属性。 有关示例，请参阅[使数据可用于 XAML 中的绑定](how-to-make-data-available-for-binding-in-xaml.md)。  
  
 另外，如果希望在个别绑定上显式指定源，可以选择以下选项。 这些选项优先于继承的数据上下文。  
  
|Property|描述|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|使用此属性将源设置为对象的实例。 如果不需要建立作用域的功能，其中有多个属性继承相同的数据上下文，则可以使用属性， <xref:System.Windows.Data.Binding.Source%2A> 而不是 `DataContext` 属性。 有关详细信息，请参阅 <xref:System.Windows.Data.Binding.Source%2A>。|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|当希望指定相对于绑定目标位置的源时，这很有用。 当想要将元素的一个属性绑定到同一元素的另一个属性时，或者如果要在样式或模板中定义绑定，则可能需要使用此属性。 有关详细信息，请参阅 <xref:System.Windows.Data.Binding.RelativeSource%2A>。|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|指定一个表示希望绑定到的元素的字符串。 当希望绑定到应用程序上另一个元素的属性时，这很有用。 例如，如果想要使用 <xref:System.Windows.Controls.Slider> 控制应用程序中另一个控件的高度，或者要将控件的绑定到控件的属性，则为 <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> <xref:System.Windows.Controls.ListBox> 。 有关详细信息，请参阅 <xref:System.Windows.Data.Binding.ElementName%2A>。|  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [属性值继承](../advanced/property-value-inheritance.md)
- [数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)
- [绑定声明概述](binding-declarations-overview.md)
- [操作指南主题](data-binding-how-to-topics.md)
