---
title: webRequestModules 的 <remove> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
ms.openlocfilehash: afa1aef8ea71f43a136987ec5b6e1925c6d9fb40
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154720"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="024be-102">webRequestModules 的 \<remove> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="024be-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="024be-103">从应用程序中移除自定义 Web 请求模块。</span><span class="sxs-lookup"><span data-stu-id="024be-103">Removes a custom Web request module from the application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**
  
## <a name="syntax"></a><span data-ttu-id="024be-104">语法</span><span class="sxs-lookup"><span data-stu-id="024be-104">Syntax</span></span>  
  
```xml  
<remove
  prefix="URI prefix"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="024be-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="024be-105">Attributes and Elements</span></span>  
 <span data-ttu-id="024be-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="024be-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="024be-107">特性</span><span class="sxs-lookup"><span data-stu-id="024be-107">Attributes</span></span>  
  
|<span data-ttu-id="024be-108">**特性**</span><span class="sxs-lookup"><span data-stu-id="024be-108">**Attribute**</span></span>|<span data-ttu-id="024be-109">**描述**</span><span class="sxs-lookup"><span data-stu-id="024be-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="024be-110">此 Web 请求模块处理的请求的 URI 前缀。</span><span class="sxs-lookup"><span data-stu-id="024be-110">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="024be-111">子元素</span><span class="sxs-lookup"><span data-stu-id="024be-111">Child Elements</span></span>  
 <span data-ttu-id="024be-112">无。</span><span class="sxs-lookup"><span data-stu-id="024be-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="024be-113">父元素</span><span class="sxs-lookup"><span data-stu-id="024be-113">Parent Elements</span></span>  
  
|<span data-ttu-id="024be-114">**元素**</span><span class="sxs-lookup"><span data-stu-id="024be-114">**Element**</span></span>|<span data-ttu-id="024be-115">**描述**</span><span class="sxs-lookup"><span data-stu-id="024be-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="024be-116">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="024be-116">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="024be-117">指定用于从网络主机请求信息的模块。</span><span class="sxs-lookup"><span data-stu-id="024be-117">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="024be-118">注解</span><span class="sxs-lookup"><span data-stu-id="024be-118">Remarks</span></span>  
 <span data-ttu-id="024be-119">`remove`元素将为指定的 URI 前缀删除已注册的 Web 请求模块。</span><span class="sxs-lookup"><span data-stu-id="024be-119">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="024be-120">特性的值 `prefix` 应为有效 URI 的前导字符，例如，" `http` " 或 " `http://www.contoso.com` "。</span><span class="sxs-lookup"><span data-stu-id="024be-120">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="024be-121">配置文件</span><span class="sxs-lookup"><span data-stu-id="024be-121">Configuration Files</span></span>  
 <span data-ttu-id="024be-122">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="024be-122">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="024be-123">示例</span><span class="sxs-lookup"><span data-stu-id="024be-123">Example</span></span>  

<span data-ttu-id="024be-124">下面的示例将删除 HTTP 的现有 Web 请求模块，然后将新的自定义 Web 请求模块注册到的 HTTP 请求 `www.contoso.com` 。</span><span class="sxs-lookup"><span data-stu-id="024be-124">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="024be-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="024be-125">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="024be-126">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="024be-126">Network Settings Schema</span></span>](index.md)
