---
title: <webProxyScript> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: e36b470b1ec348085b13a58630b0ac6833e43946
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178302"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="e9204-102">\<webProxyScript> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="e9204-102">\<webProxyScript> Element (Network Settings)</span></span>

<span data-ttu-id="e9204-103">配置用于发现 Web 代理的脚本的特征。</span><span class="sxs-lookup"><span data-stu-id="e9204-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**

## <a name="syntax"></a><span data-ttu-id="e9204-104">语法</span><span class="sxs-lookup"><span data-stu-id="e9204-104">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9204-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e9204-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e9204-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e9204-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9204-107">特性</span><span class="sxs-lookup"><span data-stu-id="e9204-107">Attributes</span></span>  
  
|<span data-ttu-id="e9204-108">属性</span><span class="sxs-lookup"><span data-stu-id="e9204-108">Attribute</span></span>|<span data-ttu-id="e9204-109">描述</span><span class="sxs-lookup"><span data-stu-id="e9204-109">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="e9204-110">指定下载脚本的最长时间，以小时、分钟和秒为单位。</span><span class="sxs-lookup"><span data-stu-id="e9204-110">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="e9204-111">默认值为一分钟。</span><span class="sxs-lookup"><span data-stu-id="e9204-111">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9204-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e9204-112">Child Elements</span></span>  

 <span data-ttu-id="e9204-113">无。</span><span class="sxs-lookup"><span data-stu-id="e9204-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9204-114">父元素</span><span class="sxs-lookup"><span data-stu-id="e9204-114">Parent Elements</span></span>  
  
|<span data-ttu-id="e9204-115">元素</span><span class="sxs-lookup"><span data-stu-id="e9204-115">Element</span></span>|<span data-ttu-id="e9204-116">描述</span><span class="sxs-lookup"><span data-stu-id="e9204-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9204-117">设置</span><span class="sxs-lookup"><span data-stu-id="e9204-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="e9204-118">配置 <xref:System.Net> 命名空间的基本网络选项。</span><span class="sxs-lookup"><span data-stu-id="e9204-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9204-119">备注</span><span class="sxs-lookup"><span data-stu-id="e9204-119">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e9204-120">配置文件</span><span class="sxs-lookup"><span data-stu-id="e9204-120">Configuration Files</span></span>  

 <span data-ttu-id="e9204-121">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="e9204-121">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9204-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="e9204-122">See also</span></span>

- [<span data-ttu-id="e9204-123">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="e9204-123">Network Settings Schema</span></span>](index.md)
