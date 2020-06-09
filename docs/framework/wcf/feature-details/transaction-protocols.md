---
title: 事务协议
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: 17131c4cd10d9441ec65f9da4137147a703eb87c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600979"
---
# <a name="transaction-protocols"></a><span data-ttu-id="9ee20-102">事务协议</span><span class="sxs-lookup"><span data-stu-id="9ee20-102">Transaction Protocols</span></span>
<span data-ttu-id="9ee20-103">Windows Communication Foundation （WCF）实现了 WS 原子事务和 WS 协调协议。</span><span class="sxs-lookup"><span data-stu-id="9ee20-103">Windows Communication Foundation (WCF) implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="9ee20-104">规范/文档</span><span class="sxs-lookup"><span data-stu-id="9ee20-104">Specification/Document</span></span>|<span data-ttu-id="9ee20-105">版本</span><span class="sxs-lookup"><span data-stu-id="9ee20-105">Version</span></span>|<span data-ttu-id="9ee20-106">链接</span><span class="sxs-lookup"><span data-stu-id="9ee20-106">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="9ee20-107">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="9ee20-107">WS-Coordination</span></span>|<span data-ttu-id="9ee20-108">1.0</span><span class="sxs-lookup"><span data-stu-id="9ee20-108">1.0</span></span><br /><br /> <span data-ttu-id="9ee20-109">1.1</span><span class="sxs-lookup"><span data-stu-id="9ee20-109">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="9ee20-110">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="9ee20-110">WS-AtomicTransaction</span></span>|<span data-ttu-id="9ee20-111">1.0</span><span class="sxs-lookup"><span data-stu-id="9ee20-111">1.0</span></span><br /><br /> <span data-ttu-id="9ee20-112">1.1</span><span class="sxs-lookup"><span data-stu-id="9ee20-112">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
  
 <span data-ttu-id="9ee20-113">这些协议规范需要在两种级别提供互操作性：在应用程序之间和在事务管理器之间（请参见下图）。</span><span class="sxs-lookup"><span data-stu-id="9ee20-113">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="9ee20-114">规范详细说明两个互操作性级别的消息格式和消息交换。</span><span class="sxs-lookup"><span data-stu-id="9ee20-114">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="9ee20-115">用于应用程序间交换的特定安全性、可靠性和编码与常规应用程序交换一样适用。</span><span class="sxs-lookup"><span data-stu-id="9ee20-115">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="9ee20-116">但是，在事务管理器之间的成功互操作还需要特定绑定的协议，因为它通常不由用户进行配置。</span><span class="sxs-lookup"><span data-stu-id="9ee20-116">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="9ee20-117">本主题说明 WS-Atomic Transaction (WS-AT) 规范与安全性的组合，并说明用于事务管理器间通信的安全绑定。</span><span class="sxs-lookup"><span data-stu-id="9ee20-117">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="9ee20-118">本文档中介绍的方法已经使用 WS-AT 和 WS-Coordination 的其他实现（包括 IBM、IONA、Sun Microsystems 等）成功进行了测试。</span><span class="sxs-lookup"><span data-stu-id="9ee20-118">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="9ee20-119">下图描绘了两个事务管理器：事务管理器1和事务管理器2之间的互操作性，以及两个应用程序：</span><span class="sxs-lookup"><span data-stu-id="9ee20-119">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![显示事务管理器之间的交互的屏幕截图。](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="9ee20-121">假设一个典型的 WS-Coordination/WS-Atomic Transaction 方案具有一个发起方 (I) 和一个参与者 (P)。</span><span class="sxs-lookup"><span data-stu-id="9ee20-121">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="9ee20-122">发起方和参与者都有事务管理器（分别为 ITM 和 PTM）。</span><span class="sxs-lookup"><span data-stu-id="9ee20-122">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="9ee20-123">两阶段提交在本主题中称为 2PC。</span><span class="sxs-lookup"><span data-stu-id="9ee20-123">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ee20-124">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="9ee20-124">1. CreateCoordinationContext</span></span>|<span data-ttu-id="9ee20-125">12. 应用程序消息响应</span><span class="sxs-lookup"><span data-stu-id="9ee20-125">12. Application Message Response</span></span>|  
|<span data-ttu-id="9ee20-126">2. 使用 createcoordinationcontextresponse</span><span class="sxs-lookup"><span data-stu-id="9ee20-126">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="9ee20-127">13. 提交（完成）</span><span class="sxs-lookup"><span data-stu-id="9ee20-127">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="9ee20-128">3. 注册（完成）</span><span class="sxs-lookup"><span data-stu-id="9ee20-128">3. Register (Completion)</span></span>|<span data-ttu-id="9ee20-129">14. 准备（2PC）</span><span class="sxs-lookup"><span data-stu-id="9ee20-129">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="9ee20-130">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="9ee20-130">4. RegisterResponse</span></span>|<span data-ttu-id="9ee20-131">15. 准备（2PC）</span><span class="sxs-lookup"><span data-stu-id="9ee20-131">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="9ee20-132">5. 应用程序消息</span><span class="sxs-lookup"><span data-stu-id="9ee20-132">5. Application Message</span></span>|<span data-ttu-id="9ee20-133">16. 已准备（2PC）</span><span class="sxs-lookup"><span data-stu-id="9ee20-133">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="9ee20-134">6. 带上下文的 CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="9ee20-134">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="9ee20-135">17. 已准备（2PC）</span><span class="sxs-lookup"><span data-stu-id="9ee20-135">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="9ee20-136">7. 注册（持久）</span><span class="sxs-lookup"><span data-stu-id="9ee20-136">7. Register (Durable)</span></span>|<span data-ttu-id="9ee20-137">18. 提交（完成）</span><span class="sxs-lookup"><span data-stu-id="9ee20-137">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="9ee20-138">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="9ee20-138">8. RegisterResponse</span></span>|<span data-ttu-id="9ee20-139">19. 提交（2PC）</span><span class="sxs-lookup"><span data-stu-id="9ee20-139">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="9ee20-140">9. 使用 createcoordinationcontextresponse</span><span class="sxs-lookup"><span data-stu-id="9ee20-140">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="9ee20-141">20. 提交（2PC）</span><span class="sxs-lookup"><span data-stu-id="9ee20-141">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="9ee20-142">10. 注册（持久）</span><span class="sxs-lookup"><span data-stu-id="9ee20-142">10. Register (Durable)</span></span>|<span data-ttu-id="9ee20-143">21. 提交（2PC）</span><span class="sxs-lookup"><span data-stu-id="9ee20-143">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="9ee20-144">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="9ee20-144">11. RegisterResponse</span></span>|<span data-ttu-id="9ee20-145">22. 提交（2PC）</span><span class="sxs-lookup"><span data-stu-id="9ee20-145">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="9ee20-146">本文档说明 WS-AtomicTransaction 规范与安全性的组合，并说明用于事务管理器间通信的安全绑定。</span><span class="sxs-lookup"><span data-stu-id="9ee20-146">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="9ee20-147">本文档中介绍的方法已经使用 WS-AT 和 WS-Coordination 的其他实现成功进行了测试。</span><span class="sxs-lookup"><span data-stu-id="9ee20-147">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="9ee20-148">图和表从安全性的角度演示了四种消息类：</span><span class="sxs-lookup"><span data-stu-id="9ee20-148">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="9ee20-149">激活消息（CreateCoordinationContext 和 CreateCoordinationContextResponse）。</span><span class="sxs-lookup"><span data-stu-id="9ee20-149">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="9ee20-150">注册消息（Register 和 RegisterResponse）</span><span class="sxs-lookup"><span data-stu-id="9ee20-150">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="9ee20-151">协议消息（Prepare、Rollback、Commit、Aborted 等）。</span><span class="sxs-lookup"><span data-stu-id="9ee20-151">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="9ee20-152">应用程序消息。</span><span class="sxs-lookup"><span data-stu-id="9ee20-152">Application messages.</span></span>  
  
 <span data-ttu-id="9ee20-153">前三种消息类可视为事务管理器消息，本主题后面的“应用程序消息交换”将说明它们的绑定配置。</span><span class="sxs-lookup"><span data-stu-id="9ee20-153">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="9ee20-154">第四种消息类是应用程序间消息，本主题后面的“消息示例”一节将对它进行说明。</span><span class="sxs-lookup"><span data-stu-id="9ee20-154">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="9ee20-155">本部分介绍 WCF 使用的每个类的协议绑定。</span><span class="sxs-lookup"><span data-stu-id="9ee20-155">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="9ee20-156">本文档中使用以下 XML 命名空间和关联的前缀。</span><span class="sxs-lookup"><span data-stu-id="9ee20-156">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="9ee20-157">前缀</span><span class="sxs-lookup"><span data-stu-id="9ee20-157">Prefix</span></span>|<span data-ttu-id="9ee20-158">版本</span><span class="sxs-lookup"><span data-stu-id="9ee20-158">Version</span></span>|<span data-ttu-id="9ee20-159">命名空间 URI</span><span class="sxs-lookup"><span data-stu-id="9ee20-159">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="9ee20-160">s11</span><span class="sxs-lookup"><span data-stu-id="9ee20-160">s11</span></span>||<https://schemas.xmlsoap.org/soap/envelope/>|  
|<span data-ttu-id="9ee20-161">wsa</span><span class="sxs-lookup"><span data-stu-id="9ee20-161">wsa</span></span>|<span data-ttu-id="9ee20-162">1.0 之前</span><span class="sxs-lookup"><span data-stu-id="9ee20-162">Pre-1.0</span></span><br /><br /> <span data-ttu-id="9ee20-163">1.0</span><span class="sxs-lookup"><span data-stu-id="9ee20-163">1.0</span></span>|`http://www.w3.org/2004/08/addressing`<br /><br /> <https://www.w3.org/2005/08/addressing/>|  
|<span data-ttu-id="9ee20-164">wscoor</span><span class="sxs-lookup"><span data-stu-id="9ee20-164">wscoor</span></span>|<span data-ttu-id="9ee20-165">1.0</span><span class="sxs-lookup"><span data-stu-id="9ee20-165">1.0</span></span><br /><br /> <span data-ttu-id="9ee20-166">1.1</span><span class="sxs-lookup"><span data-stu-id="9ee20-166">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="9ee20-167">wsat</span><span class="sxs-lookup"><span data-stu-id="9ee20-167">wsat</span></span>|<span data-ttu-id="9ee20-168">1.0</span><span class="sxs-lookup"><span data-stu-id="9ee20-168">1.0</span></span><br /><br /> <span data-ttu-id="9ee20-169">1.1</span><span class="sxs-lookup"><span data-stu-id="9ee20-169">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
|<span data-ttu-id="9ee20-170">t</span><span class="sxs-lookup"><span data-stu-id="9ee20-170">t</span></span>|<span data-ttu-id="9ee20-171">Pre-1.3</span><span class="sxs-lookup"><span data-stu-id="9ee20-171">Pre-1.3</span></span><br /><br /> <span data-ttu-id="9ee20-172">1.3</span><span class="sxs-lookup"><span data-stu-id="9ee20-172">1.3</span></span>|<http://schemas.xmlsoap.org/ws/2005/02/trust/><br /><br /> <https://docs.oasis-open.org/ws-sx/ws-trust/200512>|  
|<span data-ttu-id="9ee20-173">o</span><span class="sxs-lookup"><span data-stu-id="9ee20-173">o</span></span>||<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd>|  
|<span data-ttu-id="9ee20-174">xsd</span><span class="sxs-lookup"><span data-stu-id="9ee20-174">xsd</span></span>||<https://www.w3.org/2001/XMLSchema>|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="9ee20-175">事务管理器绑定</span><span class="sxs-lookup"><span data-stu-id="9ee20-175">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="9ee20-176">R1001：参与 WS-AT 1.0 事务的事务管理器必须使用 SOAP 1.1 和 WS-ADDRESSING 2004/08 来处理 WS 原子事务和 WS 协调消息交换。</span><span class="sxs-lookup"><span data-stu-id="9ee20-176">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="9ee20-177">R1002：参与 WS-AT 1.1 传输的事务管理器必须对 WS-Atomic Transaction 和 WS-Coordination 消息交换使用 SOAP 1.1 和 WS-Addressing 2005/08。</span><span class="sxs-lookup"><span data-stu-id="9ee20-177">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="9ee20-178">应用程序消息并不限于这些绑定，将在后面进行说明。</span><span class="sxs-lookup"><span data-stu-id="9ee20-178">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="9ee20-179">事务管理器 HTTPS 绑定</span><span class="sxs-lookup"><span data-stu-id="9ee20-179">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="9ee20-180">事务管理器 HTTPS 绑定仅依赖于传输安全以在事务树中的每个发送方-接收方对之间实现安全性和建立信任。</span><span class="sxs-lookup"><span data-stu-id="9ee20-180">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="9ee20-181">HTTPS 传输配置</span><span class="sxs-lookup"><span data-stu-id="9ee20-181">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="9ee20-182">X.509 证书用于建立事务管理器标识。</span><span class="sxs-lookup"><span data-stu-id="9ee20-182">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="9ee20-183">要求对客户端/服务器进行身份验证，客户端/服务器授权作为实现详细信息保留：</span><span class="sxs-lookup"><span data-stu-id="9ee20-183">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="9ee20-184">R1111：通过网络提供的 X.509 证书必须具有与发起方计算机的完全限定域名 (FQDN) 匹配的主题名称。</span><span class="sxs-lookup"><span data-stu-id="9ee20-184">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="9ee20-185">B1112：DNS 必须在系统中每个发送方-接收方对之间都有效，才能使 X.509 主题名称检查成功。</span><span class="sxs-lookup"><span data-stu-id="9ee20-185">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="9ee20-186">激活和注册绑定配置</span><span class="sxs-lookup"><span data-stu-id="9ee20-186">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="9ee20-187">WCF 需要通过 HTTPS 相关的请求/答复双工绑定。</span><span class="sxs-lookup"><span data-stu-id="9ee20-187">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="9ee20-188">（有关关联的更多信息和请求/答复消息交换模式的说明，请参见 WS-Atomic Transaction，第 8 节。）</span><span class="sxs-lookup"><span data-stu-id="9ee20-188">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="9ee20-189">2PC 协议绑定配置</span><span class="sxs-lookup"><span data-stu-id="9ee20-189">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="9ee20-190">WCF 通过 HTTPS 支持单向（数据报）消息。</span><span class="sxs-lookup"><span data-stu-id="9ee20-190">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="9ee20-191">消息中的关联作为实现详细信息保留。</span><span class="sxs-lookup"><span data-stu-id="9ee20-191">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="9ee20-192">B1131：实现必须支持 `wsa:ReferenceParameters` ，如 ws-addressing 中所述，以实现 WCF 的2pc 消息的关联。</span><span class="sxs-lookup"><span data-stu-id="9ee20-192">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="9ee20-193">事务管理器混合安全绑定</span><span class="sxs-lookup"><span data-stu-id="9ee20-193">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="9ee20-194">这是一个备选（混合模式）绑定，它使用传输安全和 WS-Coordination 颁发的令牌模型的组合来实现建立标识的目的。</span><span class="sxs-lookup"><span data-stu-id="9ee20-194">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="9ee20-195">激活和注册是在两个绑定间存在差异的仅有元素。</span><span class="sxs-lookup"><span data-stu-id="9ee20-195">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="9ee20-196">HTTPS 传输配置</span><span class="sxs-lookup"><span data-stu-id="9ee20-196">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="9ee20-197">X.509 证书用于建立事务管理器标识。</span><span class="sxs-lookup"><span data-stu-id="9ee20-197">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="9ee20-198">要求对客户端/服务器进行身份验证，客户端/服务器授权作为实现详细信息保留。</span><span class="sxs-lookup"><span data-stu-id="9ee20-198">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="9ee20-199">激活消息绑定配置</span><span class="sxs-lookup"><span data-stu-id="9ee20-199">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="9ee20-200">激活消息通常不参与互操作，因为他们一般出现在应用程序及其本地事务管理器之间。</span><span class="sxs-lookup"><span data-stu-id="9ee20-200">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="9ee20-201">B1221：对于激活消息，WCF 使用双工 HTTPS 绑定（在[消息协议](messaging-protocols.md)中进行了描述）。</span><span class="sxs-lookup"><span data-stu-id="9ee20-201">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="9ee20-202">使用 WS-Addressing 2004/08（针对 WS-AT 1.0）和 WS-Addressing 2005/08（针对 WS-AT 1.1）关联请求和答复消息。</span><span class="sxs-lookup"><span data-stu-id="9ee20-202">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="9ee20-203">WS-Atomic Transaction 规范第 8 节更详尽地说明了关联和消息交换模式。</span><span class="sxs-lookup"><span data-stu-id="9ee20-203">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="9ee20-204">R1222：接收到 `CreateCoordinationContext` 后，协调程序必须颁发与机密 `SecurityContextToken` 关联的 `STx`。</span><span class="sxs-lookup"><span data-stu-id="9ee20-204">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="9ee20-205">在遵循 WS-Trust 规范的 `t:IssuedTokens` 标头中返回此令牌。</span><span class="sxs-lookup"><span data-stu-id="9ee20-205">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="9ee20-206">R1223：如果激活出现在现有的协调上下文中，则具有与现有上下文关联的 `t:IssuedTokens` 的 `SecurityContextToken` 标头必须对 `CreateCoordinationContext` 消息进行流处理。</span><span class="sxs-lookup"><span data-stu-id="9ee20-206">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="9ee20-207">`t:IssuedTokens`应生成新的标头以附加到传出 `wscoor:CreateCoordinationContextResponse` 消息。</span><span class="sxs-lookup"><span data-stu-id="9ee20-207">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="9ee20-208">注册消息绑定配置</span><span class="sxs-lookup"><span data-stu-id="9ee20-208">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="9ee20-209">B1231： WCF 使用双工 HTTPS 绑定（在[消息协议](messaging-protocols.md)中介绍）。</span><span class="sxs-lookup"><span data-stu-id="9ee20-209">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](messaging-protocols.md)).</span></span> <span data-ttu-id="9ee20-210">使用 WS-Addressing 2004/08（针对 WS-AT 1.0）和 WS-Addressing 2005/08（针对 WS-AT 1.1）关联请求和答复消息。</span><span class="sxs-lookup"><span data-stu-id="9ee20-210">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="9ee20-211">WS-AtomicTransaction 第 8 节更详尽地说明了关联和消息交换模式。</span><span class="sxs-lookup"><span data-stu-id="9ee20-211">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="9ee20-212">R1232：传出 `wscoor:Register` 消息必须使用 `IssuedTokenOverTransport` [安全协议](security-protocols.md)中描述的身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="9ee20-212">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](security-protocols.md).</span></span>  
  
 <span data-ttu-id="9ee20-213">`wsse:Timestamp`元素必须使用发出的进行签名 `SecurityContextToken STx` 。</span><span class="sxs-lookup"><span data-stu-id="9ee20-213">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="9ee20-214">此签名是拥有与特定事务关联的令牌的证明，用于对登记事务的参与者进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="9ee20-214">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="9ee20-215">RegistrationResponse 消息通过 HTTPS 发回。</span><span class="sxs-lookup"><span data-stu-id="9ee20-215">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="9ee20-216">2PC 协议绑定配置</span><span class="sxs-lookup"><span data-stu-id="9ee20-216">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="9ee20-217">WCF 通过 HTTPS 支持单向（数据报）消息。</span><span class="sxs-lookup"><span data-stu-id="9ee20-217">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="9ee20-218">消息中的关联作为实现详细信息保留。</span><span class="sxs-lookup"><span data-stu-id="9ee20-218">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="9ee20-219">B1241：实现必须支持 `wsa:ReferenceParameters` ，如 ws-addressing 中所述，以实现 WCF 的2pc 消息的关联。</span><span class="sxs-lookup"><span data-stu-id="9ee20-219">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="9ee20-220">应用程序消息交换</span><span class="sxs-lookup"><span data-stu-id="9ee20-220">Application Message Exchange</span></span>  
 <span data-ttu-id="9ee20-221">只要绑定满足下面的安全要求，应用程序就可以对应用程序间消息随意使用任何特定的绑定：</span><span class="sxs-lookup"><span data-stu-id="9ee20-221">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="9ee20-222">R2001：应用程序间消息必须对 `t:IssuedTokens` 标头与消息头中的 `CoordinationContext` 一起进行流处理。</span><span class="sxs-lookup"><span data-stu-id="9ee20-222">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="9ee20-223">R2002：必须提供 `t:IssuedToken` 的完整性和保密性。</span><span class="sxs-lookup"><span data-stu-id="9ee20-223">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="9ee20-224">`CoordinationContext` 标头包含 `wscoor:Identifier`。</span><span class="sxs-lookup"><span data-stu-id="9ee20-224">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="9ee20-225">尽管的定义 `xsd:AnyURI` 允许使用绝对和相对 uri，但 WCF 仅支持 `wscoor:Identifiers` 绝对 uri。</span><span class="sxs-lookup"><span data-stu-id="9ee20-225">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="9ee20-226">B2003：如果的 `wscoor:Identifier` `wscoor:CoordinationContext` 是相对 URI，则将从事务性 WCF 服务返回错误。</span><span class="sxs-lookup"><span data-stu-id="9ee20-226">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="9ee20-227">消息示例</span><span class="sxs-lookup"><span data-stu-id="9ee20-227">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="9ee20-228">CreateCoordinationContext 请求/响应消息</span><span class="sxs-lookup"><span data-stu-id="9ee20-228">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="9ee20-229">下面的消息遵循请求/响应模式。</span><span class="sxs-lookup"><span data-stu-id="9ee20-229">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="9ee20-230">CreateCoordinationContext with WSCoor 1。0</span><span class="sxs-lookup"><span data-stu-id="9ee20-230">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wscoor/CreateCoordinationContext</Action>  
    <a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
    <a:ReplyTo>  
      <Address>https://...</a:Address>  
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security>  
      <u:Timestamp>  
        <wsu:Created>2005-12-15T23:36:09.921Z</wsu:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</wsu:Expires>  
      </u:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:CreateCoordinationContext>  
      <wscoor:CoordinationType>...</wscoor:CoordinationType>  
    </wscoor:CreateCoordinationContext>  
  </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="9ee20-231">使用 WSCoor 1.1 的 CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="9ee20-231">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>
<s:Header>  
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContext</Action>  
<a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
<a:ReplyTo>
<Address>https://...</a:Address>
</a:ReplyTo>
<a:To>https://...</a:To>
<wsse:Security>  
 <u:Timestamp>  
<wsu:Created>2005-12-15T23:36:09.921Z</wsu:Created>  
<wsu:Expires>2005-12-15T23:41:09.921Z</wsu:Expires>  
</u:Timestamp>
</wsse:Security>
</s:Header>
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
<wscoor:CreateCoordinationContext>  
<wscoor:CoordinationType>...</wscoor:CoordinationType>  
</wscoor:CreateCoordinationContext>  
 </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="9ee20-232">使用 Trust Pre-1.3 和 WSCoor 1.0 的 CreateCoordinationContextResponse </span><span class="sxs-lookup"><span data-stu-id="9ee20-232">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <!-- Data below is shown in the clear for  
       illustration purposes only. -->  
  <s:Header>  
    <a:Action>./ws/2004/10/wscoor/CreateCoordinationContextResponse </a:Action>  
    <a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
    <a:To s:mustUnderstand="1">https://... </a:To>  
    <t:IssuedTokens>  
 <wst:RequestSecurityTokenResponse
    xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
    xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
    xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
    xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
    xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
    <wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
    <wst:RequestedSecurityToken>  
      <wsc:SecurityContextToken>  
        <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
        </wssu:Identifier>  
      </wsc:SecurityContextToken>
    </wst:RequestedSecurityToken>  
    <wsp:AppliesTo>  
        http://fabrikam123.com/CCi  
    </wsp:AppliesTo>
    <wst:RequestedAttachedReference>  
      <wsse:SecurityTokenReference >  
        <wsse:Reference
           ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
           URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedAttachedReference>  
    <wst:RequestedUnattachedReference>  
      <wsse:SecurityTokenReference>  
        <wsse:Reference
          ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
          URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedUnattachedReference>  
    <wst:RequestedProofToken>  
      <wst:BinarySecret
        Type="http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey">  
        <!-- base64 encoded value -->  
      </wst:BinarySecret>  
    </wst:RequestedProofToken>  
    <wst:Lifetime>  
      <wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
      <wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
    </wst:Lifetime>  
    <wst:KeySize>256</wst:KeySize>  
</wst:RequestSecurityTokenResponse>  
    </t:IssuedTokens>  
    <o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="_0">  
        <u:Created>2005-12-15T23:36:12.015Z</u:Created>  
        <u:Expires>2005-12-15T23:41:12.015Z</u:Expires>  
      </u:Timestamp>  
    </o:Security>  
  </s:Header>  
  <s:Body>  
    <wscoor:CreateCoordinationContextResponse>  
      <wscoor:CoordinationContext>  
        <wscoor:Identifier>  
     http://fabrikam123.com/CCi  
      </wscoor:Identifier>  
        <wscoor:Expires>...</wscoor:Expires>  
        <wscoor:CoordinationType>...</wscoor:CoordinationType>  
        <wscoor:RegistrationService>  
          <a:Address>https://...</a:Address>  
          <a:ReferenceParameters>  
             ...  
          </a:ReferenceParameters>  
        </wscoor:RegistrationService>  
      </wscoor:CoordinationContext>  
    </wscoor:CreateCoordinationContextResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="9ee20-233">使用 Trust 1.3 和 WSCoor 1.1 的 CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="9ee20-233">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<!-- Data below is shown in the clear for illustration purposes only. -->
<s:Header>
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContextResponse </a:Action>  
<a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
<a:To s:mustUnderstand="1">https://... </a:To>
<t:IssuedTokens>
<wst:RequestSecurityTokenResponse
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"
xmlns:wst="http://docs.oasis-open.org/ws-sx/ws-trust/200512"  
xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
<wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
<wst:RequestedSecurityToken>
<wsc:SecurityContextToken>
<wssu:Identifier> http://fabrikam123.com/SCTi  
</wssu:Identifier>
</wsc:SecurityContextToken>
</wst:RequestedSecurityToken>
<wsp:AppliesTo> http://fabrikam123.com/CCi </wsp:AppliesTo>  
<wst:RequestedAttachedReference>
<wsse:SecurityTokenReference >
<wsse:Reference  
  ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
  URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>
</wst:RequestedAttachedReference>
<wst:RequestedUnattachedReference>
<wsse:SecurityTokenReference>
<wsse:Reference  
 ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
 URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>
</wst:RequestedUnattachedReference>
<wst:RequestedProofToken>
<wst:BinarySecret  
  Type="http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey">  
  <!-- base64 encoded value -->
</wst:BinarySecret>
</wst:RequestedProofToken>
<wst:Lifetime>
<wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
<wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
</wst:Lifetime>
<wst:KeySize>256</wst:KeySize>
</wst:RequestSecurityTokenResponse>
</t:IssuedTokens>
<o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
<u:Timestamp u:Id="_0">
<u:Created>2005-12-15T23:36:12.015Z</u:Created>
<u:Expires>2005-12-15T23:41:12.015Z</u:Expires>
</u:Timestamp>
</o:Security>
</s:Header>
<s:Body>
<wscoor:CreateCoordinationContextResponse>
<wscoor:CoordinationContext>
<wscoor:Identifier> http://fabrikam123.com/CCi  
</wscoor:Identifier>
<wscoor:Expires>...</wscoor:Expires>  
<wscoor:CoordinationType>...</wscoor:CoordinationType>  
<wscoor:RegistrationService>
<a:Address>https://...</a:Address>  
<a:ReferenceParameters> ...  
</a:ReferenceParameters>  
</wscoor:RegistrationService>
</wscoor:CoordinationContext>
</wscoor:CreateCoordinationContextResponse>
</s:Body>
</s:Envelope>  
```  
  
### <a name="registration-messages"></a><span data-ttu-id="9ee20-234">注册消息</span><span class="sxs-lookup"><span data-stu-id="9ee20-234">Registration Messages</span></span>  
 <span data-ttu-id="9ee20-235">下面的消息是注册消息。</span><span class="sxs-lookup"><span data-stu-id="9ee20-235">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="9ee20-236">注册到 WSCoor 1。0</span><span class="sxs-lookup"><span data-stu-id="9ee20-236">Register with WSCoor 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://schemas.xmlsoap.org/ws/2004/10/wscoor/Register</a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>https://...</a:Address>
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsc:SecurityContextToken>  
      <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
      </wssu:Identifier>  
      </wsc:SecurityContextToken>  
      <!-- supporting signature over the timestamp -->  
      <wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
        <ds:SignedInfo>  
          <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
          <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>  
          <ds:Reference URI="#_0">  
            <ds:Transforms>  
              <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
            </ds:Transforms>  
            <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>  
            <ds:DigestValue>  
              alRzyhjLgoUOYoh8cx4n75eTcUk=  
            </ds:DigestValue>  
          </ds:Reference>  
        </ds:SignedInfo>  
        <ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=</ds:SignatureValue>  
        <ds:KeyInfo>  
          <wsse:SecurityTokenReference  
            xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
            <wsse:Reference
              URI="http://fabrikam123.com/SCTi"/>  
          </wsse:SecurityTokenReference>  
        </ds:KeyInfo>  
      </wsse:Signature>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:Register>  
      <wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
      <wscoor:ParticipantProtocolService>  
        <a:Address>https://... </a:Address>  
      </wscoor:ParticipantProtocolService>  
    </wscoor:Register>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="9ee20-237">使用 WSCoor 1.1 注册</span><span class="sxs-lookup"><span data-stu-id="9ee20-237">Register with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/Register</a:Action>
<a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
<a:ReplyTo>
<a:Address>https://...</a:Address>
</a:ReplyTo>  
<a:To>https://...</a:To>
<wsse:Security
s:mustUnderstand="1"
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wssu:Timestamp wssu:Id="_0" >
<wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
<wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
</wssu:Timestamp>
<wsc:SecurityContextToken>
<wssu:Identifier> http://fabrikam123.com/SCTi  
</wssu:Identifier>
</wsc:SecurityContextToken>
<!-- supporting signature over the timestamp -->  
<wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
<ds:SignedInfo>
<ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
<ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>
<ds:Reference URI="#_0">
<ds:Transforms>
<ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
</ds:Transforms>
<ds:DigestMethod  
Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
<ds:DigestValue> alRzyhjLgoUOYoh8cx4n75eTcUk=  
</ds:DigestValue>
</ds:Reference>
</ds:SignedInfo>  
<ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=  
</ds:SignatureValue>  
<ds:KeyInfo>
<wsse:SecurityTokenReference xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
  <wsse:Reference URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>
</ds:KeyInfo>
</wsse:Signature>
</wsse:Security>
</s:Header>
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
<wscoor:Register>
<wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
<wscoor:ParticipantProtocolService>
<a:Address>https://... </a:Address>  
</wscoor:ParticipantProtocolService>
</wscoor:Register>
</s:Body>
</s:Envelope>  
```  
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="9ee20-238">注册 WSCoor 1.0 的响应</span><span class="sxs-lookup"><span data-stu-id="9ee20-238">Register Response with WSCoor 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>  
      http://schemas.xmlsoap.org/ws/2004/10/wscoor/RegisterResponse  
    </a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
    <a:RelatesTo>  
      urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e
    </a:RelatesTo>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp>  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:RegisterResponse>  
      <wscoor:CoordinatorProtocolService>  
        <a:Address>https://...</a:Address>  
        <a:ReferenceParameters>  
          ...  
        </a:ReferenceParameters>  
      </wscoor:CoordinatorProtocolService>  
    </wscoor:RegisterResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="9ee20-239">使用 WSCoor 1.1 的注册响应</span><span class="sxs-lookup"><span data-stu-id="9ee20-239">Register Response with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>
<a:Action> http://docs.oasis-open.org/ws-tx/wscoor/2006/06/RegisterResponse  
</a:Action>
<a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
<a:RelatesTo> urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e </a:RelatesTo>  
<a:To>https://...</a:To>
<wsse:Security
s:mustUnderstand="1"
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
<wssu:Timestamp>
<wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
<wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
</wssu:Timestamp>
</wsse:Security>
</s:Header>
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
<wscoor:RegisterResponse>
<wscoor:CoordinatorProtocolService>  
<a:Address>https://...</a:Address>  
<a:ReferenceParameters> ... </a:ReferenceParameters>  
</wscoor:CoordinatorProtocolService>
</wscoor:RegisterResponse>
</s:Body>
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="9ee20-240">两阶段提交协议消息</span><span class="sxs-lookup"><span data-stu-id="9ee20-240">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="9ee20-241">下面的消息与两阶段提交 (2PC) 协议相关。</span><span class="sxs-lookup"><span data-stu-id="9ee20-241">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="9ee20-242">WSAT 1.0 的提交</span><span class="sxs-lookup"><span data-stu-id="9ee20-242">Commit with WSAT 1.0</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wsat/Commit</a:Action>  
    <a:To>https://...</a:To>  
    <wsse:Security
      s:mustUnderstand="1"
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
   </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wsat:Commit />  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="9ee20-243">使用 WSAT 1.1 提交</span><span class="sxs-lookup"><span data-stu-id="9ee20-243">Commit with WSAT 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>
<a:Action>http://docs.oasis-open.org/ws-tx/wsat/2006/06</a:Action>  
<a:To>https://...</a:To>
<wsse:Security
s:mustUnderstand="1"
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
<wssu:Timestamp wssu:Id="_0" >
<wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
<wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
</wssu:Timestamp>
</wsse:Security>
</s:Header>
<s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
<wsat:Commit />
</s:Body>
</s:Envelope>  
```  
  
### <a name="application-messages"></a><span data-ttu-id="9ee20-244">应用程序消息。</span><span class="sxs-lookup"><span data-stu-id="9ee20-244">Application Messages</span></span>  
 <span data-ttu-id="9ee20-245">下面的消息是应用程序消息。</span><span class="sxs-lookup"><span data-stu-id="9ee20-245">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="9ee20-246">应用程序消息请求</span><span class="sxs-lookup"><span data-stu-id="9ee20-246">Application message-Request</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
<!-- Addressing headers, all signed-->  
    <wsse:Security s:mustUnderstand="1">  
      <wssu:Timestamp wssu:Id="timestamp">
        <wssu:Created>2005-10-25T06:29:18.703Z</wssu:Created>  
        <wssu:Expires>2005-10-25T06:34:18.703Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsse:BinarySecurityToken
          wssu:Id="IA_Certificate"
          ValueType="...#X509v3"
          EncodingType="...#Base64Binary">  
        <!-- IA certificate -->  
      </wsse:BinarySecurityToken>  
      <e:EncryptedKey Id="encrypted_key">  
            <!-- ephemeral key encrypted for PA certificate -->
        <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
          <e:DataReference URI="#encrypted_body"/>  
          <e:DataReference URI="#encrypted_CCi"/>  
          <e:DataReference URI="#encrypted_issuedtokens"/>  
        </e:ReferenceList>  
      </e:EncryptedKey>  
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <!-- signature over Addressing headers, Timestamp, and Body -->  
      </Signature>  
    </wsse:Security>  
    <wsse11:EncryptedHeader>  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader>
      <!-- encrypted wst:IssuedTokens header containing SCTi -->  
      <!-- wst:IssuedTokens header is taken verbatim from message #2 above, omitted for brevity -->  
    </wsse11:EncryptedHeader>  
  </s:Header>  
  <s:Body wssu:Id="body">  
    <!-- encrypted content of the Body element of the application message -->
    <e:EncryptedData Id="encrypted_body"
           Type="http://www.w3.org/2001/04/xmlenc#Content"
           xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
...  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
```
