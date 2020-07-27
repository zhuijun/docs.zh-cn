---
title: 如何：更改光标类型
description: 在 Windows Presentation Foundation 中更改元素和应用程序的鼠标指针光标。 此示例包含 XAML 和代码隐藏文件。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: ce0bc290948a0e52e85f76ceb62a330b49fd87ea
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165968"
---
# <a name="how-to-change-the-cursor-type"></a>如何：更改光标类型
此示例演示如何为 <xref:System.Windows.Input.Cursor> 特定元素和应用程序更改鼠标指针的。  
  
 此示例由一个 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 文件和一个代码隐藏文件组成。  
  
## <a name="example"></a>示例  
 将创建用户界面，其中包含一个 <xref:System.Windows.Controls.ComboBox> 来选择所需的 <xref:System.Windows.Input.Cursor> ，一对 <xref:System.Windows.Controls.RadioButton> 对象用于确定光标更改是仅适用于单个元素还是应用于整个应用程序，以及一个 <xref:System.Windows.Controls.Border> 是新光标应用于的元素。  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 下面的代码将创建一个 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 事件处理程序，当在中更改了游标类型时，将调用此事件处理程序 <xref:System.Windows.Controls.ComboBox> 。  Switch 语句筛选游标名称，并在 <xref:System.Windows.FrameworkElement.Cursor%2A> 名为 DisplayArea 的上设置 <xref:System.Windows.Controls.Border> 属性。 *DisplayArea*  
  
 如果将光标更改设置为 "整个应用程序"，则 <xref:System.Windows.Input.Mouse.OverrideCursor%2A> 属性将设置为 <xref:System.Windows.FrameworkElement.Cursor%2A> 控件的属性 <xref:System.Windows.Controls.Border> 。  这会强制更改整个应用程序的光标。  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>另请参阅

- [输入概述](input-overview.md)
