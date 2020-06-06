---
title: <supportedRuntime>配置元素-.NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: ecbe73593e5b8b87909499f6fff7e865e29b1ec8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "82796036"
---
# <a name="supportedruntime-element"></a><span data-ttu-id="52107-102">\<supportedRuntime> 元素</span><span class="sxs-lookup"><span data-stu-id="52107-102">\<supportedRuntime> element</span></span>

<span data-ttu-id="52107-103">指定应用程序支持的公共语言运行时版本和（可选） .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="52107-103">Specifies which common language runtime version and, optionally, .NET Framework version the application supports.</span></span>  

[\<configuration>](../configuration-element.md)  
&nbsp;&nbsp;[\<startup>](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<supportedRuntime>**  

## <a name="syntax"></a><span data-ttu-id="52107-104">语法</span><span class="sxs-lookup"><span data-stu-id="52107-104">Syntax</span></span>

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a><span data-ttu-id="52107-105">特性</span><span class="sxs-lookup"><span data-stu-id="52107-105">Attributes</span></span>

|<span data-ttu-id="52107-106">属性</span><span class="sxs-lookup"><span data-stu-id="52107-106">Attribute</span></span>|<span data-ttu-id="52107-107">说明</span><span class="sxs-lookup"><span data-stu-id="52107-107">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="52107-108">**version**</span><span class="sxs-lookup"><span data-stu-id="52107-108">**version**</span></span>|<span data-ttu-id="52107-109">可选特性。</span><span class="sxs-lookup"><span data-stu-id="52107-109">Optional attribute.</span></span><br /><br /> <span data-ttu-id="52107-110">一个字符串值，它指定此应用程序支持的公共语言运行时 (CLR) 版本。</span><span class="sxs-lookup"><span data-stu-id="52107-110">A string value that specifies the version of the common language runtime (CLR) that this application supports.</span></span> <span data-ttu-id="52107-111">有关属性的有效值 `version` ，请参阅["运行时版本" 值](#version)部分。</span><span class="sxs-lookup"><span data-stu-id="52107-111">For valid values of the `version` attribute, see the ["runtime version" values](#version) section.</span></span> <span data-ttu-id="52107-112">**注意：** 通过 .NET Framework 3.5，"*运行时版本*" 值采用*主*格式。*次要*。*生成*。</span><span class="sxs-lookup"><span data-stu-id="52107-112">**Note:**  Through the .NET Framework 3.5, the "*runtime version*" value takes the form *major*.*minor*.*build*.</span></span> <span data-ttu-id="52107-113">从 .NET Framework 4 开始，只需要主要版本号和次要版本号（即，"4.0.30319" 而不是 "v"）。</span><span class="sxs-lookup"><span data-stu-id="52107-113">Beginning with the .NET Framework 4, only the major and minor version numbers are required (that is, "v4.0" instead of "v4.0.30319").</span></span> <span data-ttu-id="52107-114">建议使用较短字符串。</span><span class="sxs-lookup"><span data-stu-id="52107-114">The shorter string is recommended.</span></span>|
|<span data-ttu-id="52107-115">**sku**</span><span class="sxs-lookup"><span data-stu-id="52107-115">**sku**</span></span>|<span data-ttu-id="52107-116">可选特性。</span><span class="sxs-lookup"><span data-stu-id="52107-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="52107-117">一个字符串值，该值指定库存单位 (SKU)，库存单位则指定此应用程序支持的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="52107-117">A string value that specifies the stock-keeping unit (SKU), which in turn specifies which .NET Framework release this application supports.</span></span><br /><br /> <span data-ttu-id="52107-118">从 .NET Framework 4.0 起，建议使用 `sku` 特性。</span><span class="sxs-lookup"><span data-stu-id="52107-118">Starting with the .NET Framework 4.0, the use of the `sku` attribute is recommended.</span></span>  <span data-ttu-id="52107-119">若存在该特性，则它指示应用面向的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="52107-119">When present, it indicates the version of the .NET Framework that the app targets.</span></span><br /><br /> <span data-ttu-id="52107-120">有关 sku 属性的有效值，请参阅["sku id" 值](#sku)一节。</span><span class="sxs-lookup"><span data-stu-id="52107-120">For valid values of the sku attribute, see the ["sku id" values](#sku) section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="52107-121">注解</span><span class="sxs-lookup"><span data-stu-id="52107-121">Remarks</span></span>

<span data-ttu-id="52107-122">如果 **\<supportedRuntime>** 应用程序配置文件中不存在该元素，则使用用于生成应用程序的运行时版本。</span><span class="sxs-lookup"><span data-stu-id="52107-122">If the **\<supportedRuntime>** element is not present in the application configuration file, the version of the runtime used to build the application is used.</span></span>

<span data-ttu-id="52107-123">**\<supportedRuntime>** 元素应由使用版本1.1 或更高版本的运行时生成的所有应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="52107-123">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="52107-124">构建为仅支持1.0 版运行时的应用程序必须使用 [\<requiredRuntime>](requiredruntime-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="52107-124">Applications built to support only version 1.0 of the runtime must use the [\<requiredRuntime>](requiredruntime-element.md) element.</span></span>

> [!NOTE]
> <span data-ttu-id="52107-125">如果使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)函数指定配置文件，则必须将 `<requiredRuntime>` 元素用于运行时的所有版本。</span><span class="sxs-lookup"><span data-stu-id="52107-125">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="52107-126">`<supportedRuntime>`当使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)时，将忽略元素。</span><span class="sxs-lookup"><span data-stu-id="52107-126">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>  
  
<span data-ttu-id="52107-127">对于支持从 .NET Framework 1.1 到 3.5 的运行时版本的应用，支持多个运行时版本时，第一个元素应指定优先级最高的版本，最后一个元素应指定优先级最低的版本。</span><span class="sxs-lookup"><span data-stu-id="52107-127">For apps that support versions of the runtime from the .NET Framework 1.1 through 3.5, when multiple versions of the runtime are supported, the first element should specify the most preferred version of the runtime, and the last element should specify the least preferred version.</span></span> <span data-ttu-id="52107-128">对于支持 .NET Framework 4.0 或更高版本的应用程序，该 `version` 属性指示 CLR 版本（对于 .NET Framework 4 及更高版本是通用的）， `sku` 属性指示应用面向的单一 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="52107-128">For apps that support the .NET Framework 4.0 or later versions, the `version` attribute indicates the CLR version, which is common to the .NET Framework 4 and later versions, and the `sku` attribute indicates the single .NET Framework version that the app targets.</span></span>

<span data-ttu-id="52107-129">如果 **\<supportedRuntime>** `sku` 配置文件中存在具有属性的元素，并且安装的 .NET Framework 版本低于指定的受支持版本，应用程序将无法运行，而是显示一条消息要求安装支持的版本。</span><span class="sxs-lookup"><span data-stu-id="52107-129">If the **\<supportedRuntime>** element with the `sku` attribute is present in the configuration file and the installed .NET Framework version is lower then the specified supported version, the application fails to run and instead displays a message asking to install the supported version.</span></span> <span data-ttu-id="52107-130">否则，应用程序会尝试在任何已安装的版本上运行，但如果该版本与该版本不完全兼容，则它可能会发生意外行为。</span><span class="sxs-lookup"><span data-stu-id="52107-130">Otherwise, the application attempts to run on any installed version, but it may behave unexpectedly if it is not fully compatible with that version.</span></span> <span data-ttu-id="52107-131">（若要了解 .NET Framework 版本之间的兼容性差异，请参阅[.NET Framework 中的应用程序兼容性](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility)。）因此，建议你在应用程序配置文件中包括此元素，以便更轻松地诊断错误。</span><span class="sxs-lookup"><span data-stu-id="52107-131">(For compatibility differences between versions of .NET Framework, see [Application compatibility in the .NET Framework](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility).) Therefore, we recommend that you include this element in the application configuration file for easier error diagnostics.</span></span> <span data-ttu-id="52107-132">（创建新项目时，由 Visual Studio 自动生成的配置文件已经包含了该文件。）</span><span class="sxs-lookup"><span data-stu-id="52107-132">(The configuration file automatically generated by Visual Studio when creating a new project already contains it.)</span></span>
  
> [!NOTE]
> <span data-ttu-id="52107-133">如果你的应用程序使用旧的激活路径（如[CorBindToRuntimeEx 函数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)），并且你希望这些路径激活 CLR 的版本4（而不是早期版本），或者如果你的应用程序是 .NET Framework 使用 .NET Framework 早期版本生成的混合模式程序集生成的，则在受支持的运行时列表中指定 .NET Framework 4 并不足够。</span><span class="sxs-lookup"><span data-stu-id="52107-133">If your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework, it is not sufficient to specify the .NET Framework 4 in the list of supported runtimes.</span></span> <span data-ttu-id="52107-134">此外，在配置文件的[ \<startup> 元素](startup-element.md)中，你必须将 `useLegacyV2RuntimeActivationPolicy` 属性设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="52107-134">In addition, in the [\<startup> element](startup-element.md) in your configuration file, you must set the `useLegacyV2RuntimeActivationPolicy` attribute to `true`.</span></span> <span data-ttu-id="52107-135">但是，将此特性设置为 `true` 意味着使用 .NET Framework 4 （而不是生成它们的运行时）运行使用 .NET Framework 的早期版本生成的所有组件。</span><span class="sxs-lookup"><span data-stu-id="52107-135">However, setting this attribute to `true` means that all components built with earlier versions of the .NET Framework are run using the .NET Framework 4 instead of the runtimes they were built with.</span></span>

<span data-ttu-id="52107-136">我们建议你使用应用程序可在其上运行的所有 .NET Framework 版本来测试这些应用程序。</span><span class="sxs-lookup"><span data-stu-id="52107-136">We recommend that you test applications with all the .NET Framework versions that they can run on.</span></span>

<a name="version"></a>
## <a name="runtime-version-values"></a><span data-ttu-id="52107-137">“运行时版本”值</span><span class="sxs-lookup"><span data-stu-id="52107-137">"runtime version" values</span></span>
<span data-ttu-id="52107-138">`runtime`特性指定给定应用程序所需的公共语言运行时（CLR）版本。</span><span class="sxs-lookup"><span data-stu-id="52107-138">The `runtime` attribute specifies the Common Language Runtime (CLR) version that is required for a given application.</span></span> <span data-ttu-id="52107-139">请注意，所有 .NET Framework v4. x 版本都指定 `v4.0` CLR。</span><span class="sxs-lookup"><span data-stu-id="52107-139">Note that all .NET Framework v4.x versions specify the `v4.0` CLR.</span></span> <span data-ttu-id="52107-140">下表列出了属性的*运行时版本*值的有效值 `version` 。</span><span class="sxs-lookup"><span data-stu-id="52107-140">The following table lists valid values for the *runtime version* value of the `version` attribute.</span></span>

|<span data-ttu-id="52107-141">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="52107-141">.NET Framework version</span></span>|<span data-ttu-id="52107-142">`version` 特性</span><span class="sxs-lookup"><span data-stu-id="52107-142">`version` attribute</span></span>|
|----------------------------|-------------------------|
|<span data-ttu-id="52107-143">1.0</span><span class="sxs-lookup"><span data-stu-id="52107-143">1.0</span></span>|<span data-ttu-id="52107-144">"v1.0.3705"</span><span class="sxs-lookup"><span data-stu-id="52107-144">"v1.0.3705"</span></span>|
|<span data-ttu-id="52107-145">1.1</span><span class="sxs-lookup"><span data-stu-id="52107-145">1.1</span></span>|<span data-ttu-id="52107-146">"v1.1.4322"</span><span class="sxs-lookup"><span data-stu-id="52107-146">"v1.1.4322"</span></span>|
|<span data-ttu-id="52107-147">2.0</span><span class="sxs-lookup"><span data-stu-id="52107-147">2.0</span></span>|<span data-ttu-id="52107-148">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="52107-148">"v2.0.50727"</span></span>|
|<span data-ttu-id="52107-149">3.0</span><span class="sxs-lookup"><span data-stu-id="52107-149">3.0</span></span>|<span data-ttu-id="52107-150">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="52107-150">"v2.0.50727"</span></span>|
|<span data-ttu-id="52107-151">3.5</span><span class="sxs-lookup"><span data-stu-id="52107-151">3.5</span></span>|<span data-ttu-id="52107-152">"v2.0.50727"</span><span class="sxs-lookup"><span data-stu-id="52107-152">"v2.0.50727"</span></span>|
|<span data-ttu-id="52107-153">4.0-4。8</span><span class="sxs-lookup"><span data-stu-id="52107-153">4.0-4.8</span></span>|<span data-ttu-id="52107-154">"v4.0"</span><span class="sxs-lookup"><span data-stu-id="52107-154">"v4.0"</span></span>|

## <a name="sku-id-values"></a><a name="sku"></a><span data-ttu-id="52107-155">"sku id" 值</span><span class="sxs-lookup"><span data-stu-id="52107-155">"sku id" values</span></span>

<span data-ttu-id="52107-156">`sku`属性使用目标框架名字对象（TFM）来指示应用面向的 .NET Framework 版本，并要求运行该版本。</span><span class="sxs-lookup"><span data-stu-id="52107-156">The `sku` attribute uses a target framework moniker (TFM) to indicate the version of the .NET Framework that the app targets and requires to run.</span></span> <span data-ttu-id="52107-157">下表列出了属性支持的有效值 `sku` ，从 .NET Framework 4 开始。</span><span class="sxs-lookup"><span data-stu-id="52107-157">The following table lists valid values that are supported by the `sku` attribute, starting with the .NET Framework 4.</span></span>

|<span data-ttu-id="52107-158">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="52107-158">.NET Framework version</span></span>|<span data-ttu-id="52107-159">`sku` 特性</span><span class="sxs-lookup"><span data-stu-id="52107-159">`sku` attribute</span></span>|
|----------------------------|---------------------|
|<span data-ttu-id="52107-160">4.0</span><span class="sxs-lookup"><span data-stu-id="52107-160">4.0</span></span>|<span data-ttu-id="52107-161">".NETFramework,Version=v4.0"</span><span class="sxs-lookup"><span data-stu-id="52107-161">".NETFramework,Version=v4.0"</span></span>|
|<span data-ttu-id="52107-162">4.0，客户端配置文件</span><span class="sxs-lookup"><span data-stu-id="52107-162">4.0, Client Profile</span></span>|<span data-ttu-id="52107-163">".NETFramework,Version=v4.0,Profile=Client"</span><span class="sxs-lookup"><span data-stu-id="52107-163">".NETFramework,Version=v4.0,Profile=Client"</span></span>|
|<span data-ttu-id="52107-164">4.0，平台更新 1</span><span class="sxs-lookup"><span data-stu-id="52107-164">4.0, platform update 1</span></span>|<span data-ttu-id="52107-165">"..Netframework，Version = v 4.0.1 "</span><span class="sxs-lookup"><span data-stu-id="52107-165">".NETFramework,Version=v4.0.1"</span></span>|
|<span data-ttu-id="52107-166">4.0，客户端配置文件，Update 1</span><span class="sxs-lookup"><span data-stu-id="52107-166">4.0, Client Profile, update 1</span></span>|<span data-ttu-id="52107-167">"..Netframework，Version = v 4.0.1，Profile = Client "</span><span class="sxs-lookup"><span data-stu-id="52107-167">".NETFramework,Version=v4.0.1,Profile=Client"</span></span>|
|<span data-ttu-id="52107-168">4.0，平台更新 2</span><span class="sxs-lookup"><span data-stu-id="52107-168">4.0, platform update 2</span></span>|<span data-ttu-id="52107-169">"..Netframework，Version = v 4.0.2 "</span><span class="sxs-lookup"><span data-stu-id="52107-169">".NETFramework,Version=v4.0.2"</span></span>|
|<span data-ttu-id="52107-170">4.0，客户端配置文件，Update 2</span><span class="sxs-lookup"><span data-stu-id="52107-170">4.0, Client Profile, update 2</span></span>|<span data-ttu-id="52107-171">"..Netframework，Version = v 4.0.2，Profile = Client "</span><span class="sxs-lookup"><span data-stu-id="52107-171">".NETFramework,Version=v4.0.2,Profile=Client"</span></span>|
|<span data-ttu-id="52107-172">4.0，平台更新 3</span><span class="sxs-lookup"><span data-stu-id="52107-172">4.0, platform update 3</span></span>|<span data-ttu-id="52107-173">"..Netframework，Version = v 4.0.3 "</span><span class="sxs-lookup"><span data-stu-id="52107-173">".NETFramework,Version=v4.0.3"</span></span>|
|<span data-ttu-id="52107-174">4.0，客户端配置文件，Update 3</span><span class="sxs-lookup"><span data-stu-id="52107-174">4.0, Client Profile, update 3</span></span>|<span data-ttu-id="52107-175">"..Netframework，Version = v 4.0.3，Profile = Client "</span><span class="sxs-lookup"><span data-stu-id="52107-175">".NETFramework,Version=v4.0.3,Profile=Client"</span></span>|
|<span data-ttu-id="52107-176">4.5</span><span class="sxs-lookup"><span data-stu-id="52107-176">4.5</span></span>|<span data-ttu-id="52107-177">".NETFramework,Version=v4.5"</span><span class="sxs-lookup"><span data-stu-id="52107-177">".NETFramework,Version=v4.5"</span></span>|
|<span data-ttu-id="52107-178">4.5.1</span><span class="sxs-lookup"><span data-stu-id="52107-178">4.5.1</span></span>|<span data-ttu-id="52107-179">".NETFramework,Version=v4.5"</span><span class="sxs-lookup"><span data-stu-id="52107-179">".NETFramework,Version=v4.5.1"</span></span>|
|<span data-ttu-id="52107-180">4.5.2</span><span class="sxs-lookup"><span data-stu-id="52107-180">4.5.2</span></span>|<span data-ttu-id="52107-181">".NETFramework,Version=v4.5"</span><span class="sxs-lookup"><span data-stu-id="52107-181">".NETFramework,Version=v4.5.2"</span></span>|
|<span data-ttu-id="52107-182">4.6</span><span class="sxs-lookup"><span data-stu-id="52107-182">4.6</span></span>|<span data-ttu-id="52107-183">".NETFramework,Version=v4.5"</span><span class="sxs-lookup"><span data-stu-id="52107-183">".NETFramework,Version=v4.6"</span></span>|
|<span data-ttu-id="52107-184">4.6.1</span><span class="sxs-lookup"><span data-stu-id="52107-184">4.6.1</span></span>|<span data-ttu-id="52107-185">".NETFramework,Version=v4.5"</span><span class="sxs-lookup"><span data-stu-id="52107-185">".NETFramework,Version=v4.6.1"</span></span>|
|<span data-ttu-id="52107-186">4.6.2</span><span class="sxs-lookup"><span data-stu-id="52107-186">4.6.2</span></span>|<span data-ttu-id="52107-187">"..Netframework，Version = v 4.6.2 "</span><span class="sxs-lookup"><span data-stu-id="52107-187">".NETFramework,Version=v4.6.2"</span></span>|
|<span data-ttu-id="52107-188">4.7</span><span class="sxs-lookup"><span data-stu-id="52107-188">4.7</span></span>|<span data-ttu-id="52107-189">"..Netframework，Version = 4.7 "</span><span class="sxs-lookup"><span data-stu-id="52107-189">".NETFramework,Version=v4.7"</span></span>|
|<span data-ttu-id="52107-190">4.7.1</span><span class="sxs-lookup"><span data-stu-id="52107-190">4.7.1</span></span>|<span data-ttu-id="52107-191">"..Netframework，Version = v 4.7.1 "</span><span class="sxs-lookup"><span data-stu-id="52107-191">".NETFramework,Version=v4.7.1"</span></span>|
|<span data-ttu-id="52107-192">4.7.2</span><span class="sxs-lookup"><span data-stu-id="52107-192">4.7.2</span></span>|<span data-ttu-id="52107-193">"..Netframework，Version = v 4.7.2 "</span><span class="sxs-lookup"><span data-stu-id="52107-193">".NETFramework,Version=v4.7.2"</span></span>|
|<span data-ttu-id="52107-194">4.8</span><span class="sxs-lookup"><span data-stu-id="52107-194">4.8</span></span>|<span data-ttu-id="52107-195">"..Netframework，Version = v4.0 "</span><span class="sxs-lookup"><span data-stu-id="52107-195">".NETFramework,Version=v4.8"</span></span>|

## <a name="example"></a><span data-ttu-id="52107-196">示例</span><span class="sxs-lookup"><span data-stu-id="52107-196">Example</span></span>

<span data-ttu-id="52107-197">下面的示例演示如何在配置文件中指定支持的运行时版本。</span><span class="sxs-lookup"><span data-stu-id="52107-197">The following example shows how to specify the supported runtime version in a configuration file.</span></span> <span data-ttu-id="52107-198">配置文件指示应用面向 .NET Framework 4.7。</span><span class="sxs-lookup"><span data-stu-id="52107-198">The configuration file indicates that the app targets the .NET Framework 4.7.</span></span>

```xml
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />
   </startup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="52107-199">配置文件</span><span class="sxs-lookup"><span data-stu-id="52107-199">Configuration file</span></span>

<span data-ttu-id="52107-200">此元素可用于应用程序配置文件中。</span><span class="sxs-lookup"><span data-stu-id="52107-200">This element can be used in the application configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="52107-201">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52107-201">See also</span></span>

- [<span data-ttu-id="52107-202">启动设置架构</span><span class="sxs-lookup"><span data-stu-id="52107-202">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="52107-203">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="52107-203">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="52107-204">进程内并行执行</span><span class="sxs-lookup"><span data-stu-id="52107-204">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
