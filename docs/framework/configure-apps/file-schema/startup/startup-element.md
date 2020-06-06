---
title: <startup> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: e936c069275bfa9f7ac81ef1c6fc6228828182a8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153721"
---
# <a name="startup-element"></a><span data-ttu-id="e2d87-102">\<startup> 元素</span><span class="sxs-lookup"><span data-stu-id="e2d87-102">\<startup> element</span></span>

<span data-ttu-id="e2d87-103">指定公共语言运行时启动信息。</span><span class="sxs-lookup"><span data-stu-id="e2d87-103">Specifies common language runtime startup information.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<startup>**  

## <a name="syntax"></a><span data-ttu-id="e2d87-104">语法</span><span class="sxs-lookup"><span data-stu-id="e2d87-104">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2d87-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e2d87-105">Attributes and elements</span></span>

 <span data-ttu-id="e2d87-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e2d87-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2d87-107">特性</span><span class="sxs-lookup"><span data-stu-id="e2d87-107">Attributes</span></span>

|<span data-ttu-id="e2d87-108">属性</span><span class="sxs-lookup"><span data-stu-id="e2d87-108">Attribute</span></span>|<span data-ttu-id="e2d87-109">说明</span><span class="sxs-lookup"><span data-stu-id="e2d87-109">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="e2d87-110">可选特性。</span><span class="sxs-lookup"><span data-stu-id="e2d87-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e2d87-111">指定是启用 .NET Framework 2.0 运行时激活策略还是使用 .NET Framework 4 激活策略。</span><span class="sxs-lookup"><span data-stu-id="e2d87-111">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="e2d87-112">useLegacyV2RuntimeActivationPolicy 特性</span><span class="sxs-lookup"><span data-stu-id="e2d87-112">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="e2d87-113">值</span><span class="sxs-lookup"><span data-stu-id="e2d87-113">Value</span></span>|<span data-ttu-id="e2d87-114">说明</span><span class="sxs-lookup"><span data-stu-id="e2d87-114">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="e2d87-115">为所选运行时启用 .NET Framework 2.0 运行时激活策略，该策略将旧式运行时激活技术（如[CorBindToRuntimeEx 函数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)）绑定到从配置文件中选择的运行时，而不是在 CLR 版本2.0 上覆盖它们。</span><span class="sxs-lookup"><span data-stu-id="e2d87-115">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="e2d87-116">因此，如果从配置文件中选择了 CLR 版本4或更高版本，则将用所选的 CLR 版本加载随 .NET Framework 早期版本创建的混合模式程序集。</span><span class="sxs-lookup"><span data-stu-id="e2d87-116">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="e2d87-117">设置此值可防止 CLR 版本1.1 或 CLR 版本2.0 加载到同一进程中，从而有效禁用进程内并行功能。</span><span class="sxs-lookup"><span data-stu-id="e2d87-117">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="e2d87-118">使用 .NET Framework 4 和更高版本的默认激活策略，这是为了允许旧的运行时激活技术将 CLR 版本1.1 或2.0 加载到进程中。</span><span class="sxs-lookup"><span data-stu-id="e2d87-118">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="e2d87-119">设置此值可防止混合模式程序集加载到 .NET Framework 4 或更高版本中，除非它们是用 .NET Framework 4 或更高版本生成的。</span><span class="sxs-lookup"><span data-stu-id="e2d87-119">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="e2d87-120">该值为默认值。</span><span class="sxs-lookup"><span data-stu-id="e2d87-120">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e2d87-121">子元素</span><span class="sxs-lookup"><span data-stu-id="e2d87-121">Child elements</span></span>

