---
title: 调试分析配置设置
description: 了解为 .NET Core 应用配置调试和分析的运行时设置。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 5efd0f776da4b7ce6ff7f3bdfda24feec6e00f79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761988"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="99ed7-103">用于调试和分析的运行时配置选项</span><span class="sxs-lookup"><span data-stu-id="99ed7-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="99ed7-104">启用诊断</span><span class="sxs-lookup"><span data-stu-id="99ed7-104">Enable diagnostics</span></span>

- <span data-ttu-id="99ed7-105">配置是启用还是禁用调试器、探查器和 EventPipe 诊断。</span><span class="sxs-lookup"><span data-stu-id="99ed7-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="99ed7-106">如果省略此设置，则会启用诊断。</span><span class="sxs-lookup"><span data-stu-id="99ed7-106">If you omit this setting, diagnostics are enabled.</span></span> <span data-ttu-id="99ed7-107">它等效于将值设置为 `1`。</span><span class="sxs-lookup"><span data-stu-id="99ed7-107">This is equivalent to setting the value to `1`.</span></span>

| | <span data-ttu-id="99ed7-108">设置名</span><span class="sxs-lookup"><span data-stu-id="99ed7-108">Setting name</span></span> | <span data-ttu-id="99ed7-109">值</span><span class="sxs-lookup"><span data-stu-id="99ed7-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="99ed7-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="99ed7-110">**runtimeconfig.json**</span></span> | <span data-ttu-id="99ed7-111">不可用</span><span class="sxs-lookup"><span data-stu-id="99ed7-111">N/A</span></span> | <span data-ttu-id="99ed7-112">不可用</span><span class="sxs-lookup"><span data-stu-id="99ed7-112">N/A</span></span> |
| <span data-ttu-id="99ed7-113">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="99ed7-113">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="99ed7-114">`1` - 启用</span><span class="sxs-lookup"><span data-stu-id="99ed7-114">`1` - enabled</span></span><br/><span data-ttu-id="99ed7-115">`0` - 禁用</span><span class="sxs-lookup"><span data-stu-id="99ed7-115">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="99ed7-116">启用分析</span><span class="sxs-lookup"><span data-stu-id="99ed7-116">Enable profiling</span></span>

- <span data-ttu-id="99ed7-117">配置是否为当前正在运行的进程启用分析。</span><span class="sxs-lookup"><span data-stu-id="99ed7-117">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="99ed7-118">如果省略此设置，则会禁用分析。</span><span class="sxs-lookup"><span data-stu-id="99ed7-118">If you omit this setting, profiling is disabled.</span></span> <span data-ttu-id="99ed7-119">它等效于将值设置为 `0`。</span><span class="sxs-lookup"><span data-stu-id="99ed7-119">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="99ed7-120">设置名</span><span class="sxs-lookup"><span data-stu-id="99ed7-120">Setting name</span></span> | <span data-ttu-id="99ed7-121">值</span><span class="sxs-lookup"><span data-stu-id="99ed7-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="99ed7-122">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="99ed7-122">**runtimeconfig.json**</span></span> | <span data-ttu-id="99ed7-123">不可用</span><span class="sxs-lookup"><span data-stu-id="99ed7-123">N/A</span></span> | <span data-ttu-id="99ed7-124">不可用</span><span class="sxs-lookup"><span data-stu-id="99ed7-124">N/A</span></span> |
| <span data-ttu-id="99ed7-125">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="99ed7-125">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="99ed7-126">`0` - 禁用</span><span class="sxs-lookup"><span data-stu-id="99ed7-126">`0` - disabled</span></span><br/><span data-ttu-id="99ed7-127">`1` - 启用</span><span class="sxs-lookup"><span data-stu-id="99ed7-127">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="99ed7-128">探查器 GUID</span><span class="sxs-lookup"><span data-stu-id="99ed7-128">Profiler GUID</span></span>

- <span data-ttu-id="99ed7-129">指定要加载到当前正在运行的进程中的探查器 GUID。</span><span class="sxs-lookup"><span data-stu-id="99ed7-129">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="99ed7-130">设置名</span><span class="sxs-lookup"><span data-stu-id="99ed7-130">Setting name</span></span> | <span data-ttu-id="99ed7-131">值</span><span class="sxs-lookup"><span data-stu-id="99ed7-131">Values</span></span> |
| - | - | - |
| <span data-ttu-id="99ed7-132">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="99ed7-132">**runtimeconfig.json**</span></span> | <span data-ttu-id="99ed7-133">不可用</span><span class="sxs-lookup"><span data-stu-id="99ed7-133">N/A</span></span> | <span data-ttu-id="99ed7-134">不可用</span><span class="sxs-lookup"><span data-stu-id="99ed7-134">N/A</span></span> |
| <span data-ttu-id="99ed7-135">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="99ed7-135">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="99ed7-136">string-guid</span><span class="sxs-lookup"><span data-stu-id="99ed7-136">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="99ed7-137">探查器位置</span><span class="sxs-lookup"><span data-stu-id="99ed7-137">Profiler location</span></span>

