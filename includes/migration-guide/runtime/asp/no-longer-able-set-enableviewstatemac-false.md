---
ms.openlocfilehash: c1793bb51f7da9169e912078fde202d0d62a4183
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496835"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="4aab4-101">无法再将 EnableViewStateMac 设为 false</span><span class="sxs-lookup"><span data-stu-id="4aab4-101">No longer able to set EnableViewStateMac to false</span></span>

#### <a name="details"></a><span data-ttu-id="4aab4-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="4aab4-102">Details</span></span>

<span data-ttu-id="4aab4-103">ASP.NET 不再允许开发者指定 <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> 或 <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>。</span><span class="sxs-lookup"><span data-stu-id="4aab4-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="4aab4-104">现在，针对所有带嵌入视图状态的请求强制执行视图状态消息身份验证代码 (MAC)。</span><span class="sxs-lookup"><span data-stu-id="4aab4-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="4aab4-105">仅影响将 EnableViewStateMac 属性显式设置为 <code>false</code> 的应用。</span><span class="sxs-lookup"><span data-stu-id="4aab4-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4aab4-106">建议</span><span class="sxs-lookup"><span data-stu-id="4aab4-106">Suggestion</span></span>

<span data-ttu-id="4aab4-107">EnableViewStateMac 必须假设为 true，并且必须解决任何生成的 MAC 错误（如[本指南](https://support.microsoft.com/kb/2915218)所述，该指南包含多种解决方法，具体视引发 MAC 错误的具体原因而定）。</span><span class="sxs-lookup"><span data-stu-id="4aab4-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>

| <span data-ttu-id="4aab4-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="4aab4-108">Name</span></span>    | <span data-ttu-id="4aab4-109">“值”</span><span class="sxs-lookup"><span data-stu-id="4aab4-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4aab4-110">范围</span><span class="sxs-lookup"><span data-stu-id="4aab4-110">Scope</span></span>   |<span data-ttu-id="4aab4-111">主要</span><span class="sxs-lookup"><span data-stu-id="4aab4-111">Major</span></span>|
|<span data-ttu-id="4aab4-112">Version</span><span class="sxs-lookup"><span data-stu-id="4aab4-112">Version</span></span>|<span data-ttu-id="4aab4-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="4aab4-113">4.5.2</span></span>|
|<span data-ttu-id="4aab4-114">类型</span><span class="sxs-lookup"><span data-stu-id="4aab4-114">Type</span></span>|<span data-ttu-id="4aab4-115">运行时</span><span class="sxs-lookup"><span data-stu-id="4aab4-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="4aab4-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="4aab4-116">Affected APIs</span></span>

<span data-ttu-id="4aab4-117">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="4aab4-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
