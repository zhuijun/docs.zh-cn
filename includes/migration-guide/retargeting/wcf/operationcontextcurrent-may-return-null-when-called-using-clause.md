---
ms.openlocfilehash: d25c14f93da5fe8acf06269554fed30ddc6bc95d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614362"
---
### <a name="operationcontextcurrent-may-return-null-when-called-in-a-using-clause"></a><span data-ttu-id="d8b89-101">OperationContext.Current 在 using 子句中被调用时可能返回 null</span><span class="sxs-lookup"><span data-stu-id="d8b89-101">OperationContext.Current may return null when called in a using clause</span></span>

#### <a name="details"></a><span data-ttu-id="d8b89-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="d8b89-102">Details</span></span>

<span data-ttu-id="d8b89-103">如果满足以下所有条件，那么 <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> 可能返回 `null` 且导致 <xref:System.NullReferenceException>：</span><span class="sxs-lookup"><span data-stu-id="d8b89-103"><xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> may return `null` and a <xref:System.NullReferenceException> may result if all of the following conditions are true:</span></span>

- <span data-ttu-id="d8b89-104">在返回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 的方法中检索 <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="d8b89-104">You retrieve the value of the <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> property in a method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>
- <span data-ttu-id="d8b89-105">在 `using` 子句中实例化 <xref:System.ServiceModel.OperationContextScope> 对象。</span><span class="sxs-lookup"><span data-stu-id="d8b89-105">You instantiate the <xref:System.ServiceModel.OperationContextScope> object in a `using` clause.</span></span>
- <span data-ttu-id="d8b89-106">在 `using statement` 中检索 <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="d8b89-106">You retrieve the value of the <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> property within the `using statement`.</span></span> <span data-ttu-id="d8b89-107">例如：</span><span class="sxs-lookup"><span data-stu-id="d8b89-107">For example:</span></span>

```csharp
using (new OperationContextScope(OperationContext.Current))
{
    // OperationContext.Current is null.
    OperationContext context = OperationContext.Current;

    // ...
}
```

#### <a name="suggestion"></a><span data-ttu-id="d8b89-108">建议</span><span class="sxs-lookup"><span data-stu-id="d8b89-108">Suggestion</span></span>

<span data-ttu-id="d8b89-109">要解决此问题，可执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="d8b89-109">To address this issue, you can do the following:</span></span>

- <span data-ttu-id="d8b89-110">按如下所示修改代码，实例化一个新的非 `null` <xref:System.ServiceModel.OperationContext.Current%2A> 对象：</span><span class="sxs-lookup"><span data-stu-id="d8b89-110">Modify your code as follows to instantiate a new non- `null` <xref:System.ServiceModel.OperationContext.Current%2A> object:</span></span>

    ```csharp
    OperationContext ocx = OperationContext.Current;
    using (new OperationContextScope(OperationContext.Current))
    {
        OperationContext.Current = new OperationContext(ocx.Channel);

        // ...
    }
    ```

- <span data-ttu-id="d8b89-111">安装 .NET Framework 4.6.2 的最新更新，或升级到更高版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="d8b89-111">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="d8b89-112">这将禁用 <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> 中的 <xref:System.Threading.ExecutionContext> 流并还原 .NET Framework 4.6.1 以及更低版本中的 WCF 应用程序行为。</span><span class="sxs-lookup"><span data-stu-id="d8b89-112">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> and restores the behavior of WCF applications in the .NET Framework 4.6.1 and earlier versions.</span></span> <span data-ttu-id="d8b89-113">此行为是可配置的；它相当于将以下应用设置添加到配置文件中：</span><span class="sxs-lookup"><span data-stu-id="d8b89-113">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span>

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
    </appSettings>
    ```

    <span data-ttu-id="d8b89-114">如果不需要此更改并且应用程序依赖操作上下文间的执行上下文流，那么可以启用它的流，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d8b89-114">If this change is undesirable and your application depends on execution context flowing between operation contexts, you can enable its flow as follows:</span></span>

    ```xml
    <appSettings>
      <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="false" />
    </appSettings>
    ```

| <span data-ttu-id="d8b89-115">“属性”</span><span class="sxs-lookup"><span data-stu-id="d8b89-115">Name</span></span>    | <span data-ttu-id="d8b89-116">“值”</span><span class="sxs-lookup"><span data-stu-id="d8b89-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d8b89-117">范围</span><span class="sxs-lookup"><span data-stu-id="d8b89-117">Scope</span></span>   | <span data-ttu-id="d8b89-118">边缘</span><span class="sxs-lookup"><span data-stu-id="d8b89-118">Edge</span></span>        |
| <span data-ttu-id="d8b89-119">Version</span><span class="sxs-lookup"><span data-stu-id="d8b89-119">Version</span></span> | <span data-ttu-id="d8b89-120">4.6.2</span><span class="sxs-lookup"><span data-stu-id="d8b89-120">4.6.2</span></span>       |
| <span data-ttu-id="d8b89-121">类型</span><span class="sxs-lookup"><span data-stu-id="d8b89-121">Type</span></span>    | <span data-ttu-id="d8b89-122">重定目标</span><span class="sxs-lookup"><span data-stu-id="d8b89-122">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="d8b89-123">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="d8b89-123">Affected APIs</span></span>

- <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>
