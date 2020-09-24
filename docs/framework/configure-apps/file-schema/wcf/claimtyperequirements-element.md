---
title: <claimTypeRequirements> 元素
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: 6a4e5da3bd3ef6977d6258190d397130b33eb56c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148966"
---
# <a name="claimtyperequirements-element"></a><span data-ttu-id="00712-102">\<claimTypeRequirements> 元素</span><span class="sxs-lookup"><span data-stu-id="00712-102">\<claimTypeRequirements> element</span></span>

<span data-ttu-id="00712-103">指定所需声明类型的集合。</span><span class="sxs-lookup"><span data-stu-id="00712-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="00712-104">在联合方案中，服务规定有关传入凭据的要求。</span><span class="sxs-lookup"><span data-stu-id="00712-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="00712-105">例如，传入凭据必须具有某组声明类型。</span><span class="sxs-lookup"><span data-stu-id="00712-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="00712-106">此集合中的每个子元素都指定希望出现在联合凭据中的必选和可选的声明类型。</span><span class="sxs-lookup"><span data-stu-id="00712-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="00712-107">声明类型需求由在已颁发令牌中请求的声明类型的 URI 和布尔参数组成，其中布尔参数可指示该声明类型在已颁发的令牌中是必选还是可选的。</span><span class="sxs-lookup"><span data-stu-id="00712-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00712-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="00712-108">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="00712-109">服务标识和身份验证</span><span class="sxs-lookup"><span data-stu-id="00712-109">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="00712-110">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="00712-110">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="00712-111">使用自定义绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="00712-111">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="00712-112">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="00712-112">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-claimtyperequirements.md)
- [<span data-ttu-id="00712-113">绑定</span><span class="sxs-lookup"><span data-stu-id="00712-113">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="00712-114">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="00712-114">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="00712-115">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="00712-115">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="00712-116">如何：使用 SecurityBindingElement 创建自定义绑定</span><span class="sxs-lookup"><span data-stu-id="00712-116">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="00712-117">自定义绑定安全性</span><span class="sxs-lookup"><span data-stu-id="00712-117">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
