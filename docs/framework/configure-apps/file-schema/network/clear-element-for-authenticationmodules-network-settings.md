---
title: authenticationModules 的 <clear> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
ms.openlocfilehash: e3abd1b4c76ebda885703ccf961d58657b582f19
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087502"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="0fc75-102">authenticationModules 的 \<clear> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="0fc75-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="0fc75-103">清除应用程序中的所有身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="0fc75-103">Clears all authentication modules from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="0fc75-104">语法</span><span class="sxs-lookup"><span data-stu-id="0fc75-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fc75-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0fc75-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0fc75-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0fc75-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fc75-107">特性</span><span class="sxs-lookup"><span data-stu-id="0fc75-107">Attributes</span></span>  
 <span data-ttu-id="0fc75-108">无。</span><span class="sxs-lookup"><span data-stu-id="0fc75-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0fc75-109">子元素</span><span class="sxs-lookup"><span data-stu-id="0fc75-109">Child Elements</span></span>  
 <span data-ttu-id="0fc75-110">无。</span><span class="sxs-lookup"><span data-stu-id="0fc75-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0fc75-111">父元素</span><span class="sxs-lookup"><span data-stu-id="0fc75-111">Parent Elements</span></span>  
  
|<span data-ttu-id="0fc75-112">**元素**</span><span class="sxs-lookup"><span data-stu-id="0fc75-112">**Element**</span></span>|<span data-ttu-id="0fc75-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="0fc75-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0fc75-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="0fc75-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="0fc75-115">指定用于对网络请求进行身份验证的模块。</span><span class="sxs-lookup"><span data-stu-id="0fc75-115">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fc75-116">注解</span><span class="sxs-lookup"><span data-stu-id="0fc75-116">Remarks</span></span>  
 <span data-ttu-id="0fc75-117">`clear`元素删除之前在配置文件或配置层次结构的较高级别中定义的所有身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="0fc75-117">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0fc75-118">配置文件</span><span class="sxs-lookup"><span data-stu-id="0fc75-118">Configuration Files</span></span>  
 <span data-ttu-id="0fc75-119">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="0fc75-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fc75-120">示例</span><span class="sxs-lookup"><span data-stu-id="0fc75-120">Example</span></span>  
 <span data-ttu-id="0fc75-121">下面的示例删除所有配置的身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="0fc75-121">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fc75-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0fc75-122">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="0fc75-123">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="0fc75-123">Network Settings Schema</span></span>](index.md)
