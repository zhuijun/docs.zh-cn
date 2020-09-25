---
title: <gcAllowVeryLargeObjects> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: 78a42596aae6c3ea0d94ac759d11ed52d0ace539
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178224"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="d7b6d-102">\<gcAllowVeryLargeObjects> 元素</span><span class="sxs-lookup"><span data-stu-id="d7b6d-102">\<gcAllowVeryLargeObjects> Element</span></span>

<span data-ttu-id="d7b6d-103">在 64 位平台上，启用总大小大于 2 千兆字节 (GB) 的数组。</span><span class="sxs-lookup"><span data-stu-id="d7b6d-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**  
  
## <a name="syntax"></a><span data-ttu-id="d7b6d-104">语法</span><span class="sxs-lookup"><span data-stu-id="d7b6d-104">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7b6d-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d7b6d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d7b6d-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d7b6d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7b6d-107">特性</span><span class="sxs-lookup"><span data-stu-id="d7b6d-107">Attributes</span></span>  
  
|<span data-ttu-id="d7b6d-108">属性</span><span class="sxs-lookup"><span data-stu-id="d7b6d-108">Attribute</span></span>|<span data-ttu-id="d7b6d-109">描述</span><span class="sxs-lookup"><span data-stu-id="d7b6d-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d7b6d-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="d7b6d-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="d7b6d-111">指定是否在64位平台上启用了总大小中大于 2 GB 的数组。</span><span class="sxs-lookup"><span data-stu-id="d7b6d-111">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d7b6d-112">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="d7b6d-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="d7b6d-113">值</span><span class="sxs-lookup"><span data-stu-id="d7b6d-113">Value</span></span>|<span data-ttu-id="d7b6d-114">描述</span><span class="sxs-lookup"><span data-stu-id="d7b6d-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d7b6d-115">总大小中大于 2 GB 的数组未启用。</span><span class="sxs-lookup"><span data-stu-id="d7b6d-115">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="d7b6d-116">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="d7b6d-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="d7b6d-117">在64位平台上，总大小中已启用大于 2 GB 的数组。</span><span class="sxs-lookup"><span data-stu-id="d7b6d-117">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7b6d-118">子元素</span><span class="sxs-lookup"><span data-stu-id="d7b6d-118">Child Elements</span></span>  

 <span data-ttu-id="d7b6d-119">无。</span><span class="sxs-lookup"><span data-stu-id="d7b6d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7b6d-120">父元素</span><span class="sxs-lookup"><span data-stu-id="d7b6d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d7b6d-121">元素</span><span class="sxs-lookup"><span data-stu-id="d7b6d-121">Element</span></span>|<span data-ttu-id="d7b6d-122">描述</span><span class="sxs-lookup"><span data-stu-id="d7b6d-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d7b6d-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="d7b6d-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d7b6d-124">包含有关运行时初始化选项的信息。</span><span class="sxs-lookup"><span data-stu-id="d7b6d-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7b6d-125">备注</span><span class="sxs-lookup"><span data-stu-id="d7b6d-125">Remarks</span></span>  

 <span data-ttu-id="d7b6d-126">在应用程序配置文件中使用此元素可启用大小大于 2 GB 的数组，但不会更改对象大小或数组大小的其他限制：</span><span class="sxs-lookup"><span data-stu-id="d7b6d-126">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="d7b6d-127">数组中元素的最大数目为 <xref:System.UInt32.MaxValue?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="d7b6d-127">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="d7b6d-128">任何单个维度中的最大索引为 2147483591 (0x7FFFFFC7) 用于字节数组和单字节结构数组，2146435071 (0X7FEFFFFF) 用于其他类型。</span><span class="sxs-lookup"><span data-stu-id="d7b6d-128">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="d7b6d-129">字符串和其他非数组对象的最大大小不变。</span><span class="sxs-lookup"><span data-stu-id="d7b6d-129">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="d7b6d-130">在启用此功能之前，请确保应用程序不包含不安全代码，该代码假定所有数组大小均小于 2 GB。</span><span class="sxs-lookup"><span data-stu-id="d7b6d-130">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="d7b6d-131">例如，使用数组作为缓冲区的不安全代码可能容易受到缓冲区溢出的攻击，因为假设数组不会超过 2 GB。</span><span class="sxs-lookup"><span data-stu-id="d7b6d-131">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7b6d-132">示例</span><span class="sxs-lookup"><span data-stu-id="d7b6d-132">Example</span></span>  

 <span data-ttu-id="d7b6d-133">下面的示例演示如何为应用程序启用此功能。</span><span class="sxs-lookup"><span data-stu-id="d7b6d-133">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="d7b6d-134">受以下版本支持：</span><span class="sxs-lookup"><span data-stu-id="d7b6d-134">Supported in</span></span>

<span data-ttu-id="d7b6d-135">.NET Framework 4.5 及更高版本</span><span class="sxs-lookup"><span data-stu-id="d7b6d-135">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="d7b6d-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="d7b6d-136">See also</span></span>

- [<span data-ttu-id="d7b6d-137">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="d7b6d-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d7b6d-138">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="d7b6d-138">Configuration File Schema</span></span>](../index.md)
