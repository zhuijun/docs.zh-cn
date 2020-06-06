---
title: <appDomainManagerType> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154417"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="5a87d-102">\<appDomainManagerType> 元素</span><span class="sxs-lookup"><span data-stu-id="5a87d-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="5a87d-103">指定用作默认应用程序域的应用程序域管理器的类型。</span><span class="sxs-lookup"><span data-stu-id="5a87d-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**  
  
## <a name="syntax"></a><span data-ttu-id="5a87d-104">语法</span><span class="sxs-lookup"><span data-stu-id="5a87d-104">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a87d-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="5a87d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5a87d-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5a87d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a87d-107">特性</span><span class="sxs-lookup"><span data-stu-id="5a87d-107">Attributes</span></span>  
  
|<span data-ttu-id="5a87d-108">属性</span><span class="sxs-lookup"><span data-stu-id="5a87d-108">Attribute</span></span>|<span data-ttu-id="5a87d-109">说明</span><span class="sxs-lookup"><span data-stu-id="5a87d-109">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="5a87d-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="5a87d-110">Required attribute.</span></span> <span data-ttu-id="5a87d-111">指定类型的名称（包括命名空间），该名称用作进程中默认应用程序域的应用程序域管理器。</span><span class="sxs-lookup"><span data-stu-id="5a87d-111">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a87d-112">子元素</span><span class="sxs-lookup"><span data-stu-id="5a87d-112">Child Elements</span></span>  
 <span data-ttu-id="5a87d-113">无。</span><span class="sxs-lookup"><span data-stu-id="5a87d-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a87d-114">父元素</span><span class="sxs-lookup"><span data-stu-id="5a87d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="5a87d-115">元素</span><span class="sxs-lookup"><span data-stu-id="5a87d-115">Element</span></span>|<span data-ttu-id="5a87d-116">描述</span><span class="sxs-lookup"><span data-stu-id="5a87d-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5a87d-117">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="5a87d-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5a87d-118">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="5a87d-118">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a87d-119">注解</span><span class="sxs-lookup"><span data-stu-id="5a87d-119">Remarks</span></span>  
 <span data-ttu-id="5a87d-120">若要指定应用程序域管理器的类型，必须同时指定此元素和 [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="5a87d-120">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="5a87d-121">如果未指定这些元素中的任何一个，则会忽略另一个。</span><span class="sxs-lookup"><span data-stu-id="5a87d-121">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="5a87d-122">如果指定的类型在元素指定的程序集中不存在，则在加载默认应用程序域时， <xref:System.TypeLoadException> 将引发 [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) ; 该进程无法启动。</span><span class="sxs-lookup"><span data-stu-id="5a87d-122">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="5a87d-123">指定默认应用程序域的应用程序域管理器类型时，从默认应用程序域创建的其他应用程序域将继承应用程序域管理器类型。</span><span class="sxs-lookup"><span data-stu-id="5a87d-123">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="5a87d-124">使用 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> 和 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> 属性为新的应用程序域指定不同的应用程序域管理器类型。</span><span class="sxs-lookup"><span data-stu-id="5a87d-124">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="5a87d-125">指定应用程序域管理器类型要求应用程序具有完全信任。</span><span class="sxs-lookup"><span data-stu-id="5a87d-125">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="5a87d-126">（例如，在桌面上运行的应用程序具有完全信任。）如果应用程序不具有完全信任， <xref:System.TypeLoadException> 则会引发。</span><span class="sxs-lookup"><span data-stu-id="5a87d-126">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="5a87d-127">类型和命名空间的格式与用于属性的格式相同 <xref:System.Type.FullName%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="5a87d-127">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="5a87d-128">此配置元素仅在 .NET Framework 4 及更高版本中可用。</span><span class="sxs-lookup"><span data-stu-id="5a87d-128">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a87d-129">示例</span><span class="sxs-lookup"><span data-stu-id="5a87d-129">Example</span></span>  
 <span data-ttu-id="5a87d-130">下面的示例演示如何指定进程的默认应用程序域的应用程序域管理器是 `MyMgr` `AdMgrExample` 程序集中的类型。</span><span class="sxs-lookup"><span data-stu-id="5a87d-130">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a87d-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5a87d-131">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5a87d-132">\<appDomainManagerAssembly>Element</span><span class="sxs-lookup"><span data-stu-id="5a87d-132">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="5a87d-133">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="5a87d-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5a87d-134">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="5a87d-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5a87d-135">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="5a87d-135">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
