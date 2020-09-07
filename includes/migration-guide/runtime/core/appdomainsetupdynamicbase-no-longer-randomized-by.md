---
ms.openlocfilehash: 26c50ac8b0e570e31a38b1913f73acbe21fae08b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496807"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a><span data-ttu-id="3707a-101">UseRandomizedStringHashAlgorithm 不再由 AppDomainSetup.DynamicBase 进行随机化</span><span class="sxs-lookup"><span data-stu-id="3707a-101">AppDomainSetup.DynamicBase is no longer randomized by UseRandomizedStringHashAlgorithm</span></span>

#### <a name="details"></a><span data-ttu-id="3707a-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="3707a-102">Details</span></span>

<span data-ttu-id="3707a-103">在 .NET Framework 4.6 之前，如果在应用的配置文件中启用了 UseRandomizedStringHashAlgorithm，那么 <xref:System.AppDomainSetup.DynamicBase> 的值会在应用程序域或者进程之间进行随机化。</span><span class="sxs-lookup"><span data-stu-id="3707a-103">Prior to the .NET Framework 4.6, the value of <xref:System.AppDomainSetup.DynamicBase> would be randomized between application domains, or between processes, if UseRandomizedStringHashAlgorithm was enabled in the app's config file.</span></span> <span data-ttu-id="3707a-104">自 .NET Framework 4.6 起，<xref:System.AppDomainSetup.DynamicBase> 将在运行的应用的不同实例之间，以及在不同的应用域之间返回一个稳定的结果。</span><span class="sxs-lookup"><span data-stu-id="3707a-104">Beginning in the .NET Framework 4.6, <xref:System.AppDomainSetup.DynamicBase> will return a stable result between different instances of an app running, and between different app domains.</span></span> <span data-ttu-id="3707a-105">不同应用的动态基各不相同；此更改仅删除相同应用的不同实例的随机命名元素。</span><span class="sxs-lookup"><span data-stu-id="3707a-105">Dynamic bases will still differ for different apps; this change only removes the random naming element for different instances of the same app.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3707a-106">建议</span><span class="sxs-lookup"><span data-stu-id="3707a-106">Suggestion</span></span>

<span data-ttu-id="3707a-107">请注意，启用 <code>UseRandomizedStringHashAlgorithm</code> 不会导致随机化 <xref:System.AppDomainSetup.DynamicBase>。</span><span class="sxs-lookup"><span data-stu-id="3707a-107">Be aware that enabling <code>UseRandomizedStringHashAlgorithm</code> will not result in <xref:System.AppDomainSetup.DynamicBase> being randomized.</span></span> <span data-ttu-id="3707a-108">如果需要随机基，则必须在应用代码中生成它，而不是通过此 API 生成。</span><span class="sxs-lookup"><span data-stu-id="3707a-108">If a random base is needed, it must be produced in your app's code rather than via this API.</span></span>

| <span data-ttu-id="3707a-109">名称</span><span class="sxs-lookup"><span data-stu-id="3707a-109">Name</span></span>    | <span data-ttu-id="3707a-110">值</span><span class="sxs-lookup"><span data-stu-id="3707a-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3707a-111">范围</span><span class="sxs-lookup"><span data-stu-id="3707a-111">Scope</span></span>   |<span data-ttu-id="3707a-112">边缘</span><span class="sxs-lookup"><span data-stu-id="3707a-112">Edge</span></span>|
|<span data-ttu-id="3707a-113">Version</span><span class="sxs-lookup"><span data-stu-id="3707a-113">Version</span></span>|<span data-ttu-id="3707a-114">4.6</span><span class="sxs-lookup"><span data-stu-id="3707a-114">4.6</span></span>|
|<span data-ttu-id="3707a-115">类型</span><span class="sxs-lookup"><span data-stu-id="3707a-115">Type</span></span>|<span data-ttu-id="3707a-116">运行时</span><span class="sxs-lookup"><span data-stu-id="3707a-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3707a-117">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="3707a-117">Affected APIs</span></span>

- <xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.AppDomainSetup.DynamicBase`

-->
