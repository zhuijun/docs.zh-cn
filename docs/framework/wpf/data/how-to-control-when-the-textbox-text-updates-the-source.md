---
title: 如何：控制文本框文本更新源的时间
description: 使用 Windows Presentation Foundation （WPF）中的 System.windows.data.binding.updatesourcetrigger 属性控制绑定源更新的时间。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source updates [WPF], timing of
- data binding [WPF], timing of source updates
- timing of source updates [WPF]
ms.assetid: ffb7b96a-351d-4c68-81e7-054033781c64
ms.openlocfilehash: 8f6eb5beb0d14a951f6e6cf6eb81e130f5a3e194
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622778"
---
# <a name="how-to-control-when-the-textbox-text-updates-the-source"></a><span data-ttu-id="82259-103">如何：控制文本框文本更新源的时间</span><span class="sxs-lookup"><span data-stu-id="82259-103">How to: Control When the TextBox Text Updates the Source</span></span>
<span data-ttu-id="82259-104">本主题介绍如何使用 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 属性来控制绑定源更新的计时。</span><span class="sxs-lookup"><span data-stu-id="82259-104">This topic describes how to use the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property to control the timing of binding source updates.</span></span> <span data-ttu-id="82259-105">本主题使用 <xref:System.Windows.Controls.TextBox> 控件作为示例。</span><span class="sxs-lookup"><span data-stu-id="82259-105">The topic uses the <xref:System.Windows.Controls.TextBox> control as an example.</span></span>

