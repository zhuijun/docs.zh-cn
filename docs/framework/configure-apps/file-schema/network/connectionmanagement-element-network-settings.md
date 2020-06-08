---
title: <connectionManagement> 元素（网络设置）
description: <connectionManagement>网络设置元素指定与 .NET Framework 中的网络主机的最大连接数。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 4ceec06fb0e21bfae67038efe0ce758d3d5b708f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504610"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="d8136-103">\<connectionManagement> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="d8136-103">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="d8136-104">指定到网络主机的最大连接数。</span><span class="sxs-lookup"><span data-stu-id="d8136-104">Specifies the maximum number of connections to a network host.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a><span data-ttu-id="d8136-105">语法</span><span class="sxs-lookup"><span data-stu-id="d8136-105">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8136-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="d8136-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d8136-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d8136-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8136-108">特性</span><span class="sxs-lookup"><span data-stu-id="d8136-108">Attributes</span></span>  
 <span data-ttu-id="d8136-109">无。</span><span class="sxs-lookup"><span data-stu-id="d8136-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d8136-110">子元素</span><span class="sxs-lookup"><span data-stu-id="d8136-110">Child Elements</span></span>  
  
|<span data-ttu-id="d8136-111">**元素**</span><span class="sxs-lookup"><span data-stu-id="d8136-111">**Element**</span></span>|<span data-ttu-id="d8136-112">**说明**</span><span class="sxs-lookup"><span data-stu-id="d8136-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d8136-113">add</span><span class="sxs-lookup"><span data-stu-id="d8136-113">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="d8136-114">将 IP 地址或 DNS 名称添加到连接管理列表。</span><span class="sxs-lookup"><span data-stu-id="d8136-114">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="d8136-115">清除</span><span class="sxs-lookup"><span data-stu-id="d8136-115">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="d8136-116">清除连接管理列表。</span><span class="sxs-lookup"><span data-stu-id="d8136-116">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="d8136-117">删除</span><span class="sxs-lookup"><span data-stu-id="d8136-117">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="d8136-118">从连接管理列表中删除 IP 地址或 DNS 名称。</span><span class="sxs-lookup"><span data-stu-id="d8136-118">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8136-119">父元素</span><span class="sxs-lookup"><span data-stu-id="d8136-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d8136-120">**元素**</span><span class="sxs-lookup"><span data-stu-id="d8136-120">**Element**</span></span>|<span data-ttu-id="d8136-121">**说明**</span><span class="sxs-lookup"><span data-stu-id="d8136-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d8136-122">system.net</span><span class="sxs-lookup"><span data-stu-id="d8136-122">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="d8136-123">包含指定 .NET Framework 如何连接到网络的设置。</span><span class="sxs-lookup"><span data-stu-id="d8136-123">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8136-124">注解</span><span class="sxs-lookup"><span data-stu-id="d8136-124">Remarks</span></span>  
 <span data-ttu-id="d8136-125">`connectionManagement`元素定义与服务器或服务器组的最大连接数。</span><span class="sxs-lookup"><span data-stu-id="d8136-125">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d8136-126">配置文件</span><span class="sxs-lookup"><span data-stu-id="d8136-126">Configuration Files</span></span>  
 <span data-ttu-id="d8136-127">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="d8136-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8136-128">示例</span><span class="sxs-lookup"><span data-stu-id="d8136-128">Example</span></span>  
 <span data-ttu-id="d8136-129">下面的示例将应用程序配置为使用四个到服务器的连接 `www.contoso.com` ，以及两个与其他服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="d8136-129">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8136-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d8136-130">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="d8136-131">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="d8136-131">Network Settings Schema</span></span>](index.md)
