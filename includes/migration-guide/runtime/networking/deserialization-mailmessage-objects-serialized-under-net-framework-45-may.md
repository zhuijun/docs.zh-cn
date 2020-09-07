---
ms.openlocfilehash: 2c44c2e1658f8de556d3f7222de3fa6d4594163a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497926"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="29316-101">在 .NET Framework 4.5 下序列化的 MailMessage 对象进行反序列化可能会失败</span><span class="sxs-lookup"><span data-stu-id="29316-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

#### <a name="details"></a><span data-ttu-id="29316-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="29316-102">Details</span></span>

<span data-ttu-id="29316-103">从 .NET Framework 4.5 开始，<xref:System.Web.Mail.MailMessage> 对象可以包含非 ASCII 字符。</span><span class="sxs-lookup"><span data-stu-id="29316-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="29316-104">在 .NET Framework 4 中，仅支持 ASCII 字符。</span><span class="sxs-lookup"><span data-stu-id="29316-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <span data-ttu-id="29316-105">包含非 ASCII 字符并在 .NET Framework 4.5 或更高版本下序列化的 <xref:System.Web.Mail.MailMessage> 对象不能在 .NET Framework 4 下进行反序列化。</span><span class="sxs-lookup"><span data-stu-id="29316-105"><xref:System.Web.Mail.MailMessage> objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="29316-106">建议</span><span class="sxs-lookup"><span data-stu-id="29316-106">Suggestion</span></span>

<span data-ttu-id="29316-107">请确保在反序列化 <xref:System.Web.Mail.MailMessage> 对象时，代码会提供异常处理。</span><span class="sxs-lookup"><span data-stu-id="29316-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>

| <span data-ttu-id="29316-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="29316-108">Name</span></span>    | <span data-ttu-id="29316-109">“值”</span><span class="sxs-lookup"><span data-stu-id="29316-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="29316-110">范围</span><span class="sxs-lookup"><span data-stu-id="29316-110">Scope</span></span>   |<span data-ttu-id="29316-111">次要</span><span class="sxs-lookup"><span data-stu-id="29316-111">Minor</span></span>|
|<span data-ttu-id="29316-112">Version</span><span class="sxs-lookup"><span data-stu-id="29316-112">Version</span></span>|<span data-ttu-id="29316-113">4.5</span><span class="sxs-lookup"><span data-stu-id="29316-113">4.5</span></span>|
|<span data-ttu-id="29316-114">类型</span><span class="sxs-lookup"><span data-stu-id="29316-114">Type</span></span>|<span data-ttu-id="29316-115">运行时</span><span class="sxs-lookup"><span data-stu-id="29316-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="29316-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="29316-116">Affected APIs</span></span>

- <xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Web.Mail.MailMessage`

-->
