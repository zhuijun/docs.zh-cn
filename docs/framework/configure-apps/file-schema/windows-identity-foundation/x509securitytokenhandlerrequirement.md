---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152445"
---
# \<x509SecurityTokenHandlerRequirement>
<span data-ttu-id="5d7ec-101">提供 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 类或派生类的可选配置。</span><span class="sxs-lookup"><span data-stu-id="5d7ec-101">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="5d7ec-102">语法</span><span class="sxs-lookup"><span data-stu-id="5d7ec-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d7ec-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="5d7ec-103">Attributes and Elements</span></span>  
 <span data-ttu-id="5d7ec-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5d7ec-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d7ec-105">特性</span><span class="sxs-lookup"><span data-stu-id="5d7ec-105">Attributes</span></span>  
  
|<span data-ttu-id="5d7ec-106">属性</span><span class="sxs-lookup"><span data-stu-id="5d7ec-106">Attribute</span></span>|<span data-ttu-id="5d7ec-107">说明</span><span class="sxs-lookup"><span data-stu-id="5d7ec-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5d7ec-108">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="5d7ec-108">certificateValidationMode</span></span>|<span data-ttu-id="5d7ec-109">一个 <xref:System.ServiceModel.Security.X509CertificateValidationMode> 值，该值指定要用于 x.509 证书的验证模式。</span><span class="sxs-lookup"><span data-stu-id="5d7ec-109">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="5d7ec-110">默认值为 "PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="5d7ec-110">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="5d7ec-111">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="5d7ec-111">mapToWindows</span></span>|<span data-ttu-id="5d7ec-112">指定令牌处理程序是否应使用传入 UPN 声明将验证令牌映射到 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="5d7ec-112">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="5d7ec-113">默认值为“false”。</span><span class="sxs-lookup"><span data-stu-id="5d7ec-113">The default is "false".</span></span>|  
|<span data-ttu-id="5d7ec-114">revocationMode</span><span class="sxs-lookup"><span data-stu-id="5d7ec-114">revocationMode</span></span>|<span data-ttu-id="5d7ec-115">一个 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 值，该值指定要用于 x.509 证书的吊销模式。</span><span class="sxs-lookup"><span data-stu-id="5d7ec-115">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="5d7ec-116">默认值为 "Online"。</span><span class="sxs-lookup"><span data-stu-id="5d7ec-116">The default value is "Online".</span></span>|  
|<span data-ttu-id="5d7ec-117">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="5d7ec-117">trustedStoreLocation</span></span>|<span data-ttu-id="5d7ec-118">一个 <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 值，该值指定 x.509 证书存储区。</span><span class="sxs-lookup"><span data-stu-id="5d7ec-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="5d7ec-119">默认值为 "LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="5d7ec-119">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="5d7ec-120">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="5d7ec-120">certificateValidator</span></span>|<span data-ttu-id="5d7ec-121">派生自的自定义类型 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 。</span><span class="sxs-lookup"><span data-stu-id="5d7ec-121">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="5d7ec-122">如果该 `certificateValidationMode` 属性为 "Custom"，则此类型的实例将用于颁发者证书验证。</span><span class="sxs-lookup"><span data-stu-id="5d7ec-122">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d7ec-123">子元素</span><span class="sxs-lookup"><span data-stu-id="5d7ec-123">Child Elements</span></span>  
 <span data-ttu-id="5d7ec-124">无</span><span class="sxs-lookup"><span data-stu-id="5d7ec-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d7ec-125">父元素</span><span class="sxs-lookup"><span data-stu-id="5d7ec-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5d7ec-126">元素</span><span class="sxs-lookup"><span data-stu-id="5d7ec-126">Element</span></span>|<span data-ttu-id="5d7ec-127">描述</span><span class="sxs-lookup"><span data-stu-id="5d7ec-127">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="5d7ec-128">将指定的安全令牌处理程序添加到令牌处理程序集合。</span><span class="sxs-lookup"><span data-stu-id="5d7ec-128">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5d7ec-129">示例</span><span class="sxs-lookup"><span data-stu-id="5d7ec-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
