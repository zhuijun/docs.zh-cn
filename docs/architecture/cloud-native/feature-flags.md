---
title: 功能标志
description: 利用 Azure 应用 Config 实现云本机应用程序中的功能标志
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: be4ab307069065975dc22d6bd984e12a2ea1457d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540460"
---
# <a name="feature-flags"></a><span data-ttu-id="b8cf6-103">功能标志</span><span class="sxs-lookup"><span data-stu-id="b8cf6-103">Feature flags</span></span>

<span data-ttu-id="b8cf6-104">第1章介绍了云本机的 affirmed，这就是速度和灵活性。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-104">In chapter 1, we affirmed that cloud native is much about speed and agility.</span></span> <span data-ttu-id="b8cf6-105">用户需要快速响应、创新的功能和零停机时间。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-105">Users expect rapid responsiveness, innovative features, and zero downtime.</span></span> <span data-ttu-id="b8cf6-106">`Feature flags` 是一种新式部署技术，有助于提高云本机应用程序的灵活性。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-106">`Feature flags` are a modern deployment technique that helps increase agility for cloud-native applications.</span></span> <span data-ttu-id="b8cf6-107">使用这些功能，您可以将新功能部署到生产环境中，但限制其可用性。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-107">They enable you to deploy new features into a production environment, but restrict their availability.</span></span> <span data-ttu-id="b8cf6-108">通过使用开关，你可以为特定用户激活一项新功能，而无需重新启动应用程序或部署新代码。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-108">With the flick of a switch, you can activate a new feature for specific users without restarting the app or deploying new code.</span></span> <span data-ttu-id="b8cf6-109">它们将新功能的发布与代码部署分离。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-109">They separate the release of new features from their code deployment.</span></span>

<span data-ttu-id="b8cf6-110">功能标志是基于条件逻辑构建的，它在运行时控制用户功能的可见性。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-110">Feature flags are built upon conditional logic that control visibility of functionality for users at runtime.</span></span> <span data-ttu-id="b8cf6-111">在现代的云本机系统中，通常会将新功能部署到生产环境中，但使用有限的受众进行测试。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-111">In modern cloud-native systems, it's common to deploy new features into production early, but test them with a limited audience.</span></span> <span data-ttu-id="b8cf6-112">随着置信度的增加，此功能可以以增量方式向更广泛的受众推出。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-112">As confidence increases, the feature can be incrementally rolled out to wider audiences.</span></span>

<span data-ttu-id="b8cf6-113">功能标志的其他用例包括：</span><span class="sxs-lookup"><span data-stu-id="b8cf6-113">Other use cases for feature flags include:</span></span>

- <span data-ttu-id="b8cf6-114">将高级功能限制为愿意支付更高订阅费用的特定客户组。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-114">Restrict premium functionality to specific customer groups willing to pay higher subscription fees.</span></span>
- <span data-ttu-id="b8cf6-115">通过快速停用问题功能来稳定系统，避免回滚或即时修补程序的风险。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-115">Stabilize a system by quickly deactivating a problem feature, avoiding the risks of a rollback or immediate hotfix.</span></span>
- <span data-ttu-id="b8cf6-116">禁用高峰使用期间资源消耗较高的可选功能。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-116">Disable an optional feature with high resource consumption during peak usage periods.</span></span>
- <span data-ttu-id="b8cf6-117">`experimental feature releases`向小型用户段进行验证，以验证可行性和普及程度。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-117">Conduct `experimental feature releases` to small user segments to validate feasibility and popularity.</span></span>

<span data-ttu-id="b8cf6-118">功能标志还可促进 `trunk-based` 开发。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-118">Feature flags also promote `trunk-based` development.</span></span> <span data-ttu-id="b8cf6-119">这是一种源控制分支模型，开发人员在其中协作处理单个分支中的功能。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-119">It's a source-control branching model where developers collaborate on features in a single branch.</span></span> <span data-ttu-id="b8cf6-120">此方法可最大程度地降低合并大量长时间运行的功能分支的风险和复杂性。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-120">The approach minimizes the risk and complexity of merging large numbers of long-running feature branches.</span></span> <span data-ttu-id="b8cf6-121">功能在激活前不可用。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-121">Features are unavailable until activated.</span></span>

