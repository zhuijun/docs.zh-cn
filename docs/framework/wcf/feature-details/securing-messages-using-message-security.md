---
title: 使用消息安全保护消息
ms.date: 03/30/2017
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
ms.openlocfilehash: b5f7679d5e5ec82e63b588cebd90ce873c055088
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558298"
---
# <a name="securing-messages-using-message-security"></a><span data-ttu-id="b3da6-102">使用消息安全保护消息</span><span class="sxs-lookup"><span data-stu-id="b3da6-102">Securing Messages Using Message Security</span></span>
<span data-ttu-id="b3da6-103">本部分介绍了使用时的 WCF 消息安全性 <xref:System.ServiceModel.NetMsmqBinding> 。</span><span class="sxs-lookup"><span data-stu-id="b3da6-103">This section discusses WCF message security when using <xref:System.ServiceModel.NetMsmqBinding>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3da6-104">在阅读本主题之前，建议你阅读 [安全概念](security-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="b3da6-104">Before reading through this topic, it is recommended that you read [Security Concepts](security-concepts.md).</span></span>  
  
 <span data-ttu-id="b3da6-105">下图提供了使用 WCF 进行排队通信的概念模型。</span><span class="sxs-lookup"><span data-stu-id="b3da6-105">The following illustration provides a conceptual model of queued communication using WCF.</span></span> <span data-ttu-id="b3da6-106">此图及术语用于说明</span><span class="sxs-lookup"><span data-stu-id="b3da6-106">This illustration and terminology are used to explain</span></span>  
  
 <span data-ttu-id="b3da6-107">传输安全概念。</span><span class="sxs-lookup"><span data-stu-id="b3da6-107">transport security concepts.</span></span>  
  
 <span data-ttu-id="b3da6-108">![排队应用程序关系图](media/distributed-queue-figure.jpg "分布式队列图")</span><span class="sxs-lookup"><span data-stu-id="b3da6-108">![Queued Application Diagram](media/distributed-queue-figure.jpg "Distributed-Queue-Figure")</span></span>  
  
 <span data-ttu-id="b3da6-109">使用 WCF 发送排队消息时，WCF 消息作为消息队列正文附加 (MSMQ) 消息。</span><span class="sxs-lookup"><span data-stu-id="b3da6-109">When sending queued messages using WCF, the WCF message is attached as a body of the Message Queuing (MSMQ) message.</span></span> <span data-ttu-id="b3da6-110">传输安全保护整个 MSMQ 消息，而消息（或 SOAP）安全仅保护 MSMQ 消息正文。</span><span class="sxs-lookup"><span data-stu-id="b3da6-110">While transport security secures the entire MSMQ message, message (or SOAP) security only secures the body of the MSMQ message.</span></span>  
  
 <span data-ttu-id="b3da6-111">传输安全用于在客户端保护目标队列的消息，与此不同，消息安全的关键概念在于客户端保护接收应用程序（服务）的消息。</span><span class="sxs-lookup"><span data-stu-id="b3da6-111">The key concept of message security is that the client secures the message for the receiving application (service), unlike transport security where the client secures the message for the Target Queue.</span></span> <span data-ttu-id="b3da6-112">因此，在使用消息安全保护 WCF 消息时，MSMQ 不起作用。</span><span class="sxs-lookup"><span data-stu-id="b3da6-112">As such, MSMQ plays no part when securing the WCF message using message security.</span></span>  
  
 <span data-ttu-id="b3da6-113">WCF 消息安全将安全标头添加到 WCF 消息，该消息与现有安全基础结构（如证书或 Kerberos 协议）集成。</span><span class="sxs-lookup"><span data-stu-id="b3da6-113">WCF message security adds security headers to the WCF message that integrate with existing security infrastructures, such as a certificate or the Kerberos protocol.</span></span>  
  
