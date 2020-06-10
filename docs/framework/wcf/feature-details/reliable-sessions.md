---
title: 可靠会话
ms.date: 03/30/2017
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
ms.openlocfilehash: 910ad952192243c6aa8a79417ad711d8c2a4ba2e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590535"
---
# <a name="reliable-sessions"></a><span data-ttu-id="8f47f-102">可靠会话</span><span class="sxs-lookup"><span data-stu-id="8f47f-102">Reliable Sessions</span></span>

<span data-ttu-id="8f47f-103">本部分介绍什么是 Windows Communication Foundation （WCF）可靠会话、其用途、使用方式、使用方式、使用的绑定配置以及最佳实践的指针。</span><span class="sxs-lookup"><span data-stu-id="8f47f-103">This section describes what a Windows Communication Foundation (WCF) reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="8f47f-104">下表汇总了有关本节中要点和相关主题的详细信息。</span><span class="sxs-lookup"><span data-stu-id="8f47f-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="8f47f-105">可靠会话 WCF 提供的功能可确保在终结点之间发送的消息在 SOAP 或传输中介之间传输，并且只传递一次，并根据发送的相同顺序进行传递。</span><span class="sxs-lookup"><span data-stu-id="8f47f-105">The reliable session WCF provides features ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="8f47f-106">若要对 WCF 应用程序使用可靠会话，请使用 WCF 中某个系统提供的绑定（默认情况下支持可靠会话）或作为选项，或创建你自己的支持会话的自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="8f47f-106">To use a reliable session with a WCF application, either use one of the system-provided bindings in WCF that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8f47f-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="8f47f-107">In This Section</span></span>

<span data-ttu-id="8f47f-108">[可靠会话概述](reliable-sessions-overview.md)介绍可靠会话、何时使用它们、支持可靠会话的不同绑定，以及它们的工作方式。</span><span class="sxs-lookup"><span data-stu-id="8f47f-108">[Reliable Sessions Overview](reliable-sessions-overview.md) Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="8f47f-109">[如何：在可靠会话内交换消息](how-to-exchange-messages-within-a-reliable-session.md)介绍如何使用配置中指定的自定义绑定通过 HTTP 创建可靠会话。</span><span class="sxs-lookup"><span data-stu-id="8f47f-109">[How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md) Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="8f47f-110">[如何：在可靠会话内保护消息](how-to-secure-messages-within-reliable-sessions.md)介绍如何保护可靠会话。</span><span class="sxs-lookup"><span data-stu-id="8f47f-110">[How to: Secure Messages within Reliable Sessions](how-to-secure-messages-within-reliable-sessions.md) Describes how to secure a reliable session.</span></span>

<span data-ttu-id="8f47f-111">[如何：使用 HTTPS 创建自定义可靠会话绑定](how-to-create-a-custom-reliable-session-binding-with-https.md)介绍如何通过 HTTPS 创建可靠会话。</span><span class="sxs-lookup"><span data-stu-id="8f47f-111">[How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="8f47f-112">[可靠会话的最佳做法](best-practices-for-reliable-sessions.md)介绍与使用可靠会话相关的一些最佳实践。</span><span class="sxs-lookup"><span data-stu-id="8f47f-112">[Best Practices for Reliable Sessions](best-practices-for-reliable-sessions.md) Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="8f47f-113">参考</span><span class="sxs-lookup"><span data-stu-id="8f47f-113">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="8f47f-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="8f47f-114">See also</span></span>

- [<span data-ttu-id="8f47f-115">队列和可靠会话</span><span class="sxs-lookup"><span data-stu-id="8f47f-115">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)
- [<span data-ttu-id="8f47f-116">会话、实例化和并发</span><span class="sxs-lookup"><span data-stu-id="8f47f-116">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)
