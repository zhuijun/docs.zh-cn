---
title: 使用自定义绑定的安全功能
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 48d17543f2b133c74bcfa82cfe1a2a0de28b1d01
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595188"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="25f91-102">使用自定义绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="25f91-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="25f91-103">使用系统提供的绑定之一，可以执行最常见的安全任务。</span><span class="sxs-lookup"><span data-stu-id="25f91-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="25f91-104">但是，如果你需要更多控制权，则可以使用 <xref:System.ServiceModel.Channels.SecurityBindingElement> 创建自定义绑定，如以下这些主题中所介绍。</span><span class="sxs-lookup"><span data-stu-id="25f91-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="25f91-105">有关自定义绑定的详细信息，请参阅[自定义绑定](../extending/custom-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="25f91-105">For more information about custom bindings, see [Custom Bindings](../extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="25f91-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="25f91-106">In This Section</span></span>  
 [<span data-ttu-id="25f91-107">SecurityBindingElement 身份验证模式</span><span class="sxs-lookup"><span data-stu-id="25f91-107">SecurityBindingElement Authentication Modes</span></span>](securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="25f91-108">介绍可能用于自定义绑定的身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="25f91-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="25f91-109">如何：使用 SecurityBindingElement 创建自定义绑定</span><span class="sxs-lookup"><span data-stu-id="25f91-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="25f91-110">介绍创建带有安全元素的自定义绑定的基本步骤。</span><span class="sxs-lookup"><span data-stu-id="25f91-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="25f91-111">如何：为指定的身份验证模式创建 SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="25f91-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="25f91-112">介绍如何为指定身份验证模式创建安全元素。</span><span class="sxs-lookup"><span data-stu-id="25f91-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="25f91-113">如何：在 WSFederationHttpBinding 上禁用安全会话</span><span class="sxs-lookup"><span data-stu-id="25f91-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="25f91-114">介绍如何在创建联合服务时禁用安全会话。</span><span class="sxs-lookup"><span data-stu-id="25f91-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="25f91-115">如何：启用消息重放检测</span><span class="sxs-lookup"><span data-stu-id="25f91-115">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="25f91-116">介绍如何确定重放攻击出现的时间。</span><span class="sxs-lookup"><span data-stu-id="25f91-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="25f91-117">如何：创建支持凭据</span><span class="sxs-lookup"><span data-stu-id="25f91-117">How to: Create a Supporting Credential</span></span>](how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="25f91-118">介绍如何向服务提供支持凭据（如果服务要求）。</span><span class="sxs-lookup"><span data-stu-id="25f91-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="25f91-119">如何：设置签名确认</span><span class="sxs-lookup"><span data-stu-id="25f91-119">How to: Set Up a Signature Confirmation</span></span>](how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="25f91-120">介绍在对消息进行数字签名时确认签名的步骤。</span><span class="sxs-lookup"><span data-stu-id="25f91-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="25f91-121">如何：设置最大时钟偏差</span><span class="sxs-lookup"><span data-stu-id="25f91-121">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="25f91-122">介绍如何设置服务与客户端之间所允许的最大时间差。</span><span class="sxs-lookup"><span data-stu-id="25f91-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="25f91-123">如何：禁用数字签名的加密</span><span class="sxs-lookup"><span data-stu-id="25f91-123">How to: Disable Encryption of Digital Signatures</span></span>](how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="25f91-124">介绍禁用对数字签名的加密能提高性能的方式。</span><span class="sxs-lookup"><span data-stu-id="25f91-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="25f91-125">参考</span><span class="sxs-lookup"><span data-stu-id="25f91-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="25f91-126">相关章节</span><span class="sxs-lookup"><span data-stu-id="25f91-126">Related Sections</span></span>  
 [<span data-ttu-id="25f91-127">了解保护级别</span><span class="sxs-lookup"><span data-stu-id="25f91-127">Understanding Protection Level</span></span>](../understanding-protection-level.md)  
  
 [<span data-ttu-id="25f91-128">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="25f91-128">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="25f91-129">另请参阅</span><span class="sxs-lookup"><span data-stu-id="25f91-129">See also</span></span>

- [<span data-ttu-id="25f91-130">绑定与安全</span><span class="sxs-lookup"><span data-stu-id="25f91-130">Bindings and Security</span></span>](bindings-and-security.md)
- [<span data-ttu-id="25f91-131">安全性概述</span><span class="sxs-lookup"><span data-stu-id="25f91-131">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="25f91-132">系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="25f91-132">System-Provided Bindings</span></span>](../system-provided-bindings.md)