## <a name="message-credential-type"></a><span data-ttu-id="b3da6-114">消息凭据类型</span><span class="sxs-lookup"><span data-stu-id="b3da6-114">Message Credential Type</span></span>  
 <span data-ttu-id="b3da6-115">使用消息安全，服务和客户端可以提供相互进行身份验证的凭据。</span><span class="sxs-lookup"><span data-stu-id="b3da6-115">Using message security, the service and client can present credentials to authenticate each another.</span></span> <span data-ttu-id="b3da6-116">可以通过将 <xref:System.ServiceModel.NetMsmqBinding.Security%2A> 模式设置为 `Message` 或 `Both`（即既使用传输安全又使用消息安全）来选择消息安全。</span><span class="sxs-lookup"><span data-stu-id="b3da6-116">You can select message security by setting the <xref:System.ServiceModel.NetMsmqBinding.Security%2A> mode to `Message` or `Both` (that is, use both transport security and message security).</span></span>  
  
 <span data-ttu-id="b3da6-117">该服务可以使用 <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> 属性检查用于对客户端进行身份验证的凭据。</span><span class="sxs-lookup"><span data-stu-id="b3da6-117">The service can use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to inspect the credential used to authenticate the client.</span></span> <span data-ttu-id="b3da6-118">这也可用于该服务选择实现的进一步的授权检查。</span><span class="sxs-lookup"><span data-stu-id="b3da6-118">This can also be used for further authorization checks that the service chooses to implement.</span></span>  
  
 <span data-ttu-id="b3da6-119">本节说明不同的凭据类型以及如何将其用于队列。</span><span class="sxs-lookup"><span data-stu-id="b3da6-119">This section explains the different credential types and how to use them with queues.</span></span>  
  
### <a name="certificate"></a><span data-ttu-id="b3da6-120">证书</span><span class="sxs-lookup"><span data-stu-id="b3da6-120">Certificate</span></span>  
 <span data-ttu-id="b3da6-121">证书凭据类型使用 X.509 证书来标识服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="b3da6-121">The certificate credential type uses an X.509 certificate to identify the service and the client.</span></span>  
  
 <span data-ttu-id="b3da6-122">在典型方案中，由受信任的证书颁发机构向客户端和服务颁发有效证书。</span><span class="sxs-lookup"><span data-stu-id="b3da6-122">In a typical scenario, the client and the service are issued a valid certificate by a trusted certification authority.</span></span> <span data-ttu-id="b3da6-123">然后将建立连接，客户端使用服务的证书对服务有效性进行身份验证，以决定是否可以信任该服务。</span><span class="sxs-lookup"><span data-stu-id="b3da6-123">Then the connection is established, the client authenticates the validity of the service using the service's certificate to decide whether it can trust the service.</span></span> <span data-ttu-id="b3da6-124">同样，服务使用客户端的证书来验证客户端是否可信。</span><span class="sxs-lookup"><span data-stu-id="b3da6-124">Similarly, the service uses the client's certificate to validate the client trust.</span></span>  
  
 <span data-ttu-id="b3da6-125">鉴于队列有断开连接的特性，客户端和服务可能不会同时联机。</span><span class="sxs-lookup"><span data-stu-id="b3da6-125">Given the disconnected nature of queues, the client and the service may not be online at the same time.</span></span> <span data-ttu-id="b3da6-126">这样，客户端和服务必须在带外交换证书。</span><span class="sxs-lookup"><span data-stu-id="b3da6-126">As such, the client and service have to exchange certificates out-of-band.</span></span> <span data-ttu-id="b3da6-127">尤其是，由于客户端在其受信任存储区中存有服务的证书（可以将该证书链接到证书颁发机构），因此必须信任它将与正确的服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="b3da6-127">In particular, the client, by virtue of holding the service's certificate (which can be chained to a certification authority) in its trusted store, must trust that it is communicating with the correct service.</span></span> <span data-ttu-id="b3da6-128">至于对客户端进行身份验证，服务使用附有消息的 X.509 证书将该客户端与其存储中的证书进行匹配来验证客户端的真实性。</span><span class="sxs-lookup"><span data-stu-id="b3da6-128">For authenticating the client, the service uses the X.509 certificate attached with the message to matches it with the certificate in its store to verify the authenticity of the client.</span></span> <span data-ttu-id="b3da6-129">该证书必须再次链接到证书颁发机构。</span><span class="sxs-lookup"><span data-stu-id="b3da6-129">Again, the certificate must be chained to a certification authority.</span></span>  
  
 <span data-ttu-id="b3da6-130">在运行 Windows 的计算机上，证书存放在多类存储区中。</span><span class="sxs-lookup"><span data-stu-id="b3da6-130">On a computer running Windows, certificates are held in several kinds of stores.</span></span> <span data-ttu-id="b3da6-131">有关不同存储的详细信息，请参阅 [证书存储](/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10))。</span><span class="sxs-lookup"><span data-stu-id="b3da6-131">For more information about the different stores, see [Certificate stores](/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10)).</span></span>  
  
