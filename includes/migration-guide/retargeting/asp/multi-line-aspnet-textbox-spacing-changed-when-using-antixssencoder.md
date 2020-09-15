---
ms.openlocfilehash: 150b98255b3075a8fe8cad60ce234206b788a5f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617121"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a><span data-ttu-id="a27e5-101">使用 AntiXSSEncoder 时，多行 ASP.Net 文本框间距已更改</span><span class="sxs-lookup"><span data-stu-id="a27e5-101">Multi-line ASP.Net TextBox spacing changed when using AntiXSSEncoder</span></span>

#### <a name="details"></a><span data-ttu-id="a27e5-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="a27e5-102">Details</span></span>

<span data-ttu-id="a27e5-103">在 .NET Framework 4.0 中，如果使用 <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>，则多余行将插入回发的多行文本框中的各行之间。</span><span class="sxs-lookup"><span data-stu-id="a27e5-103">In .NET Framework 4.0, extra lines were inserted between lines of a multi-line text box on postback, if using the <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>.</span></span> <span data-ttu-id="a27e5-104">在 .NET Framework 4.5 中，不包括这些多余的换行符，仅在 Web 应用面向 .NET Framework 4.5 时才可包含</span><span class="sxs-lookup"><span data-stu-id="a27e5-104">In .NET Framework 4.5, those extra line breaks are not included, but only if the web app is targeting .NET Framework 4.5</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a27e5-105">建议</span><span class="sxs-lookup"><span data-stu-id="a27e5-105">Suggestion</span></span>

<span data-ttu-id="a27e5-106">请注意，重定向到 .NET Framework 4.5 的 4.0 Web 应用可能改进了多行文本框，从而不再插入多余的换行符。</span><span class="sxs-lookup"><span data-stu-id="a27e5-106">Be aware that 4.0 web apps retargeted to .NET Framework 4.5 may have multi-line text boxes improved to no longer insert extra line breaks.</span></span> <span data-ttu-id="a27e5-107">如果不需要这样做，当应用在 .NET Framework 4.5 上运行时，通过面向 .NET Framework 4.0 可使用旧行为。</span><span class="sxs-lookup"><span data-stu-id="a27e5-107">If this is not desirable, the app  can have the old behavior when running on .NET Framework 4.5 by targeting the .NET Framework 4.0.</span></span>

| <span data-ttu-id="a27e5-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="a27e5-108">Name</span></span>    | <span data-ttu-id="a27e5-109">“值”</span><span class="sxs-lookup"><span data-stu-id="a27e5-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a27e5-110">范围</span><span class="sxs-lookup"><span data-stu-id="a27e5-110">Scope</span></span>   | <span data-ttu-id="a27e5-111">次要</span><span class="sxs-lookup"><span data-stu-id="a27e5-111">Minor</span></span>       |
| <span data-ttu-id="a27e5-112">Version</span><span class="sxs-lookup"><span data-stu-id="a27e5-112">Version</span></span> | <span data-ttu-id="a27e5-113">4.5</span><span class="sxs-lookup"><span data-stu-id="a27e5-113">4.5</span></span>         |
| <span data-ttu-id="a27e5-114">类型</span><span class="sxs-lookup"><span data-stu-id="a27e5-114">Type</span></span>    | <span data-ttu-id="a27e5-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="a27e5-115">Retargeting</span></span> |
