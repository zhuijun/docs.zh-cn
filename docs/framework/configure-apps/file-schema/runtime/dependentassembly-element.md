---
title: <dependentAssembly> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
ms.openlocfilehash: 6a924b1998651c923c64429029a118dd1e9ede69
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198998"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="d45aa-102">\<dependentAssembly> 元素</span><span class="sxs-lookup"><span data-stu-id="d45aa-102">\<dependentAssembly> Element</span></span>

<span data-ttu-id="d45aa-103">封装每个程序集的绑定策略和程序集位置。</span><span class="sxs-lookup"><span data-stu-id="d45aa-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="d45aa-104">`dependentAssembly`为每个程序集使用一个元素。</span><span class="sxs-lookup"><span data-stu-id="d45aa-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="d45aa-105">语法</span><span class="sxs-lookup"><span data-stu-id="d45aa-105">Syntax</span></span>  
  
```xml  
<dependentAssembly>
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d45aa-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d45aa-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d45aa-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d45aa-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d45aa-108">特性</span><span class="sxs-lookup"><span data-stu-id="d45aa-108">Attributes</span></span>  

 <span data-ttu-id="d45aa-109">无。</span><span class="sxs-lookup"><span data-stu-id="d45aa-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d45aa-110">子元素</span><span class="sxs-lookup"><span data-stu-id="d45aa-110">Child Elements</span></span>  
  
|<span data-ttu-id="d45aa-111">元素</span><span class="sxs-lookup"><span data-stu-id="d45aa-111">Element</span></span>|<span data-ttu-id="d45aa-112">描述</span><span class="sxs-lookup"><span data-stu-id="d45aa-112">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="d45aa-113">包含有关程序集的标识信息。</span><span class="sxs-lookup"><span data-stu-id="d45aa-113">Contains identifying information about the assembly.</span></span> <span data-ttu-id="d45aa-114">此元素必须包含在每个 `dependentAssembly` 元素中。</span><span class="sxs-lookup"><span data-stu-id="d45aa-114">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="d45aa-115">指定运行时在计算机上未安装共享程序集的情况下可以找到该程序集的位置。</span><span class="sxs-lookup"><span data-stu-id="d45aa-115">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="d45aa-116">将一个程序集版本重定向到另一个版本。</span><span class="sxs-lookup"><span data-stu-id="d45aa-116">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="d45aa-117">指定运行时是否应用此程序集的发布服务器策略。</span><span class="sxs-lookup"><span data-stu-id="d45aa-117">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d45aa-118">父元素</span><span class="sxs-lookup"><span data-stu-id="d45aa-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d45aa-119">元素</span><span class="sxs-lookup"><span data-stu-id="d45aa-119">Element</span></span>|<span data-ttu-id="d45aa-120">描述</span><span class="sxs-lookup"><span data-stu-id="d45aa-120">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="d45aa-121">包含有关程序集版本重定向和程序集位置的信息。</span><span class="sxs-lookup"><span data-stu-id="d45aa-121">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="d45aa-122">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="d45aa-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d45aa-123">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="d45aa-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d45aa-124">示例</span><span class="sxs-lookup"><span data-stu-id="d45aa-124">Example</span></span>  

 <span data-ttu-id="d45aa-125">下面的示例演示如何封装两个程序集的程序集信息。</span><span class="sxs-lookup"><span data-stu-id="d45aa-125">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d45aa-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="d45aa-126">See also</span></span>

- [<span data-ttu-id="d45aa-127">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="d45aa-127">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d45aa-128">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="d45aa-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d45aa-129">重定向程序集版本</span><span class="sxs-lookup"><span data-stu-id="d45aa-129">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
