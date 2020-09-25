---
title: bypasslist 的 <clear> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
ms.openlocfilehash: 96cef2dff3156e49a93be818230c83370dab5264
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185856"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="84a65-102">bypasslist 的 \<clear> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="84a65-102">\<clear> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="84a65-103">清除代理跳过列表。</span><span class="sxs-lookup"><span data-stu-id="84a65-103">Clears the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="84a65-104">语法</span><span class="sxs-lookup"><span data-stu-id="84a65-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84a65-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="84a65-105">Attributes and Elements</span></span>  

 <span data-ttu-id="84a65-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="84a65-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84a65-107">特性</span><span class="sxs-lookup"><span data-stu-id="84a65-107">Attributes</span></span>  

 <span data-ttu-id="84a65-108">无。</span><span class="sxs-lookup"><span data-stu-id="84a65-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="84a65-109">子元素</span><span class="sxs-lookup"><span data-stu-id="84a65-109">Child Elements</span></span>  

 <span data-ttu-id="84a65-110">无。</span><span class="sxs-lookup"><span data-stu-id="84a65-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84a65-111">父元素</span><span class="sxs-lookup"><span data-stu-id="84a65-111">Parent Elements</span></span>  
  
|<span data-ttu-id="84a65-112">**元素**</span><span class="sxs-lookup"><span data-stu-id="84a65-112">**Element**</span></span>|<span data-ttu-id="84a65-113">**说明**</span><span class="sxs-lookup"><span data-stu-id="84a65-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="84a65-114">bypasslist</span><span class="sxs-lookup"><span data-stu-id="84a65-114">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="84a65-115">提供了一组正则表达式，描述不使用代理的地址。</span><span class="sxs-lookup"><span data-stu-id="84a65-115">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84a65-116">备注</span><span class="sxs-lookup"><span data-stu-id="84a65-116">Remarks</span></span>  

 <span data-ttu-id="84a65-117">`clear`元素清除跳过列表中的所有条目。</span><span class="sxs-lookup"><span data-stu-id="84a65-117">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="84a65-118">配置文件</span><span class="sxs-lookup"><span data-stu-id="84a65-118">Configuration Files</span></span>  

 <span data-ttu-id="84a65-119">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="84a65-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="84a65-120">示例</span><span class="sxs-lookup"><span data-stu-id="84a65-120">Example</span></span>  

 <span data-ttu-id="84a65-121">下面的示例清除了跳过列表，并将两个地址添加到了跳过列表。</span><span class="sxs-lookup"><span data-stu-id="84a65-121">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="84a65-122">首先，将跳过 contoso.com 域中所有服务器的代理;第二种方式是跳过其 IP 地址以192.168 开头的所有服务器的代理。</span><span class="sxs-lookup"><span data-stu-id="84a65-122">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="84a65-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="84a65-123">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="84a65-124">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="84a65-124">Network Settings Schema</span></span>](index.md)
