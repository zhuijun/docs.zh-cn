---
title: webRequestModules 的 <clear> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, webRequestModules
- <webRequestModules>, clear element
- webRequestModules, clear element
- clear element, webRequestModules
ms.assetid: 48f38bcb-f30c-4b74-a8f0-1a3caf1aa96f
ms.openlocfilehash: 892058dd8af8a38bd7bde868b34a2c6899d9a989
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184035"
---
# <a name="clear-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="44f5f-102">webRequestModules 的 \<clear> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="44f5f-102">\<clear> Element for webRequestModules (Network Settings)</span></span>

<span data-ttu-id="44f5f-103">从应用程序中删除所有已注册的 Web 请求模块。</span><span class="sxs-lookup"><span data-stu-id="44f5f-103">Removes all registered Web request modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="44f5f-104">语法</span><span class="sxs-lookup"><span data-stu-id="44f5f-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44f5f-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="44f5f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="44f5f-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="44f5f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44f5f-107">特性</span><span class="sxs-lookup"><span data-stu-id="44f5f-107">Attributes</span></span>  

 <span data-ttu-id="44f5f-108">无。</span><span class="sxs-lookup"><span data-stu-id="44f5f-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="44f5f-109">子元素</span><span class="sxs-lookup"><span data-stu-id="44f5f-109">Child Elements</span></span>  

 <span data-ttu-id="44f5f-110">无。</span><span class="sxs-lookup"><span data-stu-id="44f5f-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44f5f-111">父元素</span><span class="sxs-lookup"><span data-stu-id="44f5f-111">Parent Elements</span></span>  
  
|<span data-ttu-id="44f5f-112">**元素**</span><span class="sxs-lookup"><span data-stu-id="44f5f-112">**Element**</span></span>|<span data-ttu-id="44f5f-113">**说明**</span><span class="sxs-lookup"><span data-stu-id="44f5f-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="44f5f-114">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="44f5f-114">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="44f5f-115">指定用于从网络主机请求信息的模块。</span><span class="sxs-lookup"><span data-stu-id="44f5f-115">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44f5f-116">备注</span><span class="sxs-lookup"><span data-stu-id="44f5f-116">Remarks</span></span>  

 <span data-ttu-id="44f5f-117">`clear`元素删除先前在配置文件中或在配置层次结构中的更高级别定义的所有已注册 Web 请求模块。</span><span class="sxs-lookup"><span data-stu-id="44f5f-117">The `clear` element removes all registered Web request modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="44f5f-118">配置文件</span><span class="sxs-lookup"><span data-stu-id="44f5f-118">Configuration Files</span></span>  

 <span data-ttu-id="44f5f-119">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="44f5f-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44f5f-120">示例</span><span class="sxs-lookup"><span data-stu-id="44f5f-120">Example</span></span>  

 <span data-ttu-id="44f5f-121">下面的示例将清除所有 Web 请求模块，然后为 HTTP 注册 Web 请求模块。</span><span class="sxs-lookup"><span data-stu-id="44f5f-121">The following example clears all Web request modules and then registers a Web request module for HTTP.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <clear/>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="44f5f-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="44f5f-122">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="44f5f-123">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="44f5f-123">Network Settings Schema</span></span>](index.md)
