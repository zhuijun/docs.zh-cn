---
title: connectionManagement 的 <remove> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
ms.openlocfilehash: 46157482d7ceb42b352c68dc9b0eab4f7688bc5c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176170"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="5452c-102">connectionManagement 的 \<remove> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="5452c-102">\<remove> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="5452c-103">从连接管理列表中删除 IP 地址或 DNS 名称。</span><span class="sxs-lookup"><span data-stu-id="5452c-103">Removes an IP address or DNS name from the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="5452c-104">语法</span><span class="sxs-lookup"><span data-stu-id="5452c-104">Syntax</span></span>  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5452c-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="5452c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5452c-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5452c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5452c-107">特性</span><span class="sxs-lookup"><span data-stu-id="5452c-107">Attributes</span></span>  
  
|<span data-ttu-id="5452c-108">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="5452c-108">**Attribute**</span></span>|<span data-ttu-id="5452c-109">**说明**</span><span class="sxs-lookup"><span data-stu-id="5452c-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="5452c-110">IP 地址或 DNS 名称。</span><span class="sxs-lookup"><span data-stu-id="5452c-110">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5452c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="5452c-111">Child Elements</span></span>  

 <span data-ttu-id="5452c-112">无。</span><span class="sxs-lookup"><span data-stu-id="5452c-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5452c-113">父元素</span><span class="sxs-lookup"><span data-stu-id="5452c-113">Parent Elements</span></span>  
  
|<span data-ttu-id="5452c-114">**元素**</span><span class="sxs-lookup"><span data-stu-id="5452c-114">**Element**</span></span>|<span data-ttu-id="5452c-115">**说明**</span><span class="sxs-lookup"><span data-stu-id="5452c-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5452c-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="5452c-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="5452c-117">指定到网络主机的最大连接数。</span><span class="sxs-lookup"><span data-stu-id="5452c-117">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5452c-118">备注</span><span class="sxs-lookup"><span data-stu-id="5452c-118">Remarks</span></span>  

 <span data-ttu-id="5452c-119">`remove`元素删除指定服务器的连接管理列表项。</span><span class="sxs-lookup"><span data-stu-id="5452c-119">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="5452c-120">该属性的值 `address` 应为有效的 IP 地址或主机名。</span><span class="sxs-lookup"><span data-stu-id="5452c-120">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5452c-121">配置文件</span><span class="sxs-lookup"><span data-stu-id="5452c-121">Configuration Files</span></span>  

 <span data-ttu-id="5452c-122">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="5452c-122">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5452c-123">示例</span><span class="sxs-lookup"><span data-stu-id="5452c-123">Example</span></span>  

 <span data-ttu-id="5452c-124">下面的示例删除服务器的任何连接管理列表项 `www.adventure-works.com` ，然后将应用程序配置为使用四个到服务器的连接 `www.contoso.com` ，以及两个与其他服务器的连接。</span><span class="sxs-lookup"><span data-stu-id="5452c-124">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address="http://www.adventure-works.com" />  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5452c-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="5452c-125">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="5452c-126">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="5452c-126">Network Settings Schema</span></span>](index.md)
