---
ms.openlocfilehash: ddc98448101c65003001ad05e67f29d75d99ad44
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616025"
---
### <a name="workflowdesignerload-doesnt-remove-symbol-property"></a><span data-ttu-id="ff903-101">WorkflowDesigner.Load 不会删除符号属性</span><span class="sxs-lookup"><span data-stu-id="ff903-101">WorkflowDesigner.Load doesn't remove symbol property</span></span>

#### <a name="details"></a><span data-ttu-id="ff903-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="ff903-102">Details</span></span>

<span data-ttu-id="ff903-103">当在工作流设计器中面向 .NET Framework 4.5，并使用 <xref:System.Activities.Presentation.WorkflowDesigner.Load> 方法加载重新托管的 3.5 工作流时，保存该工作流的同时将引发 <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="ff903-103">When targeting the .NET Framework 4.5 in the workflow designer, and loading a re-hosted 3.5 workflow with the <xref:System.Activities.Presentation.WorkflowDesigner.Load> method, a <xref:System.Xaml.XamlDuplicateMemberException?displayProperty=fullName> is thrown while saving the workflow.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ff903-104">建议</span><span class="sxs-lookup"><span data-stu-id="ff903-104">Suggestion</span></span>

<span data-ttu-id="ff903-105">此 bug 仅当在工作流设计器中面向 .NET Framework 4.5 时才显示，因此可通过将 `WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName` 设为 4.0 .NET Framework 进行解决。或者，可使用 <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> 方法而非 <xref:System.Activities.Presentation.WorkflowDesigner.Load> 方法加载工作流来避免此问题。</span><span class="sxs-lookup"><span data-stu-id="ff903-105">This bug only manifests when targeting .NET Framework 4.5 in the workflow designer, so it can be worked around by setting the `WorkflowDesigner.Context.Services.GetService&lt;DesignerConfigurationService&gt;().TargetFrameworkName` to the 4.0 .NET Framework.Alternatively, the issue may be avoided by using the <xref:System.Activities.Presentation.WorkflowDesigner.Load(System.String)> method to load the workflow, instead of <xref:System.Activities.Presentation.WorkflowDesigner.Load>.</span></span>

| <span data-ttu-id="ff903-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="ff903-106">Name</span></span>    | <span data-ttu-id="ff903-107">“值”</span><span class="sxs-lookup"><span data-stu-id="ff903-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ff903-108">范围</span><span class="sxs-lookup"><span data-stu-id="ff903-108">Scope</span></span>   | <span data-ttu-id="ff903-109">主要</span><span class="sxs-lookup"><span data-stu-id="ff903-109">Major</span></span>       |
| <span data-ttu-id="ff903-110">Version</span><span class="sxs-lookup"><span data-stu-id="ff903-110">Version</span></span> | <span data-ttu-id="ff903-111">4.5</span><span class="sxs-lookup"><span data-stu-id="ff903-111">4.5</span></span>         |
| <span data-ttu-id="ff903-112">类型</span><span class="sxs-lookup"><span data-stu-id="ff903-112">Type</span></span>    | <span data-ttu-id="ff903-113">重定目标</span><span class="sxs-lookup"><span data-stu-id="ff903-113">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ff903-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="ff903-114">Affected APIs</span></span>

- <xref:System.Activities.Presentation.WorkflowDesigner.Load?displayProperty=nameWithType>
