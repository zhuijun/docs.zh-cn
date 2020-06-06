---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: e49a564c9793b371425b2b787586bb9d3cbed58b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "77452222"
---
# \<dns>
<span data-ttu-id="e4ab8-101">指定服务器的所需标识。</span><span class="sxs-lookup"><span data-stu-id="e4ab8-101">Specifies the expected identity of the server.</span></span> <span data-ttu-id="e4ab8-102">如果服务器的证书包含具有相同值的 DNS，则此标识对于 X509 证书身份验证模式有效。</span><span class="sxs-lookup"><span data-stu-id="e4ab8-102">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="e4ab8-103">如果 SPN 具有相同值，则它对于 Windows 身份验证模式同样有效。</span><span class="sxs-lookup"><span data-stu-id="e4ab8-103">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="e4ab8-104">有关设置元素值的详细信息，请参阅[服务标识和身份验证](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="e4ab8-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**  
  
## <a name="syntax"></a><span data-ttu-id="e4ab8-105">语法</span><span class="sxs-lookup"><span data-stu-id="e4ab8-105">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4ab8-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e4ab8-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e4ab8-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e4ab8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4ab8-108">特性</span><span class="sxs-lookup"><span data-stu-id="e4ab8-108">Attributes</span></span>  
  
|<span data-ttu-id="e4ab8-109">属性</span><span class="sxs-lookup"><span data-stu-id="e4ab8-109">Attribute</span></span>|<span data-ttu-id="e4ab8-110">说明</span><span class="sxs-lookup"><span data-stu-id="e4ab8-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4ab8-111">值</span><span class="sxs-lookup"><span data-stu-id="e4ab8-111">value</span></span>|<span data-ttu-id="e4ab8-112">证书的 DNS。</span><span class="sxs-lookup"><span data-stu-id="e4ab8-112">The DNS of the certificate.</span></span> <span data-ttu-id="e4ab8-113">DNS 是一个用于在基于 IP 网络上定位计算机的行业标准协议。</span><span class="sxs-lookup"><span data-stu-id="e4ab8-113">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="e4ab8-114">用户可以记住显示名称（如 `https://go.microsoft.com/fwlink/?prd=10929` 或 `https://go.microsoft.com/fwlink/?LinkID=96165` ）比基于数字的地址更简单（如207.46.131.137）。</span><span class="sxs-lookup"><span data-stu-id="e4ab8-114">Users can remember display names, such as `https://go.microsoft.com/fwlink/?prd=10929` or `https://go.microsoft.com/fwlink/?LinkID=96165`, easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4ab8-115">子元素</span><span class="sxs-lookup"><span data-stu-id="e4ab8-115">Child Elements</span></span>  
 <span data-ttu-id="e4ab8-116">无。</span><span class="sxs-lookup"><span data-stu-id="e4ab8-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4ab8-117">父元素</span><span class="sxs-lookup"><span data-stu-id="e4ab8-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e4ab8-118">元素</span><span class="sxs-lookup"><span data-stu-id="e4ab8-118">Element</span></span>|<span data-ttu-id="e4ab8-119">描述</span><span class="sxs-lookup"><span data-stu-id="e4ab8-119">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="e4ab8-120">指定要由客户端进行身份验证的服务的标识。</span><span class="sxs-lookup"><span data-stu-id="e4ab8-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e4ab8-121">示例</span><span class="sxs-lookup"><span data-stu-id="e4ab8-121">Example</span></span>  
 <span data-ttu-id="e4ab8-122">下面的配置代码指定用于对服务器进行身份验证的 X.509 证书的 DNS。</span><span class="sxs-lookup"><span data-stu-id="e4ab8-122">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="e4ab8-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e4ab8-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="e4ab8-124">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="e4ab8-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
