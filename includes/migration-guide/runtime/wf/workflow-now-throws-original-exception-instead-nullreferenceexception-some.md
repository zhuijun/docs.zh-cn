---
ms.openlocfilehash: 61d5885c19e39b138090c1a98fa26348724893c5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496968"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="938e0-101">在某些情况下工作流现在引发原始异常，而不是 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="938e0-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

#### <a name="details"></a><span data-ttu-id="938e0-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="938e0-102">Details</span></span>

<span data-ttu-id="938e0-103">在 .NET Framework 4.6.2 和更低版本中，当工作流活动的 Execute 方法引发 <xref:System.Exception.Message> 属性 <code>null</code> 值的异常，那么 System.Activities 工作流运行时引发 <xref:System.NullReferenceException?displayProperty=fullName> 掩码原始异常。在 .NET Framework 4.7 中，引发之前掩码的异常。</span><span class="sxs-lookup"><span data-stu-id="938e0-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=fullName>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="938e0-104">建议</span><span class="sxs-lookup"><span data-stu-id="938e0-104">Suggestion</span></span>

<span data-ttu-id="938e0-105">如果你的代码依赖于处理 <xref:System.NullReferenceException?displayProperty=fullName>，请将其更改为捕获自定义活动可能引发的异常。</span><span class="sxs-lookup"><span data-stu-id="938e0-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=fullName>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>

| <span data-ttu-id="938e0-106">名称</span><span class="sxs-lookup"><span data-stu-id="938e0-106">Name</span></span>    | <span data-ttu-id="938e0-107">值</span><span class="sxs-lookup"><span data-stu-id="938e0-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="938e0-108">范围</span><span class="sxs-lookup"><span data-stu-id="938e0-108">Scope</span></span>   |<span data-ttu-id="938e0-109">次要</span><span class="sxs-lookup"><span data-stu-id="938e0-109">Minor</span></span>|
|<span data-ttu-id="938e0-110">Version</span><span class="sxs-lookup"><span data-stu-id="938e0-110">Version</span></span>|<span data-ttu-id="938e0-111">4.7</span><span class="sxs-lookup"><span data-stu-id="938e0-111">4.7</span></span>|
|<span data-ttu-id="938e0-112">类型</span><span class="sxs-lookup"><span data-stu-id="938e0-112">Type</span></span>|<span data-ttu-id="938e0-113">运行时</span><span class="sxs-lookup"><span data-stu-id="938e0-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="938e0-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="938e0-114">Affected APIs</span></span>

- <xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType>
- <xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType>
- <xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType>
- <xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)`
- `M:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)`
- ``M:System.Activities.AsyncCodeActivity`1.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)``
- `M:System.Activities.WorkflowInvoker.Invoke`

-->
