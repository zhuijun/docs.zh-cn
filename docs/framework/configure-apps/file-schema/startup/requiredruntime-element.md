---
title: <requiredRuntime> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: 19fa1561ca3acd845918d952379c5227121465b4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174064"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="e7887-102">\<requiredRuntime> 元素</span><span class="sxs-lookup"><span data-stu-id="e7887-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="e7887-103">指定应用程序仅支持 1.0 版本的公共语言运行时。</span><span class="sxs-lookup"><span data-stu-id="e7887-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="e7887-104">此元素已弃用，不应再使用。</span><span class="sxs-lookup"><span data-stu-id="e7887-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="e7887-105">[`supportedRuntime`](supportedruntime-element.md)应改用元素。</span><span class="sxs-lookup"><span data-stu-id="e7887-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<startup>**](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**  

## <a name="syntax"></a><span data-ttu-id="e7887-106">语法</span><span class="sxs-lookup"><span data-stu-id="e7887-106">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e7887-107">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e7887-107">Attributes and elements</span></span>

<span data-ttu-id="e7887-108">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e7887-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e7887-109">特性</span><span class="sxs-lookup"><span data-stu-id="e7887-109">Attributes</span></span>

|<span data-ttu-id="e7887-110">属性</span><span class="sxs-lookup"><span data-stu-id="e7887-110">Attribute</span></span>|<span data-ttu-id="e7887-111">描述</span><span class="sxs-lookup"><span data-stu-id="e7887-111">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="e7887-112">可选特性。</span><span class="sxs-lookup"><span data-stu-id="e7887-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e7887-113">一个字符串值，该值指定此应用程序支持的 .NET Framework 的版本。</span><span class="sxs-lookup"><span data-stu-id="e7887-113">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="e7887-114">字符串值必须与 .NET Framework 安装根下的目录名称匹配。</span><span class="sxs-lookup"><span data-stu-id="e7887-114">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="e7887-115">不分析字符串值的内容。</span><span class="sxs-lookup"><span data-stu-id="e7887-115">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="e7887-116">可选特性。</span><span class="sxs-lookup"><span data-stu-id="e7887-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e7887-117">指定运行时启动代码是否在注册表中搜索以确定运行时版本。</span><span class="sxs-lookup"><span data-stu-id="e7887-117">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="e7887-118">安全模式特性</span><span class="sxs-lookup"><span data-stu-id="e7887-118">safemode attribute</span></span>

|<span data-ttu-id="e7887-119">值</span><span class="sxs-lookup"><span data-stu-id="e7887-119">Value</span></span>|<span data-ttu-id="e7887-120">描述</span><span class="sxs-lookup"><span data-stu-id="e7887-120">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="e7887-121">运行时启动代码在注册表中查找。</span><span class="sxs-lookup"><span data-stu-id="e7887-121">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="e7887-122">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="e7887-122">This is the default value.</span></span>|
|`true`|<span data-ttu-id="e7887-123">运行时启动代码不会在注册表中查找。</span><span class="sxs-lookup"><span data-stu-id="e7887-123">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e7887-124">子元素</span><span class="sxs-lookup"><span data-stu-id="e7887-124">Child elements</span></span>

<span data-ttu-id="e7887-125">无。</span><span class="sxs-lookup"><span data-stu-id="e7887-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e7887-126">父元素</span><span class="sxs-lookup"><span data-stu-id="e7887-126">Parent elements</span></span>

|<span data-ttu-id="e7887-127">元素</span><span class="sxs-lookup"><span data-stu-id="e7887-127">Element</span></span>|<span data-ttu-id="e7887-128">描述</span><span class="sxs-lookup"><span data-stu-id="e7887-128">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="e7887-129">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="e7887-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="e7887-130">包含 `<requiredRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="e7887-130">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e7887-131">备注</span><span class="sxs-lookup"><span data-stu-id="e7887-131">Remarks</span></span>

 <span data-ttu-id="e7887-132">构建为仅支持1.0 版运行时的应用程序必须使用 `<requiredRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="e7887-132">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="e7887-133">使用版本1.1 或更高版本的运行时生成的应用程序必须使用 `<supportedRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="e7887-133">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="e7887-134">如果使用 [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) 函数指定配置文件，则必须将 `<requiredRuntime>` 元素用于运行时的所有版本。</span><span class="sxs-lookup"><span data-stu-id="e7887-134">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="e7887-135">`<supportedRuntime>`当使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)时，将忽略元素。</span><span class="sxs-lookup"><span data-stu-id="e7887-135">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="e7887-136">`version`特性字符串必须与指定 .NET Framework 版本的安装文件夹名称匹配。</span><span class="sxs-lookup"><span data-stu-id="e7887-136">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="e7887-137">不解释此字符串。</span><span class="sxs-lookup"><span data-stu-id="e7887-137">This string is not interpreted.</span></span> <span data-ttu-id="e7887-138">如果运行时启动代码找不到匹配的文件夹，则不加载运行时;启动代码将显示一条错误消息并退出。</span><span class="sxs-lookup"><span data-stu-id="e7887-138">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="e7887-139">在 Microsoft Internet Explorer 中托管的应用程序的启动代码将忽略该 `<requiredRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="e7887-139">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="e7887-140">示例</span><span class="sxs-lookup"><span data-stu-id="e7887-140">Example</span></span>

<span data-ttu-id="e7887-141">下面的示例演示如何在配置文件中指定运行时版本。</span><span class="sxs-lookup"><span data-stu-id="e7887-141">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e7887-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="e7887-142">See also</span></span>

- [<span data-ttu-id="e7887-143">启动设置架构</span><span class="sxs-lookup"><span data-stu-id="e7887-143">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e7887-144">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="e7887-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e7887-145">如何：将应用配置为支持 .NET Framework 4 或更高版本</span><span class="sxs-lookup"><span data-stu-id="e7887-145">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
