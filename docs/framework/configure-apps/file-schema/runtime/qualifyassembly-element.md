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
ms.openlocfilehash: 74e83900c68ab4b3fe01beb3f97657b0140d78ad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153914"
---
# <a name="qualifyassembly-element"></a><span data-ttu-id="a2f07-102">\<qualifyAssembly> 元素</span><span class="sxs-lookup"><span data-stu-id="a2f07-102">\<qualifyAssembly> Element</span></span>
<span data-ttu-id="a2f07-103">指定使用部分名称时应动态加载的程序集全名。</span><span class="sxs-lookup"><span data-stu-id="a2f07-103">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="a2f07-104">语法</span><span class="sxs-lookup"><span data-stu-id="a2f07-104">Syntax</span></span>  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2f07-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a2f07-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a2f07-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a2f07-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2f07-107">特性</span><span class="sxs-lookup"><span data-stu-id="a2f07-107">Attributes</span></span>  
  
|<span data-ttu-id="a2f07-108">属性</span><span class="sxs-lookup"><span data-stu-id="a2f07-108">Attribute</span></span>|<span data-ttu-id="a2f07-109">说明</span><span class="sxs-lookup"><span data-stu-id="a2f07-109">Description</span></span>|  
|---------------|-----------------|  
|`partialName`|<span data-ttu-id="a2f07-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="a2f07-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="a2f07-111">指定程序集在代码中出现的部分名称。</span><span class="sxs-lookup"><span data-stu-id="a2f07-111">Specifies the partial name of the assembly as it appears in the code.</span></span>|  
|`fullName`|<span data-ttu-id="a2f07-112">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="a2f07-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="a2f07-113">指定程序集在全局程序集缓存中出现时的完整名称。</span><span class="sxs-lookup"><span data-stu-id="a2f07-113">Specifies the full name of the assembly as it appears in the global assembly cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2f07-114">子元素</span><span class="sxs-lookup"><span data-stu-id="a2f07-114">Child Elements</span></span>  
 <span data-ttu-id="a2f07-115">无。</span><span class="sxs-lookup"><span data-stu-id="a2f07-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2f07-116">父元素</span><span class="sxs-lookup"><span data-stu-id="a2f07-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a2f07-117">元素</span><span class="sxs-lookup"><span data-stu-id="a2f07-117">Element</span></span>|<span data-ttu-id="a2f07-118">描述</span><span class="sxs-lookup"><span data-stu-id="a2f07-118">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="a2f07-119">包含有关程序集版本重定向和程序集位置的信息。</span><span class="sxs-lookup"><span data-stu-id="a2f07-119">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="a2f07-120">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="a2f07-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a2f07-121">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="a2f07-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2f07-122">注解</span><span class="sxs-lookup"><span data-stu-id="a2f07-122">Remarks</span></span>  
 <span data-ttu-id="a2f07-123"><xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>使用部分程序集名称调用方法会导致公共语言运行时仅查找应用程序基目录中的程序集。</span><span class="sxs-lookup"><span data-stu-id="a2f07-123">Calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method using partial assembly names causes the common language runtime to look for the assembly only in the application base directory.</span></span> <span data-ttu-id="a2f07-124">使用 **\<qualifyAssembly>** 应用程序配置文件中的元素来提供完整的程序集信息（名称、版本、公钥标记和区域性），并导致公共语言运行时在全局程序集缓存中搜索程序集。</span><span class="sxs-lookup"><span data-stu-id="a2f07-124">Use the **\<qualifyAssembly>** element in your application configuration file to provide the full assembly information (name, version, public key token, and culture) and cause the common language runtime to search for the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="a2f07-125">**FullName**特性必须包含程序集标识的四个字段：名称、版本、公钥标记和区域性。</span><span class="sxs-lookup"><span data-stu-id="a2f07-125">The **fullName** attribute must include the four fields of assembly identity: name, version, public key token, and culture.</span></span> <span data-ttu-id="a2f07-126">**PartialName**属性必须部分引用程序集。</span><span class="sxs-lookup"><span data-stu-id="a2f07-126">The **partialName** attribute must partially reference an assembly.</span></span> <span data-ttu-id="a2f07-127">必须至少指定程序集的文本名称（最常见的情况），但也可以包括版本、公钥标记或区域性（或四个（但不是全部四个）的任意组合。</span><span class="sxs-lookup"><span data-stu-id="a2f07-127">You must specify at least the assembly's text name (the most common case), but you can also include version, public key token, or culture (or any combination of the four, but not all four).</span></span> <span data-ttu-id="a2f07-128">**PartialName**必须与在调用中指定的名称相匹配。</span><span class="sxs-lookup"><span data-stu-id="a2f07-128">The **partialName** must match the name specified in your call.</span></span> <span data-ttu-id="a2f07-129">例如，你不能 `"math"` 在配置文件中将指定为**partialName**属性，然后 `Assembly.Load("math, Version=3.3.3.3")` 在代码中调用。</span><span class="sxs-lookup"><span data-stu-id="a2f07-129">For example, you cannot specify `"math"` as the **partialName** attribute in your configuration file and call `Assembly.Load("math, Version=3.3.3.3")` in your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2f07-130">示例</span><span class="sxs-lookup"><span data-stu-id="a2f07-130">Example</span></span>  
 <span data-ttu-id="a2f07-131">下面的示例以逻辑方式将调用 `Assembly.Load("math")` 转换为 `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")` 。</span><span class="sxs-lookup"><span data-stu-id="a2f07-131">The following example logically turns the call `Assembly.Load("math")` into `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2f07-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a2f07-132">See also</span></span>

- [<span data-ttu-id="a2f07-133">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="a2f07-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a2f07-134">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="a2f07-134">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
- <span data-ttu-id="a2f07-135">[部分程序集引用](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a2f07-135">[Partial Assembly References](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))</span></span>
