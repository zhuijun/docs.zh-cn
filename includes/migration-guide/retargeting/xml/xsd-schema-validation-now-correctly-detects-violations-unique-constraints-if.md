---
ms.openlocfilehash: 349854b0dec5a585990b9c5e7c0b575df5bf70f3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615615"
---
### <a name="xsd-schema-validation-now-correctly-detects-violations-of-unique-constraints-if-compound-keys-are-used-and-one-key-is-empty"></a><span data-ttu-id="4df97-101">如果使用复合密钥并且一个密钥为空，XSD 架构验证现在可正确检测是否违反唯一约束</span><span class="sxs-lookup"><span data-stu-id="4df97-101">XSD Schema validation now correctly detects violations of unique constraints if compound keys are used and one key is empty</span></span>

#### <a name="details"></a><span data-ttu-id="4df97-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="4df97-102">Details</span></span>

<span data-ttu-id="4df97-103">在版本 4.6 之前的 .NET Framework 版本中存在一个 bug，即如果其中一个密钥为空，XSD 验证无法检测复合密钥上的唯一约束。</span><span class="sxs-lookup"><span data-stu-id="4df97-103">Versions of the .NET Framework prior to 4.6 had a bug that caused XSD validation to not detect unique constraints on compound keys if one of the keys was empty.</span></span> <span data-ttu-id="4df97-104">在 .NET Framework 4.6 中，此问题已得到更正。</span><span class="sxs-lookup"><span data-stu-id="4df97-104">In the .NET Framework 4.6, this issue is corrected.</span></span> <span data-ttu-id="4df97-105">这将导致更多的正确验证，但也可能导致无法像以前版本那样验证某些 XML。</span><span class="sxs-lookup"><span data-stu-id="4df97-105">This will result in more correct validation, but it may also result in some XML not validating which previously would have.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4df97-106">建议</span><span class="sxs-lookup"><span data-stu-id="4df97-106">Suggestion</span></span>

<span data-ttu-id="4df97-107">如果需要更宽松的 .NET Framework 4.0 验证，该验证应用程序可以面向版本 4.5（或更早版本）的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="4df97-107">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.5 (or earlier) of the .NET Framework.</span></span> <span data-ttu-id="4df97-108">但在重定向到 .NET Framework 4.6 时，应执行代码评审，确保无需验证重复的复合密钥（如在此问题的描述中所述）。</span><span class="sxs-lookup"><span data-stu-id="4df97-108">When retargeting to .NET Framework 4.6, however, code review should be done to be sure that duplicate compound keys (as described in this issue's description) are not expected to validate.</span></span>

| <span data-ttu-id="4df97-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="4df97-109">Name</span></span>    | <span data-ttu-id="4df97-110">“值”</span><span class="sxs-lookup"><span data-stu-id="4df97-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4df97-111">范围</span><span class="sxs-lookup"><span data-stu-id="4df97-111">Scope</span></span>   | <span data-ttu-id="4df97-112">边缘</span><span class="sxs-lookup"><span data-stu-id="4df97-112">Edge</span></span>        |
| <span data-ttu-id="4df97-113">Version</span><span class="sxs-lookup"><span data-stu-id="4df97-113">Version</span></span> | <span data-ttu-id="4df97-114">4.6</span><span class="sxs-lookup"><span data-stu-id="4df97-114">4.6</span></span>         |
| <span data-ttu-id="4df97-115">类型</span><span class="sxs-lookup"><span data-stu-id="4df97-115">Type</span></span>    | <span data-ttu-id="4df97-116">重定目标</span><span class="sxs-lookup"><span data-stu-id="4df97-116">Retargeting</span></span> |
