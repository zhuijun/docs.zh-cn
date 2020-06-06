---
title: <developmentMode> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
ms.openlocfilehash: 4a062da31740edb8f0c7a4f4db8b09800c687587
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117629"
---
# <a name="developmentmode-element"></a><span data-ttu-id="c2425-102">\<developmentMode> 元素</span><span class="sxs-lookup"><span data-stu-id="c2425-102">\<developmentMode> Element</span></span>
<span data-ttu-id="c2425-103">指定运行时是否搜索由 DEVPATH 环境变量指定的目录中的程序集。</span><span class="sxs-lookup"><span data-stu-id="c2425-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**  
  
## <a name="syntax"></a><span data-ttu-id="c2425-104">语法</span><span class="sxs-lookup"><span data-stu-id="c2425-104">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2425-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c2425-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c2425-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c2425-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2425-107">特性</span><span class="sxs-lookup"><span data-stu-id="c2425-107">Attributes</span></span>  
  
|<span data-ttu-id="c2425-108">属性</span><span class="sxs-lookup"><span data-stu-id="c2425-108">Attribute</span></span>|<span data-ttu-id="c2425-109">说明</span><span class="sxs-lookup"><span data-stu-id="c2425-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2425-110">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="c2425-110">**developerInstallation**</span></span>|<span data-ttu-id="c2425-111">指定运行时是否搜索由 DEVPATH 环境变量指定的目录中的程序集。</span><span class="sxs-lookup"><span data-stu-id="c2425-111">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="c2425-112">developerInstallation 特性</span><span class="sxs-lookup"><span data-stu-id="c2425-112">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="c2425-113">值</span><span class="sxs-lookup"><span data-stu-id="c2425-113">Value</span></span>|<span data-ttu-id="c2425-114">说明</span><span class="sxs-lookup"><span data-stu-id="c2425-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c2425-115">true</span><span class="sxs-lookup"><span data-stu-id="c2425-115">**true**</span></span>|<span data-ttu-id="c2425-116">在由 DEVPATH 环境变量指定的目录中搜索程序集。</span><span class="sxs-lookup"><span data-stu-id="c2425-116">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="c2425-117">**false**</span><span class="sxs-lookup"><span data-stu-id="c2425-117">**false**</span></span>|<span data-ttu-id="c2425-118">不搜索由 DEVPATH 环境变量指定的目录中的程序集。</span><span class="sxs-lookup"><span data-stu-id="c2425-118">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="c2425-119">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="c2425-119">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2425-120">子元素</span><span class="sxs-lookup"><span data-stu-id="c2425-120">Child Elements</span></span>  
 <span data-ttu-id="c2425-121">无。</span><span class="sxs-lookup"><span data-stu-id="c2425-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2425-122">父元素</span><span class="sxs-lookup"><span data-stu-id="c2425-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c2425-123">元素</span><span class="sxs-lookup"><span data-stu-id="c2425-123">Element</span></span>|<span data-ttu-id="c2425-124">描述</span><span class="sxs-lookup"><span data-stu-id="c2425-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c2425-125">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="c2425-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c2425-126">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="c2425-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2425-127">注解</span><span class="sxs-lookup"><span data-stu-id="c2425-127">Remarks</span></span>  
 <span data-ttu-id="c2425-128">仅在开发时使用此设置。</span><span class="sxs-lookup"><span data-stu-id="c2425-128">Use this setting only at development time.</span></span> <span data-ttu-id="c2425-129">运行时不检查在 DEVPATH 中找到的具有强名称的程序集的版本。</span><span class="sxs-lookup"><span data-stu-id="c2425-129">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="c2425-130">它只使用它找到的第一个程序集。</span><span class="sxs-lookup"><span data-stu-id="c2425-130">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2425-131">示例</span><span class="sxs-lookup"><span data-stu-id="c2425-131">Example</span></span>  
 <span data-ttu-id="c2425-132">下面的示例演示如何使运行时在由 DEVPATH 环境变量指定的目录中搜索程序集。</span><span class="sxs-lookup"><span data-stu-id="c2425-132">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2425-133">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2425-133">See also</span></span>

- [<span data-ttu-id="c2425-134">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="c2425-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c2425-135">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="c2425-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c2425-136">如何：使用 DEVPATH 查找程序集</span><span class="sxs-lookup"><span data-stu-id="c2425-136">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
