---
title: authenticationModules 的 <remove> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, authenticationModules
- <authenticationModules>, remove element
- <remove> element, authenticationModules
- authenticationModules, remove element
ms.assetid: abf79949-b05c-465a-b51c-bbeda9a74173
ms.openlocfilehash: 0829f57d8dca91c2d895085dceaeea422229537c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176196"
---
# <a name="remove-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="4e5b5-102">authenticationModules 的 \<remove> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="4e5b5-102">\<remove> Element for authenticationModules (Network Settings)</span></span>

<span data-ttu-id="4e5b5-103">从应用程序中移除身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="4e5b5-103">Removes an authentication module from the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="4e5b5-104">语法</span><span class="sxs-lookup"><span data-stu-id="4e5b5-104">Syntax</span></span>  
  
```xml  
<remove
   type="authentication module name"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e5b5-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4e5b5-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4e5b5-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4e5b5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e5b5-107">特性</span><span class="sxs-lookup"><span data-stu-id="4e5b5-107">Attributes</span></span>  
  
|<span data-ttu-id="4e5b5-108">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="4e5b5-108">**Attribute**</span></span>|<span data-ttu-id="4e5b5-109">**说明**</span><span class="sxs-lookup"><span data-stu-id="4e5b5-109">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="4e5b5-110">type</span><span class="sxs-lookup"><span data-stu-id="4e5b5-110">**type**</span></span>|<span data-ttu-id="4e5b5-111">要删除的身份验证模块的名称。</span><span class="sxs-lookup"><span data-stu-id="4e5b5-111">The name of the authentication module to remove.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e5b5-112">子元素</span><span class="sxs-lookup"><span data-stu-id="4e5b5-112">Child Elements</span></span>  

 <span data-ttu-id="4e5b5-113">无。</span><span class="sxs-lookup"><span data-stu-id="4e5b5-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e5b5-114">父元素</span><span class="sxs-lookup"><span data-stu-id="4e5b5-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4e5b5-115">**元素**</span><span class="sxs-lookup"><span data-stu-id="4e5b5-115">**Element**</span></span>|<span data-ttu-id="4e5b5-116">**说明**</span><span class="sxs-lookup"><span data-stu-id="4e5b5-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4e5b5-117">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="4e5b5-117">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="4e5b5-118">指定用于对网络请求进行身份验证的模块。</span><span class="sxs-lookup"><span data-stu-id="4e5b5-118">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e5b5-119">备注</span><span class="sxs-lookup"><span data-stu-id="4e5b5-119">Remarks</span></span>  

 <span data-ttu-id="4e5b5-120">`remove`元素删除之前在配置文件或配置层次结构的较高级别中定义的身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="4e5b5-120">The `remove` element removes authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="4e5b5-121">特性的值 `type` 应为有效的类名。</span><span class="sxs-lookup"><span data-stu-id="4e5b5-121">The value for the `type` attribute should be a valid class name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4e5b5-122">配置文件</span><span class="sxs-lookup"><span data-stu-id="4e5b5-122">Configuration Files</span></span>  

 <span data-ttu-id="4e5b5-123">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="4e5b5-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e5b5-124">示例</span><span class="sxs-lookup"><span data-stu-id="4e5b5-124">Example</span></span>  

 <span data-ttu-id="4e5b5-125">下面的示例将删除身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="4e5b5-125">The following example removes an authentication module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <remove type="System.Net.NtlmClient" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e5b5-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="4e5b5-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="4e5b5-127">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="4e5b5-127">Network Settings Schema</span></span>](index.md)
