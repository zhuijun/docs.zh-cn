---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 841331f233bb8c42c25c88ad8e9b4fb1a86faa76
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398991"
---
# \<xmlElement>
<span data-ttu-id="2346d-101">指定一个 XML 元素，请求令牌时，该元素在消息正文中发送到安全令牌服务。</span><span class="sxs-lookup"><span data-stu-id="2346d-101">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**  
  
## <a name="syntax"></a><span data-ttu-id="2346d-102">语法</span><span class="sxs-lookup"><span data-stu-id="2346d-102">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2346d-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="2346d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="2346d-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2346d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2346d-105">特性</span><span class="sxs-lookup"><span data-stu-id="2346d-105">Attributes</span></span>  
  
|<span data-ttu-id="2346d-106">属性</span><span class="sxs-lookup"><span data-stu-id="2346d-106">Attribute</span></span>|<span data-ttu-id="2346d-107">说明</span><span class="sxs-lookup"><span data-stu-id="2346d-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2346d-108">xmlElement</span><span class="sxs-lookup"><span data-stu-id="2346d-108">xmlElement</span></span>|<span data-ttu-id="2346d-109">指定 XML 元素的字符串，请求令牌时，该元素在消息正文中发送到安全令牌服务。</span><span class="sxs-lookup"><span data-stu-id="2346d-109">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2346d-110">子元素</span><span class="sxs-lookup"><span data-stu-id="2346d-110">Child Elements</span></span>  
 <span data-ttu-id="2346d-111">无。</span><span class="sxs-lookup"><span data-stu-id="2346d-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2346d-112">父元素</span><span class="sxs-lookup"><span data-stu-id="2346d-112">Parent Elements</span></span>  
  
|<span data-ttu-id="2346d-113">元素</span><span class="sxs-lookup"><span data-stu-id="2346d-113">Element</span></span>|<span data-ttu-id="2346d-114">描述</span><span class="sxs-lookup"><span data-stu-id="2346d-114">Description</span></span>|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="2346d-115">令牌请求参数的集合。</span><span class="sxs-lookup"><span data-stu-id="2346d-115">A collection of token request parameters.</span></span> <span data-ttu-id="2346d-116">每个参数都是一个 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="2346d-116">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2346d-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2346d-117">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="2346d-118">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="2346d-118">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="2346d-119">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="2346d-119">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="2346d-120">使用自定义绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="2346d-120">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="2346d-121">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="2346d-121">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="2346d-122">绑定</span><span class="sxs-lookup"><span data-stu-id="2346d-122">Bindings</span></span>](../../../wcf/bindings.md)
