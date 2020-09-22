---
ms.openlocfilehash: b648aee35ff44730f545f0fa06f4e0a86615dece
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606844"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="cd509-101">HttpUtility.JavaScriptStringEncode 转义 & 号</span><span class="sxs-lookup"><span data-stu-id="cd509-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

#### <a name="details"></a><span data-ttu-id="cd509-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="cd509-102">Details</span></span>

<span data-ttu-id="cd509-103">自 .NET Framework 4.5 起，<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> 转义 &amp; 符号。</span><span class="sxs-lookup"><span data-stu-id="cd509-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> escapes the ampersand (&amp;) character.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cd509-104">建议</span><span class="sxs-lookup"><span data-stu-id="cd509-104">Suggestion</span></span>

<span data-ttu-id="cd509-105">如果应用依赖于此方法以前的行为，可将 aspnet:JavaScriptDoNotEncodeAmpersand 设置添加到配置文件中的 [ASP.NET appSettings 元素](/previous-versions/aspnet/hh975440(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="cd509-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>

| <span data-ttu-id="cd509-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="cd509-106">Name</span></span>    | <span data-ttu-id="cd509-107">“值”</span><span class="sxs-lookup"><span data-stu-id="cd509-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cd509-108">范围</span><span class="sxs-lookup"><span data-stu-id="cd509-108">Scope</span></span>   |<span data-ttu-id="cd509-109">次要</span><span class="sxs-lookup"><span data-stu-id="cd509-109">Minor</span></span>|
|<span data-ttu-id="cd509-110">Version</span><span class="sxs-lookup"><span data-stu-id="cd509-110">Version</span></span>|<span data-ttu-id="cd509-111">4.5</span><span class="sxs-lookup"><span data-stu-id="cd509-111">4.5</span></span>|
|<span data-ttu-id="cd509-112">类型</span><span class="sxs-lookup"><span data-stu-id="cd509-112">Type</span></span>|<span data-ttu-id="cd509-113">运行时</span><span class="sxs-lookup"><span data-stu-id="cd509-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="cd509-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="cd509-114">Affected APIs</span></span>

- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String)`
- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)`

-->
