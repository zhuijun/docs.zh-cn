---
title: <gcAllowVeryLargeObjects> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 8b2f39a0867228474afdee788474fda11f14ca82
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154122"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="69e52-102">\<gcAllowVeryLargeObjects> 元素</span><span class="sxs-lookup"><span data-stu-id="69e52-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="69e52-103">在 64 位平台上，启用总大小大于 2 千兆字节 (GB) 的数组。</span><span class="sxs-lookup"><span data-stu-id="69e52-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a><span data-ttu-id="69e52-104">语法</span><span class="sxs-lookup"><span data-stu-id="69e52-104">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69e52-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="69e52-105">Attributes and Elements</span></span>  
 <span data-ttu-id="69e52-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="69e52-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69e52-107">特性</span><span class="sxs-lookup"><span data-stu-id="69e52-107">Attributes</span></span>  
  
|<span data-ttu-id="69e52-108">属性</span><span class="sxs-lookup"><span data-stu-id="69e52-108">Attribute</span></span>|<span data-ttu-id="69e52-109">说明</span><span class="sxs-lookup"><span data-stu-id="69e52-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="69e52-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="69e52-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="69e52-111">指定是否在64位平台上启用了总大小中大于 2 GB 的数组。</span><span class="sxs-lookup"><span data-stu-id="69e52-111">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="69e52-112">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="69e52-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="69e52-113">值</span><span class="sxs-lookup"><span data-stu-id="69e52-113">Value</span></span>|<span data-ttu-id="69e52-114">说明</span><span class="sxs-lookup"><span data-stu-id="69e52-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="69e52-115">总大小中大于 2 GB 的数组未启用。</span><span class="sxs-lookup"><span data-stu-id="69e52-115">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="69e52-116">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="69e52-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="69e52-117">在64位平台上，总大小中已启用大于 2 GB 的数组。</span><span class="sxs-lookup"><span data-stu-id="69e52-117">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69e52-118">子元素</span><span class="sxs-lookup"><span data-stu-id="69e52-118">Child Elements</span></span>  
 <span data-ttu-id="69e52-119">无。</span><span class="sxs-lookup"><span data-stu-id="69e52-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69e52-120">父元素</span><span class="sxs-lookup"><span data-stu-id="69e52-120">Parent Elements</span></span>  
  
|<span data-ttu-id="69e52-121">元素</span><span class="sxs-lookup"><span data-stu-id="69e52-121">Element</span></span>|<span data-ttu-id="69e52-122">描述</span><span class="sxs-lookup"><span data-stu-id="69e52-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="69e52-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="69e52-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="69e52-124">包含有关运行时初始化选项的信息。</span><span class="sxs-lookup"><span data-stu-id="69e52-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69e52-125">注解</span><span class="sxs-lookup"><span data-stu-id="69e52-125">Remarks</span></span>  
 <span data-ttu-id="69e52-126">在应用程序配置文件中使用此元素可启用大小大于 2 GB 的数组，但不会更改对象大小或数组大小的其他限制：</span><span class="sxs-lookup"><span data-stu-id="69e52-126">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="69e52-127">数组中元素的最大数目为 <xref:System.UInt32.MaxValue?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="69e52-127">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="69e52-128">任何单个维度中的最大索引为2147483591（0x7FFFFFC7）（对于字节数组）和单字节结构数组，2146435071（0X7FEFFFFF）用于其他类型。</span><span class="sxs-lookup"><span data-stu-id="69e52-128">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="69e52-129">字符串和其他非数组对象的最大大小不变。</span><span class="sxs-lookup"><span data-stu-id="69e52-129">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="69e52-130">在启用此功能之前，请确保应用程序不包含不安全代码，该代码假定所有数组大小均小于 2 GB。</span><span class="sxs-lookup"><span data-stu-id="69e52-130">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="69e52-131">例如，使用数组作为缓冲区的不安全代码可能容易受到缓冲区溢出的攻击，因为假设数组不会超过 2 GB。</span><span class="sxs-lookup"><span data-stu-id="69e52-131">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69e52-132">示例</span><span class="sxs-lookup"><span data-stu-id="69e52-132">Example</span></span>  
 <span data-ttu-id="69e52-133">下面的示例演示如何为应用程序启用此功能。</span><span class="sxs-lookup"><span data-stu-id="69e52-133">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="69e52-134">受以下版本支持：</span><span class="sxs-lookup"><span data-stu-id="69e52-134">Supported in</span></span>

<span data-ttu-id="69e52-135">.NET Framework 4.5 及更高版本</span><span class="sxs-lookup"><span data-stu-id="69e52-135">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="69e52-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="69e52-136">See also</span></span>

- [<span data-ttu-id="69e52-137">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="69e52-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="69e52-138">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="69e52-138">Configuration File Schema</span></span>](../index.md)
