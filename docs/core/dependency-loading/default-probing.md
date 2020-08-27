---
title: 默认探测 - .NET Core
description: 用于定位依赖项的 .NET Core 的 System.Runtime.Loader.AssemblyLoadContext.Default 探测逻辑的概述。
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 13ce4c7de5f6ce1b76b2e61db810c0f19717540f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608419"
---
# <a name="default-probing"></a><span data-ttu-id="dc1b2-103">默认探测</span><span class="sxs-lookup"><span data-stu-id="dc1b2-103">Default probing</span></span>

<span data-ttu-id="dc1b2-104"><xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> 实例负责定位程序集的依赖项。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-104">The <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance is responsible for locating an assembly's dependencies.</span></span> <span data-ttu-id="dc1b2-105">本文介绍 <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> 实例的探测逻辑。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-105">This article describes the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance's probing logic.</span></span>

## <a name="host-configured-probing-properties"></a><span data-ttu-id="dc1b2-106">主机配置的探测属性</span><span class="sxs-lookup"><span data-stu-id="dc1b2-106">Host configured probing properties</span></span>

<span data-ttu-id="dc1b2-107">运行时启动时，运行时主机提供一组命名的探测属性，这些属性可配置 <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> 探测路径。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-107">When the runtime is started, the runtime host provides a set of named probing properties that configure <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> probe paths.</span></span>

<span data-ttu-id="dc1b2-108">每个探测属性均可选。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-108">Each probing property is optional.</span></span> <span data-ttu-id="dc1b2-109">如果存在，则每个属性都是一个字符串值，其中包含绝对路径的分隔列表。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-109">If present, each property is a string value that contains a delimited list of absolute paths.</span></span> <span data-ttu-id="dc1b2-110">在 Windows 上，分隔符为“;”，在所有其他平台上，分隔符为“:”。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-110">The delimiter is ';' on Windows and ':' on all other platforms.</span></span>

|<span data-ttu-id="dc1b2-111">属性名</span><span class="sxs-lookup"><span data-stu-id="dc1b2-111">Property Name</span></span>                 |<span data-ttu-id="dc1b2-112">描述</span><span class="sxs-lookup"><span data-stu-id="dc1b2-112">Description</span></span>  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | <span data-ttu-id="dc1b2-113">平台和应用程序程序集文件路径的列表。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-113">List of platform and application assembly file paths.</span></span> |
|`PLATFORM_RESOURCE_ROOTS`       | <span data-ttu-id="dc1b2-114">用于搜索附属资源程序集的目录路径的列表。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-114">List of directory paths to search for satellite resource assemblies.</span></span> |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | <span data-ttu-id="dc1b2-115">用于搜索非托管（本机）库的目录路径的列表。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-115">List of directory paths to search for unmanaged (native) libraries.</span></span>        |
|`APP_PATHS`                     | <span data-ttu-id="dc1b2-116">用于搜索托管程序集的目录路径的列表。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-116">List of directory paths to search for managed assemblies.</span></span> |
|`APP_NI_PATHS`                  | <span data-ttu-id="dc1b2-117">用于搜索托管程序集的本机映像的目录路径的列表。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-117">List of directory paths to search for native images of managed assemblies.</span></span> |

### <a name="how-are-the-properties-populated"></a><span data-ttu-id="dc1b2-118">如何填充属性？</span><span class="sxs-lookup"><span data-stu-id="dc1b2-118">How are the properties populated?</span></span>

<span data-ttu-id="dc1b2-119">填充属性有两个主要方案，具体取决于 \<myapp>.deps.json 文件是否存在。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-119">There are two main scenarios for populating the properties depending on whether the *\<myapp>.deps.json* file exists.</span></span>

- <span data-ttu-id="dc1b2-120">当 \*.deps.json 文件存在时，将对其进行分析以填充探测属性  。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-120">When the *\*.deps.json* file is present, it's parsed to populate the probing properties.</span></span>
- <span data-ttu-id="dc1b2-121">如果 \*.deps.json  文件不存在，则假定应用程序的目录以包含所有依赖项。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-121">When the *\*.deps.json* file isn't present, the application's directory is assumed to contain all the dependencies.</span></span> <span data-ttu-id="dc1b2-122">目录的内容用于填充探测属性。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-122">The directory's contents are used to populate the probing properties.</span></span>

<span data-ttu-id="dc1b2-123">此外，也会对任何引用框架的 \*.deps.json  文件进行类似的分析。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-123">Additionally, the *\*.deps.json* files for any referenced frameworks are similarly parsed.</span></span>

<span data-ttu-id="dc1b2-124">最后，可使用环境变量 `ADDITIONAL_DEPS` 添加其他依赖项。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-124">Finally the environment variable `ADDITIONAL_DEPS` can be used to add additional dependencies.</span></span>  <span data-ttu-id="dc1b2-125">`dotnet.exe` 还包含一个 `--additional-deps` 可选参数，用于在应用程序启动时设置此值。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-125">`dotnet.exe` also contains an `--additional-deps` optional parameter to set this value on application startup.</span></span>

<span data-ttu-id="dc1b2-126">默认不会填充 `APP_PATHS` 和 `APP_NI_PATHS` 属性，大多数应用程序都省略了它们。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-126">The `APP_PATHS` and `APP_NI_PATHS` properties are not populated by default and are omitted for most applications.</span></span>

