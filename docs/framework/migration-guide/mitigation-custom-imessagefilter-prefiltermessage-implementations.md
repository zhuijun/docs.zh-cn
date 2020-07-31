---
title: 缓解：自定义 IMessageFilter.PreFilterMessage 实现
description: 了解面向 .NET Framework 4.6.1 及更高版本的 Windows 窗体应用中包含的自定义 IMessageFilter.PreFilterMessage 实现。
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 5fe7500d3ed6ff293514495df150a747e7946dda
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475250"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="c1687-103">缓解：自定义 IMessageFilter.PreFilterMessage 实现</span><span class="sxs-lookup"><span data-stu-id="c1687-103">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="c1687-104">在面向从 .NET Framework 4.6.1 开始的 .NET Framework 版本的 Windows 窗体应用中，如果 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> 实现可以满足以下要求，那么在调用 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> 方法时，自定义实现 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> 可以安全地筛选消息：</span><span class="sxs-lookup"><span data-stu-id="c1687-104">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="c1687-105">执行下列一项或两项操作：</span><span class="sxs-lookup"><span data-stu-id="c1687-105">Does one or both of the following:</span></span>

  - <span data-ttu-id="c1687-106">通过调用 <xref:System.Windows.Forms.Application.AddMessageFilter%2A> 方法添加消息筛选器。</span><span class="sxs-lookup"><span data-stu-id="c1687-106">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="c1687-107">通过调用 <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> 方法，删除消息筛选器。</span><span class="sxs-lookup"><span data-stu-id="c1687-107">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="c1687-108">方法。</span><span class="sxs-lookup"><span data-stu-id="c1687-108">method.</span></span>

- <span data-ttu-id="c1687-109">以及通过调用 <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> 方法抽取消息。</span><span class="sxs-lookup"><span data-stu-id="c1687-109">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="c1687-110">影响</span><span class="sxs-lookup"><span data-stu-id="c1687-110">Impact</span></span>

<span data-ttu-id="c1687-111">此更改仅影响面向从 .NET Framework 4.6.1 开始的 .NET Framework 版本的 Windows 窗体应用。</span><span class="sxs-lookup"><span data-stu-id="c1687-111">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="c1687-112">对于面向以前版本的 .NET framework 的 Windows 窗体应用程序，在调用 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> 方法时，此类实现在某些情况下会引发 <xref:System.IndexOutOfRangeException> 异常</span><span class="sxs-lookup"><span data-stu-id="c1687-112">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="c1687-113">缓解</span><span class="sxs-lookup"><span data-stu-id="c1687-113">Mitigation</span></span>

<span data-ttu-id="c1687-114">如果此更改不可取，面向 .NET Framework 4.6.1 或更高版本的应用可通过将以下配置设置添加到应用配置文件的 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 部分，来选择放弃更改：</span><span class="sxs-lookup"><span data-stu-id="c1687-114">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="c1687-115">此外，面向 .NET Framework 以前版本但在 .NET Framework 4.6.1 或更高版本下运行的应用可通过将以下配置设置添加到应用配置文件的 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 部分，来选择实现此行为：</span><span class="sxs-lookup"><span data-stu-id="c1687-115">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="c1687-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="c1687-116">See also</span></span>

- [<span data-ttu-id="c1687-117">应用程序兼容性</span><span class="sxs-lookup"><span data-stu-id="c1687-117">Application compatibility</span></span>](application-compatibility.md)
