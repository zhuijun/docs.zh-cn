---
title: <servicePointManager> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: b7333016fea2d46285d3c98181c0ca4904c376f8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089129"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="90e34-102">\<servicePointManager> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="90e34-102">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="90e34-103">配置与网络资源的连接。</span><span class="sxs-lookup"><span data-stu-id="90e34-103">Configures connections to network resources.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**

## <a name="syntax"></a><span data-ttu-id="90e34-104">语法</span><span class="sxs-lookup"><span data-stu-id="90e34-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90e34-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="90e34-105">Attributes and Elements</span></span>  
 <span data-ttu-id="90e34-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="90e34-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90e34-107">特性</span><span class="sxs-lookup"><span data-stu-id="90e34-107">Attributes</span></span>  
  
|<span data-ttu-id="90e34-108">**特性**</span><span class="sxs-lookup"><span data-stu-id="90e34-108">**Attribute**</span></span>|<span data-ttu-id="90e34-109">**描述**</span><span class="sxs-lookup"><span data-stu-id="90e34-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="90e34-110">指定在使用证书之前，系统是否应验证证书上的名称是否与服务器主机名匹配。</span><span class="sxs-lookup"><span data-stu-id="90e34-110">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="90e34-111">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="90e34-111">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="90e34-112">指定在使用证书之前系统是否应检查证书是否已吊销。</span><span class="sxs-lookup"><span data-stu-id="90e34-112">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="90e34-113">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="90e34-113">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="90e34-114">指定域名服务（DNS）解析与 DNS 轮循机制选项一起缓存的时间长度（以毫秒为单位）。</span><span class="sxs-lookup"><span data-stu-id="90e34-114">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="90e34-115">默认值是 120,000 毫秒（2 分钟）。</span><span class="sxs-lookup"><span data-stu-id="90e34-115">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="90e34-116">指定具有多个 Internet 协议（IP）地址的主机名的 DNS 解析是返回所有地址，还是只返回第一个地址。</span><span class="sxs-lookup"><span data-stu-id="90e34-116">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="90e34-117">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="90e34-117">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="90e34-118">指定应用到实例上的 SSL/TLS 会话的加密策略 <xref:System.Net.ServicePointManager> 。</span><span class="sxs-lookup"><span data-stu-id="90e34-118">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="90e34-119">可能的值等效于枚举的值 <xref:System.Net.Security.EncryptionPolicy> 。</span><span class="sxs-lookup"><span data-stu-id="90e34-119">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="90e34-120"><xref:System.Security.Authentication.CipherAlgorithmType.Null>加密策略设置为时，需要使用 `NoEncryption` 。</span><span class="sxs-lookup"><span data-stu-id="90e34-120">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="90e34-121">默认值为 `RequireEncryption`。</span><span class="sxs-lookup"><span data-stu-id="90e34-121">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="90e34-122">指定 POST 方法是否应该接收 `100-continue` 来自服务器的响应。</span><span class="sxs-lookup"><span data-stu-id="90e34-122">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="90e34-123">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="90e34-123">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="90e34-124">指定由服务点管理器控制的连接是否使用 Nagle 算法。</span><span class="sxs-lookup"><span data-stu-id="90e34-124">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="90e34-125">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="90e34-125">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90e34-126">子元素</span><span class="sxs-lookup"><span data-stu-id="90e34-126">Child Elements</span></span>  
 <span data-ttu-id="90e34-127">无。</span><span class="sxs-lookup"><span data-stu-id="90e34-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90e34-128">父元素</span><span class="sxs-lookup"><span data-stu-id="90e34-128">Parent Elements</span></span>  
  
|<span data-ttu-id="90e34-129">**元素**</span><span class="sxs-lookup"><span data-stu-id="90e34-129">**Element**</span></span>|<span data-ttu-id="90e34-130">**描述**</span><span class="sxs-lookup"><span data-stu-id="90e34-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="90e34-131">设置</span><span class="sxs-lookup"><span data-stu-id="90e34-131">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="90e34-132">配置 <xref:System.Net> 命名空间的基本网络选项。</span><span class="sxs-lookup"><span data-stu-id="90e34-132">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90e34-133">注解</span><span class="sxs-lookup"><span data-stu-id="90e34-133">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="90e34-134">配置文件</span><span class="sxs-lookup"><span data-stu-id="90e34-134">Configuration Files</span></span>  
 <span data-ttu-id="90e34-135">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="90e34-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e34-136">另请参阅</span><span class="sxs-lookup"><span data-stu-id="90e34-136">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="90e34-137">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="90e34-137">Network Settings Schema</span></span>](index.md)
