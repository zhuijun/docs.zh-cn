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
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>如何：绑定到集合并基于选择显示信息
在简单的主-从方案中，有一个数据绑定， <xref:System.Windows.Controls.ItemsControl> 如 <xref:System.Windows.Controls.ListBox> 。 根据用户选择，将显示有关所选项目的详细信息。 此示例演示如何实现此方案。  
  
## <a name="example"></a>示例  
 在此示例中， `People` 是 <xref:System.Collections.ObjectModel.ObservableCollection%601> `Person` 类的。 此 `Person` 类包含三个属性： `FirstName` 、 `LastName` 和 `HomeTown` ，均为类型 `string` 。  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl>使用以下 <xref:System.Windows.DataTemplate> 内容来定义信息的 `Person` 显示方式：  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 下面是此示例生成内容的屏幕截图。 <xref:System.Windows.Controls.ContentControl>显示选定人员的其他属性。  
  
 ![绑定到集合](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 在此示例中，需要注意以下两个事项：  
  
1. <xref:System.Windows.Controls.ListBox>和 <xref:System.Windows.Controls.ContentControl> 绑定到同一个源。 <xref:System.Windows.Data.Binding.Path%2A>未指定这两个绑定的属性，因为这两个控件都绑定到整个集合对象。  
  
2. 必须将属性设置 <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> 为，才能 `true` 使此操作生效。 设置此属性可确保所选项始终设置为 <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A> 。 或者，如果 <xref:System.Windows.Controls.ListBox> 从获取数据 <xref:System.Windows.Data.CollectionViewSource> ，则会自动同步选定内容和货币。  
  
 请注意， `Person` 类 `ToString` 将按以下方式重写方法。 默认情况下， <xref:System.Windows.Controls.ListBox> 调用 `ToString` 并显示绑定集合中每个对象的字符串表示形式。 这就是为什么每个都 `Person` 显示为中的 <xref:System.Windows.Controls.ListBox> 名字。  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>请参阅

- [对分层数据使用主-从模式](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [对分层 XML 数据使用主-从模式](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)
- [数据模板化概述](data-templating-overview.md)
- [操作指南主题](data-binding-how-to-topics.md)
