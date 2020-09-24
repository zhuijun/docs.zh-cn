---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 9e92bbcacf529a97e1ae936e93e38c98eab19cab
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157260"
---
# \<issuer>

<span data-ttu-id="1874a-101">指定颁发安全令牌的安全令牌服务 (STS)。</span><span class="sxs-lookup"><span data-stu-id="1874a-101">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="1874a-102">语法</span><span class="sxs-lookup"><span data-stu-id="1874a-102">Syntax</span></span>  
  
```xml  
<issuer address="Uri">
  <headers>
    <add name="String"
         namespace="String" />
  </headers>
  <identity>
    <certificate encodedValue="String" />
    <certificateReference findValue="String"
                          isChainIncluded="Boolean"
                          storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                          storeLocation="LocalMachine/CurrentUser"
                          x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
    <dns value="String" />
    <rsa value="String" />
    <servicePrincipalName value="String" />
    <usePrincipalName value="String" />
  </identity>
</issuer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1874a-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1874a-103">Attributes and Elements</span></span>  

 <span data-ttu-id="1874a-104">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1874a-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1874a-105">特性</span><span class="sxs-lookup"><span data-stu-id="1874a-105">Attributes</span></span>  
  
|<span data-ttu-id="1874a-106">属性</span><span class="sxs-lookup"><span data-stu-id="1874a-106">Attribute</span></span>|<span data-ttu-id="1874a-107">描述</span><span class="sxs-lookup"><span data-stu-id="1874a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1874a-108">address</span><span class="sxs-lookup"><span data-stu-id="1874a-108">address</span></span>|<span data-ttu-id="1874a-109">必选字符串。</span><span class="sxs-lookup"><span data-stu-id="1874a-109">Required string.</span></span> <span data-ttu-id="1874a-110">STS 的 URL。</span><span class="sxs-lookup"><span data-stu-id="1874a-110">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1874a-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1874a-111">Child Elements</span></span>  
  
|<span data-ttu-id="1874a-112">元素</span><span class="sxs-lookup"><span data-stu-id="1874a-112">Element</span></span>|<span data-ttu-id="1874a-113">描述</span><span class="sxs-lookup"><span data-stu-id="1874a-113">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="1874a-114">生成器可以创建的终结点的地址标头的集合。</span><span class="sxs-lookup"><span data-stu-id="1874a-114">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="1874a-115">在使用颁发的令牌时，指定能够使客户端对服务器进行身份验证的设置。</span><span class="sxs-lookup"><span data-stu-id="1874a-115">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1874a-116">父元素</span><span class="sxs-lookup"><span data-stu-id="1874a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="1874a-117">元素</span><span class="sxs-lookup"><span data-stu-id="1874a-117">Element</span></span>|<span data-ttu-id="1874a-118">描述</span><span class="sxs-lookup"><span data-stu-id="1874a-118">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="1874a-119">定义元素的消息级安全性设置 [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="1874a-119">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1874a-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="1874a-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="1874a-121">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="1874a-121">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="1874a-122">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="1874a-122">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="1874a-123">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="1874a-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="1874a-124">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="1874a-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="1874a-125">使用自定义绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="1874a-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="1874a-126">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="1874a-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
