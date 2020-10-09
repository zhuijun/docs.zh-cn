---
ms.openlocfilehash: 53860bb867522503c5cb9bd35e25fadd00a116a2
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609151"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a><span data-ttu-id="6668c-101">使用 AntiXSSEncoder 时，多行 ASP.NET 文本框间距已更改</span><span class="sxs-lookup"><span data-stu-id="6668c-101">Multi-line ASP.NET TextBox spacing changed when using AntiXSSEncoder</span></span>

#### <a name="details"></a><span data-ttu-id="6668c-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="6668c-102">Details</span></span>

<span data-ttu-id="6668c-103">在 .NET Framework 4.0 中，如果使用 <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>，则多余行将插入回发的多行文本框中的各行之间。</span><span class="sxs-lookup"><span data-stu-id="6668c-103">In .NET Framework 4.0, extra lines were inserted between lines of a multi-line text box on postback, if using the <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>.</span></span> <span data-ttu-id="6668c-104">在 .NET Framework 4.5 中，不包括这些多余的换行符，仅在 Web 应用面向 .NET Framework 4.5 时才可包含</span><span class="sxs-lookup"><span data-stu-id="6668c-104">In .NET Framework 4.5, those extra line breaks are not included, but only if the web app is targeting .NET Framework 4.5</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6668c-105">建议</span><span class="sxs-lookup"><span data-stu-id="6668c-105">Suggestion</span></span>

<span data-ttu-id="6668c-106">请注意，重定向到 .NET Framework 4.5 的 4.0 Web 应用可能改进了多行文本框，从而不再插入多余的换行符。</span><span class="sxs-lookup"><span data-stu-id="6668c-106">Be aware that 4.0 web apps retargeted to .NET Framework 4.5 may have multi-line text boxes improved to no longer insert extra line breaks.</span></span> <span data-ttu-id="6668c-107">如果不需要这样做，当应用在 .NET Framework 4.5 上运行时，通过面向 .NET Framework 4.0 可使用旧行为。</span><span class="sxs-lookup"><span data-stu-id="6668c-107">If this is not desirable, the app  can have the old behavior when running on .NET Framework 4.5 by targeting the .NET Framework 4.0.</span></span>

| <span data-ttu-id="6668c-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="6668c-108">Name</span></span>    | <span data-ttu-id="6668c-109">“值”</span><span class="sxs-lookup"><span data-stu-id="6668c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6668c-110">范围</span><span class="sxs-lookup"><span data-stu-id="6668c-110">Scope</span></span>   | <span data-ttu-id="6668c-111">次要</span><span class="sxs-lookup"><span data-stu-id="6668c-111">Minor</span></span>       |
| <span data-ttu-id="6668c-112">Version</span><span class="sxs-lookup"><span data-stu-id="6668c-112">Version</span></span> | <span data-ttu-id="6668c-113">4.5</span><span class="sxs-lookup"><span data-stu-id="6668c-113">4.5</span></span>         |
| <span data-ttu-id="6668c-114">类型</span><span class="sxs-lookup"><span data-stu-id="6668c-114">Type</span></span>    | <span data-ttu-id="6668c-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="6668c-115">Retargeting</span></span> |
