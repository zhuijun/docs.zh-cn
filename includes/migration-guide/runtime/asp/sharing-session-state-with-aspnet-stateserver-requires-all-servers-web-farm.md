---
ms.openlocfilehash: e450c53008e7562e37518fdfd6872ff9b63b6ac3
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609124"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="cf172-101">与 ASP.NET StateServer 共享会话状态需要 Web 场中的所有服务器使用相同版本的 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cf172-101">Sharing session state with ASP.NET StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

#### <a name="details"></a><span data-ttu-id="cf172-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="cf172-102">Details</span></span>

<span data-ttu-id="cf172-103">启用 <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> 会话状态时，给定 Web 场中的所有服务器必须使用相同版本的 .NET Framework 以便正确共享状态。</span><span class="sxs-lookup"><span data-stu-id="cf172-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cf172-104">建议</span><span class="sxs-lookup"><span data-stu-id="cf172-104">Suggestion</span></span>

<span data-ttu-id="cf172-105">请务必在同时共享状态的 Web 服务器上升级 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="cf172-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>

| <span data-ttu-id="cf172-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="cf172-106">Name</span></span>    | <span data-ttu-id="cf172-107">“值”</span><span class="sxs-lookup"><span data-stu-id="cf172-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cf172-108">范围</span><span class="sxs-lookup"><span data-stu-id="cf172-108">Scope</span></span>   |<span data-ttu-id="cf172-109">边缘</span><span class="sxs-lookup"><span data-stu-id="cf172-109">Edge</span></span>|
|<span data-ttu-id="cf172-110">Version</span><span class="sxs-lookup"><span data-stu-id="cf172-110">Version</span></span>|<span data-ttu-id="cf172-111">4.5</span><span class="sxs-lookup"><span data-stu-id="cf172-111">4.5</span></span>|
|<span data-ttu-id="cf172-112">类型</span><span class="sxs-lookup"><span data-stu-id="cf172-112">Type</span></span>|<span data-ttu-id="cf172-113">运行时</span><span class="sxs-lookup"><span data-stu-id="cf172-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cf172-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="cf172-114">Affected APIs</span></span>

- <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Web.SessionState.SessionStateMode.StateServer`

-->