## <a name="example"></a><span data-ttu-id="82259-106">示例</span><span class="sxs-lookup"><span data-stu-id="82259-106">Example</span></span>
 <span data-ttu-id="82259-107"><xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>属性的默认 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值为 <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> 。</span><span class="sxs-lookup"><span data-stu-id="82259-107">The <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> property has a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span></span> <span data-ttu-id="82259-108">这意味着，如果应用程序具有 <xref:System.Windows.Controls.TextBox> 包含数据绑定属性的 <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> ，则你键入的文本将 <xref:System.Windows.Controls.TextBox> 不会更新源，直到 <xref:System.Windows.Controls.TextBox> 失去焦点为止（例如，当你单击 "离开" 时 <xref:System.Windows.Controls.TextBox> ）。</span><span class="sxs-lookup"><span data-stu-id="82259-108">This means if an application has a <xref:System.Windows.Controls.TextBox> with a data-bound <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> property, the text you type into the <xref:System.Windows.Controls.TextBox> does not update the source until the <xref:System.Windows.Controls.TextBox> loses focus (for instance, when you click away from the <xref:System.Windows.Controls.TextBox>).</span></span>

 <span data-ttu-id="82259-109">如果希望在键入时更新源，请将绑定的设置 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 为 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> 。</span><span class="sxs-lookup"><span data-stu-id="82259-109">If you want the source to be updated as you type, set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> of the binding to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="82259-110">在下面的示例中，突出显示的代码行显示了 `Text` <xref:System.Windows.Controls.TextBox> 和的属性 <xref:System.Windows.Controls.TextBlock> 都绑定到同一个源属性。</span><span class="sxs-lookup"><span data-stu-id="82259-110">In the following example, the highlighted lines of code show that the `Text` properties of both the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.TextBlock> are bound to the same source property.</span></span> <span data-ttu-id="82259-111"><xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>绑定的属性 <xref:System.Windows.Controls.TextBox> 设置为 <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> 。</span><span class="sxs-lookup"><span data-stu-id="82259-111">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property of the <xref:System.Windows.Controls.TextBox> binding is set to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span>

 [!code-xaml[SimpleBinding#USTHowTo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=33-39,41-42)]

 <span data-ttu-id="82259-112">因此，当 <xref:System.Windows.Controls.TextBlock> 用户向中输入文本时，将显示相同的文本（因为源发生更改） <xref:System.Windows.Controls.TextBox> ，如示例的以下屏幕截图所示：</span><span class="sxs-lookup"><span data-stu-id="82259-112">As a result, the <xref:System.Windows.Controls.TextBlock> shows the same text (because the source changes) as the user enters text into the <xref:System.Windows.Controls.TextBox>, as illustrated by the following screenshot of the sample:</span></span>

 ![显示简单数据绑定的屏幕截图。](./media/how-to-control-when-the-textbox-text-updates-the-source/data-binding-simple-binding-sample.png)

 <span data-ttu-id="82259-114">如果您有一个对话框或用户可编辑的窗体，而您希望在用户完成编辑字段并单击 "确定" 之前延迟源更新，则可以将绑定的 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 值设置为 <xref:System.Windows.Data.UpdateSourceTrigger.Explicit> ，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="82259-114">If you have a dialog or a user-editable form and you want to defer source updates until the user is finished editing the fields and clicks "OK", you can set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of your bindings to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, as in the following example:</span></span>

 [!code-xaml[UpdateSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml#2)]

 <span data-ttu-id="82259-115">如果将值设置 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 为 <xref:System.Windows.Data.UpdateSourceTrigger.Explicit> ，则源值仅在应用程序调用方法时才会发生更改 <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> 。</span><span class="sxs-lookup"><span data-stu-id="82259-115">When you set the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value to <xref:System.Windows.Data.UpdateSourceTrigger.Explicit>, the source value only changes when the application calls the <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> method.</span></span> <span data-ttu-id="82259-116">下面的示例演示如何调用 <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> `itemNameTextBox` ：</span><span class="sxs-lookup"><span data-stu-id="82259-116">The following example shows how to call <xref:System.Windows.Data.BindingExpression.UpdateSource%2A> for `itemNameTextBox`:</span></span>

 [!code-csharp[UpdateSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/UpdateSource/CSharp/Window1.xaml.cs#1)]
 [!code-vb[UpdateSource#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UpdateSource/VisualBasic/Window1.xaml.vb#1)]

> [!NOTE]
> <span data-ttu-id="82259-117">您可以为其他控件的属性使用相同的技术，但请记住，大多数其他属性的默认值都是 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> 。</span><span class="sxs-lookup"><span data-stu-id="82259-117">You can use the same technique for properties of other controls, but keep in mind that most other properties have a default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value of <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span> <span data-ttu-id="82259-118">有关详细信息，请参阅 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> 属性页。</span><span class="sxs-lookup"><span data-stu-id="82259-118">For more information, see the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property page.</span></span>

> [!NOTE]
> <span data-ttu-id="82259-119"><xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>属性用于处理源更新，因此仅适用于 <xref:System.Windows.Data.BindingMode.TwoWay> 或 <xref:System.Windows.Data.BindingMode.OneWayToSource> 绑定。</span><span class="sxs-lookup"><span data-stu-id="82259-119">The <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property deals with source updates and therefore is only relevant for <xref:System.Windows.Data.BindingMode.TwoWay> or <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings.</span></span> <span data-ttu-id="82259-120"><xref:System.Windows.Data.BindingMode.TwoWay>要使和 <xref:System.Windows.Data.BindingMode.OneWayToSource> 绑定正常工作，源对象需要提供属性更改通知。</span><span class="sxs-lookup"><span data-stu-id="82259-120">For <xref:System.Windows.Data.BindingMode.TwoWay> and <xref:System.Windows.Data.BindingMode.OneWayToSource> bindings to work, the source object needs to provide property change notifications.</span></span> <span data-ttu-id="82259-121">有关详细信息，可以参见本主题中引用的示例。</span><span class="sxs-lookup"><span data-stu-id="82259-121">You can refer to the samples cited in this topic for more information.</span></span> <span data-ttu-id="82259-122">此外，也可以参见[实现属性更改通知](how-to-implement-property-change-notification.md)。</span><span class="sxs-lookup"><span data-stu-id="82259-122">In addition, you can look at [Implement Property Change Notification](how-to-implement-property-change-notification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="82259-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="82259-123">See also</span></span>

- [<span data-ttu-id="82259-124">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="82259-124">How-to Topics</span></span>](data-binding-how-to-topics.md)
