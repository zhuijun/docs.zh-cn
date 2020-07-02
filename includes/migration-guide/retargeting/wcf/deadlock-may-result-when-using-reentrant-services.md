---
ms.openlocfilehash: dd7d3e445772e4b5ec148576ccd1374d56e251bd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614371"
---
### <a name="deadlock-may-result-when-using-reentrant-services"></a><span data-ttu-id="aec65-101">使用可重入服务时可能导致死锁</span><span class="sxs-lookup"><span data-stu-id="aec65-101">Deadlock may result when using Reentrant services</span></span>

#### <a name="details"></a><span data-ttu-id="aec65-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="aec65-102">Details</span></span>

<span data-ttu-id="aec65-103">死锁可能会导致一个可重入服务，该服务将服务的实例一次限制为一个执行线程。</span><span class="sxs-lookup"><span data-stu-id="aec65-103">A deadlock may result in a Reentrant service, which restricts instances of the service to one thread of execution at a time.</span></span> <span data-ttu-id="aec65-104">代码中包含以下 <xref:System.ServiceModel.ServiceBehaviorAttribute> 的服务容易遇到此问题：</span><span class="sxs-lookup"><span data-stu-id="aec65-104">Services prone to encounter this problem will have the following <xref:System.ServiceModel.ServiceBehaviorAttribute> in their code:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

#### <a name="suggestion"></a><span data-ttu-id="aec65-105">建议</span><span class="sxs-lookup"><span data-stu-id="aec65-105">Suggestion</span></span>

<span data-ttu-id="aec65-106">要解决此问题，可执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="aec65-106">To address this issue, you can do the following:</span></span>

- <span data-ttu-id="aec65-107">将服务的并发模式设置为 <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> 或 &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;。</span><span class="sxs-lookup"><span data-stu-id="aec65-107">Set the service's concurrency mode to <xref:System.ServiceModel.ConcurrencyMode.Single?displayProperty=nameWithType> or &lt;System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType&gt;.</span></span> <span data-ttu-id="aec65-108">例如：</span><span class="sxs-lookup"><span data-stu-id="aec65-108">For example:</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Reentrant)]
```

- <span data-ttu-id="aec65-109">安装 .NET Framework 4.6.2 的最新更新，或升级到更高版本的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="aec65-109">Install the latest update to the .NET Framework 4.6.2, or upgrade to a later version of the .NET Framework.</span></span> <span data-ttu-id="aec65-110">这将在 <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType> 中禁用 <xref:System.Threading.ExecutionContext> 的流。</span><span class="sxs-lookup"><span data-stu-id="aec65-110">This disables the flow of the <xref:System.Threading.ExecutionContext> in <xref:System.ServiceModel.OperationContext.Current?displayProperty=nameWithType>.</span></span> <span data-ttu-id="aec65-111">此行为是可配置的；它相当于将以下应用设置添加到配置文件中：</span><span class="sxs-lookup"><span data-stu-id="aec65-111">This behavior is configurable; it is equivalent to adding the following app setting to your configuration file:</span></span>

```xml
<appSettings>
  <add key="Switch.System.ServiceModel.DisableOperationContextAsyncFlow" value="true" />
</appSettings>
```

<span data-ttu-id="aec65-112">对于 Reentrant 服务，`Switch.System.ServiceModel.DisableOperationContextAsyncFlow` 的值绝不能设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="aec65-112">The value of `Switch.System.ServiceModel.DisableOperationContextAsyncFlow` should never be set to `false` for Reentrant services.</span></span>

| <span data-ttu-id="aec65-113">“属性”</span><span class="sxs-lookup"><span data-stu-id="aec65-113">Name</span></span>    | <span data-ttu-id="aec65-114">“值”</span><span class="sxs-lookup"><span data-stu-id="aec65-114">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="aec65-115">范围</span><span class="sxs-lookup"><span data-stu-id="aec65-115">Scope</span></span>   | <span data-ttu-id="aec65-116">次要</span><span class="sxs-lookup"><span data-stu-id="aec65-116">Minor</span></span>       |
| <span data-ttu-id="aec65-117">Version</span><span class="sxs-lookup"><span data-stu-id="aec65-117">Version</span></span> | <span data-ttu-id="aec65-118">4.6.2</span><span class="sxs-lookup"><span data-stu-id="aec65-118">4.6.2</span></span>       |
| <span data-ttu-id="aec65-119">类型</span><span class="sxs-lookup"><span data-stu-id="aec65-119">Type</span></span>    | <span data-ttu-id="aec65-120">重定目标</span><span class="sxs-lookup"><span data-stu-id="aec65-120">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="aec65-121">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="aec65-121">Affected APIs</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant?displayProperty=nameWithType>
