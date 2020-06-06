---
title: 若 <message>，表示集 <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: db6717022bf3af0c4922818668595dd3937e9c71
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "61704402"
---
# <a name="claimtyperequirements-for-message"></a>若 \<message>，表示集 \<claimTypeRequirements>
指定所需声明类型的集合。  
  
 服务使用此集合来指定任何必选和可选声明，这些声明必须位于客户端用于访问服务的已颁发令牌中。 如果 WSDL 发布已启用但 WCF 并不要求已颁发的令牌包含指定的声明类型，则服务将会在元数据中公开所需的声明类型。 希望强制显示所需声明类型的服务应该使用授权策略。  
  
 在联合客户端上，此集合包含必选和可选声明的列表，该列表将在客户端请求已颁发令牌时发送给安全令牌服务。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
