---
ms.openlocfilehash: 5c949b79eefa68ea6f8d4ad27c716c438e24f170
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619831"
---
### <a name="deserialization-of-objects-across-appdomains-can-fail"></a><span data-ttu-id="6521a-101">跨应用域的对象的反序列化可能失败</span><span class="sxs-lookup"><span data-stu-id="6521a-101">Deserialization of objects across appdomains can fail</span></span>

#### <a name="details"></a><span data-ttu-id="6521a-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="6521a-102">Details</span></span>

<span data-ttu-id="6521a-103">在某些情况下，当应用使用两个或更多带有不同应用程序基的应用域时，尝试跨应用域在逻辑调用上下文中为对象反序列化将引发异常。</span><span class="sxs-lookup"><span data-stu-id="6521a-103">In some cases, when an app uses two or more app domains with different application bases, trying to deserialize objects in the logical call context across app domains throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6521a-104">建议</span><span class="sxs-lookup"><span data-stu-id="6521a-104">Suggestion</span></span>

<span data-ttu-id="6521a-105">请参阅[缓解措施：跨应用域的对象反序列化](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span><span class="sxs-lookup"><span data-stu-id="6521a-105">See [Mitigation: Deserialization of Objects Across App Domains](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)</span></span>

| <span data-ttu-id="6521a-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="6521a-106">Name</span></span>    | <span data-ttu-id="6521a-107">“值”</span><span class="sxs-lookup"><span data-stu-id="6521a-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6521a-108">范围</span><span class="sxs-lookup"><span data-stu-id="6521a-108">Scope</span></span>   |<span data-ttu-id="6521a-109">边缘</span><span class="sxs-lookup"><span data-stu-id="6521a-109">Edge</span></span>|
|<span data-ttu-id="6521a-110">Version</span><span class="sxs-lookup"><span data-stu-id="6521a-110">Version</span></span>|<span data-ttu-id="6521a-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="6521a-111">4.5.1</span></span>|
|<span data-ttu-id="6521a-112">类型</span><span class="sxs-lookup"><span data-stu-id="6521a-112">Type</span></span>|<span data-ttu-id="6521a-113">运行时</span><span class="sxs-lookup"><span data-stu-id="6521a-113">Runtime</span></span>|
