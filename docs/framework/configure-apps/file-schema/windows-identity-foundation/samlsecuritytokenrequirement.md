---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152627"
---
# \<samlSecurityTokenRequirement>
<span data-ttu-id="30270-101">为 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 类、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 类或其中任何一个类的派生类提供配置。</span><span class="sxs-lookup"><span data-stu-id="30270-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="30270-102">由类表示 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 。</span><span class="sxs-lookup"><span data-stu-id="30270-102">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="30270-103">语法</span><span class="sxs-lookup"><span data-stu-id="30270-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30270-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="30270-104">Attributes and Elements</span></span>  
 <span data-ttu-id="30270-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="30270-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30270-106">特性</span><span class="sxs-lookup"><span data-stu-id="30270-106">Attributes</span></span>  
  
|<span data-ttu-id="30270-107">属性</span><span class="sxs-lookup"><span data-stu-id="30270-107">Attribute</span></span>|<span data-ttu-id="30270-108">说明</span><span class="sxs-lookup"><span data-stu-id="30270-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30270-109">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="30270-109">mapToWindows</span></span>|<span data-ttu-id="30270-110">指定令牌处理程序是否应使用传入 UPN 声明将验证令牌映射到 Windows 帐户。</span><span class="sxs-lookup"><span data-stu-id="30270-110">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="30270-111">默认值为“false”。</span><span class="sxs-lookup"><span data-stu-id="30270-111">The default is "false".</span></span>|  
|<span data-ttu-id="30270-112">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="30270-112">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="30270-113">一个 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 值，该值指定要用于 x.509 证书的吊销模式。</span><span class="sxs-lookup"><span data-stu-id="30270-113">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="30270-114">默认值为 "Online"。</span><span class="sxs-lookup"><span data-stu-id="30270-114">The default value is "Online".</span></span>|  
|<span data-ttu-id="30270-115">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="30270-115">issuerCertificateValidationMode</span></span>|<span data-ttu-id="30270-116">一个 <xref:System.ServiceModel.Security.X509CertificateValidationMode> 值，该值指定要用于 x.509 证书的验证模式。</span><span class="sxs-lookup"><span data-stu-id="30270-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="30270-117">默认值为 "PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="30270-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="30270-118">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="30270-118">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="30270-119">一个 <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 值，该值指定 x.509 证书存储区。</span><span class="sxs-lookup"><span data-stu-id="30270-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="30270-120">默认值为 "LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="30270-120">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="30270-121">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="30270-121">issuerCertificateValidator</span></span>|<span data-ttu-id="30270-122">派生自的自定义类型 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 。</span><span class="sxs-lookup"><span data-stu-id="30270-122">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="30270-123">如果该 `issuerCertificateValidationMode` 属性为 "Custom"，则此类型的实例将用于颁发者证书验证。</span><span class="sxs-lookup"><span data-stu-id="30270-123">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30270-124">子元素</span><span class="sxs-lookup"><span data-stu-id="30270-124">Child Elements</span></span>  
  
|<span data-ttu-id="30270-125">元素</span><span class="sxs-lookup"><span data-stu-id="30270-125">Element</span></span>|<span data-ttu-id="30270-126">描述</span><span class="sxs-lookup"><span data-stu-id="30270-126">Description</span></span>|  
|-------------|-----------------|  
|[\<nameClaimType>](nameclaimtype.md)|<span data-ttu-id="30270-127">设置指定属性的声明类型 <xref:System.Security.Principal.IIdentity.Name%2A> 。</span><span class="sxs-lookup"><span data-stu-id="30270-127">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[\<roleClaimType>](roleclaimtype.md)|<span data-ttu-id="30270-128">指定声明类型，该声明类型定义 <xref:System.Security.Claims.ClaimsIdentity> 由标记处理程序的方法返回的对象集合中的角色类型声明 <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> 。</span><span class="sxs-lookup"><span data-stu-id="30270-128">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="30270-129">父元素</span><span class="sxs-lookup"><span data-stu-id="30270-129">Parent Elements</span></span>  
  
|<span data-ttu-id="30270-130">元素</span><span class="sxs-lookup"><span data-stu-id="30270-130">Element</span></span>|<span data-ttu-id="30270-131">描述</span><span class="sxs-lookup"><span data-stu-id="30270-131">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="30270-132">将指定的安全令牌处理程序添加到令牌处理程序集合。</span><span class="sxs-lookup"><span data-stu-id="30270-132">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30270-133">注解</span><span class="sxs-lookup"><span data-stu-id="30270-133">Remarks</span></span>  
 <span data-ttu-id="30270-134">`<samlSecurityTokenRequirement>`元素由 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 对象模型中的类表示，用于 `SamlSecurityTokenRequirement` 在或上配置属性 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 。</span><span class="sxs-lookup"><span data-stu-id="30270-134">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30270-135">示例</span><span class="sxs-lookup"><span data-stu-id="30270-135">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```
