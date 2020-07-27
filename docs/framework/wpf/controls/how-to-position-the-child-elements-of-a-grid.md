---
title: 如何：定位网格的子元素
description: 了解如何使用 Windows Presentation Foundation 网格上定义的 get 和 set 方法来定位子元素。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 926d223097dd21dd0292c9523903b4be8aba8ba9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167400"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>如何：定位网格的子元素
此示例演示如何使用在上定义的 get 和 set 方法 <xref:System.Windows.Controls.Grid> 来定位子元素。  
  
## <a name="example"></a>示例  
 下面的示例定义 <xref:System.Windows.Controls.Grid> `grid1` 了包含三列和三行的父元素（）。 子 <xref:System.Windows.Shapes.Rectangle> 元素（ `rect1` ）添加到 <xref:System.Windows.Controls.Grid> 中的列位置0行位置零。 <xref:System.Windows.Controls.Button>元素表示可调用以重定位中的元素的方法 <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Controls.Grid> 。 用户单击按钮时，会激活相关方法。  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 下面的代码隐藏示例处理按钮 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件引发的方法。 该示例将这些方法调用写入到 <xref:System.Windows.Controls.TextBlock> 使用相关 get 方法的元素，以将新属性值输出为字符串。  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 下面是已完成的结果！

 ![屏幕截图描述了一个具有两列的 WPF 用户界面，右侧有一个 3 x 3 网格，左侧有一些按钮用于在网格的列和行之间移动彩色矩形](././media/grid-methods-sample.png)
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Controls.Grid>
- [面板概述](panels-overview.md)
