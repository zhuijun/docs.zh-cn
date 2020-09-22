---
ms.openlocfilehash: 1f85b1ce95ca07329aff77af4ec894622e0818d1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606357"
---
### <a name="workflow-30-types-are-obsolete"></a><span data-ttu-id="ad8d1-101">WorkFlow 3.0 类型已过时</span><span class="sxs-lookup"><span data-stu-id="ad8d1-101">WorkFlow 3.0 types are obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="ad8d1-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="ad8d1-102">Details</span></span>

<span data-ttu-id="ad8d1-103">Windows Workflow Foundation (WWF) 3.0 API（来自于 System.Workflow 命名空间）现已过时。</span><span class="sxs-lookup"><span data-stu-id="ad8d1-103">Windows Workflow Foundation (WWF) 3.0 APIs (those from the System.Workflow namespace) are now obsolete.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ad8d1-104">建议</span><span class="sxs-lookup"><span data-stu-id="ad8d1-104">Suggestion</span></span>

<span data-ttu-id="ad8d1-105">应改用新的 WWF 4.0 API（在 System.Activities 中）。</span><span class="sxs-lookup"><span data-stu-id="ad8d1-105">New WWF 4.0 APIs (in System.Activities) should be used instead.</span></span> <span data-ttu-id="ad8d1-106">可在[此处](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)找到使用新 API 的示例，[此处](/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5)还提供更深入的指导。</span><span class="sxs-lookup"><span data-stu-id="ad8d1-106">An example of using the new APIs can be found [here](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md) and further guidance is available [here](/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5).</span></span> <span data-ttu-id="ad8d1-107">或者，由于仍然支持 WWF 3.0 API，因此可能会使用它们，通过禁止显示生成时警告或使用较旧的编译器可以避免出现该警告。</span><span class="sxs-lookup"><span data-stu-id="ad8d1-107">Alternatively, since the WWF 3.0 APIs are still supported, they may be used and the build-time warning avoided either by suppressing it or by using an older compiler.</span></span>

| <span data-ttu-id="ad8d1-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="ad8d1-108">Name</span></span>    | <span data-ttu-id="ad8d1-109">“值”</span><span class="sxs-lookup"><span data-stu-id="ad8d1-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ad8d1-110">范围</span><span class="sxs-lookup"><span data-stu-id="ad8d1-110">Scope</span></span>   | <span data-ttu-id="ad8d1-111">主要</span><span class="sxs-lookup"><span data-stu-id="ad8d1-111">Major</span></span>       |
| <span data-ttu-id="ad8d1-112">Version</span><span class="sxs-lookup"><span data-stu-id="ad8d1-112">Version</span></span> | <span data-ttu-id="ad8d1-113">4.5</span><span class="sxs-lookup"><span data-stu-id="ad8d1-113">4.5</span></span>         |
| <span data-ttu-id="ad8d1-114">类型</span><span class="sxs-lookup"><span data-stu-id="ad8d1-114">Type</span></span>    | <span data-ttu-id="ad8d1-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="ad8d1-115">Retargeting</span></span> |
