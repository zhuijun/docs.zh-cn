---
title: 若 <identity>，表示集 <certificate>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 24c39b5efaee7f8db12088d272efeb3783efab04
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198855"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="156dc-102">若 \<identity>，表示集 \<certificate></span><span class="sxs-lookup"><span data-stu-id="156dc-102">\<certificate> for \<identity></span></span>

<span data-ttu-id="156dc-103">指定用于向客户端验证服务器的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="156dc-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="156dc-104">有关设置元素值的详细信息，请参阅 [服务标识和身份验证](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="156dc-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="156dc-105">语法</span><span class="sxs-lookup"><span data-stu-id="156dc-105">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="156dc-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="156dc-106">Attributes and Elements</span></span>  

 <span data-ttu-id="156dc-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="156dc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="156dc-108">特性</span><span class="sxs-lookup"><span data-stu-id="156dc-108">Attributes</span></span>  
  
|<span data-ttu-id="156dc-109">属性</span><span class="sxs-lookup"><span data-stu-id="156dc-109">Attribute</span></span>|<span data-ttu-id="156dc-110">描述</span><span class="sxs-lookup"><span data-stu-id="156dc-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="156dc-111">encodedValue</span><span class="sxs-lookup"><span data-stu-id="156dc-111">encodedValue</span></span>|<span data-ttu-id="156dc-112">证书的 Base64 编码。</span><span class="sxs-lookup"><span data-stu-id="156dc-112">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="156dc-113">子元素</span><span class="sxs-lookup"><span data-stu-id="156dc-113">Child Elements</span></span>  

 <span data-ttu-id="156dc-114">无。</span><span class="sxs-lookup"><span data-stu-id="156dc-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="156dc-115">父元素</span><span class="sxs-lookup"><span data-stu-id="156dc-115">Parent Elements</span></span>  
  
|<span data-ttu-id="156dc-116">元素</span><span class="sxs-lookup"><span data-stu-id="156dc-116">Element</span></span>|<span data-ttu-id="156dc-117">描述</span><span class="sxs-lookup"><span data-stu-id="156dc-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="156dc-118">指定要由客户端进行身份验证的服务的标识。</span><span class="sxs-lookup"><span data-stu-id="156dc-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="156dc-119">示例</span><span class="sxs-lookup"><span data-stu-id="156dc-119">Example</span></span>  

 <span data-ttu-id="156dc-120">下面的代码指定用于向客户端验证服务器的证书的编码表示形式。</span><span class="sxs-lookup"><span data-stu-id="156dc-120">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="156dc-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="156dc-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="156dc-122">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="156dc-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
