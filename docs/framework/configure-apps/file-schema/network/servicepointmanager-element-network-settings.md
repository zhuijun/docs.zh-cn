---
title: <servicePointManager> 元素（网络设置）
description: "\" <servicePointManager> 网络设置\" 元素配置与 .NET Framework 中的网络资源选项的连接。"
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: eb27716ec7c2936f32a7e4d4c983d1e175c4d044
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504519"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="525a1-103">\<servicePointManager> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="525a1-103">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="525a1-104">配置与网络资源的连接。</span><span class="sxs-lookup"><span data-stu-id="525a1-104">Configures connections to network resources.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**

## <a name="syntax"></a><span data-ttu-id="525a1-105">语法</span><span class="sxs-lookup"><span data-stu-id="525a1-105">Syntax</span></span>  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="525a1-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="525a1-106">Attributes and Elements</span></span>  
 <span data-ttu-id="525a1-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="525a1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="525a1-108">特性</span><span class="sxs-lookup"><span data-stu-id="525a1-108">Attributes</span></span>  
  
|<span data-ttu-id="525a1-109">**特性**</span><span class="sxs-lookup"><span data-stu-id="525a1-109">**Attribute**</span></span>|<span data-ttu-id="525a1-110">**说明**</span><span class="sxs-lookup"><span data-stu-id="525a1-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="525a1-111">指定在使用证书之前，系统是否应验证证书上的名称是否与服务器主机名匹配。</span><span class="sxs-lookup"><span data-stu-id="525a1-111">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="525a1-112">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="525a1-112">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="525a1-113">指定在使用证书之前系统是否应检查证书是否已吊销。</span><span class="sxs-lookup"><span data-stu-id="525a1-113">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="525a1-114">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="525a1-114">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="525a1-115">指定域名服务（DNS）解析与 DNS 轮循机制选项一起缓存的时间长度（以毫秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="525a1-115">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="525a1-116">默认值是 120,000 毫秒（2 分钟）。</span><span class="sxs-lookup"><span data-stu-id="525a1-116">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="525a1-117">指定具有多个 Internet 协议（IP）地址的主机名的 DNS 解析是返回所有地址，还是只返回第一个地址。</span><span class="sxs-lookup"><span data-stu-id="525a1-117">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="525a1-118">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="525a1-118">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="525a1-119">指定应用到实例上的 SSL/TLS 会话的加密策略 <xref:System.Net.ServicePointManager> 。</span><span class="sxs-lookup"><span data-stu-id="525a1-119">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="525a1-120">可能的值等效于枚举的值 <xref:System.Net.Security.EncryptionPolicy> 。</span><span class="sxs-lookup"><span data-stu-id="525a1-120">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="525a1-121"><xref:System.Security.Authentication.CipherAlgorithmType.Null>加密策略设置为时，需要使用 `NoEncryption` 。</span><span class="sxs-lookup"><span data-stu-id="525a1-121">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="525a1-122">默认值为 `RequireEncryption`。</span><span class="sxs-lookup"><span data-stu-id="525a1-122">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="525a1-123">指定 POST 方法是否应该接收 `100-continue` 来自服务器的响应。</span><span class="sxs-lookup"><span data-stu-id="525a1-123">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="525a1-124">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="525a1-124">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="525a1-125">指定由服务点管理器控制的连接是否使用 Nagle 算法。</span><span class="sxs-lookup"><span data-stu-id="525a1-125">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="525a1-126">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="525a1-126">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="525a1-127">子元素</span><span class="sxs-lookup"><span data-stu-id="525a1-127">Child Elements</span></span>  
 <span data-ttu-id="525a1-128">无。</span><span class="sxs-lookup"><span data-stu-id="525a1-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="525a1-129">父元素</span><span class="sxs-lookup"><span data-stu-id="525a1-129">Parent Elements</span></span>  
  
|<span data-ttu-id="525a1-130">**元素**</span><span class="sxs-lookup"><span data-stu-id="525a1-130">**Element**</span></span>|<span data-ttu-id="525a1-131">**说明**</span><span class="sxs-lookup"><span data-stu-id="525a1-131">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="525a1-132">设置</span><span class="sxs-lookup"><span data-stu-id="525a1-132">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="525a1-133">配置 <xref:System.Net> 命名空间的基本网络选项。</span><span class="sxs-lookup"><span data-stu-id="525a1-133">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="525a1-134">注解</span><span class="sxs-lookup"><span data-stu-id="525a1-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="525a1-135">配置文件</span><span class="sxs-lookup"><span data-stu-id="525a1-135">Configuration Files</span></span>  
 <span data-ttu-id="525a1-136">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="525a1-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="525a1-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="525a1-137">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="525a1-138">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="525a1-138">Network Settings Schema</span></span>](index.md)
