---
ms.openlocfilehash: 4a22d78f2308aab544d7a7d2e4d05ddc1ad5457d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617129"
---
### <a name="xml-schema-validation-is-stricter"></a><span data-ttu-id="4e27a-101">XML 架构验证更为严格</span><span class="sxs-lookup"><span data-stu-id="4e27a-101">XML schema validation is stricter</span></span>

#### <a name="details"></a><span data-ttu-id="4e27a-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="4e27a-102">Details</span></span>

<span data-ttu-id="4e27a-103">在 .NET Framework 4.5 中，XML 架构验证更为严格。</span><span class="sxs-lookup"><span data-stu-id="4e27a-103">In the .NET Framework 4.5, XML schema validation is more strict.</span></span> <span data-ttu-id="4e27a-104">如果使用 xsd:anyURI 来验证 URL（如 mailto 协议），则当 URL 中有空格时，验证将失败。</span><span class="sxs-lookup"><span data-stu-id="4e27a-104">If you use xsd:anyURI to validate a URI such as a mailto protocol, validation fails if there are spaces in the URI.</span></span> <span data-ttu-id="4e27a-105">在 .NET Framework 的早期版本中，验证将成功。</span><span class="sxs-lookup"><span data-stu-id="4e27a-105">In previous versions of the .NET Framework, validation succeeded.</span></span> <span data-ttu-id="4e27a-106">此更改仅影响面向 .NET Framework 4.5 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="4e27a-106">The change affects only applications that target the .NET Framework 4.5.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4e27a-107">建议</span><span class="sxs-lookup"><span data-stu-id="4e27a-107">Suggestion</span></span>

<span data-ttu-id="4e27a-108">如果需要更宽松的 .NET Framework 4.0 验证，该验证应用程序可以面向版本 4.0 的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="4e27a-108">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.0 of the .NET Framework.</span></span> <span data-ttu-id="4e27a-109">但是，重定向到 .NET Framework 4.5 时，应执行代码评审，确保无效的 URI（包含空格）不会作为 anyURI 数据类型的属性值。</span><span class="sxs-lookup"><span data-stu-id="4e27a-109">When retargeting to .NET Framework 4.5, however, code review should be done to be sure that invalid URIs (with spaces) are not expected as attribute values with the anyURI data type.</span></span>

| <span data-ttu-id="4e27a-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="4e27a-110">Name</span></span>    | <span data-ttu-id="4e27a-111">“值”</span><span class="sxs-lookup"><span data-stu-id="4e27a-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4e27a-112">范围</span><span class="sxs-lookup"><span data-stu-id="4e27a-112">Scope</span></span>   | <span data-ttu-id="4e27a-113">次要</span><span class="sxs-lookup"><span data-stu-id="4e27a-113">Minor</span></span>       |
| <span data-ttu-id="4e27a-114">Version</span><span class="sxs-lookup"><span data-stu-id="4e27a-114">Version</span></span> | <span data-ttu-id="4e27a-115">4.5</span><span class="sxs-lookup"><span data-stu-id="4e27a-115">4.5</span></span>         |
| <span data-ttu-id="4e27a-116">类型</span><span class="sxs-lookup"><span data-stu-id="4e27a-116">Type</span></span>    | <span data-ttu-id="4e27a-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="4e27a-117">Retargeting</span></span> |
