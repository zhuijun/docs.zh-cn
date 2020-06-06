---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 50fc7194823fb0c5c426fb54ffd50b17c3714ed9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251761"
---
# \<trustedIssuers>
<span data-ttu-id="02df2-101">配置基于配置的颁发者名称注册表（）使用的受信任颁发者证书的列表 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 。</span><span class="sxs-lookup"><span data-stu-id="02df2-101">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**  
  
## <a name="syntax"></a><span data-ttu-id="02df2-102">语法</span><span class="sxs-lookup"><span data-stu-id="02df2-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02df2-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="02df2-103">Attributes and Elements</span></span>  
 <span data-ttu-id="02df2-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="02df2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02df2-105">特性</span><span class="sxs-lookup"><span data-stu-id="02df2-105">Attributes</span></span>  
 <span data-ttu-id="02df2-106">无</span><span class="sxs-lookup"><span data-stu-id="02df2-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="02df2-107">子元素</span><span class="sxs-lookup"><span data-stu-id="02df2-107">Child Elements</span></span>  
  
|<span data-ttu-id="02df2-108">元素</span><span class="sxs-lookup"><span data-stu-id="02df2-108">Element</span></span>|<span data-ttu-id="02df2-109">说明</span><span class="sxs-lookup"><span data-stu-id="02df2-109">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="02df2-110">将证书添加到受信任的颁发者的集合中。</span><span class="sxs-lookup"><span data-stu-id="02df2-110">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="02df2-111">证书是用属性指定的 `thumbprint` 。</span><span class="sxs-lookup"><span data-stu-id="02df2-111">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="02df2-112">此属性是必需的，并且应该包含证书指纹的 ASN. 1 编码形式。</span><span class="sxs-lookup"><span data-stu-id="02df2-112">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="02df2-113">`name`属性是可选的，可用于指定证书的友好名称。</span><span class="sxs-lookup"><span data-stu-id="02df2-113">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="02df2-114">从受信任的颁发者集合中清除所有证书。</span><span class="sxs-lookup"><span data-stu-id="02df2-114">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="02df2-115">从受信任的颁发者集合中删除证书。</span><span class="sxs-lookup"><span data-stu-id="02df2-115">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="02df2-116">证书是用属性指定的 `thumbprint` 。</span><span class="sxs-lookup"><span data-stu-id="02df2-116">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="02df2-117">该属性是必选项。</span><span class="sxs-lookup"><span data-stu-id="02df2-117">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02df2-118">父元素</span><span class="sxs-lookup"><span data-stu-id="02df2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="02df2-119">元素</span><span class="sxs-lookup"><span data-stu-id="02df2-119">Element</span></span>|<span data-ttu-id="02df2-120">说明</span><span class="sxs-lookup"><span data-stu-id="02df2-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="02df2-121">配置颁发者名称注册表。</span><span class="sxs-lookup"><span data-stu-id="02df2-121">Configures the issuer name registry.</span></span> <span data-ttu-id="02df2-122">**重要提示：** `type`元素的属性 `<issuerNameRegistry>` 必须引用类，才能使 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> `<trustedIssuers>` 元素有效。</span><span class="sxs-lookup"><span data-stu-id="02df2-122">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02df2-123">注解</span><span class="sxs-lookup"><span data-stu-id="02df2-123">Remarks</span></span>  
 <span data-ttu-id="02df2-124">Windows Identity Foundation （WIF）提供类的单一实现 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 类，该类是类的一种实现 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 。</span><span class="sxs-lookup"><span data-stu-id="02df2-124">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="02df2-125">配置颁发者名称注册表将维护从配置加载的受信任颁发者的列表。</span><span class="sxs-lookup"><span data-stu-id="02df2-125">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="02df2-126">此列表将每个颁发者名称与 x.509 证书关联，该证书是验证颁发者生成的令牌签名所需的证书。</span><span class="sxs-lookup"><span data-stu-id="02df2-126">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="02df2-127">受信任颁发者证书的列表是在元素下指定的 `<trustedIssuers>` 。</span><span class="sxs-lookup"><span data-stu-id="02df2-127">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="02df2-128">列表中的每个元素都将助记键颁发者名称与 x.509 证书关联，该证书是验证该颁发者生成的令牌签名所需的。</span><span class="sxs-lookup"><span data-stu-id="02df2-128">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="02df2-129">受信任的证书是使用 "证书指纹" 的 "ASN. 1" 编码形式指定的，并使用元素添加集合 `<add>` 。</span><span class="sxs-lookup"><span data-stu-id="02df2-129">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="02df2-130">您可以使用和元素从列表中清除或删除颁发者（证书 `<clear>` ） `<remove>` 。</span><span class="sxs-lookup"><span data-stu-id="02df2-130">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="02df2-131">`type`元素的属性 `<issuerNameRegistry>` 必须引用类，才能使 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> `<trustedIssuers>` 元素有效。</span><span class="sxs-lookup"><span data-stu-id="02df2-131">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02df2-132">示例</span><span class="sxs-lookup"><span data-stu-id="02df2-132">Example</span></span>  
 <span data-ttu-id="02df2-133">下面的 XML 演示如何指定基于配置的颁发者名称注册表。</span><span class="sxs-lookup"><span data-stu-id="02df2-133">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="02df2-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02df2-134">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
