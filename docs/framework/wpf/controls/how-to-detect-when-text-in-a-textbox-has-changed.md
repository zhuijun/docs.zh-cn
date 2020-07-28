---
title: 如何：检测 TextBox 中的文本何时更改
description: 了解当 TextBox 控件中的文本在 Windows Presentation Foundation 应用程序中发生更改时，如何使用 TextChanged 事件运行方法。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1e054380a8c77d32e6bb4adbbcb032e531bbefd0
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166222"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="87000-103">如何：检测 TextBox 中的文本何时更改</span><span class="sxs-lookup"><span data-stu-id="87000-103">How to: Detect When Text in a TextBox Has Changed</span></span>

<span data-ttu-id="87000-104">此示例演示一种在 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 控件中的文本发生更改时使用事件执行方法的一种方法 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="87000-104">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>

<span data-ttu-id="87000-105">在包含要监视其更改的控件的代码隐藏类中 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.TextBox> ，插入每当事件激发时要调用的方法 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 。</span><span class="sxs-lookup"><span data-stu-id="87000-105">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="87000-106">此方法的签名必须与委托所需的签名相匹配 <xref:System.Windows.Controls.TextChangedEventHandler> 。</span><span class="sxs-lookup"><span data-stu-id="87000-106">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

<span data-ttu-id="87000-107">只要 <xref:System.Windows.Controls.TextBox> 用户或以编程方式更改控件的内容，就会调用事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="87000-107">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="87000-108">此事件在 <xref:System.Windows.Controls.TextBox> 创建控件时和最初用文本填充时引发。</span><span class="sxs-lookup"><span data-stu-id="87000-108">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

## <a name="example"></a><span data-ttu-id="87000-109">示例</span><span class="sxs-lookup"><span data-stu-id="87000-109">Example</span></span>

<span data-ttu-id="87000-110">在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 定义控件的中 <xref:System.Windows.Controls.TextBox> ， <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 使用与事件处理程序方法名称匹配的值指定特性。</span><span class="sxs-lookup"><span data-stu-id="87000-110">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a><span data-ttu-id="87000-111">示例</span><span class="sxs-lookup"><span data-stu-id="87000-111">Example</span></span>

<span data-ttu-id="87000-112">在包含要监视其更改的控件的代码隐藏类中 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.TextBox> ，插入每当事件激发时要调用的方法 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 。</span><span class="sxs-lookup"><span data-stu-id="87000-112">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="87000-113">此方法的签名必须与委托所需的签名相匹配 <xref:System.Windows.Controls.TextChangedEventHandler> 。</span><span class="sxs-lookup"><span data-stu-id="87000-113">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

<span data-ttu-id="87000-114">只要 <xref:System.Windows.Controls.TextBox> 用户或以编程方式更改控件的内容，就会调用事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="87000-114">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>

> [!NOTE]
> <span data-ttu-id="87000-115">此事件在 <xref:System.Windows.Controls.TextBox> 创建控件时和最初用文本填充时引发。</span><span class="sxs-lookup"><span data-stu-id="87000-115">This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>

<span data-ttu-id="87000-116">注释</span><span class="sxs-lookup"><span data-stu-id="87000-116">Comments</span></span>

## <a name="see-also"></a><span data-ttu-id="87000-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="87000-117">See also</span></span>

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [<span data-ttu-id="87000-118">TextBox 概述</span><span class="sxs-lookup"><span data-stu-id="87000-118">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="87000-119">RichTextBox 概述</span><span class="sxs-lookup"><span data-stu-id="87000-119">RichTextBox Overview</span></span>](richtextbox-overview.md)
