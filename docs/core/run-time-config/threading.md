---
title: 线程配置设置
description: 了解为 .NET Core 应用配置线程的运行时设置。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 1c7c16993a07ef95223481791153b75ab2f61533
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761923"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="a0781-103">用于线程的运行时配置选项</span><span class="sxs-lookup"><span data-stu-id="a0781-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="a0781-104">CPU 组</span><span class="sxs-lookup"><span data-stu-id="a0781-104">CPU groups</span></span>

- <span data-ttu-id="a0781-105">配置是否在各 CPU 组之间自动分布线程。</span><span class="sxs-lookup"><span data-stu-id="a0781-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="a0781-106">如果省略此设置，则不会跨 CPU 组分布线程。</span><span class="sxs-lookup"><span data-stu-id="a0781-106">If you omit this setting, threads are not distributed across CPU groups.</span></span> <span data-ttu-id="a0781-107">它等效于将值设置为 `0`。</span><span class="sxs-lookup"><span data-stu-id="a0781-107">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="a0781-108">设置名</span><span class="sxs-lookup"><span data-stu-id="a0781-108">Setting name</span></span> | <span data-ttu-id="a0781-109">值</span><span class="sxs-lookup"><span data-stu-id="a0781-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a0781-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a0781-110">**runtimeconfig.json**</span></span> | <span data-ttu-id="a0781-111">不可用</span><span class="sxs-lookup"><span data-stu-id="a0781-111">N/A</span></span> | <span data-ttu-id="a0781-112">不可用</span><span class="sxs-lookup"><span data-stu-id="a0781-112">N/A</span></span> |
| <span data-ttu-id="a0781-113">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="a0781-113">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="a0781-114">`0` - 禁用</span><span class="sxs-lookup"><span data-stu-id="a0781-114">`0` - disabled</span></span><br/><span data-ttu-id="a0781-115">`1` - 启用</span><span class="sxs-lookup"><span data-stu-id="a0781-115">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="a0781-116">最小线程数</span><span class="sxs-lookup"><span data-stu-id="a0781-116">Minimum threads</span></span>

- <span data-ttu-id="a0781-117">指定工作线程池的最小线程数。</span><span class="sxs-lookup"><span data-stu-id="a0781-117">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="a0781-118">对应于 <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a0781-118">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="a0781-119">设置名</span><span class="sxs-lookup"><span data-stu-id="a0781-119">Setting name</span></span> | <span data-ttu-id="a0781-120">值</span><span class="sxs-lookup"><span data-stu-id="a0781-120">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a0781-121">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a0781-121">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="a0781-122">一个表示最小线程数的整数</span><span class="sxs-lookup"><span data-stu-id="a0781-122">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="a0781-123">MSBuild 属性</span><span class="sxs-lookup"><span data-stu-id="a0781-123">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="a0781-124">一个表示最小线程数的整数</span><span class="sxs-lookup"><span data-stu-id="a0781-124">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="a0781-125">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="a0781-125">**Environment variable**</span></span> | <span data-ttu-id="a0781-126">不可用</span><span class="sxs-lookup"><span data-stu-id="a0781-126">N/A</span></span> | <span data-ttu-id="a0781-127">不可用</span><span class="sxs-lookup"><span data-stu-id="a0781-127">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="a0781-128">示例</span><span class="sxs-lookup"><span data-stu-id="a0781-128">Examples</span></span>

<span data-ttu-id="a0781-129">runtimeconfig.json 文件：</span><span class="sxs-lookup"><span data-stu-id="a0781-129">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="a0781-130">项目文件：</span><span class="sxs-lookup"><span data-stu-id="a0781-130">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="a0781-131">最大线程数</span><span class="sxs-lookup"><span data-stu-id="a0781-131">Maximum threads</span></span>

- <span data-ttu-id="a0781-132">指定工作线程池的最大线程数。</span><span class="sxs-lookup"><span data-stu-id="a0781-132">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="a0781-133">对应于 <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a0781-133">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="a0781-134">设置名</span><span class="sxs-lookup"><span data-stu-id="a0781-134">Setting name</span></span> | <span data-ttu-id="a0781-135">值</span><span class="sxs-lookup"><span data-stu-id="a0781-135">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a0781-136">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a0781-136">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="a0781-137">一个表示最大线程数的整数</span><span class="sxs-lookup"><span data-stu-id="a0781-137">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="a0781-138">MSBuild 属性</span><span class="sxs-lookup"><span data-stu-id="a0781-138">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="a0781-139">一个表示最大线程数的整数</span><span class="sxs-lookup"><span data-stu-id="a0781-139">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="a0781-140">**环境变量**</span><span class="sxs-lookup"><span data-stu-id="a0781-140">**Environment variable**</span></span> | <span data-ttu-id="a0781-141">不可用</span><span class="sxs-lookup"><span data-stu-id="a0781-141">N/A</span></span> | <span data-ttu-id="a0781-142">不可用</span><span class="sxs-lookup"><span data-stu-id="a0781-142">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="a0781-143">示例</span><span class="sxs-lookup"><span data-stu-id="a0781-143">Examples</span></span>

<span data-ttu-id="a0781-144">runtimeconfig.json 文件：</span><span class="sxs-lookup"><span data-stu-id="a0781-144">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="a0781-145">项目文件：</span><span class="sxs-lookup"><span data-stu-id="a0781-145">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
