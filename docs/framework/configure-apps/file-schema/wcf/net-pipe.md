---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: dd984b2ab89060451b1b2d02c324e803766908ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397714"
---
# \<net.pipe>
<span data-ttu-id="61298-102">指定命名管道激活服务的配置设置，命名管道激活服务将管理命名管道连接的生存期，并处理通过命名管道到达的激活请求。</span><span class="sxs-lookup"><span data-stu-id="61298-102">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**  
  
## <a name="syntax"></a><span data-ttu-id="61298-103">语法</span><span class="sxs-lookup"><span data-stu-id="61298-103">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.pipe maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              receiveTimeout="TimeSpan">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="61298-104">类型</span><span class="sxs-lookup"><span data-stu-id="61298-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61298-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="61298-105">Attributes and Elements</span></span>  
 <span data-ttu-id="61298-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="61298-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61298-107">特性</span><span class="sxs-lookup"><span data-stu-id="61298-107">Attributes</span></span>  
  
|<span data-ttu-id="61298-108">属性</span><span class="sxs-lookup"><span data-stu-id="61298-108">Attribute</span></span>|<span data-ttu-id="61298-109">说明</span><span class="sxs-lookup"><span data-stu-id="61298-109">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="61298-110">一个整数，指定共享服务侦听终结点上的最大未完成并发接受线程数。</span><span class="sxs-lookup"><span data-stu-id="61298-110">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="61298-111">默认值为 2。</span><span class="sxs-lookup"><span data-stu-id="61298-111">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="61298-112">一个整数，指定可等待调度的最大连接数。</span><span class="sxs-lookup"><span data-stu-id="61298-112">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="61298-113">默认值为 100。</span><span class="sxs-lookup"><span data-stu-id="61298-113">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="61298-114"><xref:System.TimeSpan>，它将为读取组帧数据并执行来自基础连接的连接调度指定超时值。</span><span class="sxs-lookup"><span data-stu-id="61298-114">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="61298-115">默认值为“00:00:10”</span><span class="sxs-lookup"><span data-stu-id="61298-115">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61298-116">子元素</span><span class="sxs-lookup"><span data-stu-id="61298-116">Child Elements</span></span>  
  
|<span data-ttu-id="61298-117">元素</span><span class="sxs-lookup"><span data-stu-id="61298-117">Element</span></span>|<span data-ttu-id="61298-118">描述</span><span class="sxs-lookup"><span data-stu-id="61298-118">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="61298-119">一个配置元素的集合，这些元素包含一个 `securityIdentifier` 属性，用于为承载 WCF 服务并被授予对共享服务的连接访问权限的进程指定用户帐户。</span><span class="sxs-lookup"><span data-stu-id="61298-119">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61298-120">父元素</span><span class="sxs-lookup"><span data-stu-id="61298-120">Parent Elements</span></span>  
  
|<span data-ttu-id="61298-121">元素</span><span class="sxs-lookup"><span data-stu-id="61298-121">Element</span></span>|<span data-ttu-id="61298-122">描述</span><span class="sxs-lookup"><span data-stu-id="61298-122">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="61298-123">包含侦听器进程 SMSvcHost.exe 的配置设置。</span><span class="sxs-lookup"><span data-stu-id="61298-123">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61298-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="61298-124">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
