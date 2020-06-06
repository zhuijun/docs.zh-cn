---
title: <httpWebRequest> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: d33dadc14510feb00e05ca557b507b0cf8fa0dd0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087461"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="cf8f0-102">\<httpWebRequest> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="cf8f0-102">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="cf8f0-103">自定义 Web 请求参数。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-103">Customizes Web request parameters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpWebRequest>**

## <a name="syntax"></a><span data-ttu-id="cf8f0-104">语法</span><span class="sxs-lookup"><span data-stu-id="cf8f0-104">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf8f0-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cf8f0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cf8f0-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf8f0-107">特性</span><span class="sxs-lookup"><span data-stu-id="cf8f0-107">Attributes</span></span>  
  
|<span data-ttu-id="cf8f0-108">**特性**</span><span class="sxs-lookup"><span data-stu-id="cf8f0-108">**Attribute**</span></span>|<span data-ttu-id="cf8f0-109">**描述**</span><span class="sxs-lookup"><span data-stu-id="cf8f0-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="cf8f0-110">指定响应标头的最大长度（以 kb 为单位）。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-110">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="cf8f0-111">默认值为 64。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-111">The default is 64.</span></span> <span data-ttu-id="cf8f0-112">如果值为-1，则指示不会对响应标头施加大小限制。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-112">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="cf8f0-113">指定错误响应的最大长度（以 kb 为单位）。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-113">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="cf8f0-114">默认值为 64。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-114">The default is 64.</span></span> <span data-ttu-id="cf8f0-115">如果值为-1，则表示不对错误响应施加大小限制。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-115">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="cf8f0-116">指定用于响应未经授权的错误代码的上载的最大长度（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-116">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="cf8f0-117">默认值为 -1。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-117">The default is -1.</span></span> <span data-ttu-id="cf8f0-118">值 -1 表示没有对上载施加大小限制。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-118">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="cf8f0-119">指定是否启用安全标头分析。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-119">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="cf8f0-120">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-120">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf8f0-121">子元素</span><span class="sxs-lookup"><span data-stu-id="cf8f0-121">Child Elements</span></span>  
 <span data-ttu-id="cf8f0-122">无。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf8f0-123">父元素</span><span class="sxs-lookup"><span data-stu-id="cf8f0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="cf8f0-124">**元素**</span><span class="sxs-lookup"><span data-stu-id="cf8f0-124">**Element**</span></span>|<span data-ttu-id="cf8f0-125">**描述**</span><span class="sxs-lookup"><span data-stu-id="cf8f0-125">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cf8f0-126">设置</span><span class="sxs-lookup"><span data-stu-id="cf8f0-126">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="cf8f0-127">配置 <xref:System.Net> 命名空间的基本网络选项。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-127">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf8f0-128">注解</span><span class="sxs-lookup"><span data-stu-id="cf8f0-128">Remarks</span></span>  
 <span data-ttu-id="cf8f0-129">默认情况下，.NET Framework 严格地强制执行 RFC 2616，以便进行 URI 分析。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-129">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="cf8f0-130">某些服务器响应可能在禁止字段中包含控制字符，这将导致 <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> 方法引发 <xref:System.Net.WebException> 。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-130">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="cf8f0-131">如果**useUnsafeHeaderParsing**设置为**true**，则 <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> 在这种情况下将不会引发; 但是，你的应用程序将容易受到多种形式的 URI 分析攻击的攻击。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-131">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="cf8f0-132">最佳解决方案是更改服务器，使响应不包含控制字符。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-132">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cf8f0-133">配置文件</span><span class="sxs-lookup"><span data-stu-id="cf8f0-133">Configuration Files</span></span>  
 <span data-ttu-id="cf8f0-134">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf8f0-135">示例</span><span class="sxs-lookup"><span data-stu-id="cf8f0-135">Example</span></span>  
 <span data-ttu-id="cf8f0-136">下面的示例演示如何指定大于标准最大标头长度。</span><span class="sxs-lookup"><span data-stu-id="cf8f0-136">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf8f0-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cf8f0-137">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="cf8f0-138">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="cf8f0-138">Network Settings Schema</span></span>](index.md)
