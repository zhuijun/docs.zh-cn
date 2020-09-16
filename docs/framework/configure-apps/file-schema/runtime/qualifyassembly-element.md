---
title: <qualifyAssembly> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 0479b966abd0cfa3c570355e62e4b42264a3114f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554549"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="10b36-102">\<qualifyAssembly> 元素</span><span class="sxs-lookup"><span data-stu-id="10b36-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="10b36-103">指定使用部分名称时应动态加载的程序集全名。</span><span class="sxs-lookup"><span data-stu-id="10b36-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="10b36-104">语法</span><span class="sxs-lookup"><span data-stu-id="10b36-104">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10b36-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="10b36-105">Attributes and Elements</span></span>  
 <span data-ttu-id="10b36-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="10b36-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10b36-107">特性</span><span class="sxs-lookup"><span data-stu-id="10b36-107">Attributes</span></span>  
  
|<span data-ttu-id="10b36-108">属性</span><span class="sxs-lookup"><span data-stu-id="10b36-108">Attribute</span></span>|<span data-ttu-id="10b36-109">描述</span><span class="sxs-lookup"><span data-stu-id="10b36-109">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="10b36-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="10b36-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="10b36-111">指定程序集在代码中出现的部分名称。</span><span class="sxs-lookup"><span data-stu-id="10b36-111">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="10b36-112">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="10b36-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="10b36-113">指定程序集在全局程序集缓存中出现时的完整名称。</span><span class="sxs-lookup"><span data-stu-id="10b36-113">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10b36-114">子元素</span><span class="sxs-lookup"><span data-stu-id="10b36-114">Child Elements</span></span>  
 <span data-ttu-id="10b36-115">无。</span><span class="sxs-lookup"><span data-stu-id="10b36-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10b36-116">父元素</span><span class="sxs-lookup"><span data-stu-id="10b36-116">Parent Elements</span></span>  
  
|<span data-ttu-id="10b36-117">元素</span><span class="sxs-lookup"><span data-stu-id="10b36-117">Element</span></span>|<span data-ttu-id="10b36-118">说明</span><span class="sxs-lookup"><span data-stu-id="10b36-118">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="10b36-119">包含有关程序集版本重定向和程序集位置的信息。</span><span class="sxs-lookup"><span data-stu-id="10b36-119">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="10b36-120">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="10b36-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="10b36-121">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="10b36-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10b36-122">备注</span><span class="sxs-lookup"><span data-stu-id="10b36-122">Remarks</span></span>  
 <span data-ttu-id="10b36-123"><xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>使用部分程序集名称调用方法会导致公共语言运行时仅查找应用程序基目录中的程序集。</span><span class="sxs-lookup"><span data-stu-id="10b36-123">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="10b36-124">使用 **\<qualifyAssembly>** 应用程序配置文件中的元素来提供完整的程序集信息 (名称、版本、公钥标记和区域性) 并导致公共语言运行时在全局程序集缓存中搜索程序集。</span><span class="sxs-lookup"><span data-stu-id="10b36-124">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="10b36-125">**FullName**特性必须包含程序集标识的四个字段：名称、版本、公钥标记和区域性。</span><span class="sxs-lookup"><span data-stu-id="10b36-125">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="10b36-126">**PartialName**属性必须部分引用程序集。</span><span class="sxs-lookup"><span data-stu-id="10b36-126">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="10b36-127">您必须至少指定程序集的文本名称 (最常见的情况) ，但也可以包括版本、公钥标记或区域性 (或四个（但不是全部四) 个）的任意组合。</span><span class="sxs-lookup"><span data-stu-id="10b36-127">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="10b36-128">**PartialName**必须与在调用中指定的名称相匹配。</span><span class="sxs-lookup"><span data-stu-id="10b36-128">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="10b36-129">例如，你不能 `"math"` 在配置文件中将指定为 **partialName** 属性，然后 `Assembly.Load("math, Version=3.3.3.3")` 在代码中调用。</span><span class="sxs-lookup"><span data-stu-id="10b36-129">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10b36-130">示例</span><span class="sxs-lookup"><span data-stu-id="10b36-130">Example</span></span>  
 <span data-ttu-id="10b36-131">下面的示例以逻辑方式将调用 `Assembly.Load("math")` 转换为 `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")` 。</span><span class="sxs-lookup"><span data-stu-id="10b36-131">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="10b36-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="10b36-132">See also</span></span>

- [<span data-ttu-id="10b36-133">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="10b36-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="10b36-134">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="10b36-134">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="10b36-135">[部分程序集引用](/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10b36-135">[Partial Assembly References](/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
