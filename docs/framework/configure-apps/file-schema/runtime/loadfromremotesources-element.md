---
title: <loadFromRemoteSources> 元素
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: 568c0c814dcc57be0f5be435bb7750c970ffec19
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192446"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="cd236-102">\<loadFromRemoteSources> 元素</span><span class="sxs-lookup"><span data-stu-id="cd236-102">\<loadFromRemoteSources> element</span></span>

<span data-ttu-id="cd236-103">指定是否应在 .NET Framework 4 及更高版本中将从远程源加载的程序集授予完全信任。</span><span class="sxs-lookup"><span data-stu-id="cd236-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
> <span data-ttu-id="cd236-104">如果由于 Visual Studio 项目错误列表中的错误消息或生成错误而定向到本文，请参阅 [如何：在 Visual studio 中使用 Web 程序集](/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="cd236-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**  
  
## <a name="syntax"></a><span data-ttu-id="cd236-105">语法</span><span class="sxs-lookup"><span data-stu-id="cd236-105">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd236-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cd236-106">Attributes and elements</span></span>

 <span data-ttu-id="cd236-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cd236-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd236-108">特性</span><span class="sxs-lookup"><span data-stu-id="cd236-108">Attributes</span></span>  
  
|<span data-ttu-id="cd236-109">属性</span><span class="sxs-lookup"><span data-stu-id="cd236-109">Attribute</span></span>|<span data-ttu-id="cd236-110">描述</span><span class="sxs-lookup"><span data-stu-id="cd236-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="cd236-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="cd236-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="cd236-112">指定是否应向从远程源加载的程序集授予完全信任。</span><span class="sxs-lookup"><span data-stu-id="cd236-112">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="cd236-113">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="cd236-113">enabled attribute</span></span>  
  
|<span data-ttu-id="cd236-114">值</span><span class="sxs-lookup"><span data-stu-id="cd236-114">Value</span></span>|<span data-ttu-id="cd236-115">描述</span><span class="sxs-lookup"><span data-stu-id="cd236-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="cd236-116">不要向远程源的应用程序授予完全信任。</span><span class="sxs-lookup"><span data-stu-id="cd236-116">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="cd236-117">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="cd236-117">This is the default.</span></span>|  
|`true`|<span data-ttu-id="cd236-118">向远程源的应用程序授予完全信任。</span><span class="sxs-lookup"><span data-stu-id="cd236-118">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd236-119">子元素</span><span class="sxs-lookup"><span data-stu-id="cd236-119">Child elements</span></span>  

 <span data-ttu-id="cd236-120">无。</span><span class="sxs-lookup"><span data-stu-id="cd236-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd236-121">父元素</span><span class="sxs-lookup"><span data-stu-id="cd236-121">Parent elements</span></span>  
  
|<span data-ttu-id="cd236-122">元素</span><span class="sxs-lookup"><span data-stu-id="cd236-122">Element</span></span>|<span data-ttu-id="cd236-123">描述</span><span class="sxs-lookup"><span data-stu-id="cd236-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cd236-124">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="cd236-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="cd236-125">包含有关运行时初始化选项的信息。</span><span class="sxs-lookup"><span data-stu-id="cd236-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd236-126">备注</span><span class="sxs-lookup"><span data-stu-id="cd236-126">Remarks</span></span>

<span data-ttu-id="cd236-127">在 .NET Framework 3.5 及更早版本中，如果从远程位置加载程序集，程序集中的代码将以部分信任的方式与依赖于它的区域的授权集一起运行。</span><span class="sxs-lookup"><span data-stu-id="cd236-127">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="cd236-128">例如，如果从网站加载程序集，则该程序集将加载到 Internet 区域并被授予 Internet 权限集。</span><span class="sxs-lookup"><span data-stu-id="cd236-128">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="cd236-129">换句话说，它是在 Internet 沙箱中执行的。</span><span class="sxs-lookup"><span data-stu-id="cd236-129">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="cd236-130">从 .NET Framework 4 开始，将禁用代码访问安全性 (CAS) 策略，并以完全信任方式加载程序集。</span><span class="sxs-lookup"><span data-stu-id="cd236-130">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="cd236-131">通常情况下，这会向用先前已进行沙盒处理的方法加载的程序集授予完全信任 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="cd236-131">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="cd236-132">为了防止出现这种情况，默认情况下，将禁用在从远程源加载的程序集中运行代码的功能。</span><span class="sxs-lookup"><span data-stu-id="cd236-132">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="cd236-133">默认情况下，如果尝试加载远程程序集，则 <xref:System.IO.FileLoadException> 会引发并引发如下异常消息：</span><span class="sxs-lookup"><span data-stu-id="cd236-133">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported.
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' --->
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default,
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch.
```

<span data-ttu-id="cd236-134">若要加载程序集并执行其代码，你必须：</span><span class="sxs-lookup"><span data-stu-id="cd236-134">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="cd236-135">为程序集显式创建沙盒 (参阅 [如何：在沙盒中运行部分受信任的代码](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)) 。</span><span class="sxs-lookup"><span data-stu-id="cd236-135">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="cd236-136">在完全信任环境中运行程序集的代码。</span><span class="sxs-lookup"><span data-stu-id="cd236-136">Run the assembly's code in full trust.</span></span> <span data-ttu-id="cd236-137">可以通过配置元素来执行此操作 `<loadFromRemoteSources>` 。</span><span class="sxs-lookup"><span data-stu-id="cd236-137">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="cd236-138">它使你能够指定在 .NET Framework 早期版本中以部分信任模式运行的程序集现在在 .NET Framework 4 及更高版本中以完全信任模式运行。</span><span class="sxs-lookup"><span data-stu-id="cd236-138">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cd236-139">如果程序集不应在完全信任环境中运行，请不要设置此配置元素。</span><span class="sxs-lookup"><span data-stu-id="cd236-139">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="cd236-140">而是创建一个 <xref:System.AppDomain> 可在其中加载程序集的沙盒。</span><span class="sxs-lookup"><span data-stu-id="cd236-140">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="cd236-141">`enabled` `<loadFromRemoteSources>` 仅当禁用 (CAS) 的代码访问安全性时，元素的特性才有效。</span><span class="sxs-lookup"><span data-stu-id="cd236-141">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="cd236-142">默认情况下，CAS 策略在 .NET Framework 4 及更高版本中处于禁用状态。</span><span class="sxs-lookup"><span data-stu-id="cd236-142">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="cd236-143">如果将设置 `enabled` 为 `true` ，则会向远程程序集授予完全信任。</span><span class="sxs-lookup"><span data-stu-id="cd236-143">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="cd236-144">如果未 `enabled` 设置为 `true` ，则 <xref:System.IO.FileLoadException> 在以下条件之一下引发：</span><span class="sxs-lookup"><span data-stu-id="cd236-144">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="cd236-145">当前域的沙盒行为与 .NET Framework 3.5 中的行为不同。</span><span class="sxs-lookup"><span data-stu-id="cd236-145">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="cd236-146">这要求禁用 CAS 策略，当前域不会进行沙盒处理。</span><span class="sxs-lookup"><span data-stu-id="cd236-146">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="cd236-147">正在加载的程序集不是来自 `MyComputer` 区域。</span><span class="sxs-lookup"><span data-stu-id="cd236-147">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="cd236-148">设置 `<loadFromRemoteSources>` 元素可 `true` 防止引发此异常。</span><span class="sxs-lookup"><span data-stu-id="cd236-148">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="cd236-149">使用此方法，您可以指定不依赖公共语言运行时来对加载的程序集进行沙盒处理，以确保安全，并确保它们可以在完全信任的环境中执行。</span><span class="sxs-lookup"><span data-stu-id="cd236-149">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="cd236-150">说明</span><span class="sxs-lookup"><span data-stu-id="cd236-150">Notes</span></span>

- <span data-ttu-id="cd236-151">在 .NET Framework 4.5 及更高版本中，本地网络共享上的程序集默认情况下以完全信任方式运行;您无需启用该 `<loadFromRemoteSources>` 元素。</span><span class="sxs-lookup"><span data-stu-id="cd236-151">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="cd236-152">如果应用程序是从 Web 复制而来，Windows 会将其标记为 Web 应用程序，即使它驻留在本地计算机上也不例外。</span><span class="sxs-lookup"><span data-stu-id="cd236-152">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="cd236-153">您可以通过更改其文件属性来更改该指定，或者可以使用 `<loadFromRemoteSources>` 元素授予程序集完全信任。</span><span class="sxs-lookup"><span data-stu-id="cd236-153">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="cd236-154">对于操作系统标记为从 Web 加载的本地程序集，也可以使用 <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> 方法进行加载。</span><span class="sxs-lookup"><span data-stu-id="cd236-154">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="cd236-155">你可能会 <xref:System.IO.FileLoadException> 在正在运行的应用程序中获取 Windows 虚拟 PC 应用程序。</span><span class="sxs-lookup"><span data-stu-id="cd236-155">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="cd236-156">当你尝试从宿主计算机上的链接文件夹中加载文件时，会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="cd236-156">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="cd236-157">当你尝试从 (终端服务) [远程桌面服务](/windows/win32/termserv/terminal-services-portal) 链接的文件夹中加载文件时，也会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="cd236-157">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](/windows/win32/termserv/terminal-services-portal) (Terminal Services).</span></span> <span data-ttu-id="cd236-158">若要避免此异常，请将设置 `enabled` 为 `true` 。</span><span class="sxs-lookup"><span data-stu-id="cd236-158">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="cd236-159">配置文件</span><span class="sxs-lookup"><span data-stu-id="cd236-159">Configuration file</span></span>

<span data-ttu-id="cd236-160">此元素通常用在应用程序配置文件中，但可根据上下文用于其他配置文件。</span><span class="sxs-lookup"><span data-stu-id="cd236-160">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="cd236-161">有关详细信息，请参阅 .NET Security 博客中的 [更隐式使用 CAS 策略： loadFromRemoteSources 一](/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) 文。</span><span class="sxs-lookup"><span data-stu-id="cd236-161">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="cd236-162">示例</span><span class="sxs-lookup"><span data-stu-id="cd236-162">Example</span></span>

<span data-ttu-id="cd236-163">下面的示例演示如何向从远程源加载的程序集授予完全信任。</span><span class="sxs-lookup"><span data-stu-id="cd236-163">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="cd236-164">请参阅</span><span class="sxs-lookup"><span data-stu-id="cd236-164">See also</span></span>

- [<span data-ttu-id="cd236-165">CAS 策略的更隐式使用： loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="cd236-165">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)
- [<span data-ttu-id="cd236-166">如何：运行沙盒中部分受信任的代码</span><span class="sxs-lookup"><span data-stu-id="cd236-166">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="cd236-167">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="cd236-167">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cd236-168">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="cd236-168">Configuration File Schema</span></span>](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
