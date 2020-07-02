---
title: 如何：绑定到方法
description: 按照以下示例，了解如何绑定到 Windows Presentation Foundation （WPF）中的对象的方法。
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 9501e6357203c21651e85f1d65059be1d70becf2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619593"
---
# <a name="how-to-bind-to-a-method"></a><span data-ttu-id="5c65a-103">如何：绑定到方法</span><span class="sxs-lookup"><span data-stu-id="5c65a-103">How to: Bind to a Method</span></span>
<span data-ttu-id="5c65a-104">下面的示例演示如何使用绑定到方法 <xref:System.Windows.Data.ObjectDataProvider> 。</span><span class="sxs-lookup"><span data-stu-id="5c65a-104">The following example shows how to bind to a method using <xref:System.Windows.Data.ObjectDataProvider>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c65a-105">示例</span><span class="sxs-lookup"><span data-stu-id="5c65a-105">Example</span></span>  
 <span data-ttu-id="5c65a-106">在本示例中，`TemperatureScale` 是一个具有方法 `ConvertTemp` 的类，该方法接收两个参数（分别为 `double` 和 `enum` 类型的 `TempType)`），并将给定值从一个温标转换为另一个温标。</span><span class="sxs-lookup"><span data-stu-id="5c65a-106">In this example, `TemperatureScale` is a class that has a method `ConvertTemp`, which takes two parameters (one of `double` and one of the `enum` type `TempType)` and converts the given value from one temperature scale to another.</span></span> <span data-ttu-id="5c65a-107">在下面的示例中， <xref:System.Windows.Data.ObjectDataProvider> 使用来实例化 `TemperatureScale` 对象。</span><span class="sxs-lookup"><span data-stu-id="5c65a-107">In the following example, an <xref:System.Windows.Data.ObjectDataProvider> is used to instantiate the `TemperatureScale` object.</span></span> <span data-ttu-id="5c65a-108">将使用两个指定参数调用 `ConvertTemp` 方法。</span><span class="sxs-lookup"><span data-stu-id="5c65a-108">The `ConvertTemp` method is called with two specified parameters.</span></span>  
  
 [!code-xaml[BindToMethod#WindowResources](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 <span data-ttu-id="5c65a-109">现在方法可以作为资源使用，因此可绑定到其结果。</span><span class="sxs-lookup"><span data-stu-id="5c65a-109">Now that the method is available as a resource, you can bind to its results.</span></span> <span data-ttu-id="5c65a-110">在下面的示例中，的 <xref:System.Windows.Controls.TextBox.Text%2A> 和的属性 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> <xref:System.Windows.Controls.ComboBox> 绑定到了方法的两个参数。</span><span class="sxs-lookup"><span data-stu-id="5c65a-110">In the following example, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> of the <xref:System.Windows.Controls.ComboBox> are bound to the two parameters of the method.</span></span> <span data-ttu-id="5c65a-111">这允许用户指定要转换的温度以及要转换自的温标。</span><span class="sxs-lookup"><span data-stu-id="5c65a-111">This allows users to specify the temperature to convert and the temperature scale to convert from.</span></span> <span data-ttu-id="5c65a-112">请注意， <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> 设置为， `true` 因为我们要绑定到 <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> 实例的属性 <xref:System.Windows.Data.ObjectDataProvider> ，而不是由 <xref:System.Windows.Data.ObjectDataProvider> （对象）包装的对象的属性 `TemperatureScale` 。</span><span class="sxs-lookup"><span data-stu-id="5c65a-112">Note that <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> is set to `true` because we are binding to the <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> property of the <xref:System.Windows.Data.ObjectDataProvider> instance and not properties of the object wrapped by the <xref:System.Windows.Data.ObjectDataProvider> (the `TemperatureScale` object).</span></span>  
  
 <span data-ttu-id="5c65a-113"><xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.Label> 当用户修改的内容或所选内容时，最后一次更新的 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.ComboBox> 。</span><span class="sxs-lookup"><span data-stu-id="5c65a-113">The <xref:System.Windows.Controls.ContentControl.Content%2A> of the last <xref:System.Windows.Controls.Label> updates when the user modifies the content of the <xref:System.Windows.Controls.TextBox> or the selection of the <xref:System.Windows.Controls.ComboBox>.</span></span>  
  
 [!code-xaml[BindToMethod#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 <span data-ttu-id="5c65a-114">转换器 `DoubleToString` 使用 double，并按方向将其转换为字符串 <xref:System.Windows.Data.IValueConverter.Convert%2A> （从绑定源到绑定目标，这是 <xref:System.Windows.Controls.TextBox.Text%2A> 属性），并将 `string` `double` 在方向转换为 <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> 。</span><span class="sxs-lookup"><span data-stu-id="5c65a-114">The converter `DoubleToString` takes a double and turns it into a string in the <xref:System.Windows.Data.IValueConverter.Convert%2A> direction (from the binding source to binding target, which is the <xref:System.Windows.Controls.TextBox.Text%2A> property) and converts a `string` to a `double` in the <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> direction.</span></span>  
  
 <span data-ttu-id="5c65a-115">用于 `InvalidationCharacterRule` <xref:System.Windows.Controls.ValidationRule> 检查无效字符的。</span><span class="sxs-lookup"><span data-stu-id="5c65a-115">The `InvalidationCharacterRule` is a <xref:System.Windows.Controls.ValidationRule> that checks for invalid characters.</span></span> <span data-ttu-id="5c65a-116">默认错误模板为周围的红色边框 <xref:System.Windows.Controls.TextBox> ，当输入值不是双精度值时，将显示通知用户。</span><span class="sxs-lookup"><span data-stu-id="5c65a-116">The default error template, which is a red border around the <xref:System.Windows.Controls.TextBox>, appears to notify users when the input value is not a double value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c65a-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="5c65a-117">See also</span></span>

- [<span data-ttu-id="5c65a-118">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="5c65a-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
- [<span data-ttu-id="5c65a-119">绑定到枚举</span><span class="sxs-lookup"><span data-stu-id="5c65a-119">Bind to an Enumeration</span></span>](how-to-bind-to-an-enumeration.md)
