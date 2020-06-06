---
title: <connectionManagement> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 9f1e382bbbaad2cb95e2c33bbbdfb4c505378c9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154889"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="862d5-102">\<connectionManagement> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="862d5-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="862d5-103">指定到网络主机的最大连接数。</span><span class="sxs-lookup"><span data-stu-id="862d5-103">Specifies the maximum number of connections to a network host.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a><span data-ttu-id="862d5-104">语法</span><span class="sxs-lookup"><span data-stu-id="862d5-104">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="862d5-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="862d5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="862d5-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="862d5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="862d5-107">特性</span><span class="sxs-lookup"><span data-stu-id="862d5-107">Attributes</span></span>  
 <span data-ttu-id="862d5-108">无。</span><span class="sxs-lookup"><span data-stu-id="862d5-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="862d5-109">子元素</span><span class="sxs-lookup"><span data-stu-id="862d5-109">Child Elements</span></span>  
  
|<span data-ttu-id="862d5-110">**元素**</span><span class="sxs-lookup"><span data-stu-id="862d5-110">**Element**</span></span>|<span data-ttu-id="862d5-111">**描述**</span><span class="sxs-lookup"><span data-stu-id="862d5-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="862d5-112">add</span><span class="sxs-lookup"><span data-stu-id="862d5-112">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="862d5-113">将 IP 地址或 DNS 名称添加到连接管理列表。</span><span class="sxs-lookup"><span data-stu-id="862d5-113">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="862d5-114">清除</span><span class="sxs-lookup"><span data-stu-id="862d5-114">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="862d5-115">清除连接管理列表。</span><span class="sxs-lookup"><span data-stu-id="862d5-115">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="862d5-116">删除</span><span class="sxs-lookup"><span data-stu-id="862d5-116">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="862d5-117">从连接管理列表中删除 IP 地址或 DNS 名称。</span><span class="sxs-lookup"><span data-stu-id="862d5-117">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="862d5-118">父元素</span><span class="sxs-lookup"><span data-stu-id="862d5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="862d5-119">**元素**</span><span class="sxs-lookup"><span data-stu-id="862d5-119">**Element**</span></span>|<span data-ttu-id="862d5-120">**描述**</span><span class="sxs-lookup"><span data-stu-id="862d5-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="862d5-121">system.net</span><span class="sxs-lookup"><span data-stu-id="862d5-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="862d5-122">包含指定 .NET Framework 如何连接到网络的设置。</span><span class="sxs-lookup"><span data-stu-id="862d5-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="862d5-123">注解</span><span class="sxs-lookup"><span data-stu-id="862d5-123">Remarks</span></span>  
 <span data-ttu-id="862d5-124">`connectionManagement`元素定义与服务器或服务器组的最大连接数。</span><span class="sxs-lookup"><span data-stu-id="862d5-124">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="862d5-125">配置文件</span><span class="sxs-lookup"><span data-stu-id="862d5-125">Configuration Files</span></span>  
 <span data-ttu-id="862d5-126">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="862d5-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="862d5-127">示例</span><span class="sxs-lookup"><span data-stu-id="862d5-127">Example</span></span>  
 <span data-ttu-id="862d5-128">下面的示例将应用程序配置为使用四个到服务器的连接 `www.contoso.com` ，以及两个与其他服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="862d5-128">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="862d5-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="862d5-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="862d5-130">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="862d5-130">Network Settings Schema</span></span>](index.md)