|<span data-ttu-id="e2d87-122">元素</span><span class="sxs-lookup"><span data-stu-id="e2d87-122">Element</span></span>|<span data-ttu-id="e2d87-123">描述</span><span class="sxs-lookup"><span data-stu-id="e2d87-123">Description</span></span>|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="e2d87-124">指定应用程序仅支持 1.0 版本的公共语言运行时。</span><span class="sxs-lookup"><span data-stu-id="e2d87-124">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="e2d87-125">使用运行时版本1.1 或更高版本生成的应用程序应使用 **\<supportedRuntime>** 元素。</span><span class="sxs-lookup"><span data-stu-id="e2d87-125">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="e2d87-126">指定应用程序支持的公共语言运行时版本。</span><span class="sxs-lookup"><span data-stu-id="e2d87-126">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e2d87-127">父元素</span><span class="sxs-lookup"><span data-stu-id="e2d87-127">Parent elements</span></span>

|<span data-ttu-id="e2d87-128">元素</span><span class="sxs-lookup"><span data-stu-id="e2d87-128">Element</span></span>|<span data-ttu-id="e2d87-129">描述</span><span class="sxs-lookup"><span data-stu-id="e2d87-129">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="e2d87-130">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="e2d87-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e2d87-131">注解</span><span class="sxs-lookup"><span data-stu-id="e2d87-131">Remarks</span></span>

 <span data-ttu-id="e2d87-132">**\<supportedRuntime>** 元素应由使用版本1.1 或更高版本的运行时生成的所有应用程序使用。</span><span class="sxs-lookup"><span data-stu-id="e2d87-132">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="e2d87-133">构建为仅支持1.0 版运行时的应用程序必须使用 **\<requiredRuntime>** 元素。</span><span class="sxs-lookup"><span data-stu-id="e2d87-133">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="e2d87-134">在 Microsoft Internet Explorer 中托管的应用程序的启动代码将忽略该 **\<startup>** 元素及其子元素。</span><span class="sxs-lookup"><span data-stu-id="e2d87-134">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="e2d87-135">UseLegacyV2RuntimeActivationPolicy 特性</span><span class="sxs-lookup"><span data-stu-id="e2d87-135">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="e2d87-136">如果你的应用程序使用旧的激活路径（如[CorBindToRuntimeEx 函数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)），并且你希望这些路径激活 CLR 版本4（而不是早期版本），或者如果你的应用程序是 .NET Framework 使用 .NET Framework 早期版本生成的混合模式程序集生成的，则此属性很有用。</span><span class="sxs-lookup"><span data-stu-id="e2d87-136">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="e2d87-137">在这些情况下，请将属性设置为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="e2d87-137">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="e2d87-138">设置属性可 `true` 防止 clr 版本1.1 或 clr 版本2.0 加载到同一个进程中，从而有效禁用进程内并行功能（请参阅[COM 互操作的并行执行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))）。</span><span class="sxs-lookup"><span data-stu-id="e2d87-138">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="e2d87-139">示例</span><span class="sxs-lookup"><span data-stu-id="e2d87-139">Example</span></span>

 <span data-ttu-id="e2d87-140">下面的示例演示如何在配置文件中指定运行时版本。</span><span class="sxs-lookup"><span data-stu-id="e2d87-140">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<!-- When used with version 1.0 of the .NET Framework runtime -->
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
<!-- When used with version 1.1 (or later) of the runtime -->
<configuration>
   <startup>
      <supportedRuntime version="v1.1.4322"/>
      <supportedRuntime version="v1.0.3705"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e2d87-141">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e2d87-141">See also</span></span>

- [<span data-ttu-id="e2d87-142">启动设置架构</span><span class="sxs-lookup"><span data-stu-id="e2d87-142">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e2d87-143">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="e2d87-143">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e2d87-144">如何：将应用配置为支持 .NET Framework 4 或更高版本</span><span class="sxs-lookup"><span data-stu-id="e2d87-144">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="e2d87-145">[COM 互操作的并行执行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e2d87-145">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="e2d87-146">进程内并行执行</span><span class="sxs-lookup"><span data-stu-id="e2d87-146">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
