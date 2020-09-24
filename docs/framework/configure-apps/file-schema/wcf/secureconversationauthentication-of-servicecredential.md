---
title: <secureConversationAuthentication> 的 <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: be2a9298a78de1503271f41076b9f5bb63c73f74
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162229"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="18efa-102">\<secureConversationAuthentication> 的 \<serviceCredential></span><span class="sxs-lookup"><span data-stu-id="18efa-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>

<span data-ttu-id="18efa-103">指定安全对话服务的设置。</span><span class="sxs-lookup"><span data-stu-id="18efa-103">Specifies the settings for a secure conversation service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="18efa-104">语法</span><span class="sxs-lookup"><span data-stu-id="18efa-104">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18efa-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="18efa-105">Attributes and Elements</span></span>  

 <span data-ttu-id="18efa-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="18efa-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18efa-107">特性</span><span class="sxs-lookup"><span data-stu-id="18efa-107">Attributes</span></span>  
  
|<span data-ttu-id="18efa-108">属性</span><span class="sxs-lookup"><span data-stu-id="18efa-108">Attribute</span></span>|<span data-ttu-id="18efa-109">描述</span><span class="sxs-lookup"><span data-stu-id="18efa-109">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="18efa-110">一个字符串，指定要使用的 <xref:System.ServiceModel.Security.SecurityStateEncoder> 的类型。</span><span class="sxs-lookup"><span data-stu-id="18efa-110">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18efa-111">子元素</span><span class="sxs-lookup"><span data-stu-id="18efa-111">Child Elements</span></span>  

 <span data-ttu-id="18efa-112">无。</span><span class="sxs-lookup"><span data-stu-id="18efa-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18efa-113">父元素</span><span class="sxs-lookup"><span data-stu-id="18efa-113">Parent Elements</span></span>  
  
|<span data-ttu-id="18efa-114">元素</span><span class="sxs-lookup"><span data-stu-id="18efa-114">Element</span></span>|<span data-ttu-id="18efa-115">描述</span><span class="sxs-lookup"><span data-stu-id="18efa-115">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="18efa-116">指定要用于对服务进行身份验证的凭据以及与客户端凭据验证相关的设置。</span><span class="sxs-lookup"><span data-stu-id="18efa-116">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18efa-117">备注</span><span class="sxs-lookup"><span data-stu-id="18efa-117">Remarks</span></span>  

 <span data-ttu-id="18efa-118">使用此配置元素可指定用于安全上下文令牌 (SCT) Cookie 序列化的已知声明类型的列表和用于编码和保护 Cookie 信息的编码器。</span><span class="sxs-lookup"><span data-stu-id="18efa-118">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="18efa-119">有关 SCT 的更多信息，请参见 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>。</span><span class="sxs-lookup"><span data-stu-id="18efa-119">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18efa-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="18efa-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
