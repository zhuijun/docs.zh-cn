---
ms.openlocfilehash: 12fb72d5ee9fc0d6c57899589cb2b0da7db41f4a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496806"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="dd323-101">HttpUtility.JavaScriptStringEncode 转义 & 号</span><span class="sxs-lookup"><span data-stu-id="dd323-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

#### <a name="details"></a><span data-ttu-id="dd323-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="dd323-102">Details</span></span>

<span data-ttu-id="dd323-103">自 .NET Framework 4.5 起，<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> 转义 &amp; 符号。</span><span class="sxs-lookup"><span data-stu-id="dd323-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> escapes the ampersand (&amp;) character.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="dd323-104">建议</span><span class="sxs-lookup"><span data-stu-id="dd323-104">Suggestion</span></span>

<span data-ttu-id="dd323-105">如果应用依赖于此方法以前的行为，可将 aspnet:JavaScriptDoNotEncodeAmpersand 设置添加到配置文件中的 [ASP.NET appSettings 元素](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="dd323-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>

| <span data-ttu-id="dd323-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="dd323-106">Name</span></span>    | <span data-ttu-id="dd323-107">“值”</span><span class="sxs-lookup"><span data-stu-id="dd323-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="dd323-108">范围</span><span class="sxs-lookup"><span data-stu-id="dd323-108">Scope</span></span>   |<span data-ttu-id="dd323-109">次要</span><span class="sxs-lookup"><span data-stu-id="dd323-109">Minor</span></span>|
|<span data-ttu-id="dd323-110">Version</span><span class="sxs-lookup"><span data-stu-id="dd323-110">Version</span></span>|<span data-ttu-id="dd323-111">4.5</span><span class="sxs-lookup"><span data-stu-id="dd323-111">4.5</span></span>|
|<span data-ttu-id="dd323-112">类型</span><span class="sxs-lookup"><span data-stu-id="dd323-112">Type</span></span>|<span data-ttu-id="dd323-113">运行时</span><span class="sxs-lookup"><span data-stu-id="dd323-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="dd323-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="dd323-114">Affected APIs</span></span>

- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String)`
- `M:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)`

-->
