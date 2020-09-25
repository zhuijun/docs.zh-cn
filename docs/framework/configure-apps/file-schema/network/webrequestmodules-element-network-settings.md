---
title: <webRequestModules> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: 9396ca393523dce5593531f332e5c07241987947
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186999"
---
# <a name="webrequestmodules-element-network-settings"></a><span data-ttu-id="c42ac-102">\<webRequestModules> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="c42ac-102">\<webRequestModules> Element (Network Settings)</span></span>

<span data-ttu-id="c42ac-103">指定用于从网络主机请求信息的模块。</span><span class="sxs-lookup"><span data-stu-id="c42ac-103">Specifies modules to use to request information from network hosts.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules>  
  
## <a name="syntax"></a><span data-ttu-id="c42ac-104">语法</span><span class="sxs-lookup"><span data-stu-id="c42ac-104">Syntax</span></span>  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c42ac-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c42ac-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c42ac-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c42ac-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c42ac-107">特性</span><span class="sxs-lookup"><span data-stu-id="c42ac-107">Attributes</span></span>  

 <span data-ttu-id="c42ac-108">无。</span><span class="sxs-lookup"><span data-stu-id="c42ac-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c42ac-109">子元素</span><span class="sxs-lookup"><span data-stu-id="c42ac-109">Child Elements</span></span>  
  
|<span data-ttu-id="c42ac-110">**元素**</span><span class="sxs-lookup"><span data-stu-id="c42ac-110">**Element**</span></span>|<span data-ttu-id="c42ac-111">**说明**</span><span class="sxs-lookup"><span data-stu-id="c42ac-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c42ac-112">add</span><span class="sxs-lookup"><span data-stu-id="c42ac-112">add</span></span>](add-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="c42ac-113">向应用程序添加自定义 Web 请求模块。</span><span class="sxs-lookup"><span data-stu-id="c42ac-113">Adds a custom Web request module to the application.</span></span>|  
|[<span data-ttu-id="c42ac-114">clear</span><span class="sxs-lookup"><span data-stu-id="c42ac-114">clear</span></span>](clear-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="c42ac-115">从应用程序中删除所有已注册的 Web 请求模块。</span><span class="sxs-lookup"><span data-stu-id="c42ac-115">Removes all registered Web request modules from the application.</span></span>|  
|[<span data-ttu-id="c42ac-116">remove</span><span class="sxs-lookup"><span data-stu-id="c42ac-116">remove</span></span>](remove-element-for-webrequestmodules-network-settings.md)|<span data-ttu-id="c42ac-117">从应用程序中移除自定义 Web 请求模块。</span><span class="sxs-lookup"><span data-stu-id="c42ac-117">Removes a custom Web request module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c42ac-118">父元素</span><span class="sxs-lookup"><span data-stu-id="c42ac-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c42ac-119">**元素**</span><span class="sxs-lookup"><span data-stu-id="c42ac-119">**Element**</span></span>|<span data-ttu-id="c42ac-120">**说明**</span><span class="sxs-lookup"><span data-stu-id="c42ac-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c42ac-121">system.net</span><span class="sxs-lookup"><span data-stu-id="c42ac-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="c42ac-122">包含指定 .NET Framework 如何连接到网络的设置。</span><span class="sxs-lookup"><span data-stu-id="c42ac-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c42ac-123">备注</span><span class="sxs-lookup"><span data-stu-id="c42ac-123">Remarks</span></span>  

 <span data-ttu-id="c42ac-124">此 `webRequestModules` 元素注册 <xref:System.Net.WebRequest> 类的子代，以处理向网络主机发出的信息请求。</span><span class="sxs-lookup"><span data-stu-id="c42ac-124">The `webRequestModules` element registers descendants of the <xref:System.Net.WebRequest> class to handle information requests to network hosts.</span></span> <span data-ttu-id="c42ac-125">Web 请求模块必须实现 <xref:System.Net.IWebRequestCreate> 接口。</span><span class="sxs-lookup"><span data-stu-id="c42ac-125">Web request modules must implement the <xref:System.Net.IWebRequestCreate> interface.</span></span>  
  
 <span data-ttu-id="c42ac-126">.NET Framework 包含以、和开头的 Uri 的 Web 请求 `http://` 模块 `https://` `file://` 。</span><span class="sxs-lookup"><span data-stu-id="c42ac-126">The .NET Framework includes Web request modules for URIs that begin with `http://`, `https://`, and `file://`.</span></span> <span data-ttu-id="c42ac-127">只能通过在配置文件中注册自定义模块来重写默认模块。</span><span class="sxs-lookup"><span data-stu-id="c42ac-127">You can override the default modules only by registering a custom module in the configuration file.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c42ac-128">配置文件</span><span class="sxs-lookup"><span data-stu-id="c42ac-128">Configuration Files</span></span>  

 <span data-ttu-id="c42ac-129">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="c42ac-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c42ac-130">示例</span><span class="sxs-lookup"><span data-stu-id="c42ac-130">Example</span></span>  

 <span data-ttu-id="c42ac-131">下面的示例将注册默认的 HTTP 模块。</span><span class="sxs-lookup"><span data-stu-id="c42ac-131">The following example registers the default HTTP module.</span></span> <span data-ttu-id="c42ac-132">应将版本和 PublicKeyToken 的值替换为指定模块的正确值。</span><span class="sxs-lookup"><span data-stu-id="c42ac-132">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c42ac-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="c42ac-133">See also</span></span>

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [<span data-ttu-id="c42ac-134">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="c42ac-134">Network Settings Schema</span></span>](index.md)
