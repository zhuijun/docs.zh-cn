---
title: 安全会话
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: cb02adc7514e27175088e7664b12e45bc8ca5cd9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590080"
---
# <a name="secure-sessions"></a><span data-ttu-id="361b7-102">安全会话</span><span class="sxs-lookup"><span data-stu-id="361b7-102">Secure Sessions</span></span>
<span data-ttu-id="361b7-103">Windows Communication Foundation （WCF）的一项功能是可靠会话，可保证按消息发送顺序接收消息。</span><span class="sxs-lookup"><span data-stu-id="361b7-103">A feature of Windows Communication Foundation (WCF) is reliable sessions that guarantee messages are received in the order they were sent.</span></span> <span data-ttu-id="361b7-104">本节中的主题讨论在创建可靠会话时要考虑的安全性问题。</span><span class="sxs-lookup"><span data-stu-id="361b7-104">The topics in this section discuss the security implications to consider when creating a reliable session.</span></span> <span data-ttu-id="361b7-105">有关可靠会话的详细信息，请参阅[使用会话](../using-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="361b7-105">For more information about reliable sessions, see [Using Sessions](../using-sessions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="361b7-106">当需要在 Windows XP 上进行模拟时，请不要在安全会话中使用有状态安全令牌上下文 (SCT)。</span><span class="sxs-lookup"><span data-stu-id="361b7-106">When impersonation is required on Windows XP, use a secure session without a stateful security context token (SCT).</span></span> <span data-ttu-id="361b7-107">如果在模拟时使用有状态 SCT，则会引发 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="361b7-107">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="361b7-108">有关详细信息，请参阅[不支持的方案](unsupported-scenarios.md)。</span><span class="sxs-lookup"><span data-stu-id="361b7-108">For more information, see [Unsupported Scenarios](unsupported-scenarios.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="361b7-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="361b7-109">In This Section</span></span>  
  
|||  
|-|-|  
|[<span data-ttu-id="361b7-110">安全对话和安全会话</span><span class="sxs-lookup"><span data-stu-id="361b7-110">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)|<span data-ttu-id="361b7-111">安全对话和安全会话是同义词。</span><span class="sxs-lookup"><span data-stu-id="361b7-111">Secure conversations and secure sessions are synonymous.</span></span> <span data-ttu-id="361b7-112">本主题解释安全对话的工作方式以及使用该模式的时机和原因。</span><span class="sxs-lookup"><span data-stu-id="361b7-112">This topic explains the way a secure conversation works, and when and why to use the pattern.</span></span>|  
|[<span data-ttu-id="361b7-113">如何：创建安全会话</span><span class="sxs-lookup"><span data-stu-id="361b7-113">How to: Create a Secure Session</span></span>](how-to-create-a-secure-session.md)|<span data-ttu-id="361b7-114">演练创建安全会话的基本操作。</span><span class="sxs-lookup"><span data-stu-id="361b7-114">Walks through of the basics of creating a secure session.</span></span>|  
|[<span data-ttu-id="361b7-115">如何：为安全会话创建安全上下文令牌</span><span class="sxs-lookup"><span data-stu-id="361b7-115">How to: Create a Security Context Token for a Secure Session</span></span>](how-to-create-a-security-context-token-for-a-secure-session.md)|<span data-ttu-id="361b7-116">演练创建能够保持状态以及与客户端之间会话的网络场的步骤。</span><span class="sxs-lookup"><span data-stu-id="361b7-116">Walks through the steps of creating a Web farm that will maintain state and sessions with clients.</span></span>|  
|[<span data-ttu-id="361b7-117">安全会话的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="361b7-117">Security Considerations for Secure Sessions</span></span>](security-considerations-for-secure-sessions.md)|<span data-ttu-id="361b7-118">描述安全会话的特殊注意事项。</span><span class="sxs-lookup"><span data-stu-id="361b7-118">Describes special considerations for secure sessions.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="361b7-119">参考</span><span class="sxs-lookup"><span data-stu-id="361b7-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="361b7-120">相关章节</span><span class="sxs-lookup"><span data-stu-id="361b7-120">Related Sections</span></span>  
 [<span data-ttu-id="361b7-121">会话、实例化和并发</span><span class="sxs-lookup"><span data-stu-id="361b7-121">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)  
  
 [<span data-ttu-id="361b7-122">设计和实现服务</span><span class="sxs-lookup"><span data-stu-id="361b7-122">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="361b7-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="361b7-123">See also</span></span>

- [<span data-ttu-id="361b7-124">如何：启用消息重放检测</span><span class="sxs-lookup"><span data-stu-id="361b7-124">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)
- [<span data-ttu-id="361b7-125">重播攻击</span><span class="sxs-lookup"><span data-stu-id="361b7-125">Replay Attacks</span></span>](replay-attacks.md)
- [<span data-ttu-id="361b7-126">如何：创建要求会话的服务</span><span class="sxs-lookup"><span data-stu-id="361b7-126">How to: Create a Service That Requires Sessions</span></span>](how-to-create-a-service-that-requires-sessions.md)