## <a name="implementing-feature-flags"></a><span data-ttu-id="b8cf6-122">实现功能标志</span><span class="sxs-lookup"><span data-stu-id="b8cf6-122">Implementing feature flags</span></span>

<span data-ttu-id="b8cf6-123">功能标志的核心是一个简单的引用 `decision object` 。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-123">At its core, a feature flag is a reference to a simple `decision object`.</span></span> <span data-ttu-id="b8cf6-124">它返回或的布尔状态 `on` `off` 。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-124">It returns a Boolean state of `on` or `off`.</span></span> <span data-ttu-id="b8cf6-125">该标志通常包装一个封装功能功能的代码块。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-125">The flag typically wraps a block of code that encapsulates a feature capability.</span></span> <span data-ttu-id="b8cf6-126">标志的状态确定是否为给定用户执行代码块。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-126">The state of the flag determines whether that code block executes for a given user.</span></span> <span data-ttu-id="b8cf6-127">图10-11 显示了实现。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-127">Figure 10-11 shows the implementation.</span></span>

```csharp
if (featureFlag) {
    // Run this code block if the featureFlag value is true
} else {
    // Run this code block if the featureFlag value is false
}
```

<span data-ttu-id="b8cf6-128">**图 10-11** -简单的功能标志实现。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-128">**Figure 10-11** - Simple feature flag implementation.</span></span>

<span data-ttu-id="b8cf6-129">请注意，此方法如何将决策逻辑与功能代码分隔开来。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-129">Note how this approach separates the decision logic from the feature code.</span></span>

<span data-ttu-id="b8cf6-130">第1章介绍了 `Twelve-Factor App` 。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-130">In chapter 1, we discussed the `Twelve-Factor App`.</span></span> <span data-ttu-id="b8cf6-131">建议在应用程序可执行代码中保留外部配置设置。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-131">The guidance recommended keeping configuration settings external from application executable code.</span></span> <span data-ttu-id="b8cf6-132">如果需要，可以从外部源中读取设置。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-132">When needed, settings can be read in from the external source.</span></span> <span data-ttu-id="b8cf6-133">功能标志配置值还应独立于其基本代码。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-133">Feature flag configuration values should also be independent from their codebase.</span></span> <span data-ttu-id="b8cf6-134">通过在单独的存储库中外部化标记配置，可以更改标记状态，而无需修改和重新部署应用程序。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-134">By externalizing flag configuration in a separate repository, you can change flag state without modifying and redeploying the application.</span></span>

