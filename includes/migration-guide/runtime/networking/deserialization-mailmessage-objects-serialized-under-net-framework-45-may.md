---
ms.openlocfilehash: ad953a1562db407c04d7860c60eb5964fe6fe2ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619857"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a><span data-ttu-id="5babb-101">在 .NET Framework 4.5 下序列化的 MailMessage 对象进行反序列化可能会失败</span><span class="sxs-lookup"><span data-stu-id="5babb-101">Deserialization of MailMessage objects serialized under the .NET Framework 4.5 may fail</span></span>

#### <a name="details"></a><span data-ttu-id="5babb-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="5babb-102">Details</span></span>

<span data-ttu-id="5babb-103">从 .NET Framework 4.5 开始，<xref:System.Web.Mail.MailMessage> 对象可以包含非 ASCII 字符。</span><span class="sxs-lookup"><span data-stu-id="5babb-103">Starting with the .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objects can include non-ASCII characters.</span></span> <span data-ttu-id="5babb-104">在 .NET Framework 4 中，仅支持 ASCII 字符。</span><span class="sxs-lookup"><span data-stu-id="5babb-104">In the .NET Framework 4, only ASCII characters are supported.</span></span> <span data-ttu-id="5babb-105">包含非 ASCII 字符并在 .NET Framework 4.5 或更高版本下序列化的 <xref:System.Web.Mail.MailMessage> 对象不能在 .NET Framework 4 下进行反序列化。</span><span class="sxs-lookup"><span data-stu-id="5babb-105"><xref:System.Web.Mail.MailMessage> objects that contain non-ASCII characters and that are serialized under the .NET Framework 4.5 or later cannot be deserialized under the .NET Framework 4.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5babb-106">建议</span><span class="sxs-lookup"><span data-stu-id="5babb-106">Suggestion</span></span>

<span data-ttu-id="5babb-107">请确保在反序列化 <xref:System.Web.Mail.MailMessage> 对象时，代码会提供异常处理。</span><span class="sxs-lookup"><span data-stu-id="5babb-107">Ensure that your code provides exception handling when deserializing a <xref:System.Web.Mail.MailMessage> object.</span></span>

| <span data-ttu-id="5babb-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="5babb-108">Name</span></span>    | <span data-ttu-id="5babb-109">“值”</span><span class="sxs-lookup"><span data-stu-id="5babb-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5babb-110">范围</span><span class="sxs-lookup"><span data-stu-id="5babb-110">Scope</span></span>   |<span data-ttu-id="5babb-111">次要</span><span class="sxs-lookup"><span data-stu-id="5babb-111">Minor</span></span>|
|<span data-ttu-id="5babb-112">Version</span><span class="sxs-lookup"><span data-stu-id="5babb-112">Version</span></span>|<span data-ttu-id="5babb-113">4.5</span><span class="sxs-lookup"><span data-stu-id="5babb-113">4.5</span></span>|
|<span data-ttu-id="5babb-114">类型</span><span class="sxs-lookup"><span data-stu-id="5babb-114">Type</span></span>|<span data-ttu-id="5babb-115">运行时</span><span class="sxs-lookup"><span data-stu-id="5babb-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5babb-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="5babb-116">Affected APIs</span></span>

-<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
