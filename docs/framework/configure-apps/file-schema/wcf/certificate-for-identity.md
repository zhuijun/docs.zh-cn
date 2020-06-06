---
title: 若 <identity>，表示集 <certificate>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 1cfd207afc72cc71359d9d262e30b0696ba63d2b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850012"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="2ebdb-102">若 \<identity>，表示集 \<certificate></span><span class="sxs-lookup"><span data-stu-id="2ebdb-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="2ebdb-103">指定用于向客户端验证服务器的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="2ebdb-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="2ebdb-104">有关设置元素值的详细信息，请参阅[服务标识和身份验证](../../../wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="2ebdb-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="2ebdb-105">语法</span><span class="sxs-lookup"><span data-stu-id="2ebdb-105">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ebdb-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="2ebdb-106">Attributes and Elements</span></span>  
 <span data-ttu-id="2ebdb-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2ebdb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ebdb-108">特性</span><span class="sxs-lookup"><span data-stu-id="2ebdb-108">Attributes</span></span>  
  
|<span data-ttu-id="2ebdb-109">属性</span><span class="sxs-lookup"><span data-stu-id="2ebdb-109">Attribute</span></span>|<span data-ttu-id="2ebdb-110">说明</span><span class="sxs-lookup"><span data-stu-id="2ebdb-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ebdb-111">encodedValue</span><span class="sxs-lookup"><span data-stu-id="2ebdb-111">encodedValue</span></span>|<span data-ttu-id="2ebdb-112">证书的 Base64 编码。</span><span class="sxs-lookup"><span data-stu-id="2ebdb-112">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ebdb-113">子元素</span><span class="sxs-lookup"><span data-stu-id="2ebdb-113">Child Elements</span></span>  
 <span data-ttu-id="2ebdb-114">无。</span><span class="sxs-lookup"><span data-stu-id="2ebdb-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ebdb-115">父元素</span><span class="sxs-lookup"><span data-stu-id="2ebdb-115">Parent Elements</span></span>  
  
|<span data-ttu-id="2ebdb-116">元素</span><span class="sxs-lookup"><span data-stu-id="2ebdb-116">Element</span></span>|<span data-ttu-id="2ebdb-117">描述</span><span class="sxs-lookup"><span data-stu-id="2ebdb-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="2ebdb-118">指定要由客户端进行身份验证的服务的标识。</span><span class="sxs-lookup"><span data-stu-id="2ebdb-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2ebdb-119">示例</span><span class="sxs-lookup"><span data-stu-id="2ebdb-119">Example</span></span>  
 <span data-ttu-id="2ebdb-120">下面的代码指定用于向客户端验证服务器的证书的编码表示形式。</span><span class="sxs-lookup"><span data-stu-id="2ebdb-120">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="2ebdb-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="2ebdb-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="2ebdb-122">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="2ebdb-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
