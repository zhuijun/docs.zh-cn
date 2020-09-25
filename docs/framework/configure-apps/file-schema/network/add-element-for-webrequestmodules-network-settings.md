---
title: webRequestModules 的 <add> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: 8d792b967d967540469dca7c090e0f905ecb2e6b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201754"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="3614b-102">webRequestModules 的 \<add> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="3614b-102">\<add> Element for webRequestModules (Network Settings)</span></span>

<span data-ttu-id="3614b-103">向应用程序添加自定义 Web 请求模块。</span><span class="sxs-lookup"><span data-stu-id="3614b-103">Adds a custom Web request module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="3614b-104">语法</span><span class="sxs-lookup"><span data-stu-id="3614b-104">Syntax</span></span>  
  
```xml  
<add
  prefix="URI prefix"
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3614b-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3614b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3614b-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3614b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3614b-107">特性</span><span class="sxs-lookup"><span data-stu-id="3614b-107">Attributes</span></span>  
  
|<span data-ttu-id="3614b-108">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="3614b-108">**Attribute**</span></span>|<span data-ttu-id="3614b-109">**说明**</span><span class="sxs-lookup"><span data-stu-id="3614b-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="3614b-110">此 Web 请求模块处理的请求的 URI 前缀。</span><span class="sxs-lookup"><span data-stu-id="3614b-110">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="3614b-111">完全限定的类型名称 (由) 的 <xref:System.Type.FullName%2A> 属性和程序集名称指示 (由 <xref:System.Reflection.Assembly.FullName%2A> 实现此 Web 请求模块的由逗号分隔的) 属性指示。</span><span class="sxs-lookup"><span data-stu-id="3614b-111">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3614b-112">子元素</span><span class="sxs-lookup"><span data-stu-id="3614b-112">Child Elements</span></span>  

 <span data-ttu-id="3614b-113">无。</span><span class="sxs-lookup"><span data-stu-id="3614b-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3614b-114">父元素</span><span class="sxs-lookup"><span data-stu-id="3614b-114">Parent Elements</span></span>  
  
|<span data-ttu-id="3614b-115">**元素**</span><span class="sxs-lookup"><span data-stu-id="3614b-115">**Element**</span></span>|<span data-ttu-id="3614b-116">**说明**</span><span class="sxs-lookup"><span data-stu-id="3614b-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3614b-117">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="3614b-117">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="3614b-118">指定用于从网络主机请求信息的模块。</span><span class="sxs-lookup"><span data-stu-id="3614b-118">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3614b-119">备注</span><span class="sxs-lookup"><span data-stu-id="3614b-119">Remarks</span></span>  

 <span data-ttu-id="3614b-120">`prefix`特性定义使用指定 Web 请求模块的 URI 前缀。</span><span class="sxs-lookup"><span data-stu-id="3614b-120">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="3614b-121">通常会将 Web 请求模块注册为处理特定协议（如 HTTP 或 FTP），但可以注册它来处理对服务器上特定服务器或路径的请求。</span><span class="sxs-lookup"><span data-stu-id="3614b-121">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="3614b-122">当 URI 匹配前缀传递到方法时，将创建 Web 请求模块 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="3614b-122">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="3614b-123">特性的值 `prefix` 应为有效 URI 的前导字符。</span><span class="sxs-lookup"><span data-stu-id="3614b-123">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="3614b-124">例如，`http` 或 `http://www.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="3614b-124">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="3614b-125">特性的值 `type` 应为有效的类型名称和相应的程序集名称，用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="3614b-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="3614b-126">配置文件</span><span class="sxs-lookup"><span data-stu-id="3614b-126">Configuration Files</span></span>  

 <span data-ttu-id="3614b-127">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="3614b-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3614b-128">示例</span><span class="sxs-lookup"><span data-stu-id="3614b-128">Example</span></span>  

 <span data-ttu-id="3614b-129">下面的示例为 HTTP 注册自定义 Web 请求模块。</span><span class="sxs-lookup"><span data-stu-id="3614b-129">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="3614b-130">应将版本和 PublicKeyToken 的值替换为指定模块的正确值。</span><span class="sxs-lookup"><span data-stu-id="3614b-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3614b-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="3614b-131">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="3614b-132">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="3614b-132">Network Settings Schema</span></span>](index.md)
