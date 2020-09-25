---
title: connectionManagement 的 <clear> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, connectionManagement
- connectionManagement, clear element
- clear element, connectionManagement
- <connectionManagement>, clear element
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
ms.openlocfilehash: 446bec116118ee8b604ef3664a6eb0452e6d5a38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184100"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="141fc-102">connectionManagement 的 \<clear> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="141fc-102">\<clear> Element for connectionManagement (Network Settings)</span></span>

<span data-ttu-id="141fc-103">清除连接管理列表。</span><span class="sxs-lookup"><span data-stu-id="141fc-103">Clears the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="141fc-104">语法</span><span class="sxs-lookup"><span data-stu-id="141fc-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="141fc-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="141fc-105">Attributes and Elements</span></span>  

 <span data-ttu-id="141fc-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="141fc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="141fc-107">特性</span><span class="sxs-lookup"><span data-stu-id="141fc-107">Attributes</span></span>  

 <span data-ttu-id="141fc-108">无。</span><span class="sxs-lookup"><span data-stu-id="141fc-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="141fc-109">子元素</span><span class="sxs-lookup"><span data-stu-id="141fc-109">Child Elements</span></span>  

 <span data-ttu-id="141fc-110">无。</span><span class="sxs-lookup"><span data-stu-id="141fc-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="141fc-111">父元素</span><span class="sxs-lookup"><span data-stu-id="141fc-111">Parent Elements</span></span>  
  
|<span data-ttu-id="141fc-112">**元素**</span><span class="sxs-lookup"><span data-stu-id="141fc-112">**Element**</span></span>|<span data-ttu-id="141fc-113">**说明**</span><span class="sxs-lookup"><span data-stu-id="141fc-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="141fc-114">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="141fc-114">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="141fc-115">指定到网络主机的最大连接数。</span><span class="sxs-lookup"><span data-stu-id="141fc-115">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="141fc-116">备注</span><span class="sxs-lookup"><span data-stu-id="141fc-116">Remarks</span></span>  

 <span data-ttu-id="141fc-117">`clear`元素清除连接管理列表中的所有条目。</span><span class="sxs-lookup"><span data-stu-id="141fc-117">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="141fc-118">配置文件</span><span class="sxs-lookup"><span data-stu-id="141fc-118">Configuration Files</span></span>  

 <span data-ttu-id="141fc-119">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="141fc-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="141fc-120">示例</span><span class="sxs-lookup"><span data-stu-id="141fc-120">Example</span></span>  

 <span data-ttu-id="141fc-121">下面的示例将清除 "连接管理" 列表，然后为服务器 `www.contoso.com` 和所有其他网络主机添加新的连接管理条目。</span><span class="sxs-lookup"><span data-stu-id="141fc-121">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <clear/>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="141fc-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="141fc-122">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="141fc-123">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="141fc-123">Network Settings Schema</span></span>](index.md)
