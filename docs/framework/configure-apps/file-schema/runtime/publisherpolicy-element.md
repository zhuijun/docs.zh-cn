---
title: <publisherPolicy> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
ms.openlocfilehash: 89fa8a991cc7d0352eb0a13cdfd3a6063ea468e7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115850"
---
# <a name="publisherpolicy-element"></a><span data-ttu-id="c85fc-102">\<publisherPolicy> 元素</span><span class="sxs-lookup"><span data-stu-id="c85fc-102">\<publisherPolicy> Element</span></span>
<span data-ttu-id="c85fc-103">指定运行时是否使用发布者策略。</span><span class="sxs-lookup"><span data-stu-id="c85fc-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="c85fc-104">语法</span><span class="sxs-lookup"><span data-stu-id="c85fc-104">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c85fc-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c85fc-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c85fc-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c85fc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c85fc-107">特性</span><span class="sxs-lookup"><span data-stu-id="c85fc-107">Attributes</span></span>  
  
|<span data-ttu-id="c85fc-108">属性</span><span class="sxs-lookup"><span data-stu-id="c85fc-108">Attribute</span></span>|<span data-ttu-id="c85fc-109">说明</span><span class="sxs-lookup"><span data-stu-id="c85fc-109">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="c85fc-110">指定是否应用发布者策略。</span><span class="sxs-lookup"><span data-stu-id="c85fc-110">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="c85fc-111">应用属性</span><span class="sxs-lookup"><span data-stu-id="c85fc-111">apply Attribute</span></span>  
  
|<span data-ttu-id="c85fc-112">值</span><span class="sxs-lookup"><span data-stu-id="c85fc-112">Value</span></span>|<span data-ttu-id="c85fc-113">说明</span><span class="sxs-lookup"><span data-stu-id="c85fc-113">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="c85fc-114">应用发布者策略。</span><span class="sxs-lookup"><span data-stu-id="c85fc-114">Applies publisher policy.</span></span> <span data-ttu-id="c85fc-115">此设置为默认设置。</span><span class="sxs-lookup"><span data-stu-id="c85fc-115">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="c85fc-116">不应用发布者策略。</span><span class="sxs-lookup"><span data-stu-id="c85fc-116">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c85fc-117">子元素</span><span class="sxs-lookup"><span data-stu-id="c85fc-117">Child Elements</span></span>  

<span data-ttu-id="c85fc-118">无。</span><span class="sxs-lookup"><span data-stu-id="c85fc-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c85fc-119">父元素</span><span class="sxs-lookup"><span data-stu-id="c85fc-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c85fc-120">元素</span><span class="sxs-lookup"><span data-stu-id="c85fc-120">Element</span></span>|<span data-ttu-id="c85fc-121">描述</span><span class="sxs-lookup"><span data-stu-id="c85fc-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="c85fc-122">包含有关程序集版本重定向和程序集位置的信息。</span><span class="sxs-lookup"><span data-stu-id="c85fc-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="c85fc-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="c85fc-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="c85fc-124">封装每个程序集的绑定策略和程序集位置。</span><span class="sxs-lookup"><span data-stu-id="c85fc-124">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="c85fc-125">`<dependentAssembly>`为每个程序集使用一个元素。</span><span class="sxs-lookup"><span data-stu-id="c85fc-125">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="c85fc-126">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="c85fc-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c85fc-127">注解</span><span class="sxs-lookup"><span data-stu-id="c85fc-127">Remarks</span></span>  
 <span data-ttu-id="c85fc-128">当组件供应商发布程序集的新版本时，供应商可以包括发行者策略，以便使用旧版本的应用程序现在使用新版本。</span><span class="sxs-lookup"><span data-stu-id="c85fc-128">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="c85fc-129">若要指定是否将发布服务器策略应用于特定程序集，请将该 **\<publisherPolicy>** 元素放在 **\<dependentAssembly>** 元素中。</span><span class="sxs-lookup"><span data-stu-id="c85fc-129">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="c85fc-130">**Apply**属性的默认设置为 **"是"**。</span><span class="sxs-lookup"><span data-stu-id="c85fc-130">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="c85fc-131">如果将**apply**特性设置为 "**否**"，则将替代程序集以前的 **"是"** 设置。</span><span class="sxs-lookup"><span data-stu-id="c85fc-131">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="c85fc-132">若要让应用程序使用 [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) 应用程序配置文件中的元素显式忽略发行者策略，则需要权限。</span><span class="sxs-lookup"><span data-stu-id="c85fc-132">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="c85fc-133">通过在上设置标志来授予权限 <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> 。</span><span class="sxs-lookup"><span data-stu-id="c85fc-133">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="c85fc-134">有关详细信息，请参阅[程序集绑定重定向安全权限](../../assembly-binding-redirection-security-permission.md)。</span><span class="sxs-lookup"><span data-stu-id="c85fc-134">For more information, see [Assembly Binding Redirection Security Permission](../../assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c85fc-135">示例</span><span class="sxs-lookup"><span data-stu-id="c85fc-135">Example</span></span>  
 <span data-ttu-id="c85fc-136">下面的示例将关闭程序集的发布服务器策略 `myAssembly` 。</span><span class="sxs-lookup"><span data-stu-id="c85fc-136">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c85fc-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c85fc-137">See also</span></span>

- [<span data-ttu-id="c85fc-138">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="c85fc-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c85fc-139">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="c85fc-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c85fc-140">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="c85fc-140">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="c85fc-141">重定向程序集版本</span><span class="sxs-lookup"><span data-stu-id="c85fc-141">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
