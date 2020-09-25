---
title: <appDomainManagerAssembly> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 1716b11106775bed2c0d6ccb62e8d5b032b6e8be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176131"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="bb2a8-102">\<appDomainManagerAssembly> 元素</span><span class="sxs-lookup"><span data-stu-id="bb2a8-102">\<appDomainManagerAssembly> Element</span></span>

<span data-ttu-id="bb2a8-103">指定为过程中的默认应用程序域提供应用程序域管理器的程序集。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="bb2a8-104">语法</span><span class="sxs-lookup"><span data-stu-id="bb2a8-104">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb2a8-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="bb2a8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="bb2a8-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb2a8-107">特性</span><span class="sxs-lookup"><span data-stu-id="bb2a8-107">Attributes</span></span>  
  
|<span data-ttu-id="bb2a8-108">属性</span><span class="sxs-lookup"><span data-stu-id="bb2a8-108">Attribute</span></span>|<span data-ttu-id="bb2a8-109">描述</span><span class="sxs-lookup"><span data-stu-id="bb2a8-109">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="bb2a8-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-110">Required attribute.</span></span> <span data-ttu-id="bb2a8-111">指定为进程中的默认应用程序域提供应用程序域管理器的程序集的显示名称。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-111">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb2a8-112">子元素</span><span class="sxs-lookup"><span data-stu-id="bb2a8-112">Child Elements</span></span>  

 <span data-ttu-id="bb2a8-113">无。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb2a8-114">父元素</span><span class="sxs-lookup"><span data-stu-id="bb2a8-114">Parent Elements</span></span>  
  
|<span data-ttu-id="bb2a8-115">元素</span><span class="sxs-lookup"><span data-stu-id="bb2a8-115">Element</span></span>|<span data-ttu-id="bb2a8-116">描述</span><span class="sxs-lookup"><span data-stu-id="bb2a8-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bb2a8-117">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bb2a8-118">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-118">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb2a8-119">备注</span><span class="sxs-lookup"><span data-stu-id="bb2a8-119">Remarks</span></span>  

 <span data-ttu-id="bb2a8-120">若要指定应用程序域管理器的类型，必须同时指定此元素和 [\<appDomainManagerType>](appdomainmanagertype-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-120">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="bb2a8-121">如果未指定这些元素中的任何一个，则会忽略另一个。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-121">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="bb2a8-122">在加载默认应用程序域时， <xref:System.TypeLoadException> 如果指定的程序集不存在，或者如果程序集不包含元素指定的类型，则会引发 [\<appDomainManagerType>](appdomainmanagertype-element.md) ; 并且进程无法启动。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-122">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="bb2a8-123">如果找到程序集，但版本信息不匹配， <xref:System.IO.FileLoadException> 则会引发。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-123">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="bb2a8-124">指定默认应用程序域的应用程序域管理器类型时，从默认应用程序域创建的其他应用程序域将继承应用程序域管理器类型。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-124">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="bb2a8-125">使用 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> 和 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> 属性为新的应用程序域指定不同的应用程序域管理器类型。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-125">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="bb2a8-126">指定应用程序域管理器类型要求应用程序具有完全信任。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-126">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="bb2a8-127"> (例如，在桌面上运行的应用程序具有完全信任。 ) 如果应用程序不具有完全信任， <xref:System.TypeLoadException> 则会引发。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-127">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="bb2a8-128">有关程序集显示名称的格式，请参见 <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> 属性。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-128">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="bb2a8-129">此配置元素仅在 .NET Framework 4 及更高版本中可用。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-129">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb2a8-130">示例</span><span class="sxs-lookup"><span data-stu-id="bb2a8-130">Example</span></span>  

 <span data-ttu-id="bb2a8-131">下面的示例演示如何指定进程的默认应用程序域的应用程序域管理器是 `MyMgr` `AdMgrExample` 程序集中的类型。</span><span class="sxs-lookup"><span data-stu-id="bb2a8-131">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bb2a8-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="bb2a8-132">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bb2a8-133">\<appDomainManagerType> 元素</span><span class="sxs-lookup"><span data-stu-id="bb2a8-133">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="bb2a8-134">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="bb2a8-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bb2a8-135">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="bb2a8-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bb2a8-136">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="bb2a8-136">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
