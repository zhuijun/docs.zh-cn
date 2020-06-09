---
title: 声明创建和资源值
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: fabd0a2606560d99174e5ad28940c3b59ee689d9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587048"
---
# <a name="claim-creation-and-resource-values"></a><span data-ttu-id="8dffd-102">声明创建和资源值</span><span class="sxs-lookup"><span data-stu-id="8dffd-102">Claim Creation and Resource Values</span></span>
<span data-ttu-id="8dffd-103"><xref:System.IdentityModel.Claims.Claim> 类提供了多种创建内置声明类型的实例的方法。</span><span class="sxs-lookup"><span data-stu-id="8dffd-103">The <xref:System.IdentityModel.Claims.Claim> class provides several methods for creating instances of built-in claims types.</span></span> <span data-ttu-id="8dffd-104">在这些方法中，以下方法不对提供的资源执行语义或格式检查：</span><span class="sxs-lookup"><span data-stu-id="8dffd-104">Of these methods, the following perform no semantic or format checking on the supplied resource:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
- <span data-ttu-id="8dffd-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A>（不检查字节数组的长度或内容）</span><span class="sxs-lookup"><span data-stu-id="8dffd-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
- <span data-ttu-id="8dffd-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A>（不检查字节数组的长度或内容）</span><span class="sxs-lookup"><span data-stu-id="8dffd-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 <span data-ttu-id="8dffd-107">调用上述方法时应该小心，确保传入的资源值使用正确的格式和/或包含正确的信息类型。</span><span class="sxs-lookup"><span data-stu-id="8dffd-107">Care should be taken when calling the above methods to ensure that the resource values passed in are of the correct format or contain the correct kind of information (or both).</span></span>  
  
 <span data-ttu-id="8dffd-108">以下方法采用特定类型：</span><span class="sxs-lookup"><span data-stu-id="8dffd-108">The following methods take specific types:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a><span data-ttu-id="8dffd-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8dffd-109">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [<span data-ttu-id="8dffd-110">使用标识模型管理声明和授权</span><span class="sxs-lookup"><span data-stu-id="8dffd-110">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
