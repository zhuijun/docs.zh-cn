---
title: 如何：在使用 GridView 的 ListView 中为行的样式
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 4b8b8e2f1b2d7207a37205d981bf2dab3f65122e
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271940"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>如何：为实现 GridView 的 ListView 中的行设置样式
此示例演示如何对使用模式的控件中的行进行样式 <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> 。  
  
## <a name="example"></a>示例  
 <xref:System.Windows.Controls.ListView>通过 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 在控件上设置，可以在控件中设置行的样式 <xref:System.Windows.Controls.ListView> 。 为表示为对象的项设置样式 <xref:System.Windows.Controls.ListViewItem> 。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>引用 <xref:System.Windows.Controls.ControlTemplate> 用于显示行内容的对象。  
  
 下面的示例从中提取的完整示例显示了存储在 XML 数据库中的歌曲信息的集合。 数据库中的每首歌都有一个评级字段，此字段的值指定了歌曲信息行的显示方式。  
  
 下面的示例演示如何为 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ListViewItem> 表示歌曲集中歌曲的对象定义。 用于 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ControlTemplate> 指定如何显示歌曲信息行的引用对象。  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 下面的示例演示了一个 <xref:System.Windows.Controls.ControlTemplate> 向行添加文本字符串的 `"Strongly Recommended"` 。 此模板在中引用 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> ，并显示歌曲的评分值为 5 (五个) 。 <xref:System.Windows.Controls.ControlTemplate>包含一个 <xref:System.Windows.Controls.GridViewRowPresenter> 对象，该对象按照视图模式的定义在列中布局行的内容 <xref:System.Windows.Controls.GridView> 。  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 下面的示例定义 <xref:System.Windows.Controls.GridView> 。  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [操作指南主题](listview-how-to-topics.md)
- [ListView 概述](listview-overview.md)
- [样式设置和模板化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
