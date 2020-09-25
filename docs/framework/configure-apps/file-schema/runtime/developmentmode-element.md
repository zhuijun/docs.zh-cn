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
ms.openlocfilehash: ddcabb831193baee30016f663f32d8562283d936
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205017"
---
# <a name="developmentmode-element"></a><span data-ttu-id="16e9f-102">\<developmentMode> 元素</span><span class="sxs-lookup"><span data-stu-id="16e9f-102">\<developmentMode> Element</span></span>

<span data-ttu-id="16e9f-103">指定运行时是否搜索由 DEVPATH 环境变量指定的目录中的程序集。</span><span class="sxs-lookup"><span data-stu-id="16e9f-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**  
  
## <a name="syntax"></a><span data-ttu-id="16e9f-104">语法</span><span class="sxs-lookup"><span data-stu-id="16e9f-104">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16e9f-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="16e9f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="16e9f-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="16e9f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16e9f-107">特性</span><span class="sxs-lookup"><span data-stu-id="16e9f-107">Attributes</span></span>  
  
|<span data-ttu-id="16e9f-108">属性</span><span class="sxs-lookup"><span data-stu-id="16e9f-108">Attribute</span></span>|<span data-ttu-id="16e9f-109">描述</span><span class="sxs-lookup"><span data-stu-id="16e9f-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16e9f-110">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="16e9f-110">**developerInstallation**</span></span>|<span data-ttu-id="16e9f-111">指定运行时是否搜索由 DEVPATH 环境变量指定的目录中的程序集。</span><span class="sxs-lookup"><span data-stu-id="16e9f-111">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="16e9f-112">developerInstallation 特性</span><span class="sxs-lookup"><span data-stu-id="16e9f-112">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="16e9f-113">值</span><span class="sxs-lookup"><span data-stu-id="16e9f-113">Value</span></span>|<span data-ttu-id="16e9f-114">描述</span><span class="sxs-lookup"><span data-stu-id="16e9f-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="16e9f-115">**true**</span><span class="sxs-lookup"><span data-stu-id="16e9f-115">**true**</span></span>|<span data-ttu-id="16e9f-116">在由 DEVPATH 环境变量指定的目录中搜索程序集。</span><span class="sxs-lookup"><span data-stu-id="16e9f-116">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="16e9f-117">**false**</span><span class="sxs-lookup"><span data-stu-id="16e9f-117">**false**</span></span>|<span data-ttu-id="16e9f-118">不搜索由 DEVPATH 环境变量指定的目录中的程序集。</span><span class="sxs-lookup"><span data-stu-id="16e9f-118">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="16e9f-119">这是默认值。</span><span class="sxs-lookup"><span data-stu-id="16e9f-119">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16e9f-120">子元素</span><span class="sxs-lookup"><span data-stu-id="16e9f-120">Child Elements</span></span>  

 <span data-ttu-id="16e9f-121">无。</span><span class="sxs-lookup"><span data-stu-id="16e9f-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16e9f-122">父元素</span><span class="sxs-lookup"><span data-stu-id="16e9f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="16e9f-123">元素</span><span class="sxs-lookup"><span data-stu-id="16e9f-123">Element</span></span>|<span data-ttu-id="16e9f-124">描述</span><span class="sxs-lookup"><span data-stu-id="16e9f-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="16e9f-125">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="16e9f-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="16e9f-126">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="16e9f-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16e9f-127">备注</span><span class="sxs-lookup"><span data-stu-id="16e9f-127">Remarks</span></span>  

 <span data-ttu-id="16e9f-128">仅在开发时使用此设置。</span><span class="sxs-lookup"><span data-stu-id="16e9f-128">Use this setting only at development time.</span></span> <span data-ttu-id="16e9f-129">运行时不检查在 DEVPATH 中找到的具有强名称的程序集的版本。</span><span class="sxs-lookup"><span data-stu-id="16e9f-129">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="16e9f-130">它只使用它找到的第一个程序集。</span><span class="sxs-lookup"><span data-stu-id="16e9f-130">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16e9f-131">示例</span><span class="sxs-lookup"><span data-stu-id="16e9f-131">Example</span></span>  

 <span data-ttu-id="16e9f-132">下面的示例演示如何使运行时在由 DEVPATH 环境变量指定的目录中搜索程序集。</span><span class="sxs-lookup"><span data-stu-id="16e9f-132">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="16e9f-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="16e9f-133">See also</span></span>

- [<span data-ttu-id="16e9f-134">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="16e9f-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="16e9f-135">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="16e9f-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="16e9f-136">如何：使用 DEVPATH 查找程序集</span><span class="sxs-lookup"><span data-stu-id="16e9f-136">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