### <a name="windows"></a><span data-ttu-id="b3da6-132">Windows</span><span class="sxs-lookup"><span data-stu-id="b3da6-132">Windows</span></span>  
 <span data-ttu-id="b3da6-133">Windows 消息凭据类型使用 Kerberos 协议。</span><span class="sxs-lookup"><span data-stu-id="b3da6-133">Windows message credential type uses the Kerberos protocol.</span></span>  
  
 <span data-ttu-id="b3da6-134">Kerberos 协议是一种安全机制，可用于对域中的用户进行身份验证，并允许通过身份验证的用户与域中的其他实体建立安全上下文。</span><span class="sxs-lookup"><span data-stu-id="b3da6-134">The Kerberos protocol is a security mechanism that authenticates users on a domain and allows the authenticated users to establish secure contexts with other entities on a domain.</span></span>  
  
 <span data-ttu-id="b3da6-135">将 Kerberos 协议用于排队通信的问题在于包含密钥分发中心 (KDC) 所分发客户端标识的票证的生存期相对较短。</span><span class="sxs-lookup"><span data-stu-id="b3da6-135">The problem with using the Kerberos protocol for queued communication is that the tickets that contain client identity that the Key Distribution Center (KDC) distributes are relatively short-lived.</span></span> <span data-ttu-id="b3da6-136">*生存期*与指示票证有效性的 Kerberos 票证关联。</span><span class="sxs-lookup"><span data-stu-id="b3da6-136">A *lifetime* is associated with the Kerberos ticket that indicates the validity of the ticket.</span></span> <span data-ttu-id="b3da6-137">这样，鉴于滞后时间较长，您将无法确定令牌对于对客户端进行身份验证的服务仍有效。</span><span class="sxs-lookup"><span data-stu-id="b3da6-137">As such, given high latency, you cannot be sure that the token is still valid for the service that authenticates the client.</span></span>  
  
 <span data-ttu-id="b3da6-138">请注意，在使用此凭据类型时，服务必须在 SERVICE 帐户下运行。</span><span class="sxs-lookup"><span data-stu-id="b3da6-138">Note that when using this credential type, the service must be running under the SERVICE account.</span></span>  
  
 <span data-ttu-id="b3da6-139">默认情况下，在选择消息凭据时使用 Kerberos 协议。</span><span class="sxs-lookup"><span data-stu-id="b3da6-139">The Kerberos protocol is used by default when choosing message credential.</span></span>
  
### <a name="username-password"></a><span data-ttu-id="b3da6-140">用户名密码</span><span class="sxs-lookup"><span data-stu-id="b3da6-140">Username Password</span></span>  
 <span data-ttu-id="b3da6-141">使用此属性，可以使用消息安全标头中的用户名密码将客户端向服务器进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b3da6-141">Using this property, the client can authenticate to the server using a username password in the security header of the message.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="b3da6-142">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="b3da6-142">IssuedToken</span></span>  
 <span data-ttu-id="b3da6-143">客户端可以使用安全令牌服务发出随后可以附加到消息中的令牌，以供服务对客户端进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="b3da6-143">The client can use the security token service to issue a token that can then be attached to the message for the service to authenticate the client.</span></span>  
  
## <a name="using-transport-and-message-security"></a><span data-ttu-id="b3da6-144">使用传输安全和消息安全</span><span class="sxs-lookup"><span data-stu-id="b3da6-144">Using Transport and Message Security</span></span>  
 <span data-ttu-id="b3da6-145">在既使用传输安全又使用消息安全时，用于在传输级别和 SOAP 消息级别保护消息的证书必须相同。</span><span class="sxs-lookup"><span data-stu-id="b3da6-145">When using both transport security and message security, the certificate used to secure the message both at the transport and the SOAP message level must be the same.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3da6-146">请参阅</span><span class="sxs-lookup"><span data-stu-id="b3da6-146">See also</span></span>

- [<span data-ttu-id="b3da6-147">使用传输安全保护消息</span><span class="sxs-lookup"><span data-stu-id="b3da6-147">Securing Messages Using Transport Security</span></span>](securing-messages-using-transport-security.md)
- [<span data-ttu-id="b3da6-148">基于消息队列的消息安全性</span><span class="sxs-lookup"><span data-stu-id="b3da6-148">Message Security over Message Queuing</span></span>](../samples/message-security-over-message-queuing.md)
- [<span data-ttu-id="b3da6-149">安全概念</span><span class="sxs-lookup"><span data-stu-id="b3da6-149">Security Concepts</span></span>](security-concepts.md)
- [<span data-ttu-id="b3da6-150">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="b3da6-150">Securing Services and Clients</span></span>](securing-services-and-clients.md)
