---
title: ML.NET CLI 遥测收集
description: 了解收集使用情况信息以供分析的 ML.NET CLI 遥测功能、收集的数据，以及如何禁用遥测。 此外，还可以找到 .NET 许可协议的链接以及有关 Microsoft GDPR 合规性的信息。
ms.topic: conceptual
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 833ee2ae54cf3a52adaf070837a33e00267d25dc
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599826"
---
# <a name="telemetry-collection-by-the-mlnet-cli"></a><span data-ttu-id="ffbf4-104">ML.NET CLI 遥测收集</span><span class="sxs-lookup"><span data-stu-id="ffbf4-104">Telemetry collection by the ML.NET CLI</span></span>

<span data-ttu-id="ffbf4-105">[ML.NET CLI](https://aka.ms/mlnet-cli) 包含遥测功能，可收集聚合后供 Microsoft 使用的匿名使用数据。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-105">The [ML.NET CLI](https://aka.ms/mlnet-cli) includes a telemetry feature that collects anonymous usage data that is aggregated for use by Microsoft.</span></span>

## <a name="how-microsoft-uses-the-data"></a><span data-ttu-id="ffbf4-106">Microsoft 如何使用这些数据</span><span class="sxs-lookup"><span data-stu-id="ffbf4-106">How Microsoft uses the data</span></span>

<span data-ttu-id="ffbf4-107">产品团队使用 ML.NET CLI 遥测数据来帮助了解如何改进工具。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-107">The product team uses ML.NET CLI telemetry data to help understand how to improve the tools.</span></span> <span data-ttu-id="ffbf4-108">例如，如果客户不经常使用特定机器学习任务，则产品团队可调查原因并使用调查结果来确定功能开发的优先级。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-108">For example, if customers infrequently use a particular machine learning task, the product team investigates why and uses findings to prioritize feature development.</span></span> <span data-ttu-id="ffbf4-109">ML.NET CLI 遥测还可以帮助调试崩溃和代码异常等问题。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-109">ML.NET CLI telemetry also helps with debugging of issues such as crashes and code anomalies.</span></span>

<span data-ttu-id="ffbf4-110">尽管产品团队很感激大家提供此类见解，我们也知道并非每位用户都愿意发送此类数据。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-110">While the product team appreciates this insight, we also know that not everyone wants to send this data.</span></span> [<span data-ttu-id="ffbf4-111">了解如何禁用遥测。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-111">Find out how to disable telemetry.</span></span>](#opt-out-of-data-collection)

## <a name="scope"></a><span data-ttu-id="ffbf4-112">范围</span><span class="sxs-lookup"><span data-stu-id="ffbf4-112">Scope</span></span>

<span data-ttu-id="ffbf4-113">`mlnet` 命令可启动 ML.NET CLI，但命令本身不收集遥测。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-113">The `mlnet` command launches the ML.NET CLI, but the command itself doesn't collect telemetry.</span></span>

<span data-ttu-id="ffbf4-114">在未附加其他命令的情况下，遥测在运行 `mlnet` 命令时处于*未启用*状态。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-114">Telemetry *isn't enabled* when you run the `mlnet` command with no other command attached.</span></span> <span data-ttu-id="ffbf4-115">例如：</span><span class="sxs-lookup"><span data-stu-id="ffbf4-115">For example:</span></span>

- `mlnet`
- `mlnet --help`

<span data-ttu-id="ffbf4-116">运行 [ML.NET CLI 命令](../reference/ml-net-cli-reference.md)（例如 `mlnet classification`）时，遥测处于*启用*状态。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-116">Telemetry *is enabled* when you run an [ML.NET CLI command](../reference/ml-net-cli-reference.md), such as `mlnet classification`.</span></span>

## <a name="opt-out-of-data-collection"></a><span data-ttu-id="ffbf4-117">选择退出数据收集</span><span class="sxs-lookup"><span data-stu-id="ffbf4-117">Opt out of data collection</span></span>

<span data-ttu-id="ffbf4-118">ML.NET CLI 遥测功能默认处于启用状态。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-118">The ML.NET CLI telemetry feature is enabled by default.</span></span>

<span data-ttu-id="ffbf4-119">通过将 `MLDOTNET_CLI_TELEMETRY_OPTOUT` 环境变量设置为 `1` 或 `true`，可以选择退出遥测功能。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-119">Opt out of the telemetry feature by setting the `MLDOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.</span></span> <span data-ttu-id="ffbf4-120">此环境变量全局适用于 ML.NET CLI 工具。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-120">This environment variable applies globally to the ML.NET CLI tool.</span></span>

## <a name="data-points-collected"></a><span data-ttu-id="ffbf4-121">收集的数据点</span><span class="sxs-lookup"><span data-stu-id="ffbf4-121">Data points collected</span></span>

<span data-ttu-id="ffbf4-122">此功能收集以下数据：</span><span class="sxs-lookup"><span data-stu-id="ffbf4-122">The feature collects the following data:</span></span>

- <span data-ttu-id="ffbf4-123">调用了哪个命令，如 `classification`</span><span class="sxs-lookup"><span data-stu-id="ffbf4-123">What command was invoked, such as `classification`</span></span>
- <span data-ttu-id="ffbf4-124">使用的命令行参数名称（即“dataset、label-col、output-path、train-time、verbosity”）</span><span class="sxs-lookup"><span data-stu-id="ffbf4-124">Command-line parameter names used (that is, "dataset, label-col, output-path, train-time, verbosity")</span></span>
- <span data-ttu-id="ffbf4-125">经过哈希处理的 MAC 地址：计算机的加密 (SHA256) 匿名唯一 ID</span><span class="sxs-lookup"><span data-stu-id="ffbf4-125">Hashed MAC address: a cryptographically (SHA256) anonymous and unique ID for a machine</span></span>
- <span data-ttu-id="ffbf4-126">调用时间戳</span><span class="sxs-lookup"><span data-stu-id="ffbf4-126">Timestamp of an invocation</span></span>
- <span data-ttu-id="ffbf4-127">仅用于确定地理位置的三个八进制数 IP 地址（不是完整 IP 地址）</span><span class="sxs-lookup"><span data-stu-id="ffbf4-127">Three octet IP address (not full IP address) used only to determine geographical location</span></span>
- <span data-ttu-id="ffbf4-128">使用的所有自变量/参数的名称。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-128">Name of all arguments/parameters used.</span></span> <span data-ttu-id="ffbf4-129">不属于客户提供的值，例如字符串</span><span class="sxs-lookup"><span data-stu-id="ffbf4-129">Not the customer's values, such as strings</span></span>
- <span data-ttu-id="ffbf4-130">经过哈希处理的数据集的文件名</span><span class="sxs-lookup"><span data-stu-id="ffbf4-130">Hashed dataset filename</span></span>
- <span data-ttu-id="ffbf4-131">数据集文件大小存储桶</span><span class="sxs-lookup"><span data-stu-id="ffbf4-131">Dataset file-size bucket</span></span>
- <span data-ttu-id="ffbf4-132">操作系统和版本</span><span class="sxs-lookup"><span data-stu-id="ffbf4-132">Operating system and version</span></span>
- <span data-ttu-id="ffbf4-133">ML 任务命令的值：分类值，例如 `regression`、`classification` 和 `recommendation`</span><span class="sxs-lookup"><span data-stu-id="ffbf4-133">Value of ML task commands: Categorical values, such as `regression`, `classification`, and `recommendation`</span></span>
- <span data-ttu-id="ffbf4-134">ML.NET CLI 版本（即 0.3.27703.4）</span><span class="sxs-lookup"><span data-stu-id="ffbf4-134">ML.NET CLI version (that is, 0.3.27703.4)</span></span>

<span data-ttu-id="ffbf4-135">数据通过 [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) 技术安全地发送到 Microsoft 服务器，提供对保留数据的受限访问权限，并在严格的安全控制下从安全的 [Azure 存储](https://azure.microsoft.com/services/storage/)系统进行使用。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-135">The data is sent securely to Microsoft servers using [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) technology, held under restricted access, and used under strict security controls from secure [Azure Storage](https://azure.microsoft.com/services/storage/) systems.</span></span>

### <a name="data-points-not-collected"></a><span data-ttu-id="ffbf4-136">未收集的数据点</span><span class="sxs-lookup"><span data-stu-id="ffbf4-136">Data points not collected</span></span>

<span data-ttu-id="ffbf4-137">遥测功能*不*收集：</span><span class="sxs-lookup"><span data-stu-id="ffbf4-137">The telemetry feature *doesn't* collect:</span></span>

- <span data-ttu-id="ffbf4-138">个人数据，例如用户名</span><span class="sxs-lookup"><span data-stu-id="ffbf4-138">personal data, such as usernames</span></span>
- <span data-ttu-id="ffbf4-139">数据集文件名</span><span class="sxs-lookup"><span data-stu-id="ffbf4-139">dataset filenames</span></span>
- <span data-ttu-id="ffbf4-140">数据集文件中的数据</span><span class="sxs-lookup"><span data-stu-id="ffbf4-140">data from dataset files</span></span>

<span data-ttu-id="ffbf4-141">如果怀疑 ML.NET CLI 遥测在收集敏感数据，或认为我们处理数据的方式不安全或不恰当，请在 [ML.NET](https://github.com/dotnet/machinelearning) 存储库中记录问题以供调查。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-141">If you suspect that the ML.NET CLI telemetry is collecting sensitive data or that the data is being insecurely or inappropriately handled, file an issue in the [ML.NET](https://github.com/dotnet/machinelearning) repository for investigation.</span></span>

## <a name="license"></a><span data-ttu-id="ffbf4-142">许可证</span><span class="sxs-lookup"><span data-stu-id="ffbf4-142">License</span></span>

<span data-ttu-id="ffbf4-143">ML.NET CLI 的 Microsoft 分发由 [Microsoft 软件许可条款：Microsoft .NET 库](https://aka.ms/dotnet-core-eula)许可。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-143">The Microsoft distribution of ML.NET CLI is licensed with the [Microsoft Software License Terms: Microsoft .NET Library](https://aka.ms/dotnet-core-eula).</span></span> <span data-ttu-id="ffbf4-144">有关数据收集和处理的详细信息，请参阅标题为“数据”的部分。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-144">For details on data collection and processing, see the section entitled "Data."</span></span>

## <a name="disclosure"></a><span data-ttu-id="ffbf4-145">公开</span><span class="sxs-lookup"><span data-stu-id="ffbf4-145">Disclosure</span></span>

<span data-ttu-id="ffbf4-146">首次运行 [ML.NET CLI 命令](../reference/ml-net-cli-reference.md)（例如 `mlnet classification`）时，ML.NET CLI 工具会显示披露信息文本，告诉如何选择退出遥测。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-146">When you first run a [ML.NET CLI command](../reference/ml-net-cli-reference.md) such as `mlnet classification`, the ML.NET CLI tool displays disclosure text that tells you how to opt out of telemetry.</span></span> <span data-ttu-id="ffbf4-147">文本可能会因运行的 CLI 版本而略有不同。</span><span class="sxs-lookup"><span data-stu-id="ffbf4-147">Text may vary slightly depending on the version of the CLI you're running.</span></span>

## <a name="see-also"></a><span data-ttu-id="ffbf4-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="ffbf4-148">See also</span></span>

- [<span data-ttu-id="ffbf4-149">ML.NET CLI 参考</span><span class="sxs-lookup"><span data-stu-id="ffbf4-149">ML.NET CLI reference</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="ffbf4-150">Microsoft 软件许可条款：Microsoft .NET 库</span><span class="sxs-lookup"><span data-stu-id="ffbf4-150">Microsoft Software License Terms: Microsoft .NET Library</span></span>](https://aka.ms/dotnet-core-eula)
- [<span data-ttu-id="ffbf4-151">Microsoft 隐私政策</span><span class="sxs-lookup"><span data-stu-id="ffbf4-151">Privacy at Microsoft</span></span>](https://www.microsoft.com/trustcenter/privacy/)
- [<span data-ttu-id="ffbf4-152">Microsoft 隐私声明</span><span class="sxs-lookup"><span data-stu-id="ffbf4-152">Microsoft Privacy Statement</span></span>](https://privacy.microsoft.com/privacystatement)
