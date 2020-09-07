---
ms.openlocfilehash: eb5c032a020799fa19cc0a8cfaabb56e01417ff4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496387"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a><span data-ttu-id="78213-101">ContentDisposition DateTimes 返回稍微不同的字符串</span><span class="sxs-lookup"><span data-stu-id="78213-101">ContentDisposition DateTimes returns slightly different string</span></span>

#### <a name="details"></a><span data-ttu-id="78213-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="78213-102">Details</span></span>

<span data-ttu-id="78213-103">从 4.6 开始，已更新 <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName> 的字符串表示形式，以始终使用两位数表示 <xref:System.DateTime?displayProperty=fullName> 的小时部分。</span><span class="sxs-lookup"><span data-stu-id="78213-103">String representations of <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName>'s have been updated, beginning in 4.6, to always represent the hour component of a <xref:System.DateTime?displayProperty=fullName> with two digits.</span></span> <span data-ttu-id="78213-104">这是为了符合 [RFC822](https://www.ietf.org/rfc/rfc0822.txt) 和 [RFC2822](https://www.ietf.org/rfc/rfc2822.txt)。</span><span class="sxs-lookup"><span data-stu-id="78213-104">This is to comply with [RFC822](https://www.ietf.org/rfc/rfc0822.txt) and [RFC2822](https://www.ietf.org/rfc/rfc2822.txt).</span></span> <span data-ttu-id="78213-105">这将导致在 4.6 中，当其中一个处理时间元素早于上午 10 点时，<xref:System.Net.Mime.ContentDisposition.ToString> 将返回稍微不同的字符串。</span><span class="sxs-lookup"><span data-stu-id="78213-105">This causes <xref:System.Net.Mime.ContentDisposition.ToString> to return a slightly different string in 4.6 in scenarios where one of the disposition's time elements was before 10:00 AM.</span></span> <span data-ttu-id="78213-106">请注意，ContentDispositions 有时通过将它们转换为字符串以进行序列化，因此应检查任何 <xref:System.Net.Mime.ContentDisposition.ToString> 操作、序列化或 GetHashCode 调用。</span><span class="sxs-lookup"><span data-stu-id="78213-106">Note that ContentDispositions are sometimes serialized via converting them to strings, so any <xref:System.Net.Mime.ContentDisposition.ToString> operations, serialization, or GetHashCode calls should be reviewed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="78213-107">建议</span><span class="sxs-lookup"><span data-stu-id="78213-107">Suggestion</span></span>

<span data-ttu-id="78213-108">不要期望不同 .NET Framework 版本的 ContentDispositions 的字符串表示形式相互进行正确比较。</span><span class="sxs-lookup"><span data-stu-id="78213-108">Do not expect that string representations of ContentDispositions from different .NET Framework versions will correctly compare to one another.</span></span> <span data-ttu-id="78213-109">如果可以，请在执行比较前将字符串转换回 ContentDispositions。</span><span class="sxs-lookup"><span data-stu-id="78213-109">Convert the strings back to ContentDispositions, if possible, before conducting a comparison.</span></span>

| <span data-ttu-id="78213-110">名称</span><span class="sxs-lookup"><span data-stu-id="78213-110">Name</span></span>    | <span data-ttu-id="78213-111">值</span><span class="sxs-lookup"><span data-stu-id="78213-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="78213-112">范围</span><span class="sxs-lookup"><span data-stu-id="78213-112">Scope</span></span>   |<span data-ttu-id="78213-113">次要</span><span class="sxs-lookup"><span data-stu-id="78213-113">Minor</span></span>|
|<span data-ttu-id="78213-114">Version</span><span class="sxs-lookup"><span data-stu-id="78213-114">Version</span></span>|<span data-ttu-id="78213-115">4.6</span><span class="sxs-lookup"><span data-stu-id="78213-115">4.6</span></span>|
|<span data-ttu-id="78213-116">类型</span><span class="sxs-lookup"><span data-stu-id="78213-116">Type</span></span>|<span data-ttu-id="78213-117">运行时</span><span class="sxs-lookup"><span data-stu-id="78213-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="78213-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="78213-118">Affected APIs</span></span>

- <xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType>
- <xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Net.Mime.ContentDisposition.ToString`
- `M:System.Net.Mime.ContentDisposition.GetHashCode`

-->
