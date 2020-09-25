---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 0ab7fbd64cc92e940617f5334eeb16fcb3a50c4a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181227"
---
# \<xmlElement>

<span data-ttu-id="4997e-101">指定一个 XML 元素，请求令牌时，该元素在消息正文中发送到安全令牌服务。</span><span class="sxs-lookup"><span data-stu-id="4997e-101">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**  
  
## <a name="syntax"></a><span data-ttu-id="4997e-102">语法</span><span class="sxs-lookup"><span data-stu-id="4997e-102">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4997e-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4997e-103">Attributes and Elements</span></span>  

 <span data-ttu-id="4997e-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4997e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4997e-105">特性</span><span class="sxs-lookup"><span data-stu-id="4997e-105">Attributes</span></span>  
  
|<span data-ttu-id="4997e-106">属性</span><span class="sxs-lookup"><span data-stu-id="4997e-106">Attribute</span></span>|<span data-ttu-id="4997e-107">描述</span><span class="sxs-lookup"><span data-stu-id="4997e-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4997e-108">xmlElement</span><span class="sxs-lookup"><span data-stu-id="4997e-108">xmlElement</span></span>|<span data-ttu-id="4997e-109">指定 XML 元素的字符串，请求令牌时，该元素在消息正文中发送到安全令牌服务。</span><span class="sxs-lookup"><span data-stu-id="4997e-109">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4997e-110">子元素</span><span class="sxs-lookup"><span data-stu-id="4997e-110">Child Elements</span></span>  

 <span data-ttu-id="4997e-111">无。</span><span class="sxs-lookup"><span data-stu-id="4997e-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4997e-112">父元素</span><span class="sxs-lookup"><span data-stu-id="4997e-112">Parent Elements</span></span>  
  
|<span data-ttu-id="4997e-113">元素</span><span class="sxs-lookup"><span data-stu-id="4997e-113">Element</span></span>|<span data-ttu-id="4997e-114">描述</span><span class="sxs-lookup"><span data-stu-id="4997e-114">Description</span></span>|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="4997e-115">令牌请求参数的集合。</span><span class="sxs-lookup"><span data-stu-id="4997e-115">A collection of token request parameters.</span></span> <span data-ttu-id="4997e-116">每个参数都是一个 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="4997e-116">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4997e-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="4997e-117">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="4997e-118">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="4997e-118">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="4997e-119">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="4997e-119">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="4997e-120">使用自定义绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="4997e-120">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="4997e-121">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="4997e-121">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="4997e-122">绑定</span><span class="sxs-lookup"><span data-stu-id="4997e-122">Bindings</span></span>](../../../wcf/bindings.md)
