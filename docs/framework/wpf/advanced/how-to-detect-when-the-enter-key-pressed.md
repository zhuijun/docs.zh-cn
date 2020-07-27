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
# <a name="how-to-detect-when-the-enter-key-pressed"></a><span data-ttu-id="15139-104">如何：检测何时按下 Enter 键</span><span class="sxs-lookup"><span data-stu-id="15139-104">How to: Detect When the Enter Key Pressed</span></span>
<span data-ttu-id="15139-105">此示例演示如何检测在 <xref:System.Windows.Input.Key.Enter> 键盘上按下键的时间。</span><span class="sxs-lookup"><span data-stu-id="15139-105">This example shows how to detect when the <xref:System.Windows.Input.Key.Enter> key is pressed on the keyboard.</span></span>  
  
 <span data-ttu-id="15139-106">此示例由一个 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 文件和一个代码隐藏文件组成。</span><span class="sxs-lookup"><span data-stu-id="15139-106">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15139-107">示例</span><span class="sxs-lookup"><span data-stu-id="15139-107">Example</span></span>  
 <span data-ttu-id="15139-108">当用户按下的 <xref:System.Windows.Input.Key.Enter> 键时 <xref:System.Windows.Controls.TextBox> ，文本框中的输入将显示在的另一个区域中 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="15139-108">When the user presses the <xref:System.Windows.Input.Key.Enter> key in the <xref:System.Windows.Controls.TextBox>, the input in the text box appears in another area of the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span>  
  
 <span data-ttu-id="15139-109">以下 XAML 创建用户界面，该用户界面由 <xref:System.Windows.Controls.StackPanel> 、 <xref:System.Windows.Controls.TextBlock> 和组成 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="15139-109">The following XAML creates the user interface, which consists of a <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.TextBlock>, and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 <span data-ttu-id="15139-110">下面的代码将创建 <xref:System.Windows.UIElement.KeyDown> 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="15139-110">The following code behind creates the <xref:System.Windows.UIElement.KeyDown> event handler.</span></span>  <span data-ttu-id="15139-111">如果按下的键是 <xref:System.Windows.Input.Key.Enter> 键，则会在中显示一条消息 <xref:System.Windows.Controls.TextBlock> 。</span><span class="sxs-lookup"><span data-stu-id="15139-111">If the key that is pressed is the <xref:System.Windows.Input.Key.Enter> key, a message is displayed in the <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a><span data-ttu-id="15139-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="15139-112">See also</span></span>

- [<span data-ttu-id="15139-113">输入概述</span><span class="sxs-lookup"><span data-stu-id="15139-113">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="15139-114">路由事件概述</span><span class="sxs-lookup"><span data-stu-id="15139-114">Routed Events Overview</span></span>](routed-events-overview.md)
