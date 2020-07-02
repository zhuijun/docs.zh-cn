---
ms.openlocfilehash: 6f5c1ecead4e2f74e621354058aab70bfa1cccb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619833"
---
### <a name="eventlistener-truncates-strings-with-embedded-nulls"></a><span data-ttu-id="614a3-101">EventListener 将截断带有嵌入 NULL 的字符串</span><span class="sxs-lookup"><span data-stu-id="614a3-101">EventListener truncates strings with embedded nulls</span></span>

#### <a name="details"></a><span data-ttu-id="614a3-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="614a3-102">Details</span></span>

<span data-ttu-id="614a3-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> 将截断带有嵌入的 null 的字符串。</span><span class="sxs-lookup"><span data-stu-id="614a3-103"><xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> truncates strings with embedded nulls.</span></span> <span data-ttu-id="614a3-104">Null 字符不受 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 类支持。</span><span class="sxs-lookup"><span data-stu-id="614a3-104">Null characters are not supported by the <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> class.</span></span> <span data-ttu-id="614a3-105">此更改仅影响使用 <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> 读取进程中 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 数据的应用以及使用 null 字符串作为分隔符的应用。</span><span class="sxs-lookup"><span data-stu-id="614a3-105">The change only affects apps that use <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> to read <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data in process and that use null characters as delimiters.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="614a3-106">建议</span><span class="sxs-lookup"><span data-stu-id="614a3-106">Suggestion</span></span>

<span data-ttu-id="614a3-107">应可能更新 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 数据，以便不使用嵌入的空字符。</span><span class="sxs-lookup"><span data-stu-id="614a3-107"><xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data should be updated, if possible, to not use embedded null characters.</span></span>

| <span data-ttu-id="614a3-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="614a3-108">Name</span></span>    | <span data-ttu-id="614a3-109">“值”</span><span class="sxs-lookup"><span data-stu-id="614a3-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="614a3-110">范围</span><span class="sxs-lookup"><span data-stu-id="614a3-110">Scope</span></span>   |<span data-ttu-id="614a3-111">边缘</span><span class="sxs-lookup"><span data-stu-id="614a3-111">Edge</span></span>|
|<span data-ttu-id="614a3-112">Version</span><span class="sxs-lookup"><span data-stu-id="614a3-112">Version</span></span>|<span data-ttu-id="614a3-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="614a3-113">4.5.1</span></span>|
|<span data-ttu-id="614a3-114">类型</span><span class="sxs-lookup"><span data-stu-id="614a3-114">Type</span></span>|<span data-ttu-id="614a3-115">运行时</span><span class="sxs-lookup"><span data-stu-id="614a3-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="614a3-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="614a3-116">Affected APIs</span></span>

-<xref:System.Diagnostics.Tracing.EventListener.%23ctor></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Tracing.EventListener.EnableEvents(System.Diagnostics.Tracing.EventSource,System.Diagnostics.Tracing.EventLevel,System.Diagnostics.Tracing.EventKeywords,System.Collections.Generic.IDictionary{System.String,System.String})?displayProperty=nameWithType></li></ul>|
