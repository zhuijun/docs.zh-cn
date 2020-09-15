---
ms.openlocfilehash: 358103d5816eb61c88738e9626fb02c563b507f8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617131"
---
### <a name="workflow-30-types-are-obsolete"></a><span data-ttu-id="85fb6-101">WorkFlow 3.0 类型已过时</span><span class="sxs-lookup"><span data-stu-id="85fb6-101">WorkFlow 3.0 types are obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="85fb6-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="85fb6-102">Details</span></span>

<span data-ttu-id="85fb6-103">Windows Workflow Foundation (WWF) 3.0 API（来自于 System.Workflow 命名空间）现已过时。</span><span class="sxs-lookup"><span data-stu-id="85fb6-103">Windows Workflow Foundation (WWF) 3.0 APIs (those from the System.Workflow namespace) are now obsolete.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="85fb6-104">建议</span><span class="sxs-lookup"><span data-stu-id="85fb6-104">Suggestion</span></span>

<span data-ttu-id="85fb6-105">应改用新的 WWF 4.0 API（在 System.Activities 中）。</span><span class="sxs-lookup"><span data-stu-id="85fb6-105">New WWF 4.0 APIs (in System.Activities) should be used instead.</span></span> <span data-ttu-id="85fb6-106">可在[此处](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)找到使用新 API 的示例，[此处](https://docs.microsoft.com/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5)还提供更深入的指导。</span><span class="sxs-lookup"><span data-stu-id="85fb6-106">An example of using the new APIs can be found [here](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md) and further guidance is available [here](https://docs.microsoft.com/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5).</span></span> <span data-ttu-id="85fb6-107">或者，由于仍然支持 WWF 3.0 API，因此可能会使用它们，通过禁止显示生成时警告或使用较旧的编译器可以避免出现该警告。</span><span class="sxs-lookup"><span data-stu-id="85fb6-107">Alternatively, since the WWF 3.0 APIs are still supported, they may be used and the build-time warning avoided either by suppressing it or by using an older compiler.</span></span>

| <span data-ttu-id="85fb6-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="85fb6-108">Name</span></span>    | <span data-ttu-id="85fb6-109">“值”</span><span class="sxs-lookup"><span data-stu-id="85fb6-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="85fb6-110">范围</span><span class="sxs-lookup"><span data-stu-id="85fb6-110">Scope</span></span>   | <span data-ttu-id="85fb6-111">主要</span><span class="sxs-lookup"><span data-stu-id="85fb6-111">Major</span></span>       |
| <span data-ttu-id="85fb6-112">Version</span><span class="sxs-lookup"><span data-stu-id="85fb6-112">Version</span></span> | <span data-ttu-id="85fb6-113">4.5</span><span class="sxs-lookup"><span data-stu-id="85fb6-113">4.5</span></span>         |
| <span data-ttu-id="85fb6-114">类型</span><span class="sxs-lookup"><span data-stu-id="85fb6-114">Type</span></span>    | <span data-ttu-id="85fb6-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="85fb6-115">Retargeting</span></span> |
