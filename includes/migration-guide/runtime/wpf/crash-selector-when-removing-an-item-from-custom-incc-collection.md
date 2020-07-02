---
ms.openlocfilehash: 6da589057cebfbf3f67a46b8d49d3a61f037c4c7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622227"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a><span data-ttu-id="972da-101">从自定义 INCC 集合删除项时选择器出现故障</span><span class="sxs-lookup"><span data-stu-id="972da-101">Crash in Selector when removing an item from a custom INCC collection</span></span>

#### <a name="details"></a><span data-ttu-id="972da-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="972da-102">Details</span></span>

<span data-ttu-id="972da-103"><code>T:System.InvalidOperationException</code> 会在以下方案中发生：</span><span class="sxs-lookup"><span data-stu-id="972da-103">An <code>T:System.InvalidOperationException</code> can occur in the following scenario:</span></span><ul><li><span data-ttu-id="972da-104"><code>T:System.Windows.Controls.Primitives.Selector</code> 的 ItemsSource 是 <code>T:System.Collections.Specialized.INotifyCollectionChanged</code> 自定义实现的集合。</span><span class="sxs-lookup"><span data-stu-id="972da-104">The ItemsSource for a <code>T:System.Windows.Controls.Primitives.Selector</code> is a collection with a custom implementation of <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</span></span></li><li><span data-ttu-id="972da-105">从集合中删除所选的项。</span><span class="sxs-lookup"><span data-stu-id="972da-105">The selected item is removed from the collection.</span></span></li><li><span data-ttu-id="972da-106"><code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> 中 <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1（表示未知位置）。</span><span class="sxs-lookup"><span data-stu-id="972da-106">The <code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> has <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (indicating an unknown position).</span></span></li></ul><span data-ttu-id="972da-107">异常的调用堆栈开始于 System.Windows.Threading.Dispatcher.VerifyAccess()、System.Windows.DependencyObject.GetValue(DependencyProperty dp)、System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject element)。如果应用程序的 Dispatcher 线程不止一个，则 .NET Framework 4.5 中可能发生此异常。</span><span class="sxs-lookup"><span data-stu-id="972da-107">The exception's callstack begins at System.Windows.Threading.Dispatcher.VerifyAccess() at System.Windows.DependencyObject.GetValue(DependencyProperty dp) at System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject element)This exception can occur in .NET Framework 4.5 if the application has more than one Dispatcher thread.</span></span> <span data-ttu-id="972da-108">在 .NET Framework 4.7 中，也可能在具有单个 Dispatcher 线程的应用程序中发生该异常。</span><span class="sxs-lookup"><span data-stu-id="972da-108">In .NET Framework 4.7 the exception can also occur in applications with a single Dispatcher thread.</span></span> <span data-ttu-id="972da-109">此问题已在 .NET Framework 4.7.1 中解决。</span><span class="sxs-lookup"><span data-stu-id="972da-109">The issue is fixed in .NET Framework 4.7.1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="972da-110">建议</span><span class="sxs-lookup"><span data-stu-id="972da-110">Suggestion</span></span>

<span data-ttu-id="972da-111">升级到 .NET Framework 4.7.1。</span><span class="sxs-lookup"><span data-stu-id="972da-111">Upgrade to .NET Framework 4.7.1.</span></span>

| <span data-ttu-id="972da-112">“属性”</span><span class="sxs-lookup"><span data-stu-id="972da-112">Name</span></span>    | <span data-ttu-id="972da-113">值</span><span class="sxs-lookup"><span data-stu-id="972da-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="972da-114">范围</span><span class="sxs-lookup"><span data-stu-id="972da-114">Scope</span></span>   |<span data-ttu-id="972da-115">次要</span><span class="sxs-lookup"><span data-stu-id="972da-115">Minor</span></span>|
|<span data-ttu-id="972da-116">Version</span><span class="sxs-lookup"><span data-stu-id="972da-116">Version</span></span>|<span data-ttu-id="972da-117">4.7</span><span class="sxs-lookup"><span data-stu-id="972da-117">4.7</span></span>|
|<span data-ttu-id="972da-118">类型</span><span class="sxs-lookup"><span data-stu-id="972da-118">Type</span></span>|<span data-ttu-id="972da-119">运行时</span><span class="sxs-lookup"><span data-stu-id="972da-119">Runtime</span></span>|
