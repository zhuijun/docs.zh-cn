---
title: <settings> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: c5fe0b9eccd1c429c0041fcfab06b0cc20a20aa2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167270"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="6dc4f-102">\<settings> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="6dc4f-102">\<settings> Element (Network Settings)</span></span>

<span data-ttu-id="6dc4f-103">配置 <xref:System.Net?displayProperty=nameWithType> 命名空间的基本网络选项。</span><span class="sxs-lookup"><span data-stu-id="6dc4f-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a><span data-ttu-id="6dc4f-104">语法</span><span class="sxs-lookup"><span data-stu-id="6dc4f-104">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6dc4f-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6dc4f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6dc4f-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6dc4f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6dc4f-107">特性</span><span class="sxs-lookup"><span data-stu-id="6dc4f-107">Attributes</span></span>  

 <span data-ttu-id="6dc4f-108">无。</span><span class="sxs-lookup"><span data-stu-id="6dc4f-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6dc4f-109">子元素</span><span class="sxs-lookup"><span data-stu-id="6dc4f-109">Child Elements</span></span>  
  
|<span data-ttu-id="6dc4f-110">元素</span><span class="sxs-lookup"><span data-stu-id="6dc4f-110">Element</span></span>|<span data-ttu-id="6dc4f-111">描述</span><span class="sxs-lookup"><span data-stu-id="6dc4f-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6dc4f-112">httpListener</span><span class="sxs-lookup"><span data-stu-id="6dc4f-112">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="6dc4f-113">自定义类使用的参数 <xref:System.Net.HttpListener> 。</span><span class="sxs-lookup"><span data-stu-id="6dc4f-113">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="6dc4f-114">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="6dc4f-114">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="6dc4f-115">自定义 Web 请求参数。</span><span class="sxs-lookup"><span data-stu-id="6dc4f-115">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="6dc4f-116">ipv6</span><span class="sxs-lookup"><span data-stu-id="6dc4f-116">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="6dc4f-117">启用 Internet 协议版本 6 (IPv6) 支持。</span><span class="sxs-lookup"><span data-stu-id="6dc4f-117">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="6dc4f-118">\<performanceCounter> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="6dc4f-118">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="6dc4f-119">启用网络性能计数器。</span><span class="sxs-lookup"><span data-stu-id="6dc4f-119">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="6dc4f-120">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="6dc4f-120">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="6dc4f-121">配置与网络资源的连接。</span><span class="sxs-lookup"><span data-stu-id="6dc4f-121">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="6dc4f-122">片</span><span class="sxs-lookup"><span data-stu-id="6dc4f-122">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="6dc4f-123">指定套接字操作是否使用完成端口。</span><span class="sxs-lookup"><span data-stu-id="6dc4f-123">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="6dc4f-124">\<webProxyScript> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="6dc4f-124">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="6dc4f-125">配置用于发现 Web 代理的脚本的特征。</span><span class="sxs-lookup"><span data-stu-id="6dc4f-125">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6dc4f-126">父元素</span><span class="sxs-lookup"><span data-stu-id="6dc4f-126">Parent Elements</span></span>  
  
|<span data-ttu-id="6dc4f-127">元素</span><span class="sxs-lookup"><span data-stu-id="6dc4f-127">Element</span></span>|<span data-ttu-id="6dc4f-128">描述</span><span class="sxs-lookup"><span data-stu-id="6dc4f-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6dc4f-129">system.net</span><span class="sxs-lookup"><span data-stu-id="6dc4f-129">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="6dc4f-130">包含指定 .NET Framework 如何连接到网络的设置。</span><span class="sxs-lookup"><span data-stu-id="6dc4f-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6dc4f-131">备注</span><span class="sxs-lookup"><span data-stu-id="6dc4f-131">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6dc4f-132">配置文件</span><span class="sxs-lookup"><span data-stu-id="6dc4f-132">Configuration Files</span></span>  

 <span data-ttu-id="6dc4f-133">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="6dc4f-133">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dc4f-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="6dc4f-134">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="6dc4f-135">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="6dc4f-135">Network Settings Schema</span></span>](index.md)