<span data-ttu-id="dc1b2-127">可以通过 `System.AppContext.GetData("APP_CONTEXT_DEPS_FILES")` 访问应用程序使用的所有 \*.deps.json 文件的列表。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-127">The list of all *\*.deps.json* files used by the application can be accessed via `System.AppContext.GetData("APP_CONTEXT_DEPS_FILES")`.</span></span>

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a><span data-ttu-id="dc1b2-128">如何查看托管代码中的探测属性？</span><span class="sxs-lookup"><span data-stu-id="dc1b2-128">How do I see the probing properties from managed code?</span></span>

<span data-ttu-id="dc1b2-129">通过使用上表中的属性名称调用 <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> 函数，可查看每个属性。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-129">Each property is available by calling the <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> function with the property name from the table above.</span></span>

### <a name="how-do-i-debug-the-probing-properties-construction"></a><span data-ttu-id="dc1b2-130">如何调试探测属性的构造？</span><span class="sxs-lookup"><span data-stu-id="dc1b2-130">How do I debug the probing properties' construction?</span></span>

<span data-ttu-id="dc1b2-131">启用某些环境变量后，.NET Core 运行时主机将输出有用的跟踪消息：</span><span class="sxs-lookup"><span data-stu-id="dc1b2-131">The .NET Core runtime host will output useful trace messages when certain environment variables are enabled:</span></span>

|<span data-ttu-id="dc1b2-132">环境变量</span><span class="sxs-lookup"><span data-stu-id="dc1b2-132">Environment Variable</span></span>        |<span data-ttu-id="dc1b2-133">描述</span><span class="sxs-lookup"><span data-stu-id="dc1b2-133">Description</span></span>  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |<span data-ttu-id="dc1b2-134">启用跟踪。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-134">Enables tracing.</span></span>|
|`COREHOST_TRACEFILE=<path>` |<span data-ttu-id="dc1b2-135">跟踪文件路径而不是默认 `stderr`。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-135">Traces to a file path instead of the default `stderr`.</span></span>|
|`COREHOST_TRACE_VERBOSITY`  |<span data-ttu-id="dc1b2-136">将详细程度设置为从 1（最低）到 4（最高）。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-136">Sets the verbosity from 1 (lowest) to 4 (highest).</span></span>|

## <a name="managed-assembly-default-probing"></a><span data-ttu-id="dc1b2-137">托管程序集默认探测</span><span class="sxs-lookup"><span data-stu-id="dc1b2-137">Managed assembly default probing</span></span>

<span data-ttu-id="dc1b2-138">当探测以定位托管程序集时，<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> 会按以下顺序查找：</span><span class="sxs-lookup"><span data-stu-id="dc1b2-138">When probing to locate a managed assembly, the <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> looks in order at:</span></span>

- <span data-ttu-id="dc1b2-139">与 `TRUSTED_PLATFORM_ASSEMBLIES` 中的 <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> 匹配的文件（在删除文件扩展名之后）。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-139">Files matching the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> in `TRUSTED_PLATFORM_ASSEMBLIES` (after removing file extensions).</span></span>
- <span data-ttu-id="dc1b2-140">包含公共文件扩展名的 `APP_NI_PATHS` 中的本机映像程序集文件。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-140">Native image assembly files in `APP_NI_PATHS` with common file extensions.</span></span>
- <span data-ttu-id="dc1b2-141">包含公共文件扩展名的 `APP_PATHS` 中的程序集文件。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-141">Assembly files in `APP_PATHS` with common file extensions.</span></span>

## <a name="satellite-resource-assembly-probing"></a><span data-ttu-id="dc1b2-142">附属（资源）程序集探测</span><span class="sxs-lookup"><span data-stu-id="dc1b2-142">Satellite (resource) assembly probing</span></span>

<span data-ttu-id="dc1b2-143">若要查找特定区域性的附属程序集，请构造一组文件路径。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-143">To find a satellite assembly for a specific culture, construct a set of file paths.</span></span>

<span data-ttu-id="dc1b2-144">对于 `PLATFORM_RESOURCE_ROOTS` 和 `APP_PATHS` 中的每个路径，附加 <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> 字符串、目录分隔符、<xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> 字符串和扩展名“.dll”。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-144">For each path in `PLATFORM_RESOURCE_ROOTS` and then `APP_PATHS`, append the <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> string, a directory separator, the <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> string, and the extension '.dll'.</span></span>

<span data-ttu-id="dc1b2-145">如果存在任何匹配的文件，请尝试加载并返回该文件。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-145">If any matching file exists, attempt to load and return it.</span></span>

## <a name="unmanaged-native-library-probing"></a><span data-ttu-id="dc1b2-146">非托管（本机）库探测</span><span class="sxs-lookup"><span data-stu-id="dc1b2-146">Unmanaged (native) library probing</span></span>

<span data-ttu-id="dc1b2-147">当探测以查找非托管库时，将搜索 `NATIVE_DLL_SEARCH_DIRECTORIES` 以查找匹配库。</span><span class="sxs-lookup"><span data-stu-id="dc1b2-147">When probing to locate an unmanaged library, the `NATIVE_DLL_SEARCH_DIRECTORIES` are searched looking for a matching library.</span></span>
