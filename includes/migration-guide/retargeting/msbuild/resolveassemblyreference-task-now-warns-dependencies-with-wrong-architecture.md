---
ms.openlocfilehash: 4d410811095786b33580d25f6c6eab3ac2f27148
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616027"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a><span data-ttu-id="235a2-101">ResolveAssemblyReference 任务现在将对体系结构错误的依赖项发出警告</span><span class="sxs-lookup"><span data-stu-id="235a2-101">ResolveAssemblyReference task now warns of dependencies with the wrong architecture</span></span>

#### <a name="details"></a><span data-ttu-id="235a2-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="235a2-102">Details</span></span>

<span data-ttu-id="235a2-103">此任务发出警告 MSB3270，它表示引用或任何依赖项不匹配应用程序的体系结构。</span><span class="sxs-lookup"><span data-stu-id="235a2-103">The task emits a warning, MSB3270, which indicates that a reference or any of its dependencies does not match the app's architecture.</span></span> <span data-ttu-id="235a2-104">例如，如果使用 `AnyCPU` 选项编译的应用程序包括 x86 引用，则会发生此情况。</span><span class="sxs-lookup"><span data-stu-id="235a2-104">For example, this occurs if an app that was compiled with the `AnyCPU` option includes an x86 reference.</span></span> <span data-ttu-id="235a2-105">这样的情况可能导致运行时应用失败（在本例中为，如果应用部署为 x64 过程）。</span><span class="sxs-lookup"><span data-stu-id="235a2-105">Such a scenario could result in an app failure at run time (in this case, if the app is deployed as an x64 process).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="235a2-106">建议</span><span class="sxs-lookup"><span data-stu-id="235a2-106">Suggestion</span></span>

<span data-ttu-id="235a2-107">有两方面的影响：</span><span class="sxs-lookup"><span data-stu-id="235a2-107">There are two areas of impact:</span></span>

- <span data-ttu-id="235a2-108">重新编译将生成警告，当应用在以前版本的 MSBuild 下编译时，此类警告未显示。</span><span class="sxs-lookup"><span data-stu-id="235a2-108">Recompilation generates warnings that did not appear when the app was compiled under a previous version of MSBuild.</span></span> <span data-ttu-id="235a2-109">但是，由于该警告可标识运行时失败可能的来源，所以应该调查并处理它。</span><span class="sxs-lookup"><span data-stu-id="235a2-109">However, because the warning identifies a possible source of runtime failure, it should be investigated and addressed.</span></span>
- <span data-ttu-id="235a2-110">如果警告被视为错误，则应用将无法进行编译。</span><span class="sxs-lookup"><span data-stu-id="235a2-110">If warnings are treated as errors, the app will fail to compile.</span></span>

| <span data-ttu-id="235a2-111">“属性”</span><span class="sxs-lookup"><span data-stu-id="235a2-111">Name</span></span>    | <span data-ttu-id="235a2-112">“值”</span><span class="sxs-lookup"><span data-stu-id="235a2-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="235a2-113">范围</span><span class="sxs-lookup"><span data-stu-id="235a2-113">Scope</span></span>   | <span data-ttu-id="235a2-114">次要</span><span class="sxs-lookup"><span data-stu-id="235a2-114">Minor</span></span>       |
| <span data-ttu-id="235a2-115">Version</span><span class="sxs-lookup"><span data-stu-id="235a2-115">Version</span></span> | <span data-ttu-id="235a2-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="235a2-116">4.5.1</span></span>       |
| <span data-ttu-id="235a2-117">类型</span><span class="sxs-lookup"><span data-stu-id="235a2-117">Type</span></span>    | <span data-ttu-id="235a2-118">重定目标</span><span class="sxs-lookup"><span data-stu-id="235a2-118">Retargeting</span></span> |
