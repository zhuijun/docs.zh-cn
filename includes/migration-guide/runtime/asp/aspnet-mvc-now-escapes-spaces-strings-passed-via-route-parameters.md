---
ms.openlocfilehash: afbf34710c75d0f0586ddfdb2e7937d8d76d5399
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496194"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="49a5b-101">ASP.NET MVC 现在将转义通过路由参数传递的字符串中的空格</span><span class="sxs-lookup"><span data-stu-id="49a5b-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

#### <a name="details"></a><span data-ttu-id="49a5b-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="49a5b-102">Details</span></span>

<span data-ttu-id="49a5b-103">为了遵守 RFC 2396，从路由中填充操作参数时，现在将转义路由路径中的空格。</span><span class="sxs-lookup"><span data-stu-id="49a5b-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="49a5b-104">因此，尽管 <code>/controller/action/some data</code> 之前会匹配路由 <code>/controller/action/{data}</code> 并提供 <code>some data</code> 作为数据参数，但它现在将改为提供 <code>some%20data</code>。</span><span class="sxs-lookup"><span data-stu-id="49a5b-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="49a5b-105">建议</span><span class="sxs-lookup"><span data-stu-id="49a5b-105">Suggestion</span></span>

<span data-ttu-id="49a5b-106">应更新代码，以取消转义路由中的字符串参数。</span><span class="sxs-lookup"><span data-stu-id="49a5b-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="49a5b-107">如果需要原始 URI，可通过 <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API 进行访问。</span><span class="sxs-lookup"><span data-stu-id="49a5b-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>

| <span data-ttu-id="49a5b-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="49a5b-108">Name</span></span>    | <span data-ttu-id="49a5b-109">“值”</span><span class="sxs-lookup"><span data-stu-id="49a5b-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="49a5b-110">范围</span><span class="sxs-lookup"><span data-stu-id="49a5b-110">Scope</span></span>   |<span data-ttu-id="49a5b-111">次要</span><span class="sxs-lookup"><span data-stu-id="49a5b-111">Minor</span></span>|
|<span data-ttu-id="49a5b-112">Version</span><span class="sxs-lookup"><span data-stu-id="49a5b-112">Version</span></span>|<span data-ttu-id="49a5b-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="49a5b-113">4.5.2</span></span>|
|<span data-ttu-id="49a5b-114">类型</span><span class="sxs-lookup"><span data-stu-id="49a5b-114">Type</span></span>|<span data-ttu-id="49a5b-115">运行时</span><span class="sxs-lookup"><span data-stu-id="49a5b-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="49a5b-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="49a5b-116">Affected APIs</span></span>

- <xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)>

<!--

#### Affected APIs

- `M:System.Web.Mvc.RouteAttribute.#ctor(System.String)`

-->
