---
title: authenticationModules 的 <add> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/add
helpviewer_keywords:
- authenticationModules, add element
- add element, authenticationModules
- <authenticationModules>, add element
- <add> element, authenticationModules
ms.assetid: 333c5fb0-a2ab-4db8-8531-a7fe37bb9b5b
ms.openlocfilehash: 4181a045079bdb455a63ebda722dd6b0daf33c4d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155110"
---
# <a name="add-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="6e14c-102">authenticationModules 的 \<add> 元素（网络设置）</span><span class="sxs-lookup"><span data-stu-id="6e14c-102">\<add> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="6e14c-103">向应用程序添加身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="6e14c-103">Adds an authentication module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="6e14c-104">语法</span><span class="sxs-lookup"><span data-stu-id="6e14c-104">Syntax</span></span>  
  
```xml  
<add
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e14c-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6e14c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6e14c-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6e14c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e14c-107">特性</span><span class="sxs-lookup"><span data-stu-id="6e14c-107">Attributes</span></span>  
  
|<span data-ttu-id="6e14c-108">**特性**</span><span class="sxs-lookup"><span data-stu-id="6e14c-108">**Attribute**</span></span>|<span data-ttu-id="6e14c-109">**描述**</span><span class="sxs-lookup"><span data-stu-id="6e14c-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="6e14c-110">完全限定的类型名称（由属性指示 <xref:System.Type.FullName%2A> ）和程序集名称（由 <xref:System.Reflection.Assembly.FullName%2A> 属性指示），用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="6e14c-110">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e14c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="6e14c-111">Child Elements</span></span>  
 <span data-ttu-id="6e14c-112">无。</span><span class="sxs-lookup"><span data-stu-id="6e14c-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e14c-113">父元素</span><span class="sxs-lookup"><span data-stu-id="6e14c-113">Parent Elements</span></span>  
  
|<span data-ttu-id="6e14c-114">**元素**</span><span class="sxs-lookup"><span data-stu-id="6e14c-114">**Element**</span></span>|<span data-ttu-id="6e14c-115">**描述**</span><span class="sxs-lookup"><span data-stu-id="6e14c-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6e14c-116">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="6e14c-116">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="6e14c-117">指定用于对网络请求进行身份验证的模块。</span><span class="sxs-lookup"><span data-stu-id="6e14c-117">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e14c-118">注解</span><span class="sxs-lookup"><span data-stu-id="6e14c-118">Remarks</span></span>  
 <span data-ttu-id="6e14c-119">`add` 元素会在已注册的身份验证模块列表末尾添加一个身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="6e14c-119">The `add` element adds an authentication module to the end of the list of registered authentication modules.</span></span> <span data-ttu-id="6e14c-120">身份验证模块按照它们添加到列表中的顺序进行调用。</span><span class="sxs-lookup"><span data-stu-id="6e14c-120">Authentication modules are called in the order in which they were added to the list.</span></span>  
  
 <span data-ttu-id="6e14c-121">特性的值 `type` 应为有效的类型名称和相应的程序集名称，用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="6e14c-121">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6e14c-122">配置文件</span><span class="sxs-lookup"><span data-stu-id="6e14c-122">Configuration Files</span></span>  
 <span data-ttu-id="6e14c-123">此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。</span><span class="sxs-lookup"><span data-stu-id="6e14c-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e14c-124">示例</span><span class="sxs-lookup"><span data-stu-id="6e14c-124">Example</span></span>  
 <span data-ttu-id="6e14c-125">下面的示例启用了默认的身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="6e14c-125">The following example enables the default authentication modules.</span></span> <span data-ttu-id="6e14c-126">应将版本和 PublicKeyToken 的值替换为指定模块的正确值。</span><span class="sxs-lookup"><span data-stu-id="6e14c-126">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
        <authenticationModules>  
            <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NegotiateClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.KerberosClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.NtlmClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
            <add type="System.Net.BasicClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e14c-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6e14c-127">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="6e14c-128">网络设置架构</span><span class="sxs-lookup"><span data-stu-id="6e14c-128">Network Settings Schema</span></span>](index.md)
