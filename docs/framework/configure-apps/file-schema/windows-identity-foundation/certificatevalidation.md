---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 583fef7eb364c39890b3f9304770b383c1ea6d2a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183502"
---
# \<certificateValidation>

<span data-ttu-id="0c8e8-101">控制标记处理程序用于验证证书的设置。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-101">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="0c8e8-102">如果为特定处理程序配置了其自己的验证程序，则会重写这些设置。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-102">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**  
  
## <a name="syntax"></a><span data-ttu-id="0c8e8-103">语法</span><span class="sxs-lookup"><span data-stu-id="0c8e8-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c8e8-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0c8e8-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0c8e8-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c8e8-106">特性</span><span class="sxs-lookup"><span data-stu-id="0c8e8-106">Attributes</span></span>  
  
|<span data-ttu-id="0c8e8-107">属性</span><span class="sxs-lookup"><span data-stu-id="0c8e8-107">Attribute</span></span>|<span data-ttu-id="0c8e8-108">描述</span><span class="sxs-lookup"><span data-stu-id="0c8e8-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c8e8-109">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="0c8e8-109">certificateValidationMode</span></span>|<span data-ttu-id="0c8e8-110">一个 <xref:System.ServiceModel.Security.X509CertificateValidationMode> 值，该值指定要用于 x.509 证书的验证模式。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-110">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="0c8e8-111">默认值为 "PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-111">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="0c8e8-112">若要指定自定义验证程序，请将此特性设置为 "Custom"，并使用元素指定验证程序 [\<certificateValidator>](certificatevalidator.md) 。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-112">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="0c8e8-113">可选。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-113">Optional.</span></span>|  
|<span data-ttu-id="0c8e8-114">revocationMode</span><span class="sxs-lookup"><span data-stu-id="0c8e8-114">revocationMode</span></span>|<span data-ttu-id="0c8e8-115">一个 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 值，该值指定要用于 x.509 证书的吊销模式。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-115">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="0c8e8-116">默认值为 "Online"。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-116">The default value is "Online".</span></span> <span data-ttu-id="0c8e8-117">可选。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-117">Optional.</span></span>|  
|<span data-ttu-id="0c8e8-118">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="0c8e8-118">trustedStoreLocation</span></span>|<span data-ttu-id="0c8e8-119">一个 <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 值，该值指定 x.509 证书存储区。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="0c8e8-120">默认值为 "LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="0c8e8-121">可选。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-121">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c8e8-122">子元素</span><span class="sxs-lookup"><span data-stu-id="0c8e8-122">Child Elements</span></span>  
  
|<span data-ttu-id="0c8e8-123">元素</span><span class="sxs-lookup"><span data-stu-id="0c8e8-123">Element</span></span>|<span data-ttu-id="0c8e8-124">描述</span><span class="sxs-lookup"><span data-stu-id="0c8e8-124">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidator>](certificatevalidator.md)|<span data-ttu-id="0c8e8-125">指定证书验证的自定义类型。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-125">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="0c8e8-126">仅当 `certificateValidationMode` 元素的属性 [\<certificateValidation>](certificatevalidation.md) 设置为 "Custom" 时才使用此类型。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-126">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c8e8-127">父元素</span><span class="sxs-lookup"><span data-stu-id="0c8e8-127">Parent Elements</span></span>  
  
|<span data-ttu-id="0c8e8-128">元素</span><span class="sxs-lookup"><span data-stu-id="0c8e8-128">Element</span></span>|<span data-ttu-id="0c8e8-129">描述</span><span class="sxs-lookup"><span data-stu-id="0c8e8-129">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="0c8e8-130">指定服务级别标识设置。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-130">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="0c8e8-131">为安全标记处理程序的集合提供配置。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-131">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c8e8-132">备注</span><span class="sxs-lookup"><span data-stu-id="0c8e8-132">Remarks</span></span>  

 <span data-ttu-id="0c8e8-133">可以在元素 `<certificateValidation>` 下的服务级别指定元素， `<identityConfiguration>` 或在元素下的安全令牌处理程序集合级别指定元素 `<securityTokenHandlerConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-133">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="0c8e8-134">标记处理程序集合上的设置将重写服务上指定的设置。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-134">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="0c8e8-135">某些标记处理程序允许您在配置中指定证书验证设置。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-135">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="0c8e8-136">各个标记处理程序上的设置将覆盖在服务级别和安全令牌处理程序集合上指定的设置。</span><span class="sxs-lookup"><span data-stu-id="0c8e8-136">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c8e8-137">示例</span><span class="sxs-lookup"><span data-stu-id="0c8e8-137">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
