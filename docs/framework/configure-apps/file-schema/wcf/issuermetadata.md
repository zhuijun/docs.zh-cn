---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 10a6d2aaad7d63d00b3a57032d0d218f756454d8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175949"
---
# \<issuerMetadata>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="5ff5a-101">语法</span><span class="sxs-lookup"><span data-stu-id="5ff5a-101">Syntax</span></span>  
  
```xml  
<issuerMetadata address="String">
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
</issuerMetadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ff5a-102">特性和元素</span><span class="sxs-lookup"><span data-stu-id="5ff5a-102">Attributes and Elements</span></span>  

 <span data-ttu-id="5ff5a-103">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5ff5a-103">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ff5a-104">特性</span><span class="sxs-lookup"><span data-stu-id="5ff5a-104">Attributes</span></span>  
  
|<span data-ttu-id="5ff5a-105">属性</span><span class="sxs-lookup"><span data-stu-id="5ff5a-105">Attribute</span></span>|<span data-ttu-id="5ff5a-106">描述</span><span class="sxs-lookup"><span data-stu-id="5ff5a-106">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ff5a-107">address</span><span class="sxs-lookup"><span data-stu-id="5ff5a-107">address</span></span>|<span data-ttu-id="5ff5a-108">必选的 `string` 特性。</span><span class="sxs-lookup"><span data-stu-id="5ff5a-108">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="5ff5a-109">指定终结点的地址。</span><span class="sxs-lookup"><span data-stu-id="5ff5a-109">Specifies the address of the endpoint.</span></span> <span data-ttu-id="5ff5a-110">该地址必须为绝对 URI。</span><span class="sxs-lookup"><span data-stu-id="5ff5a-110">The address must be an absolute URI.</span></span> <span data-ttu-id="5ff5a-111">默认值为空字符串。</span><span class="sxs-lookup"><span data-stu-id="5ff5a-111">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ff5a-112">子元素</span><span class="sxs-lookup"><span data-stu-id="5ff5a-112">Child Elements</span></span>  
  
|<span data-ttu-id="5ff5a-113">元素</span><span class="sxs-lookup"><span data-stu-id="5ff5a-113">Element</span></span>|<span data-ttu-id="5ff5a-114">描述</span><span class="sxs-lookup"><span data-stu-id="5ff5a-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="5ff5a-115">一个地址标头集合。</span><span class="sxs-lookup"><span data-stu-id="5ff5a-115">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="5ff5a-116">一个标识，与某个终结点交换消息的其他终结点可以使用该标识对该终结点进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="5ff5a-116">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ff5a-117">父元素</span><span class="sxs-lookup"><span data-stu-id="5ff5a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5ff5a-118">元素</span><span class="sxs-lookup"><span data-stu-id="5ff5a-118">Element</span></span>|<span data-ttu-id="5ff5a-119">描述</span><span class="sxs-lookup"><span data-stu-id="5ff5a-119">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="5ff5a-120">定义元素的消息级安全性设置 [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="5ff5a-120">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ff5a-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="5ff5a-121">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="5ff5a-122">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="5ff5a-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="5ff5a-123">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="5ff5a-123">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="5ff5a-124">使用自定义绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="5ff5a-124">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="5ff5a-125">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="5ff5a-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
