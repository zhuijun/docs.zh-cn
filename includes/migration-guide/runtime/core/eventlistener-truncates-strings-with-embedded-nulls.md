---
ms.openlocfilehash: e47a24239872e3fe86ff6902f66b38daaa106598
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497313"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a><span data-ttu-id="eb9cb-101">EventListener 将截断带有嵌入 NULL 的字符串</span><span class="sxs-lookup"><span data-stu-id="eb9cb-101">EventListener truncates strings with embedded nulls</span></span>

#### <a name="details"></a><span data-ttu-id="eb9cb-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="eb9cb-102">Details</span></span>

<span data-ttu-id="eb9cb-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> 将截断带有嵌入的 null 的字符串。</span><span class="sxs-lookup"><span data-stu-id="eb9cb-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> truncates strings with embedded nulls.</span></span> <span data-ttu-id="eb9cb-104">Null 字符不受 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 类支持。</span><span class="sxs-lookup"><span data-stu-id="eb9cb-104">Null characters are not supported by the <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> class.</span></span> <span data-ttu-id="eb9cb-105">此更改仅影响使用 <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> 读取进程中 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 数据的应用以及使用 null 字符串作为分隔符的应用。</span><span class="sxs-lookup"><span data-stu-id="eb9cb-105">The change only affects apps that use <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> to read <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data in process and that use null characters as delimiters.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="eb9cb-106">建议</span><span class="sxs-lookup"><span data-stu-id="eb9cb-106">Suggestion</span></span>

<span data-ttu-id="eb9cb-107">应可能更新 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 数据，以便不使用嵌入的空字符。</span><span class="sxs-lookup"><span data-stu-id="eb9cb-107"><xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data should be updated, if possible, to not use embedded null characters.</span></span>

| <span data-ttu-id="eb9cb-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="eb9cb-108">Name</span></span>    | <span data-ttu-id="eb9cb-109">“值”</span><span class="sxs-lookup"><span data-stu-id="eb9cb-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="eb9cb-110">范围</span><span class="sxs-lookup"><span data-stu-id="eb9cb-110">Scope</span></span>   |<span data-ttu-id="eb9cb-111">边缘</span><span class="sxs-lookup"><span data-stu-id="eb9cb-111">Edge</span></span>|
|<span data-ttu-id="eb9cb-112">Version</span><span class="sxs-lookup"><span data-stu-id="eb9cb-112">Version</span></span>|<span data-ttu-id="eb9cb-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="eb9cb-113">4.5.1</span></span>|
|<span data-ttu-id="eb9cb-114">类型</span><span class="sxs-lookup"><span data-stu-id="eb9cb-114">Type</span></span>|<span data-ttu-id="eb9cb-115">运行时</span><span class="sxs-lookup"><span data-stu-id="eb9cb-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="eb9cb-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="eb9cb-116">Affected APIs</span></span>

- <xref:System.Diagnostics.Tracing.EventListener.%23ctor>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Tracing.EventListener.#ctor`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)`
- `M:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})`

-->
