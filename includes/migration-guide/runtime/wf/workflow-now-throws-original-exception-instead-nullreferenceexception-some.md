---
ms.openlocfilehash: ae0c7322b7415157838278b5568e6e49936e9a93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621056"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="6723c-101">在某些情况下工作流现在引发原始异常，而不是 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="6723c-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

#### <a name="details"></a><span data-ttu-id="6723c-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="6723c-102">Details</span></span>

<span data-ttu-id="6723c-103">在 .NET Framework 4.6.2 和更低版本中，当工作流活动的 Execute 方法引发 <xref:System.Exception.Message> 属性 <code>null</code> 值的异常，那么 System.Activities 工作流运行时引发 <xref:System.NullReferenceException?displayProperty=fullName> 掩码原始异常。在 .NET Framework 4.7 中，引发之前掩码的异常。</span><span class="sxs-lookup"><span data-stu-id="6723c-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=fullName>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6723c-104">建议</span><span class="sxs-lookup"><span data-stu-id="6723c-104">Suggestion</span></span>

<span data-ttu-id="6723c-105">如果你的代码依赖于处理 <xref:System.NullReferenceException?displayProperty=fullName>，请将其更改为捕获自定义活动可能引发的异常。</span><span class="sxs-lookup"><span data-stu-id="6723c-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=fullName>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>

| <span data-ttu-id="6723c-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="6723c-106">Name</span></span>    | <span data-ttu-id="6723c-107">值</span><span class="sxs-lookup"><span data-stu-id="6723c-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6723c-108">范围</span><span class="sxs-lookup"><span data-stu-id="6723c-108">Scope</span></span>   |<span data-ttu-id="6723c-109">次要</span><span class="sxs-lookup"><span data-stu-id="6723c-109">Minor</span></span>|
|<span data-ttu-id="6723c-110">Version</span><span class="sxs-lookup"><span data-stu-id="6723c-110">Version</span></span>|<span data-ttu-id="6723c-111">4.7</span><span class="sxs-lookup"><span data-stu-id="6723c-111">4.7</span></span>|
|<span data-ttu-id="6723c-112">类型</span><span class="sxs-lookup"><span data-stu-id="6723c-112">Type</span></span>|<span data-ttu-id="6723c-113">运行时</span><span class="sxs-lookup"><span data-stu-id="6723c-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6723c-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="6723c-114">Affected APIs</span></span>

-<xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
