---
ms.openlocfilehash: 9b184f54650d2efb31ec66f443198b19ceaeb5f3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614346"
---
### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a><span data-ttu-id="67e0e-101">IMessageFilter.PreFilterMessage 的可重入实现不会再引发 Application.FilterMessage</span><span class="sxs-lookup"><span data-stu-id="67e0e-101">Application.FilterMessage no longer throws for re-entrant implementations of IMessageFilter.PreFilterMessage</span></span>

#### <a name="details"></a><span data-ttu-id="67e0e-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="67e0e-102">Details</span></span>

<span data-ttu-id="67e0e-103">在 .NET Framework 4.6.1 之前的版本中，使用调用 <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=fullName> 或 <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=fullName>（同时也调用 <xref:System.Windows.Forms.Application.DoEvents>）的 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> 调用 <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> 可能导致 <xref:System.IndexOutOfRangeException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="67e0e-103">Prior to the .NET Framework 4.6.1, calling <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> with an <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> which called <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=fullName> or <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=fullName> (while also calling <xref:System.Windows.Forms.Application.DoEvents>) would cause an <xref:System.IndexOutOfRangeException?displayProperty=fullName>.</span></span><p/><span data-ttu-id="67e0e-104">从面向 .NET Framework 4.6.1 的应用程序开始，不再引发此异常，并且可能使用上述的可重入筛选器。</span><span class="sxs-lookup"><span data-stu-id="67e0e-104">Beginning with applications targeting the .NET Framework 4.6.1, this exception is no longer thrown, and re-entrant filters as described above may be used.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="67e0e-105">建议</span><span class="sxs-lookup"><span data-stu-id="67e0e-105">Suggestion</span></span>

<span data-ttu-id="67e0e-106">请注意，上述的可重入 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> 行为将不再引发 <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)>。</span><span class="sxs-lookup"><span data-stu-id="67e0e-106">Be aware that <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> will no longer throw for the re-entrant <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> behavior described above.</span></span> <span data-ttu-id="67e0e-107">此更改仅影响面向 .NET Framework 4.6.1 的应用程序。面向 .NET Framework 4.6.1 的应用可使用 [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) 兼容性开关，选择退出此更改（或者面向较早的 Framework 的应用可选择使用此更改）。</span><span class="sxs-lookup"><span data-stu-id="67e0e-107">This only affects applications targeting the .NET Framework 4.6.1.Apps targeting the .NET Framework 4.6.1 can opt out of this change (or apps targeting older Frameworks may opt in) by using the [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) compatibility switch.</span></span>

| <span data-ttu-id="67e0e-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="67e0e-108">Name</span></span>          | <span data-ttu-id="67e0e-109">“值”</span><span class="sxs-lookup"><span data-stu-id="67e0e-109">Value</span></span>       |
|:--------------|:------------|
| <span data-ttu-id="67e0e-110">范围</span><span class="sxs-lookup"><span data-stu-id="67e0e-110">Scope</span></span>         | <span data-ttu-id="67e0e-111">边缘</span><span class="sxs-lookup"><span data-stu-id="67e0e-111">Edge</span></span>        |
| <span data-ttu-id="67e0e-112">Version</span><span class="sxs-lookup"><span data-stu-id="67e0e-112">Version</span></span>       | <span data-ttu-id="67e0e-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="67e0e-113">4.6.1</span></span>       |
| <span data-ttu-id="67e0e-114">类型</span><span class="sxs-lookup"><span data-stu-id="67e0e-114">Type</span></span>          | <span data-ttu-id="67e0e-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="67e0e-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="67e0e-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="67e0e-116">Affected APIs</span></span>

- <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType>
