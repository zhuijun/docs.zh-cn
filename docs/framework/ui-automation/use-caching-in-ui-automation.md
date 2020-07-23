---
title: 在 UI 自动化中使用缓存
description: 请参阅如何在 UI 自动化中使用缓存。 查看用于激活缓存请求、缓存 AutomationElement 属性和获取缓存模式的步骤。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: 8dff9db77e39dc66a16b6a7b395c76a3c768d48e
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924482"
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="b6c18-104">在 UI 自动化中使用缓存</span><span class="sxs-lookup"><span data-stu-id="b6c18-104">Use Caching in UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="b6c18-105">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="b6c18-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b6c18-106">有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="b6c18-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="b6c18-107">本部分演示如何实现 <xref:System.Windows.Automation.AutomationElement> 属性和控件模式的缓存。</span><span class="sxs-lookup"><span data-stu-id="b6c18-107">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="b6c18-108">激活缓存请求</span><span class="sxs-lookup"><span data-stu-id="b6c18-108">Activate a Cache Request</span></span>  
  
1. <span data-ttu-id="b6c18-109">创建 <xref:System.Windows.Automation.CacheRequest>。</span><span class="sxs-lookup"><span data-stu-id="b6c18-109">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="b6c18-110">使用 <xref:System.Windows.Automation.CacheRequest.Add%2A>指定要缓存的属性和模式。</span><span class="sxs-lookup"><span data-stu-id="b6c18-110">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3. <span data-ttu-id="b6c18-111">通过设置 <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> 属性来指定缓存的范围。</span><span class="sxs-lookup"><span data-stu-id="b6c18-111">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4. <span data-ttu-id="b6c18-112">通过设置 <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> 属性来指定子树视图。</span><span class="sxs-lookup"><span data-stu-id="b6c18-112">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5. <span data-ttu-id="b6c18-113">如果想通过不检索对对象的完全引用来提高效率，请将 <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> 属性设置为 <xref:System.Windows.Automation.AutomationElementMode.None> 。</span><span class="sxs-lookup"><span data-stu-id="b6c18-113">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="b6c18-114">（这将导致无法从那些对象中检索当前值。）</span><span class="sxs-lookup"><span data-stu-id="b6c18-114">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6. <span data-ttu-id="b6c18-115">使用 <xref:System.Windows.Automation.CacheRequest.Activate%2A> 块中的 `using` （ `Using` 在 Microsoft Visual Basic .net 中）激活请求。</span><span class="sxs-lookup"><span data-stu-id="b6c18-115">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="b6c18-116">在获得 <xref:System.Windows.Automation.AutomationElement> 对象或订阅事件后，通过使用 <xref:System.Windows.Automation.CacheRequest.Pop%2A> （如果使用了 <xref:System.Windows.Automation.CacheRequest.Push%2A> ）或处理 <xref:System.Windows.Automation.CacheRequest.Activate%2A>创建的对象来禁用请求。</span><span class="sxs-lookup"><span data-stu-id="b6c18-116">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="b6c18-117">（在 <xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` `Using` Microsoft Visual Basic .net 中的块中使用。</span><span class="sxs-lookup"><span data-stu-id="b6c18-117">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="b6c18-118">缓存 AutomationElement 属性</span><span class="sxs-lookup"><span data-stu-id="b6c18-118">Cache AutomationElement Properties</span></span>  
  
1. <span data-ttu-id="b6c18-119">当 <xref:System.Windows.Automation.CacheRequest> 处于活动状态时，使用 <xref:System.Windows.Automation.AutomationElement> 或 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> 获取 <xref:System.Windows.Automation.AutomationElement.FindAll%2A>对象，或者获取 <xref:System.Windows.Automation.AutomationElement> 并将其作为 <xref:System.Windows.Automation.CacheRequest> 处于活动状态时注册的事件的源。</span><span class="sxs-lookup"><span data-stu-id="b6c18-119">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="b6c18-120">（也可以通过下面的方法创建缓存：将 <xref:System.Windows.Automation.CacheRequest> 传递给 GetUpdatedCache 或 <xref:System.Windows.Automation.TreeWalker> 方法之一。）</span><span class="sxs-lookup"><span data-stu-id="b6c18-120">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="b6c18-121">使用 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> 或从 <xref:System.Windows.Automation.AutomationElement.Cached%2A> 的 <xref:System.Windows.Automation.AutomationElement>属性中检索属性。</span><span class="sxs-lookup"><span data-stu-id="b6c18-121">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="b6c18-122">获取缓存模式及其属性</span><span class="sxs-lookup"><span data-stu-id="b6c18-122">Obtain Cached Patterns and Their Properties</span></span>  
  
1. <span data-ttu-id="b6c18-123">当 <xref:System.Windows.Automation.CacheRequest> 处于活动状态时，使用 <xref:System.Windows.Automation.AutomationElement> 或 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> 获取 <xref:System.Windows.Automation.AutomationElement.FindAll%2A>对象，或者获取 <xref:System.Windows.Automation.AutomationElement> 并将其作为 <xref:System.Windows.Automation.CacheRequest> 处于活动状态时注册的事件的源。</span><span class="sxs-lookup"><span data-stu-id="b6c18-123">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="b6c18-124">（也可以通过下面的方法创建缓存：将 <xref:System.Windows.Automation.CacheRequest> 传递给 GetUpdatedCache 或 <xref:System.Windows.Automation.TreeWalker> 方法之一。）</span><span class="sxs-lookup"><span data-stu-id="b6c18-124">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="b6c18-125">使用 <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> 或 <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> 检索缓存的模式。</span><span class="sxs-lookup"><span data-stu-id="b6c18-125">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3. <span data-ttu-id="b6c18-126">控件模式的 `Cached` 属性中检索属性值。</span><span class="sxs-lookup"><span data-stu-id="b6c18-126">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6c18-127">示例</span><span class="sxs-lookup"><span data-stu-id="b6c18-127">Example</span></span>  
 <span data-ttu-id="b6c18-128">下面的代码示例使用 <xref:System.Windows.Automation.CacheRequest.Activate%2A> 激活 <xref:System.Windows.Automation.CacheRequest>，演示了缓存的各个方面。</span><span class="sxs-lookup"><span data-stu-id="b6c18-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="b6c18-129">示例</span><span class="sxs-lookup"><span data-stu-id="b6c18-129">Example</span></span>  
 <span data-ttu-id="b6c18-130">下面的代码示例使用 <xref:System.Windows.Automation.CacheRequest.Push%2A> 激活 <xref:System.Windows.Automation.CacheRequest>，演示了缓存的各个方面。</span><span class="sxs-lookup"><span data-stu-id="b6c18-130">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="b6c18-131">除非希望嵌套缓存请求，否则最好是使用 <xref:System.Windows.Automation.CacheRequest.Activate%2A>。</span><span class="sxs-lookup"><span data-stu-id="b6c18-131">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="b6c18-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b6c18-132">See also</span></span>

- [<span data-ttu-id="b6c18-133">在 UI 自动化客户端中缓存</span><span class="sxs-lookup"><span data-stu-id="b6c18-133">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
