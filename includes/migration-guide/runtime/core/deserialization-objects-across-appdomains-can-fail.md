---
ms.openlocfilehash: 3f82a4daac3b5d8981532f0c82e9a76f13c68b6e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496542"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="17da2-101">跨应用域的对象的反序列化可能失败</span><span class="sxs-lookup"><span data-stu-id="17da2-101">Deserialization of objects across appdomains can fail</span></span>

#### <a name="details"></a><span data-ttu-id="17da2-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="17da2-102">Details</span></span>

<span data-ttu-id="17da2-103">在某些情况下，当应用使用两个或更多带有不同应用程序基的应用域时，尝试跨应用域在逻辑调用上下文中为对象反序列化将引发异常。</span><span class="sxs-lookup"><span data-stu-id="17da2-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="17da2-104">建议</span><span class="sxs-lookup"><span data-stu-id="17da2-104">Suggestion</span></span>

<span data-ttu-id="17da2-105">请参阅[缓解措施：跨应用域的对象反序列化](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="17da2-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>

| <span data-ttu-id="17da2-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="17da2-106">Name</span></span>    | <span data-ttu-id="17da2-107">“值”</span><span class="sxs-lookup"><span data-stu-id="17da2-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="17da2-108">范围</span><span class="sxs-lookup"><span data-stu-id="17da2-108">Scope</span></span>   |<span data-ttu-id="17da2-109">边缘</span><span class="sxs-lookup"><span data-stu-id="17da2-109">Edge</span></span>|
|<span data-ttu-id="17da2-110">Version</span><span class="sxs-lookup"><span data-stu-id="17da2-110">Version</span></span>|<span data-ttu-id="17da2-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="17da2-111">4.5.1</span></span>|
|<span data-ttu-id="17da2-112">类型</span><span class="sxs-lookup"><span data-stu-id="17da2-112">Type</span></span>|<span data-ttu-id="17da2-113">运行时</span><span class="sxs-lookup"><span data-stu-id="17da2-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="17da2-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="17da2-114">Affected APIs</span></span>

<span data-ttu-id="17da2-115">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="17da2-115">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
