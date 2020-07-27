---
title: 如何：使用代码添加事件处理程序
description: 使用此示例来了解如何使用代码将事件处理程序添加到 Windows Presentation Foundation 中的元素，而不是使用 XAML 来声明它。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: b36969f7a65ccbf6c9d03b22767d9eacdc177ad1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166371"
---
# <a name="how-to-add-an-event-handler-using-code"></a>如何：使用代码添加事件处理程序
此示例演示如何使用代码将事件处理程序添加到元素。  
  
 如果要向元素添加一个事件处理程序 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，并且已加载包含该元素的标记页，则必须使用代码添加该处理程序。 或者，如果您正在使用代码完全构建应用程序的元素树，而不使用声明任何元素 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，则可以调用特定的方法将事件处理程序添加到构造的元素树中。  
  
## <a name="example"></a>示例  
 下面的示例将新的添加 <xref:System.Windows.Controls.Button> 到最初在中定义的现有页 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。 代码隐藏文件实现事件处理程序方法，然后将该方法作为的新事件处理程序添加到中 <xref:System.Windows.Controls.Button> 。  
  
 C # 示例使用 `+=` 运算符为事件分配处理程序。 这是用于在公共语言运行时（CLR）事件处理模型中分配处理程序的同一运算符。 Microsoft Visual Basic 不支持将此运算符作为添加事件处理程序的方法。 而是需要以下两种方法之一：  
  
- 结合使用 <xref:System.Windows.UIElement.AddHandler%2A> 方法和 `AddressOf` 运算符来引用事件处理程序实现。  
  
- 在 `Handles` 事件处理程序定义中使用关键字。 此处未显示此方法;请参阅[Visual Basic 和 WPF 事件处理](visual-basic-and-wpf-event-handling.md)。  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> 在初始分析页中添加事件处理程序 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 要简单得多。 在要添加事件处理程序的对象元素中，添加一个与你要处理的事件的名称相匹配的属性。 然后，将该属性的值指定为在该页的代码隐藏文件中定义的事件处理程序方法的名称 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。 有关详细信息，请参阅[XAML 概述（WPF）](../../../desktop-wpf/fundamentals/xaml.md)或[路由事件概述](routed-events-overview.md)。  
  
## <a name="see-also"></a>另请参阅

- [路由事件概述](routed-events-overview.md)
- [操作指南主题](events-how-to-topics.md)