- <span data-ttu-id="99ed7-138">指定要加载到当前正在运行的进程（或 32 位/64 位进程）的探查器 DLL 路径。</span><span class="sxs-lookup"><span data-stu-id="99ed7-138">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="99ed7-139">如果设置了多个变量，则优先使用指定位数的变量。</span><span class="sxs-lookup"><span data-stu-id="99ed7-139">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="99ed7-140">它们指定要加载的探查器的位数。</span><span class="sxs-lookup"><span data-stu-id="99ed7-140">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="99ed7-141">有关详细信息，请参阅 [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md)（查找探查器库）。</span><span class="sxs-lookup"><span data-stu-id="99ed7-141">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="99ed7-142">设置名</span><span class="sxs-lookup"><span data-stu-id="99ed7-142">Setting name</span></span> | <span data-ttu-id="99ed7-143">值</span><span class="sxs-lookup"><span data-stu-id="99ed7-143">Values</span></span> |
| - | - | - |
| <span data-ttu-id="99ed7-144">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="99ed7-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="99ed7-145">string-path</span><span class="sxs-lookup"><span data-stu-id="99ed7-145">*string-path*</span></span> |
| <span data-ttu-id="99ed7-146">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="99ed7-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="99ed7-147">string-path</span><span class="sxs-lookup"><span data-stu-id="99ed7-147">*string-path*</span></span> |
| <span data-ttu-id="99ed7-148">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="99ed7-148">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="99ed7-149">string-path</span><span class="sxs-lookup"><span data-stu-id="99ed7-149">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="99ed7-150">写入 Perf 映射</span><span class="sxs-lookup"><span data-stu-id="99ed7-150">Write perf map</span></span>

- <span data-ttu-id="99ed7-151">允许或禁止在 Linux 系统上写入 /tmp/perf-$pid.map。</span><span class="sxs-lookup"><span data-stu-id="99ed7-151">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="99ed7-152">如果省略此设置，则会禁止写入 Perf 映射。</span><span class="sxs-lookup"><span data-stu-id="99ed7-152">If you omit this setting, writing the perf map is disabled.</span></span> <span data-ttu-id="99ed7-153">它等效于将值设置为 `0`。</span><span class="sxs-lookup"><span data-stu-id="99ed7-153">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="99ed7-154">设置名</span><span class="sxs-lookup"><span data-stu-id="99ed7-154">Setting name</span></span> | <span data-ttu-id="99ed7-155">值</span><span class="sxs-lookup"><span data-stu-id="99ed7-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="99ed7-156">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="99ed7-156">**runtimeconfig.json**</span></span> | <span data-ttu-id="99ed7-157">不可用</span><span class="sxs-lookup"><span data-stu-id="99ed7-157">N/A</span></span> | <span data-ttu-id="99ed7-158">不可用</span><span class="sxs-lookup"><span data-stu-id="99ed7-158">N/A</span></span> |
| <span data-ttu-id="99ed7-159">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="99ed7-159">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="99ed7-160">`0` - 禁用</span><span class="sxs-lookup"><span data-stu-id="99ed7-160">`0` - disabled</span></span><br/><span data-ttu-id="99ed7-161">`1` - 启用</span><span class="sxs-lookup"><span data-stu-id="99ed7-161">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="99ed7-162">性能日志标记</span><span class="sxs-lookup"><span data-stu-id="99ed7-162">Perf log markers</span></span>

- <span data-ttu-id="99ed7-163">允许或禁止在性能日志中将指定信号作为标记予以接受和忽略。</span><span class="sxs-lookup"><span data-stu-id="99ed7-163">Enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="99ed7-164">如果省略此设置，则不会忽略指定的信号。</span><span class="sxs-lookup"><span data-stu-id="99ed7-164">If you omit this setting, the specified signal is not ignored.</span></span> <span data-ttu-id="99ed7-165">它等效于将值设置为 `0`。</span><span class="sxs-lookup"><span data-stu-id="99ed7-165">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="99ed7-166">设置名</span><span class="sxs-lookup"><span data-stu-id="99ed7-166">Setting name</span></span> | <span data-ttu-id="99ed7-167">值</span><span class="sxs-lookup"><span data-stu-id="99ed7-167">Values</span></span> |
| - | - | - |
| <span data-ttu-id="99ed7-168">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="99ed7-168">**runtimeconfig.json**</span></span> | <span data-ttu-id="99ed7-169">不可用</span><span class="sxs-lookup"><span data-stu-id="99ed7-169">N/A</span></span> | <span data-ttu-id="99ed7-170">不可用</span><span class="sxs-lookup"><span data-stu-id="99ed7-170">N/A</span></span> |
| <span data-ttu-id="99ed7-171">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="99ed7-171">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="99ed7-172">`0` - 禁用</span><span class="sxs-lookup"><span data-stu-id="99ed7-172">`0` - disabled</span></span><br/><span data-ttu-id="99ed7-173">`1` - 启用</span><span class="sxs-lookup"><span data-stu-id="99ed7-173">`1` - enabled</span></span> |

> [!NOTE]
> <span data-ttu-id="99ed7-174">如果省略 [COMPlus_PerfMapEnabled](#write-perf-map) 或设置为 `0`（即禁用），则将忽略此设置。</span><span class="sxs-lookup"><span data-stu-id="99ed7-174">This setting is ignored if [COMPlus_PerfMapEnabled](#write-perf-map) is omitted or set to `0` (that is, disabled).</span></span>
