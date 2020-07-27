---
title: 如何：检测何时按下 Enter 键
description: 在 Windows Presentation Foundation 的键盘上选择 "输入密钥" 时进行检测。 此示例包含 XAML 和代码隐藏文件。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: a955f52ec7bf93b32c70259b27fb51747664ac2e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163188"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>如何：检测何时按下 Enter 键
此示例演示如何检测在 <xref:System.Windows.Input.Key.Enter> 键盘上按下键的时间。  
  
 此示例由一个 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 文件和一个代码隐藏文件组成。  
  
## <a name="example"></a>示例  
 当用户按下的 <xref:System.Windows.Input.Key.Enter> 键时 <xref:System.Windows.Controls.TextBox> ，文本框中的输入将显示在的另一个区域中 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 。  
  
 以下 XAML 创建用户界面，该用户界面由 <xref:System.Windows.Controls.StackPanel> 、 <xref:System.Windows.Controls.TextBlock> 和组成 <xref:System.Windows.Controls.TextBox> 。  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 下面的代码将创建 <xref:System.Windows.UIElement.KeyDown> 事件处理程序。  如果按下的键是 <xref:System.Windows.Input.Key.Enter> 键，则会在中显示一条消息 <xref:System.Windows.Controls.TextBlock> 。  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>另请参阅

- [输入概述](input-overview.md)
- [路由事件概述](routed-events-overview.md)
