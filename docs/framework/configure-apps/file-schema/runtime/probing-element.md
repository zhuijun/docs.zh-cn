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
ms.openlocfilehash: e9e48ea97e1b70fef7fcc78a113e18c5fec23b7c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115862"
---
# <a name="probing-element"></a><span data-ttu-id="7a53a-102">\<probing> 元素</span><span class="sxs-lookup"><span data-stu-id="7a53a-102">\<probing> Element</span></span>
<span data-ttu-id="7a53a-103">指定加载程序集时要搜索的公共语言运行时的应用程序基子目录。</span><span class="sxs-lookup"><span data-stu-id="7a53a-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**  
  
## <a name="syntax"></a><span data-ttu-id="7a53a-104">语法</span><span class="sxs-lookup"><span data-stu-id="7a53a-104">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a53a-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="7a53a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7a53a-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7a53a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a53a-107">特性</span><span class="sxs-lookup"><span data-stu-id="7a53a-107">Attributes</span></span>  
  
|<span data-ttu-id="7a53a-108">属性</span><span class="sxs-lookup"><span data-stu-id="7a53a-108">Attribute</span></span>|<span data-ttu-id="7a53a-109">说明</span><span class="sxs-lookup"><span data-stu-id="7a53a-109">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="7a53a-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="7a53a-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="7a53a-111">指定可能包含程序集的应用程序基目录的子目录。</span><span class="sxs-lookup"><span data-stu-id="7a53a-111">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="7a53a-112">用分号分隔每个子目录。</span><span class="sxs-lookup"><span data-stu-id="7a53a-112">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a53a-113">子元素</span><span class="sxs-lookup"><span data-stu-id="7a53a-113">Child Elements</span></span>  

<span data-ttu-id="7a53a-114">无。</span><span class="sxs-lookup"><span data-stu-id="7a53a-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a53a-115">父元素</span><span class="sxs-lookup"><span data-stu-id="7a53a-115">Parent Elements</span></span>  
  
|<span data-ttu-id="7a53a-116">元素</span><span class="sxs-lookup"><span data-stu-id="7a53a-116">Element</span></span>|<span data-ttu-id="7a53a-117">描述</span><span class="sxs-lookup"><span data-stu-id="7a53a-117">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="7a53a-118">包含有关程序集版本重定向和程序集位置的信息。</span><span class="sxs-lookup"><span data-stu-id="7a53a-118">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="7a53a-119">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="7a53a-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7a53a-120">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="7a53a-120">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7a53a-121">示例</span><span class="sxs-lookup"><span data-stu-id="7a53a-121">Example</span></span>  
 <span data-ttu-id="7a53a-122">下面的示例演示如何指定运行时应搜索程序集的应用程序基子目录。</span><span class="sxs-lookup"><span data-stu-id="7a53a-122">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a53a-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7a53a-123">See also</span></span>

- [<span data-ttu-id="7a53a-124">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="7a53a-124">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="7a53a-125">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="7a53a-125">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="7a53a-126">指定程序集的位置</span><span class="sxs-lookup"><span data-stu-id="7a53a-126">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="7a53a-127">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="7a53a-127">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
