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
ms.openlocfilehash: a76df48a9de084e1121a5e96b22edf7aa3acba23
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088487"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="8c582-102">connectionManagement 的 \<clear> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="8c582-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="8c582-103">清除连接管理列表。</span><span class="sxs-lookup"><span data-stu-id="8c582-103">Clears the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="8c582-104">语法</span><span class="sxs-lookup"><span data-stu-id="8c582-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c582-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="8c582-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8c582-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8c582-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c582-107">特性</span><span class="sxs-lookup"><span data-stu-id="8c582-107">Attributes</span></span>  
 <span data-ttu-id="8c582-108">无。</span><span class="sxs-lookup"><span data-stu-id="8c582-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8c582-109">子元素</span><span class="sxs-lookup"><span data-stu-id="8c582-109">Child Elements</span></span>  
 <span data-ttu-id="8c582-110">无。</span><span class="sxs-lookup"><span data-stu-id="8c582-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c582-111">父元素</span><span class="sxs-lookup"><span data-stu-id="8c582-111">Parent Elements</span></span>  
  
|<span data-ttu-id="8c582-112">**元素**</span><span class="sxs-lookup"><span data-stu-id="8c582-112">**Element**</span></span>|<span data-ttu-id="8c582-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="8c582-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8c582-114">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="8c582-114">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="8c582-115">指定到网络主机的最大连接数。</span><span class="sxs-lookup"><span data-stu-id="8c582-115">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c582-116">注解</span><span class="sxs-lookup"><span data-stu-id="8c582-116">Remarks</span></span>  
 <span data-ttu-id="8c582-117">`clear`元素清除连接管理列表中的所有条目。</span><span class="sxs-lookup"><span data-stu-id="8c582-117">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8c582-118">配置文件</span><span class="sxs-lookup"><span data-stu-id="8c582-118">Configuration Files</span></span>  
 <span data-ttu-id="8c582-119">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="8c582-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c582-120">示例</span><span class="sxs-lookup"><span data-stu-id="8c582-120">Example</span></span>  
 <span data-ttu-id="8c582-121">下面的示例将清除 "连接管理" 列表，然后为服务器 `www.contoso.com` 和所有其他网络主机添加新的连接管理条目。</span><span class="sxs-lookup"><span data-stu-id="8c582-121">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8c582-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c582-122">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="8c582-123">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="8c582-123">Network Settings Schema</span></span>](index.md)
