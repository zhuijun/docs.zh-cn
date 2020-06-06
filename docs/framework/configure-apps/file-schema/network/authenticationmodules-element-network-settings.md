---
title: <authenticationModules> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: b502cc4a0958f074018d4b0ce6b3fb118b811c2f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154967"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="5099b-102">\<authenticationModules> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="5099b-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="5099b-103">指定用于对网络请求进行身份验证的模块。</span><span class="sxs-lookup"><span data-stu-id="5099b-103">Specifies modules used to authenticate network requests.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**

## <a name="syntax"></a><span data-ttu-id="5099b-104">语法</span><span class="sxs-lookup"><span data-stu-id="5099b-104">Syntax</span></span>  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5099b-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="5099b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5099b-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5099b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5099b-107">特性</span><span class="sxs-lookup"><span data-stu-id="5099b-107">Attributes</span></span>  
 <span data-ttu-id="5099b-108">无。</span><span class="sxs-lookup"><span data-stu-id="5099b-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5099b-109">子元素</span><span class="sxs-lookup"><span data-stu-id="5099b-109">Child Elements</span></span>  
  
|<span data-ttu-id="5099b-110">**元素**</span><span class="sxs-lookup"><span data-stu-id="5099b-110">**Element**</span></span>|<span data-ttu-id="5099b-111">**描述**</span><span class="sxs-lookup"><span data-stu-id="5099b-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5099b-112">add</span><span class="sxs-lookup"><span data-stu-id="5099b-112">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="5099b-113">向应用程序添加身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="5099b-113">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="5099b-114">清除</span><span class="sxs-lookup"><span data-stu-id="5099b-114">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="5099b-115">清除应用程序中的所有身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="5099b-115">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="5099b-116">删除</span><span class="sxs-lookup"><span data-stu-id="5099b-116">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="5099b-117">从应用程序中移除身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="5099b-117">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5099b-118">父元素</span><span class="sxs-lookup"><span data-stu-id="5099b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5099b-119">**元素**</span><span class="sxs-lookup"><span data-stu-id="5099b-119">**Element**</span></span>|<span data-ttu-id="5099b-120">**描述**</span><span class="sxs-lookup"><span data-stu-id="5099b-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5099b-121">system.net</span><span class="sxs-lookup"><span data-stu-id="5099b-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="5099b-122">包含指定 .NET Framework 如何连接到网络的设置。</span><span class="sxs-lookup"><span data-stu-id="5099b-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5099b-123">注解</span><span class="sxs-lookup"><span data-stu-id="5099b-123">Remarks</span></span>  
 <span data-ttu-id="5099b-124">`authenticationModule`元素指定对服务器执行身份验证过程的身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="5099b-124">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="5099b-125">身份验证模块必须实现 <xref:System.Net.IAuthenticationModule> 接口。</span><span class="sxs-lookup"><span data-stu-id="5099b-125">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5099b-126">配置文件</span><span class="sxs-lookup"><span data-stu-id="5099b-126">Configuration Files</span></span>  
 <span data-ttu-id="5099b-127">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="5099b-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5099b-128">示例</span><span class="sxs-lookup"><span data-stu-id="5099b-128">Example</span></span>  
 <span data-ttu-id="5099b-129">下面的示例启用了身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="5099b-129">The following example enables an authentication module.</span></span> <span data-ttu-id="5099b-130">应将版本和 PublicKeyToken 的值替换为指定模块的正确值。</span><span class="sxs-lookup"><span data-stu-id="5099b-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5099b-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5099b-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="5099b-132">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="5099b-132">Network Settings Schema</span></span>](index.md)
