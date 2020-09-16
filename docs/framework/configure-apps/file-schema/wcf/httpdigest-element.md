---
title: <httpDigest> 元素
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 0ffaba218d31a77407c598f8b7fa0260daa4e39c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556897"
---
# <a name="httpdigest-element"></a><span data-ttu-id="ad2e1-102">\<httpDigest> 元素</span><span class="sxs-lookup"><span data-stu-id="ad2e1-102">\<httpDigest> Element</span></span>
<span data-ttu-id="ad2e1-103">指定一个在向服务证明客户端身份时使用的摘要类型凭据。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**  
  
## <a name="syntax"></a><span data-ttu-id="ad2e1-104">语法</span><span class="sxs-lookup"><span data-stu-id="ad2e1-104">Syntax</span></span>  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad2e1-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ad2e1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ad2e1-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad2e1-107">特性</span><span class="sxs-lookup"><span data-stu-id="ad2e1-107">Attributes</span></span>  
  
|<span data-ttu-id="ad2e1-108">属性</span><span class="sxs-lookup"><span data-stu-id="ad2e1-108">Attribute</span></span>|<span data-ttu-id="ad2e1-109">说明</span><span class="sxs-lookup"><span data-stu-id="ad2e1-109">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="ad2e1-110">设置客户端用于与服务器进行通信的模拟首选项。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-110">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="ad2e1-111">服务器上不强制使用客户端所选择的模拟模式。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-111">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="ad2e1-112">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="ad2e1-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ad2e1-113">-标识：服务器可以获取客户端的标识和特权，但不能模拟客户端。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-113">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="ad2e1-114">-模拟：服务器可以在本地系统上模拟客户端的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-114">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="ad2e1-115">-委派：服务器可以在远程系统上模拟客户端的安全上下文。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-115">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="ad2e1-116">-Anonymous：服务器无法模拟或标识客户端。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-116">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="ad2e1-117">-None：不分配模拟级别。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-117">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="ad2e1-118">默认值为 Identification。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-118">The default is Identification.</span></span> <span data-ttu-id="ad2e1-119">此属性的类型为 <xref:System.Security.Principal.TokenImpersonationLevel>。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-119">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad2e1-120">子元素</span><span class="sxs-lookup"><span data-stu-id="ad2e1-120">Child Elements</span></span>  
 <span data-ttu-id="ad2e1-121">无</span><span class="sxs-lookup"><span data-stu-id="ad2e1-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad2e1-122">父元素</span><span class="sxs-lookup"><span data-stu-id="ad2e1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ad2e1-123">元素</span><span class="sxs-lookup"><span data-stu-id="ad2e1-123">Element</span></span>|<span data-ttu-id="ad2e1-124">说明</span><span class="sxs-lookup"><span data-stu-id="ad2e1-124">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="ad2e1-125">指定用于向服务验证客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-125">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad2e1-126">备注</span><span class="sxs-lookup"><span data-stu-id="ad2e1-126">Remarks</span></span>  
 <span data-ttu-id="ad2e1-127">摘要是使用算法和一组输入确定的哈希。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-127">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="ad2e1-128">身份验证器和被验证方一致同意某种算法并交换用作输入的数据。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-128">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="ad2e1-129">客户端可以计算哈希并将其发送给服务。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-129">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="ad2e1-130">服务也可以计算哈希并比较值。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-130">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="ad2e1-131">如果匹配，则客户端将通过验证。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-131">A match validates the client.</span></span>  
  
 <span data-ttu-id="ad2e1-132">必须使用 Windows 上的 Active Directory 和 Internet 信息服务 (IIS) 启用此功能。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-132">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="ad2e1-133">有关详细信息，请参阅 [IIS 6.0 中的摘要式身份验证](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10))。</span><span class="sxs-lookup"><span data-stu-id="ad2e1-133">For more information, see [Digest Authentication in IIS 6.0](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad2e1-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="ad2e1-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="ad2e1-135">安全行为</span><span class="sxs-lookup"><span data-stu-id="ad2e1-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="ad2e1-136">保证客户端的安全</span><span class="sxs-lookup"><span data-stu-id="ad2e1-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="ad2e1-137">使用证书</span><span class="sxs-lookup"><span data-stu-id="ad2e1-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="ad2e1-138">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="ad2e1-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
