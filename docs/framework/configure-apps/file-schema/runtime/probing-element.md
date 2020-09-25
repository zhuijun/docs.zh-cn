---
title: <probing> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
ms.openlocfilehash: 1435ee8ea887b5d7d3e785eef0f25ffed14b1b97
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195267"
---
# <a name="probing-element"></a><span data-ttu-id="8e032-102">\<probing> 元素</span><span class="sxs-lookup"><span data-stu-id="8e032-102">\<probing> Element</span></span>

<span data-ttu-id="8e032-103">指定加载程序集时要搜索的公共语言运行时的应用程序基子目录。</span><span class="sxs-lookup"><span data-stu-id="8e032-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**  
  
## <a name="syntax"></a><span data-ttu-id="8e032-104">语法</span><span class="sxs-lookup"><span data-stu-id="8e032-104">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e032-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="8e032-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8e032-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8e032-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e032-107">特性</span><span class="sxs-lookup"><span data-stu-id="8e032-107">Attributes</span></span>  
  
|<span data-ttu-id="8e032-108">属性</span><span class="sxs-lookup"><span data-stu-id="8e032-108">Attribute</span></span>|<span data-ttu-id="8e032-109">描述</span><span class="sxs-lookup"><span data-stu-id="8e032-109">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="8e032-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="8e032-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="8e032-111">指定可能包含程序集的应用程序基目录的子目录。</span><span class="sxs-lookup"><span data-stu-id="8e032-111">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="8e032-112">用分号分隔每个子目录。</span><span class="sxs-lookup"><span data-stu-id="8e032-112">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e032-113">子元素</span><span class="sxs-lookup"><span data-stu-id="8e032-113">Child Elements</span></span>  

<span data-ttu-id="8e032-114">无。</span><span class="sxs-lookup"><span data-stu-id="8e032-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8e032-115">父元素</span><span class="sxs-lookup"><span data-stu-id="8e032-115">Parent Elements</span></span>  
  
|<span data-ttu-id="8e032-116">元素</span><span class="sxs-lookup"><span data-stu-id="8e032-116">Element</span></span>|<span data-ttu-id="8e032-117">描述</span><span class="sxs-lookup"><span data-stu-id="8e032-117">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="8e032-118">包含有关程序集版本重定向和程序集位置的信息。</span><span class="sxs-lookup"><span data-stu-id="8e032-118">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="8e032-119">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="8e032-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8e032-120">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="8e032-120">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8e032-121">示例</span><span class="sxs-lookup"><span data-stu-id="8e032-121">Example</span></span>  

 <span data-ttu-id="8e032-122">下面的示例演示如何指定运行时应搜索程序集的应用程序基子目录。</span><span class="sxs-lookup"><span data-stu-id="8e032-122">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e032-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="8e032-123">See also</span></span>

- [<span data-ttu-id="8e032-124">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="8e032-124">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="8e032-125">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="8e032-125">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="8e032-126">指定程序集的位置</span><span class="sxs-lookup"><span data-stu-id="8e032-126">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="8e032-127">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="8e032-127">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
