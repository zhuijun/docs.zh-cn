---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252111"
---
# \<chunkedCookieHandler>
<span data-ttu-id="f0fb1-101">配置 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 。</span><span class="sxs-lookup"><span data-stu-id="f0fb1-101">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="f0fb1-102">仅当 `mode` 元素的属性 `<cookieHandler>` 为 "默认值" 或 "分块" 时，此元素才能存在。</span><span class="sxs-lookup"><span data-stu-id="f0fb1-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="f0fb1-103">语法</span><span class="sxs-lookup"><span data-stu-id="f0fb1-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0fb1-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="f0fb1-104">Attributes and Elements</span></span>  
 <span data-ttu-id="f0fb1-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f0fb1-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0fb1-106">特性</span><span class="sxs-lookup"><span data-stu-id="f0fb1-106">Attributes</span></span>  
  
|<span data-ttu-id="f0fb1-107">属性</span><span class="sxs-lookup"><span data-stu-id="f0fb1-107">Attribute</span></span>|<span data-ttu-id="f0fb1-108">说明</span><span class="sxs-lookup"><span data-stu-id="f0fb1-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0fb1-109">chunkSize</span><span class="sxs-lookup"><span data-stu-id="f0fb1-109">chunkSize</span></span>|<span data-ttu-id="f0fb1-110">任何一个 HTTP cookie 的 HTTP cookie 数据的最大大小（字符数）。</span><span class="sxs-lookup"><span data-stu-id="f0fb1-110">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="f0fb1-111">调整块区大小时必须小心谨慎。</span><span class="sxs-lookup"><span data-stu-id="f0fb1-111">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="f0fb1-112">Web 浏览器对 cookie 和每个域允许的数量有不同的限制。</span><span class="sxs-lookup"><span data-stu-id="f0fb1-112">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="f0fb1-113">例如，原始 Netscape 规范规定这些限制： 300 cookie 总数、每个 cookie 标头4096个字节（包括元数据，而不仅仅是 cookie 值）和每个域20个 cookie。</span><span class="sxs-lookup"><span data-stu-id="f0fb1-113">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="f0fb1-114">默认为 2000。</span><span class="sxs-lookup"><span data-stu-id="f0fb1-114">The default is 2000.</span></span> <span data-ttu-id="f0fb1-115">必需。</span><span class="sxs-lookup"><span data-stu-id="f0fb1-115">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0fb1-116">子元素</span><span class="sxs-lookup"><span data-stu-id="f0fb1-116">Child Elements</span></span>  
 <span data-ttu-id="f0fb1-117">无</span><span class="sxs-lookup"><span data-stu-id="f0fb1-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0fb1-118">父元素</span><span class="sxs-lookup"><span data-stu-id="f0fb1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f0fb1-119">元素</span><span class="sxs-lookup"><span data-stu-id="f0fb1-119">Element</span></span>|<span data-ttu-id="f0fb1-120">描述</span><span class="sxs-lookup"><span data-stu-id="f0fb1-120">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="f0fb1-121">配置 <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> （SAM）用于读取和写入 cookie 的。</span><span class="sxs-lookup"><span data-stu-id="f0fb1-121">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0fb1-122">注解</span><span class="sxs-lookup"><span data-stu-id="f0fb1-122">Remarks</span></span>  
 <span data-ttu-id="f0fb1-123"><xref:System.IdentityModel.Services.ChunkedCookieHandler>通过将 `mode` 元素的属性设置 `<cookieHandler>` 为 "默认值" 或 "分块" 指定时，可以指定 cookie 处理程序用来读取和写入 cookie 的块区大小，方法是包含一个 `<chunkedCookieHandler>` 子元素并设置其 `chunkSize` 属性。</span><span class="sxs-lookup"><span data-stu-id="f0fb1-123">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="f0fb1-124">如果该 `<chunkedCookieHandler>` 元素不存在，则使用默认的块区大小（2000字节）。</span><span class="sxs-lookup"><span data-stu-id="f0fb1-124">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="f0fb1-125">当 `mode` 特性设置为 "Custom" 时，不能指定此元素。</span><span class="sxs-lookup"><span data-stu-id="f0fb1-125">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="f0fb1-126">`<chunkedCookieHandler>`元素由 <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> 类表示。</span><span class="sxs-lookup"><span data-stu-id="f0fb1-126">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0fb1-127">示例</span><span class="sxs-lookup"><span data-stu-id="f0fb1-127">Example</span></span>  
 <span data-ttu-id="f0fb1-128">下面的示例配置一个分块 cookie 处理程序，该处理程序以3000字节的块写入 cookie。</span><span class="sxs-lookup"><span data-stu-id="f0fb1-128">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f0fb1-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0fb1-129">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
