---
ms.openlocfilehash: d587e542a72d584502ac3ac892619cc38b88ef77
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619819"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="089af-101">HttpUtility.JavaScriptStringEncode 转义 & 号</span><span class="sxs-lookup"><span data-stu-id="089af-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

#### <a name="details"></a><span data-ttu-id="089af-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="089af-102">Details</span></span>

<span data-ttu-id="089af-103">自 .NET Framework 4.5 起，<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> 转义 &amp; 符号。</span><span class="sxs-lookup"><span data-stu-id="089af-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> escapes the ampersand (&amp;) character.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="089af-104">建议</span><span class="sxs-lookup"><span data-stu-id="089af-104">Suggestion</span></span>

<span data-ttu-id="089af-105">如果应用依赖于此方法以前的行为，可将 aspnet:JavaScriptDoNotEncodeAmpersand 设置添加到配置文件中的 [ASP.NET appSettings 元素](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="089af-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>

| <span data-ttu-id="089af-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="089af-106">Name</span></span>    | <span data-ttu-id="089af-107">“值”</span><span class="sxs-lookup"><span data-stu-id="089af-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="089af-108">范围</span><span class="sxs-lookup"><span data-stu-id="089af-108">Scope</span></span>   |<span data-ttu-id="089af-109">次要</span><span class="sxs-lookup"><span data-stu-id="089af-109">Minor</span></span>|
|<span data-ttu-id="089af-110">Version</span><span class="sxs-lookup"><span data-stu-id="089af-110">Version</span></span>|<span data-ttu-id="089af-111">4.5</span><span class="sxs-lookup"><span data-stu-id="089af-111">4.5</span></span>|
|<span data-ttu-id="089af-112">类型</span><span class="sxs-lookup"><span data-stu-id="089af-112">Type</span></span>|<span data-ttu-id="089af-113">运行时</span><span class="sxs-lookup"><span data-stu-id="089af-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="089af-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="089af-114">Affected APIs</span></span>

-<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
