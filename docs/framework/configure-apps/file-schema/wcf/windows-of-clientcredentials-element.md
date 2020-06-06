---
title: <windows>of <clientCredentials> 元素
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 61ca99213f0b83a5af5df0184a8c1de405366288
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399119"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="67187-102">\<windows>of \<clientCredentials> 元素</span><span class="sxs-lookup"><span data-stu-id="67187-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="67187-103">指定用于表示客户端的 Windows 凭据的设置。</span><span class="sxs-lookup"><span data-stu-id="67187-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**  
  
## <a name="syntax"></a><span data-ttu-id="67187-104">语法</span><span class="sxs-lookup"><span data-stu-id="67187-104">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67187-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="67187-105">Attributes and Elements</span></span>  
 <span data-ttu-id="67187-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="67187-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67187-107">特性</span><span class="sxs-lookup"><span data-stu-id="67187-107">Attributes</span></span>  
  
|<span data-ttu-id="67187-108">属性</span><span class="sxs-lookup"><span data-stu-id="67187-108">Attribute</span></span>|<span data-ttu-id="67187-109">说明</span><span class="sxs-lookup"><span data-stu-id="67187-109">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="67187-110">设置客户端用于与服务器进行通信的模拟首选项。</span><span class="sxs-lookup"><span data-stu-id="67187-110">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="67187-111">服务器上不强制使用客户端所选择的模拟模式。</span><span class="sxs-lookup"><span data-stu-id="67187-111">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="67187-112">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="67187-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="67187-113">-标识：服务器可以获取客户端的标识和特权，但不能模拟客户端。</span><span class="sxs-lookup"><span data-stu-id="67187-113">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="67187-114">-模拟：服务器可以在本地系统上模拟客户端的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="67187-114">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="67187-115">-委派：服务器可以在远程系统上模拟客户端的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="67187-115">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="67187-116">-Anonymous：服务器无法模拟或标识客户端。</span><span class="sxs-lookup"><span data-stu-id="67187-116">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="67187-117">-None：不分配模拟级别。</span><span class="sxs-lookup"><span data-stu-id="67187-117">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="67187-118">默认值为 Identification。</span><span class="sxs-lookup"><span data-stu-id="67187-118">The default is Identification.</span></span> <span data-ttu-id="67187-119">此属性的类型为 <xref:System.Security.Principal.TokenImpersonationLevel>。</span><span class="sxs-lookup"><span data-stu-id="67187-119">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="67187-120">如果 Kerberos 不可用，则将此属性设置为 `true` 可令身份验证降级到 NTLM。</span><span class="sxs-lookup"><span data-stu-id="67187-120">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="67187-121">如果将此属性设置为，则 `false` 会导致 Windows Communication Foundation （WCF）在使用 NTLM 时尽力引发异常。</span><span class="sxs-lookup"><span data-stu-id="67187-121">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="67187-122">请注意，将此属性设置为 `false` 可能不阻止通过网络发送 NTLM 凭据。</span><span class="sxs-lookup"><span data-stu-id="67187-122">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67187-123">子元素</span><span class="sxs-lookup"><span data-stu-id="67187-123">Child Elements</span></span>  
 <span data-ttu-id="67187-124">无。</span><span class="sxs-lookup"><span data-stu-id="67187-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67187-125">父元素</span><span class="sxs-lookup"><span data-stu-id="67187-125">Parent Elements</span></span>  
  
|<span data-ttu-id="67187-126">元素</span><span class="sxs-lookup"><span data-stu-id="67187-126">Element</span></span>|<span data-ttu-id="67187-127">描述</span><span class="sxs-lookup"><span data-stu-id="67187-127">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="67187-128">指定用于向服务证明客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="67187-128">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67187-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="67187-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="67187-130">保证客户端的安全</span><span class="sxs-lookup"><span data-stu-id="67187-130">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="67187-131">使用证书</span><span class="sxs-lookup"><span data-stu-id="67187-131">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="67187-132">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="67187-132">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
