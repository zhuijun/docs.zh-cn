---
title: <windowsAuthentication> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ded04f6e87fce2e12dac8f681ba2d4178f8fd204
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399115"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="c39a7-102">\<windowsAuthentication> 的 \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c39a7-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="c39a7-103">指定 Windows 服务凭据的设置。</span><span class="sxs-lookup"><span data-stu-id="c39a7-103">Specifies the settings of a Windows service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="c39a7-104">语法</span><span class="sxs-lookup"><span data-stu-id="c39a7-104">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c39a7-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c39a7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c39a7-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c39a7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c39a7-107">特性</span><span class="sxs-lookup"><span data-stu-id="c39a7-107">Attributes</span></span>  
  
|<span data-ttu-id="c39a7-108">属性</span><span class="sxs-lookup"><span data-stu-id="c39a7-108">Attribute</span></span>|<span data-ttu-id="c39a7-109">说明</span><span class="sxs-lookup"><span data-stu-id="c39a7-109">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="c39a7-110">一个可选的布尔值属性，指定系统是否将 Windows 组包含在安全上下文中。</span><span class="sxs-lookup"><span data-stu-id="c39a7-110">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="c39a7-111">默认为 `true`。</span><span class="sxs-lookup"><span data-stu-id="c39a7-111">The default is `true`.</span></span><br /><br /> <span data-ttu-id="c39a7-112">将此属性设置为 `true` 会影响性能，因为这会导致完全组扩展。</span><span class="sxs-lookup"><span data-stu-id="c39a7-112">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="c39a7-113">如果不需要建立用户所属组的列表，请将此属性设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="c39a7-113">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="c39a7-114">一个可选的布尔值属性，指定是否允许匿名的未经过身份验证的调用方。</span><span class="sxs-lookup"><span data-stu-id="c39a7-114">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="c39a7-115">默认为 `false`。</span><span class="sxs-lookup"><span data-stu-id="c39a7-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="c39a7-116">如果将绑定的 `clientCredentialType` 属性设置为 `Windows`，则系统不允许匿名的调用方。</span><span class="sxs-lookup"><span data-stu-id="c39a7-116">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="c39a7-117">这意味着，只有经过身份验证的域或工作组调用方才可以访问系统。</span><span class="sxs-lookup"><span data-stu-id="c39a7-117">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="c39a7-118">可以使用此属性重写此行为。</span><span class="sxs-lookup"><span data-stu-id="c39a7-118">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="c39a7-119">使用此设置应特别小心。</span><span class="sxs-lookup"><span data-stu-id="c39a7-119">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c39a7-120">子元素</span><span class="sxs-lookup"><span data-stu-id="c39a7-120">Child Elements</span></span>  
 <span data-ttu-id="c39a7-121">无。</span><span class="sxs-lookup"><span data-stu-id="c39a7-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c39a7-122">父元素</span><span class="sxs-lookup"><span data-stu-id="c39a7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c39a7-123">元素</span><span class="sxs-lookup"><span data-stu-id="c39a7-123">Element</span></span>|<span data-ttu-id="c39a7-124">描述</span><span class="sxs-lookup"><span data-stu-id="c39a7-124">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="c39a7-125">指定要用于对服务进行身份验证的凭据以及与客户端凭据验证相关的设置。</span><span class="sxs-lookup"><span data-stu-id="c39a7-125">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c39a7-126">注解</span><span class="sxs-lookup"><span data-stu-id="c39a7-126">Remarks</span></span>  
 <span data-ttu-id="c39a7-127">通过设置 `allowAnonymousLogons` 属性，使用此元素可指定是否允许匿名 Windows 用户访问。</span><span class="sxs-lookup"><span data-stu-id="c39a7-127">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="c39a7-128">此外，通过设置 `includeWindowsGroups` 属性还可以指定是否在 AuthorizationContext 中包含用户所属的组信息。</span><span class="sxs-lookup"><span data-stu-id="c39a7-128">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="c39a7-129">如果将它设置为 `true`（默认设置），服务就可以确定客户端所属的 Windows 组。</span><span class="sxs-lookup"><span data-stu-id="c39a7-129">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c39a7-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c39a7-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