<span data-ttu-id="b8cf6-135">[Azure 应用配置](https://docs.microsoft.com/azure/azure-app-configuration/overview) 提供了一个用于功能标志的集中式存储库。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-135">[Azure App Configuration](https://docs.microsoft.com/azure/azure-app-configuration/overview) provides a centralized repository for feature flags.</span></span> <span data-ttu-id="b8cf6-136">利用它，你可以定义不同种类的功能标志，并快速、自信地操作其状态。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-136">With it, you define different kinds of feature flags and manipulate their states quickly and confidently.</span></span> <span data-ttu-id="b8cf6-137">将应用配置客户端库添加到应用程序以启用功能标志功能。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-137">You add the App Configuration client libraries to your application to enable feature flag functionality.</span></span> <span data-ttu-id="b8cf6-138">支持各种编程语言框架。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-138">Various programming language frameworks are supported.</span></span>

<span data-ttu-id="b8cf6-139">可以在 [ASP.NET Core 服务](https://docs.microsoft.com/azure/azure-app-configuration/use-feature-flags-dotnet-core)中轻松实现功能标志。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-139">Feature flags can be easily implemented in an [ASP.NET Core service](https://docs.microsoft.com/azure/azure-app-configuration/use-feature-flags-dotnet-core).</span></span> <span data-ttu-id="b8cf6-140">安装 .NET 功能管理库和应用配置提供程序使您能够以声明方式向代码添加功能标志。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-140">Installing the .NET Feature Management libraries and App Configuration provider enable you to declaratively add feature flags to your code.</span></span> <span data-ttu-id="b8cf6-141">它们启用 `FeatureGate` 了属性，这样就无需在代码库中手动编写 if 语句。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-141">They enable `FeatureGate` attributes so that you don't have to manually write if statements across your codebase.</span></span>

<span data-ttu-id="b8cf6-142">在 Startup 类中配置后，可以在控制器、操作或中间件级别添加功能标志功能。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-142">Once configured in your Startup class, you can add feature flag functionality at the controller, action, or middleware level.</span></span> <span data-ttu-id="b8cf6-143">图10-12 提供控制器和操作实现：</span><span class="sxs-lookup"><span data-stu-id="b8cf6-143">Figure 10-12 presents controller and action implementation:</span></span>

```csharp
[FeatureGate(MyFeatureFlags.FeatureA)]
public class ProductController : Controller
{
    ...
}
```

```csharp
[FeatureGate(MyFeatureFlags.FeatureA)]
public IActionResult UpdateProductStatus()
{
    return ObjectResult(ProductDto);
}
```

<span data-ttu-id="b8cf6-144">**图 10-12** -控制器和操作中的功能标志实现。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-144">**Figure 10-12** - Feature flag implementation in a controller and action.</span></span>

<span data-ttu-id="b8cf6-145">如果禁用功能标志，则在没有响应正文的状态代码) ，用户将收到 404 (找不到。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-145">If a feature flag is disabled, the user will receive a 404 (Not Found) status code with no response body.</span></span>

<span data-ttu-id="b8cf6-146">功能标志还可以直接注入 c # 类中。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-146">Feature flags can also be injected directly into C# classes.</span></span> <span data-ttu-id="b8cf6-147">图10-13 显示了功能标志注入：</span><span class="sxs-lookup"><span data-stu-id="b8cf6-147">Figure 10-13 shows feature flag injection:</span></span>

```csharp
public class ProductController : Controller
{
    private readonly IFeatureManager _featureManager;

    public ProductController(IFeatureManager featureManager)
    {
        _featureManager = featureManager;
    }
}
```

<span data-ttu-id="b8cf6-148">**图 10-13** -将功能标志注入到类中。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-148">**Figure 10-13** - Feature flag injection into a class.</span></span>

<span data-ttu-id="b8cf6-149">功能管理库管理后台的功能标志生命周期。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-149">The Feature Management libraries manage the feature flag lifecycle behind the scenes.</span></span> <span data-ttu-id="b8cf6-150">例如，若要最大程度地减少对配置存储的大量调用，库将在指定的持续时间内缓存标记状态。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-150">For example, to minimize high numbers of calls to the configuration store, the libraries cache flag states for a specified duration.</span></span> <span data-ttu-id="b8cf6-151">它们可以保证请求调用期间标记状态不相等。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-151">They can guarantee the immutability of flag states during a request call.</span></span> <span data-ttu-id="b8cf6-152">它们还提供 `Point-in-time snapshot` 。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-152">They also offer a `Point-in-time snapshot`.</span></span> <span data-ttu-id="b8cf6-153">您可以重新构造任何键-值的历史记录，并在过去七天内的任何时刻提供其过去的值。</span><span class="sxs-lookup"><span data-stu-id="b8cf6-153">You can reconstruct the history of any key-value and provide its past value at any moment within the previous seven days.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b8cf6-154">[上一页](devops.md)
>[下一页](infrastructure-as-code.md)</span><span class="sxs-lookup"><span data-stu-id="b8cf6-154">[Previous](devops.md)
[Next](infrastructure-as-code.md)</span></span>
