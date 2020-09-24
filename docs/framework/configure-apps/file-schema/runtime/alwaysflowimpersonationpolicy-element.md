---
title: <alwaysFlowImpersonationPolicy> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
ms.openlocfilehash: 9316f026a807b6ad36014157061f67bdbd7d3d18
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149434"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="f73b4-102">\<alwaysFlowImpersonationPolicy> 元素</span><span class="sxs-lookup"><span data-stu-id="f73b4-102">\<alwaysFlowImpersonationPolicy> Element</span></span>

<span data-ttu-id="f73b4-103">指定 Windows 标识始终流经异步点，而不考虑执行模拟的方式。</span><span class="sxs-lookup"><span data-stu-id="f73b4-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**\  
  
## <a name="syntax"></a><span data-ttu-id="f73b4-104">语法</span><span class="sxs-lookup"><span data-stu-id="f73b4-104">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f73b4-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f73b4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f73b4-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f73b4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f73b4-107">特性</span><span class="sxs-lookup"><span data-stu-id="f73b4-107">Attributes</span></span>  
  
|<span data-ttu-id="f73b4-108">属性</span><span class="sxs-lookup"><span data-stu-id="f73b4-108">Attribute</span></span>|<span data-ttu-id="f73b4-109">描述</span><span class="sxs-lookup"><span data-stu-id="f73b4-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f73b4-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="f73b4-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="f73b4-111">指示 Windows 标识是否流经异步点。</span><span class="sxs-lookup"><span data-stu-id="f73b4-111">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f73b4-112">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="f73b4-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="f73b4-113">值</span><span class="sxs-lookup"><span data-stu-id="f73b4-113">Value</span></span>|<span data-ttu-id="f73b4-114">描述</span><span class="sxs-lookup"><span data-stu-id="f73b4-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f73b4-115">Windows 标识不流经异步点，除非模拟是通过托管方法（如）执行的 <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> 。</span><span class="sxs-lookup"><span data-stu-id="f73b4-115">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="f73b4-116">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="f73b4-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="f73b4-117">无论模拟的执行方式如何，Windows 标识始终流经异步点。</span><span class="sxs-lookup"><span data-stu-id="f73b4-117">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f73b4-118">子元素</span><span class="sxs-lookup"><span data-stu-id="f73b4-118">Child Elements</span></span>  

 <span data-ttu-id="f73b4-119">无。</span><span class="sxs-lookup"><span data-stu-id="f73b4-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f73b4-120">父元素</span><span class="sxs-lookup"><span data-stu-id="f73b4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f73b4-121">元素</span><span class="sxs-lookup"><span data-stu-id="f73b4-121">Element</span></span>|<span data-ttu-id="f73b4-122">描述</span><span class="sxs-lookup"><span data-stu-id="f73b4-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f73b4-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="f73b4-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f73b4-124">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="f73b4-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f73b4-125">备注</span><span class="sxs-lookup"><span data-stu-id="f73b4-125">Remarks</span></span>  

 <span data-ttu-id="f73b4-126">在 .NET Framework 版本1.0 和1.1 中，Windows 标识不流经异步点。</span><span class="sxs-lookup"><span data-stu-id="f73b4-126">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="f73b4-127">在 .NET Framework 版本2.0 中，有一个 <xref:System.Threading.ExecutionContext> 对象包含当前正在执行的线程的相关信息，并在应用程序域中的异步点之间流动。</span><span class="sxs-lookup"><span data-stu-id="f73b4-127">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="f73b4-128"><xref:System.Security.Principal.WindowsIdentity>如果通过使用托管方法（如） <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> 而不是通过其他方式（例如，平台调用到本机方法）来实现模拟，则还会将流作为流过异步点的信息的一部分。</span><span class="sxs-lookup"><span data-stu-id="f73b4-128">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="f73b4-129">此元素用于指定无论如何实现模拟，Windows 标识都将流经异步点。</span><span class="sxs-lookup"><span data-stu-id="f73b4-129">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="f73b4-130">可以通过两种其他方式更改此默认行为：</span><span class="sxs-lookup"><span data-stu-id="f73b4-130">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="f73b4-131">在托管代码中，在每个线程的基础上。</span><span class="sxs-lookup"><span data-stu-id="f73b4-131">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="f73b4-132">通过 <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> 使用 <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> 、 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> 或方法修改和设置，可以在每个线程上禁止显示流 <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f73b4-132">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="f73b4-133">在调用非托管承载接口时， (CLR) 加载公共语言运行时。</span><span class="sxs-lookup"><span data-stu-id="f73b4-133">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="f73b4-134">如果使用非托管宿主 (接口而不是简单的托管可执行) 文件来加载 CLR，则可以在 [CorBindToRuntimeEx 函数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) 函数的调用中指定特殊标志。</span><span class="sxs-lookup"><span data-stu-id="f73b4-134">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="f73b4-135">若要为整个进程启用兼容模式，请将 `flags` [CorBindToRuntimeEx 函数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) 的参数设置为 `STARTUP_ALWAYSFLOW_IMPERSONATION` 。</span><span class="sxs-lookup"><span data-stu-id="f73b4-135">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="f73b4-136">配置文件</span><span class="sxs-lookup"><span data-stu-id="f73b4-136">Configuration File</span></span>  

 <span data-ttu-id="f73b4-137">在 .NET Framework 应用程序中，此元素只能在应用程序配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="f73b4-137">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="f73b4-138">对于 ASP.NET 应用程序，可以在 \Microsoft.NET\Framework\vx.x.xxxx 目录中找到的 aspnet.config 文件中配置模拟流 \<Windows Folder> 。</span><span class="sxs-lookup"><span data-stu-id="f73b4-138">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="f73b4-139">默认情况下，ASP.NET 使用以下配置设置禁用 aspnet.config 文件中的模拟流：</span><span class="sxs-lookup"><span data-stu-id="f73b4-139">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="f73b4-140">在 ASP.NET 中，如果要改为允许模拟流，则必须显式使用以下配置设置：</span><span class="sxs-lookup"><span data-stu-id="f73b4-140">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="f73b4-141">示例</span><span class="sxs-lookup"><span data-stu-id="f73b4-141">Example</span></span>  

 <span data-ttu-id="f73b4-142">下面的示例演示如何指定 Windows 标识流经异步点，即使通过非托管方法实现模拟也是如此。</span><span class="sxs-lookup"><span data-stu-id="f73b4-142">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f73b4-143">请参阅</span><span class="sxs-lookup"><span data-stu-id="f73b4-143">See also</span></span>

- [<span data-ttu-id="f73b4-144">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="f73b4-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f73b4-145">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="f73b4-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f73b4-146">\<legacyImpersonationPolicy> 元素</span><span class="sxs-lookup"><span data-stu-id="f73b4-146">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)
