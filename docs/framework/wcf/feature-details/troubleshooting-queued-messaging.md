---
title: 排队消息处理疑难解答
ms.date: 03/30/2017
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
ms.openlocfilehash: f695af3d2ad498e1f5975e1a396f1e7b05bf63bc
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595123"
---
# <a name="troubleshooting-queued-messaging"></a><span data-ttu-id="fad3a-102">排队消息处理疑难解答</span><span class="sxs-lookup"><span data-stu-id="fad3a-102">Troubleshooting Queued Messaging</span></span>

<span data-ttu-id="fad3a-103">本部分包含有关在 Windows Communication Foundation （WCF）中使用队列的常见问题和故障排除帮助。</span><span class="sxs-lookup"><span data-stu-id="fad3a-103">This section contains common questions and troubleshooting help for using queues in Windows Communication Foundation (WCF).</span></span>

## <a name="common-questions"></a><span data-ttu-id="fad3a-104">常见问题</span><span class="sxs-lookup"><span data-stu-id="fad3a-104">Common Questions</span></span>

<span data-ttu-id="fad3a-105">**问：** 我使用了 WCF Beta 1 并安装了 MSMQ 修补程序。</span><span class="sxs-lookup"><span data-stu-id="fad3a-105">**Q:** I used WCF Beta 1 and I installed the MSMQ hotfix.</span></span> <span data-ttu-id="fad3a-106">现在，是否需要移除此修补程序？</span><span class="sxs-lookup"><span data-stu-id="fad3a-106">Do I need to remove the hotfix?</span></span>

<span data-ttu-id="fad3a-107">**答:** 是的。</span><span class="sxs-lookup"><span data-stu-id="fad3a-107">**A:** Yes.</span></span> <span data-ttu-id="fad3a-108">此修补程序不再受支持。</span><span class="sxs-lookup"><span data-stu-id="fad3a-108">This hotfix is no longer supported.</span></span> <span data-ttu-id="fad3a-109">WCF 现在可以在没有修补程序要求的情况下运行 MSMQ。</span><span class="sxs-lookup"><span data-stu-id="fad3a-109">WCF now works on MSMQ without a hotfix requirement.</span></span>

<span data-ttu-id="fad3a-110">**问：** MSMQ：和有两个绑定 <xref:System.ServiceModel.NetMsmqBinding> <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 。</span><span class="sxs-lookup"><span data-stu-id="fad3a-110">**Q:** There are two bindings for MSMQ: <xref:System.ServiceModel.NetMsmqBinding> and <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span> <span data-ttu-id="fad3a-111">我应该使用哪一种绑定以及在什么情况下使用？</span><span class="sxs-lookup"><span data-stu-id="fad3a-111">What should I use and when?</span></span>

<span data-ttu-id="fad3a-112">**答：**<xref:System.ServiceModel.NetMsmqBinding>当你希望使用 MSMQ 作为两个 WCF 应用程序之间排队通信的传输时，请使用。</span><span class="sxs-lookup"><span data-stu-id="fad3a-112">**A:** Use the <xref:System.ServiceModel.NetMsmqBinding> when you want to use MSMQ as a transport for queued communication between two WCF applications.</span></span> <span data-ttu-id="fad3a-113"><xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>当你想要使用现有的 MSMQ 应用程序与新的 WCF 应用程序通信时，请使用。</span><span class="sxs-lookup"><span data-stu-id="fad3a-113">Use the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> when you want to use existing MSMQ applications to communicate with new WCF applications.</span></span>

<span data-ttu-id="fad3a-114">**问：** 是否必须升级 MSMQ 才能使用 <xref:System.ServiceModel.NetMsmqBinding> 和 `MsmqIntegration` 绑定？</span><span class="sxs-lookup"><span data-stu-id="fad3a-114">**Q:** Do I have to upgrade MSMQ to use the <xref:System.ServiceModel.NetMsmqBinding> and `MsmqIntegration` bindings?</span></span>

<span data-ttu-id="fad3a-115">**答:** 否。</span><span class="sxs-lookup"><span data-stu-id="fad3a-115">**A:** No.</span></span> <span data-ttu-id="fad3a-116">在 Windows XP 和 Windows Server 2003 上，这两种绑定都适用于 MSMQ 3.0。</span><span class="sxs-lookup"><span data-stu-id="fad3a-116">Both bindings work with MSMQ 3.0 on Windows XP and Windows Server 2003.</span></span> <span data-ttu-id="fad3a-117">升级到 Windows Vista 中的 MSMQ 4.0 时，绑定的某些功能将变为可用。</span><span class="sxs-lookup"><span data-stu-id="fad3a-117">Certain features of the bindings become available when you upgrade to MSMQ 4.0 in Windows Vista.</span></span>

<span data-ttu-id="fad3a-118">**问：** 和绑定的哪些 <xref:System.ServiceModel.NetMsmqBinding> 功能 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 在 msmq 4.0 中可用，但在 msmq 3.0 中不可用？</span><span class="sxs-lookup"><span data-stu-id="fad3a-118">**Q:** What features of the <xref:System.ServiceModel.NetMsmqBinding> and <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> bindings are available in MSMQ 4.0 but not in MSMQ 3.0?</span></span>

<span data-ttu-id="fad3a-119">**答：** 以下功能在 MSMQ 4.0 中可用，但在 MSMQ 3.0 中不可用：</span><span class="sxs-lookup"><span data-stu-id="fad3a-119">**A:** The following features are available in MSMQ 4.0 but not in MSMQ 3.0:</span></span>

- <span data-ttu-id="fad3a-120">只有 MSMQ 4.0 才支持自定义死信队列。</span><span class="sxs-lookup"><span data-stu-id="fad3a-120">Custom dead-letter queue is supported only on MSMQ 4.0.</span></span>

- <span data-ttu-id="fad3a-121">MSMQ 3.0 和 MSMQ 4.0 处理病毒消息的方式不同。</span><span class="sxs-lookup"><span data-stu-id="fad3a-121">MSMQ 3.0 and 4.0 handle poison messages differently.</span></span>

- <span data-ttu-id="fad3a-122">只有 MSMQ 4.0 才支持远程事务处理读取。</span><span class="sxs-lookup"><span data-stu-id="fad3a-122">Only MSMQ 4.0 supports remote transacted read.</span></span>

<span data-ttu-id="fad3a-123">有关详细信息，请参阅[Windows Vista、Windows Server 2003 和 WINDOWS XP 中的队列功能](diff-in-queue-in-vista-server-2003-windows-xp.md)之间的差异。</span><span class="sxs-lookup"><span data-stu-id="fad3a-123">For more information, see [Differences in Queuing Features in Windows Vista, Windows Server 2003, and Windows XP](diff-in-queue-in-vista-server-2003-windows-xp.md).</span></span>

<span data-ttu-id="fad3a-124">**问：** 是否可以在一侧排队通信和 MSMQ 4.0 一端使用 MSMQ 3.0？</span><span class="sxs-lookup"><span data-stu-id="fad3a-124">**Q:** Can I use MSMQ 3.0 on one side of a queued communication and MSMQ 4.0 on the other side?</span></span>

<span data-ttu-id="fad3a-125">**答:** 是的。</span><span class="sxs-lookup"><span data-stu-id="fad3a-125">**A:** Yes.</span></span>

<span data-ttu-id="fad3a-126">**问：** 我想要将现有的 MSMQ 应用程序与新的 WCF 客户端或服务器集成。</span><span class="sxs-lookup"><span data-stu-id="fad3a-126">**Q:** I want to integrate existing MSMQ applications with new WCF clients or servers.</span></span> <span data-ttu-id="fad3a-127">是否需要升级两端的 MSMQ 基础结构？</span><span class="sxs-lookup"><span data-stu-id="fad3a-127">Do I need to upgrade both sides of my MSMQ infrastructure?</span></span>

<span data-ttu-id="fad3a-128">**答:** 否。</span><span class="sxs-lookup"><span data-stu-id="fad3a-128">**A:** No.</span></span> <span data-ttu-id="fad3a-129">您不必将任何一端升级到 MSMQ 4.0。</span><span class="sxs-lookup"><span data-stu-id="fad3a-129">You do not have to upgrade to MSMQ 4.0 on either side.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="fad3a-130">疑难解答</span><span class="sxs-lookup"><span data-stu-id="fad3a-130">Troubleshooting</span></span>

<span data-ttu-id="fad3a-131">此部分包含大多数常见疑难问题的答案。</span><span class="sxs-lookup"><span data-stu-id="fad3a-131">This section contains answers to most common troubleshooting issues.</span></span> <span data-ttu-id="fad3a-132">某些已知限制问题还将在发行说明中进行介绍。</span><span class="sxs-lookup"><span data-stu-id="fad3a-132">Some issues that are known limitations are also described in the release notes.</span></span>

<span data-ttu-id="fad3a-133">**问：** 我尝试使用专用队列，但收到以下异常： `System.InvalidOperationException` ： URL 无效。</span><span class="sxs-lookup"><span data-stu-id="fad3a-133">**Q:** I am trying to use a private queue and I get the following exception: `System.InvalidOperationException`: The URL is invalid.</span></span> <span data-ttu-id="fad3a-134">队列的 URL 不能包含“$”字符。</span><span class="sxs-lookup"><span data-stu-id="fad3a-134">The URL for the queue cannot contain the '$' character.</span></span> <span data-ttu-id="fad3a-135">使用 net.msmq://machine/private/queueName 中的语法指定专有队列的地址。</span><span class="sxs-lookup"><span data-stu-id="fad3a-135">Use the syntax in net.msmq://machine/private/queueName to address a private queue.</span></span>

<span data-ttu-id="fad3a-136">**答：** 检查配置和代码中的队列统一资源标识符（URI）。</span><span class="sxs-lookup"><span data-stu-id="fad3a-136">**A:** Check the queue Uniform Resource Identifier (URI) in your configuration and code.</span></span> <span data-ttu-id="fad3a-137">不要在 URI 中使用“$”字符。</span><span class="sxs-lookup"><span data-stu-id="fad3a-137">Do not use the "$" character in the URI.</span></span> <span data-ttu-id="fad3a-138">例如，若要对名为 OrdersQueue 的专用队列进行寻址，请将 URI 指定为 `net.msmq://localhost/private/ordersQueue` 。</span><span class="sxs-lookup"><span data-stu-id="fad3a-138">For example, to address a private queue named OrdersQueue, specify the URI as `net.msmq://localhost/private/ordersQueue`.</span></span>

<span data-ttu-id="fad3a-139">**问：**`ServiceHost.Open()`对排队的应用程序调用会引发以下异常： `System.ArgumentException` ：基址中不能包含 URI 查询字符串。</span><span class="sxs-lookup"><span data-stu-id="fad3a-139">**Q:** Calling `ServiceHost.Open()` on my queued application throws the following exception: `System.ArgumentException`: A base address cannot contain a URI query string.</span></span> <span data-ttu-id="fad3a-140">为什么？</span><span class="sxs-lookup"><span data-stu-id="fad3a-140">Why?</span></span>

<span data-ttu-id="fad3a-141">**答：** 检查配置文件和代码中的队列 URI。</span><span class="sxs-lookup"><span data-stu-id="fad3a-141">**A:** Check the queue URI in your configuration file and in your code.</span></span> <span data-ttu-id="fad3a-142">虽然 MSMQ 队列支持使用“?”字符，但 URI 将此字符解释为字符串查询的开头。</span><span class="sxs-lookup"><span data-stu-id="fad3a-142">While MSMQ queues support the use of the '?' character, URIs interpret this character as the beginning of a string query.</span></span> <span data-ttu-id="fad3a-143">若要避免此问题，请使用不包含“?”字符的队列名称。</span><span class="sxs-lookup"><span data-stu-id="fad3a-143">To avoid this issue, use queue names that do not contain '?' characters.</span></span>

<span data-ttu-id="fad3a-144">**问：** 已成功发送，但没有在接收方调用任何服务操作。</span><span class="sxs-lookup"><span data-stu-id="fad3a-144">**Q:** My send succeeded but no service operation is invoked on the receiver.</span></span> <span data-ttu-id="fad3a-145">为什么？</span><span class="sxs-lookup"><span data-stu-id="fad3a-145">Why?</span></span>

<span data-ttu-id="fad3a-146">**答：** 若要确定答案，请通过以下检查列表进行操作：</span><span class="sxs-lookup"><span data-stu-id="fad3a-146">**A:** To determine the answer, work through the following check list:</span></span>

- <span data-ttu-id="fad3a-147">检查事务性队列需求是否与指定的保证相符。</span><span class="sxs-lookup"><span data-stu-id="fad3a-147">Check that the transactional queue requirements are compatible with the assurances specified.</span></span> <span data-ttu-id="fad3a-148">请注意下面的原则：</span><span class="sxs-lookup"><span data-stu-id="fad3a-148">Note the following principles:</span></span>

  - <span data-ttu-id="fad3a-149"><xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>  =  只能向事务性队列发送持久消息（数据报和会话）并只使用 "一次性" 保证（ `true` ）。</span><span class="sxs-lookup"><span data-stu-id="fad3a-149">You can send durable messages (datagrams and sessions) with "exactly once" assurances (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`) only to a transactional queue.</span></span>

  - <span data-ttu-id="fad3a-150">可以发送只具有“一次性”保证的会话。</span><span class="sxs-lookup"><span data-stu-id="fad3a-150">You can send sessions only with "exactly once" assurances.</span></span>

  - <span data-ttu-id="fad3a-151">需要使用事务从事务性队列接收会话中的消息。</span><span class="sxs-lookup"><span data-stu-id="fad3a-151">A transaction is required to receive messages in a session from a transactional queue.</span></span>

  - <span data-ttu-id="fad3a-152">只能 <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>  =  向非事务性队列发送或接收易变或持久消息（仅限数据报）且无保证（ `false` ）。</span><span class="sxs-lookup"><span data-stu-id="fad3a-152">You can send or receive volatile or durable messages (datagrams only) with no assurances (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`) only to a non-transactional queue.</span></span>

- <span data-ttu-id="fad3a-153">检查死信队列。</span><span class="sxs-lookup"><span data-stu-id="fad3a-153">Check the dead-letter queue.</span></span> <span data-ttu-id="fad3a-154">如果在此处找到消息，则确定没有传送这些消息的原因。</span><span class="sxs-lookup"><span data-stu-id="fad3a-154">If you find the messages there, determine why they were not delivered.</span></span>

- <span data-ttu-id="fad3a-155">检查传出队列的连通性或寻址问题。</span><span class="sxs-lookup"><span data-stu-id="fad3a-155">Check the outgoing queues for connectivity or addressing problems.</span></span>

<span data-ttu-id="fad3a-156">**问：** 我指定了一个自定义死信队列，但当我启动发送程序应用程序时，我收到一个例外，指出未找到死信队列，或发送应用程序没有对死信队列的权限。</span><span class="sxs-lookup"><span data-stu-id="fad3a-156">**Q:** I have specified a custom dead-letter queue, but when I start the sender application, I get an exception that either the dead-letter queue is not found, or the sending application has no permission to the dead-letter queue.</span></span> <span data-ttu-id="fad3a-157">为何会发生这种情况？</span><span class="sxs-lookup"><span data-stu-id="fad3a-157">Why is this happening?</span></span>

<span data-ttu-id="fad3a-158">**答：** 自定义死信队列 URI 必须在第一段包含 "localhost" 或计算机名称，例如，net.pipe：//localhost/private/myAppdead-letter queue。</span><span class="sxs-lookup"><span data-stu-id="fad3a-158">**A:** The custom dead-letter queue URI must include a "localhost" or the computer name in the first segment, for example, net.msmq://localhost/private/myAppdead-letter queue.</span></span>

<span data-ttu-id="fad3a-159">**问：** 是否始终需要定义自定义死信队列，或是否有默认的死信队列？</span><span class="sxs-lookup"><span data-stu-id="fad3a-159">**Q:** Is it always necessary to define a custom dead-letter queue, or is there a default dead-letter queue?</span></span>

<span data-ttu-id="fad3a-160">**答：** 如果保证为 "恰好一次" （ <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>  =  `true` ），并且如果未指定自定义死信队列，则默认为系统级事务性死信队列。</span><span class="sxs-lookup"><span data-stu-id="fad3a-160">**A:** If assurances are "exactly once" (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`), and if you do not specify a custom dead-letter queue, the default is a system-wide transactional dead-letter queue.</span></span>

<span data-ttu-id="fad3a-161">如果保证为 "无 <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>  =  `false` " （），则默认情况下不是 "死信队列" 功能。</span><span class="sxs-lookup"><span data-stu-id="fad3a-161">If assurances are none (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`), then the default is no dead-letter queue functionality.</span></span>

<span data-ttu-id="fad3a-162">**问：** 我的服务在 SvcHost 上抛出。打开并出现消息 "调用 svchost.open 时无法满足 EndpointListener 要求"。</span><span class="sxs-lookup"><span data-stu-id="fad3a-162">**Q:** My service throws on SvcHost.Open with a message "EndpointListener requirements cannot be met by the ListenerFactory".</span></span> <span data-ttu-id="fad3a-163">为什么？</span><span class="sxs-lookup"><span data-stu-id="fad3a-163">Why?</span></span>

<span data-ttu-id="fad3a-164">A.</span><span class="sxs-lookup"><span data-stu-id="fad3a-164">A.</span></span> <span data-ttu-id="fad3a-165">请检查您的服务协定。</span><span class="sxs-lookup"><span data-stu-id="fad3a-165">Check your service contract.</span></span> <span data-ttu-id="fad3a-166">您可能忘记了 `true` 在所有服务操作上放置 "IsOneWay ="。</span><span class="sxs-lookup"><span data-stu-id="fad3a-166">You may have forgotten to put "IsOneWay=`true`" on all the service operations.</span></span> <span data-ttu-id="fad3a-167">队列仅支持单向服务操作。</span><span class="sxs-lookup"><span data-stu-id="fad3a-167">Queues support only one-way service operations.</span></span>

<span data-ttu-id="fad3a-168">**问：** 队列中有消息，但未调用任何服务操作。</span><span class="sxs-lookup"><span data-stu-id="fad3a-168">**Q:** There are messages in the queue but no service operation is invoked.</span></span> <span data-ttu-id="fad3a-169">遇到了什么问题？</span><span class="sxs-lookup"><span data-stu-id="fad3a-169">What is the problem?</span></span>

<span data-ttu-id="fad3a-170">**答：** 确定服务主机是否出错。</span><span class="sxs-lookup"><span data-stu-id="fad3a-170">**A:** Determine if your service host is faulted.</span></span> <span data-ttu-id="fad3a-171">可以通过查看跟踪情况或实现 `IErrorHandler` 进行检查。</span><span class="sxs-lookup"><span data-stu-id="fad3a-171">You can check by looking at the trace or implementing `IErrorHandler`.</span></span> <span data-ttu-id="fad3a-172">默认情况下，如果检测到病毒消息，则服务主机将出现故障。</span><span class="sxs-lookup"><span data-stu-id="fad3a-172">Service host faults, by default, if a poison message is detected.</span></span>

<span data-ttu-id="fad3a-173">**问：** 队列中有消息，但 Web 托管的排队服务未激活。</span><span class="sxs-lookup"><span data-stu-id="fad3a-173">**Q:** There are messages in the queue but my Web-hosted queued service is not getting activated.</span></span> <span data-ttu-id="fad3a-174">为什么？</span><span class="sxs-lookup"><span data-stu-id="fad3a-174">Why?</span></span>

<span data-ttu-id="fad3a-175">**答：** 最常见的原因是权限。</span><span class="sxs-lookup"><span data-stu-id="fad3a-175">**A:** The most common reason is permissions.</span></span>

1. <span data-ttu-id="fad3a-176">确保 `NetMsmqActivator` 进程正在运行，并为 `NetMsmqActivator` 进程的标识提供对此队列的读取和查找权限。</span><span class="sxs-lookup"><span data-stu-id="fad3a-176">Ensure that the `NetMsmqActivator` process is running and the identity of the `NetMsmqActivator` process is given read and seek permission on the queue.</span></span>

2. <span data-ttu-id="fad3a-177">如果 `NetMsmqActivator` 正在监视远程计算机上的队列，请确保 `NetMsmqActivator` 不使用受限制的令牌运行。</span><span class="sxs-lookup"><span data-stu-id="fad3a-177">If the `NetMsmqActivator` is monitoring queues on a remote machine, ensure that `NetMsmqActivator` does not run under a restricted token.</span></span> <span data-ttu-id="fad3a-178">若要使用不受限制的令牌运行 `NetMsmqActivator`，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="fad3a-178">To run the `NetMsmqActivator` with an unrestricted token:</span></span>

    ```console
    sc sidtype NetMsmqActivator unrestricted
    ```

<span data-ttu-id="fad3a-179">有关非安全相关的 Web 主机问题，请参阅：[承载排队应用程序的 web](web-hosting-a-queued-application.md)。</span><span class="sxs-lookup"><span data-stu-id="fad3a-179">For non-security related Web host issues refer to: [Web Hosting a Queued Application](web-hosting-a-queued-application.md).</span></span>

<span data-ttu-id="fad3a-180">**问：** 访问会话的最简单方法是什么？</span><span class="sxs-lookup"><span data-stu-id="fad3a-180">**Q:** What is the easiest way to access sessions?</span></span>

<span data-ttu-id="fad3a-181">**答：**`true`在与会话中的最后一条消息相对应的操作上设置自动完成 =，并设置 `false` 所有剩余服务操作的 "自动完成"。</span><span class="sxs-lookup"><span data-stu-id="fad3a-181">**A:** Set AutoComplete=`true` on the operation that corresponds to the last message in the session, and set AutoComplete=`false` on all remaining service operations.</span></span>

<span data-ttu-id="fad3a-182">**问：** 为什么 `ProtocolException` 当从包含排队会话消息和排队数据报消息的队列中进行读取时，服务才会引发。</span><span class="sxs-lookup"><span data-stu-id="fad3a-182">**Q:** Why does my service throw a `ProtocolException` when reading from a queue that contains both queued session messages and queued datagram messages?</span></span>

<span data-ttu-id="fad3a-183">**答：** 排队会话消息和排队数据报消息的构建方式存在根本的差异。</span><span class="sxs-lookup"><span data-stu-id="fad3a-183">**A:** There is a fundamental difference in the way queued session messages and queued datagram messages are composed.</span></span> <span data-ttu-id="fad3a-184">因此，要读取排队会话消息的服务无法接收排队数据报消息，而要读取排队数据报消息的服务也无法接收会话消息。</span><span class="sxs-lookup"><span data-stu-id="fad3a-184">Because of this, a service that is expecting to read a queued session message cannot receive a queued datagram message and a service expecting to read a queued datagram message cannot receive a session message.</span></span> <span data-ttu-id="fad3a-185">试图从同一个队列读取这两种消息时将引发以下异常：</span><span class="sxs-lookup"><span data-stu-id="fad3a-185">Attempting to read both types of messages from the same queue throws the following exception:</span></span>

```console
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.
```

<span data-ttu-id="fad3a-186">当应用程序从同一台计算机既发送排队会话消息又发送排队数据报消息时，系统死信队列以及任何自定义死信队列对这种问题尤其敏感。</span><span class="sxs-lookup"><span data-stu-id="fad3a-186">The system dead-letter queue, as well as any custom dead-letter queue, is particularly susceptible to this issue if an application sends both queued session messages and queued datagram messages from the same computer.</span></span> <span data-ttu-id="fad3a-187">如果消息无法成功发送，则会被移入死信队列。</span><span class="sxs-lookup"><span data-stu-id="fad3a-187">If a message cannot be sent successfully, it is moved to the dead-letter queue.</span></span> <span data-ttu-id="fad3a-188">在这些情况下，很有可能将会话消息和数据报消息都移入死信队列。</span><span class="sxs-lookup"><span data-stu-id="fad3a-188">Under these circumstances, it is possible to have both session and datagram messages in the dead-letter queue.</span></span> <span data-ttu-id="fad3a-189">从队列进行读取时，无法在运行时将两种消息分开。因此，应用程序不应从同一台计算机既发送排队会话消息又发送排队数据报消息。</span><span class="sxs-lookup"><span data-stu-id="fad3a-189">There is no way to separate both types of messages at runtime when reading from a queue, therefore, applications should not send both queued session messages and queued datagram messages from the same computer.</span></span>

### <a name="msmq-integration-specific-troubleshooting"></a><span data-ttu-id="fad3a-190">MSMQ 集成：特定的疑难解答</span><span class="sxs-lookup"><span data-stu-id="fad3a-190">MSMQ Integration: Specific Troubleshooting</span></span>

<span data-ttu-id="fad3a-191">**问：** 发送消息时，或打开服务主机时，出现错误，指出方案错误。</span><span class="sxs-lookup"><span data-stu-id="fad3a-191">**Q:** When I send a message, or when I open the service host, I get an error that indicates the scheme is wrong.</span></span> <span data-ttu-id="fad3a-192">为什么？</span><span class="sxs-lookup"><span data-stu-id="fad3a-192">Why?</span></span>

<span data-ttu-id="fad3a-193">**答：** 如果使用 MSMQ 集成绑定，则必须使用 msmq.formatname 方案。</span><span class="sxs-lookup"><span data-stu-id="fad3a-193">**A:** When you use the MSMQ integration binding, you must use the msmq.formatname scheme.</span></span> <span data-ttu-id="fad3a-194">例如，msmq.formatname:DIRECT=OS:.\private$\OrdersQueue。</span><span class="sxs-lookup"><span data-stu-id="fad3a-194">For example, msmq.formatname:DIRECT=OS:.\private$\OrdersQueue.</span></span> <span data-ttu-id="fad3a-195">但是，如果您指定自定义死信队列，则必须使用 net.msmq 方案。</span><span class="sxs-lookup"><span data-stu-id="fad3a-195">But when you specify the custom dead-letter queue, you must use the net.msmq scheme.</span></span>

<span data-ttu-id="fad3a-196">**问：** 使用公用或专用格式名称并在 Windows Vista 上打开服务主机时，出现错误。</span><span class="sxs-lookup"><span data-stu-id="fad3a-196">**Q:** When I use a public or private format name and open the service host on Windows Vista, I get an error.</span></span> <span data-ttu-id="fad3a-197">为什么？</span><span class="sxs-lookup"><span data-stu-id="fad3a-197">Why?</span></span>

<span data-ttu-id="fad3a-198">**答：** Windows Vista 上的 WCF 集成通道检查是否可以打开用于处理有害消息的主应用程序队列的子队列。</span><span class="sxs-lookup"><span data-stu-id="fad3a-198">**A:** The WCF integration channel on Windows Vista checks to see if a subqueue can be opened for the main application queue for handling poison messages.</span></span> <span data-ttu-id="fad3a-199">子队列名称派生自传递到侦听器的 msmq.formatname URI。</span><span class="sxs-lookup"><span data-stu-id="fad3a-199">The subqueue name is derived from an msmq.formatname URI passed to the listener.</span></span> <span data-ttu-id="fad3a-200">MSMQ 中的子队列名称只能是直接格式名称。</span><span class="sxs-lookup"><span data-stu-id="fad3a-200">The subqueue name in MSMQ can only be a direct format name.</span></span> <span data-ttu-id="fad3a-201">因此，您会发现以上错误。</span><span class="sxs-lookup"><span data-stu-id="fad3a-201">So you see the error.</span></span> <span data-ttu-id="fad3a-202">将队列 URI 改为直接格式名。</span><span class="sxs-lookup"><span data-stu-id="fad3a-202">Change the queue URI to a direct format name.</span></span>

<span data-ttu-id="fad3a-203">**问：** 从 MSMQ 应用程序接收消息时，消息位于队列中，并且不由接收 WCF 应用程序读取。</span><span class="sxs-lookup"><span data-stu-id="fad3a-203">**Q:** When receiving a message from an MSMQ application, the message sits in the queue and is not read by the receiving WCF application.</span></span> <span data-ttu-id="fad3a-204">为什么？</span><span class="sxs-lookup"><span data-stu-id="fad3a-204">Why?</span></span>

<span data-ttu-id="fad3a-205">**答：** 检查消息是否具有正文。</span><span class="sxs-lookup"><span data-stu-id="fad3a-205">**A:** Check to see whether the message has a body.</span></span> <span data-ttu-id="fad3a-206">如果消息没有正文，则 MSMQ 集成通道会忽略此消息。</span><span class="sxs-lookup"><span data-stu-id="fad3a-206">If the message has no body, the MSMQ integration channel ignores the message.</span></span> <span data-ttu-id="fad3a-207">实现向其通知异常的 `IErrorHandler` 并检查跟踪情况。</span><span class="sxs-lookup"><span data-stu-id="fad3a-207">Implement `IErrorHandler` to be notified of exceptions and check the traces.</span></span>

### <a name="security-related-troubleshooting"></a><span data-ttu-id="fad3a-208">与安全相关的疑难解答</span><span class="sxs-lookup"><span data-stu-id="fad3a-208">Security-Related Troubleshooting</span></span>

<span data-ttu-id="fad3a-209">**问：** 当我在工作组模式下运行使用默认绑定的示例时，消息似乎已发送，但接收方永远无法接收。</span><span class="sxs-lookup"><span data-stu-id="fad3a-209">**Q:** When I run the sample that uses a default binding in workgroup mode, messages seem to get sent but are never received by the receiver.</span></span>

<span data-ttu-id="fad3a-210">**答：** 默认情况下，使用需要 Active Directory Directory 服务的 MSMQ 内部证书对消息进行签名。</span><span class="sxs-lookup"><span data-stu-id="fad3a-210">**A:** By default, messages are signed using an MSMQ internal certificate that requires the Active Directory directory service.</span></span> <span data-ttu-id="fad3a-211">在工作组模式下，因为 Active Directory 不可用，所以对消息的签名会失败。</span><span class="sxs-lookup"><span data-stu-id="fad3a-211">In workgroup mode, because Active Directory is not available, signing the message fails.</span></span> <span data-ttu-id="fad3a-212">因此，会显示消息 "死信队列" 和 "失败原因"，如 "签名无效"。</span><span class="sxs-lookup"><span data-stu-id="fad3a-212">So the message lands in the dead-letter queue and failure cause, such as "Bad signature", is indicated.</span></span>

<span data-ttu-id="fad3a-213">解决方法是关闭安全性。</span><span class="sxs-lookup"><span data-stu-id="fad3a-213">The workaround is to turn off security.</span></span> <span data-ttu-id="fad3a-214">这是通过将设置 <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A>  =  <xref:System.ServiceModel.NetMsmqSecurityMode.None> 为在工作组模式下工作来完成的。</span><span class="sxs-lookup"><span data-stu-id="fad3a-214">This is done by setting <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A> = <xref:System.ServiceModel.NetMsmqSecurityMode.None> to make it work in workgroup mode.</span></span>

<span data-ttu-id="fad3a-215">另一个解决方法是从 <xref:System.ServiceModel.MsmqTransportSecurity> 属性获取 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> 并将其设置为 <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>，然后设置客户端证书。</span><span class="sxs-lookup"><span data-stu-id="fad3a-215">Another workaround is to get the <xref:System.ServiceModel.MsmqTransportSecurity> from the <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> property and set it to <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>, and set the client certificate.</span></span>

<span data-ttu-id="fad3a-216">还有一种解决方法就是安装集成了 Active Directory 的 MSMQ。</span><span class="sxs-lookup"><span data-stu-id="fad3a-216">Yet another workaround is to install MSMQ with Active Directory integration.</span></span>

<span data-ttu-id="fad3a-217">**问：** 当我将 Active Directory 中的消息发送到队列时，会收到 "未找到内部证书" 消息。</span><span class="sxs-lookup"><span data-stu-id="fad3a-217">**Q:** When I send a message with default binding (transport security turned on) in Active Directory to a queue, I get an "internal certificate not found" message.</span></span> <span data-ttu-id="fad3a-218">如何修复此问题？</span><span class="sxs-lookup"><span data-stu-id="fad3a-218">How do I fix this?</span></span>

<span data-ttu-id="fad3a-219">**答：** 这意味着必须续订发送方 Active Directory 的证书。</span><span class="sxs-lookup"><span data-stu-id="fad3a-219">**A:** This means that the certificate in Active Directory for the sender must be renewed.</span></span> <span data-ttu-id="fad3a-220">为此，请打开 **"控制面板**"、"**管理工具**"、"**计算机管理**"，右键单击 " **MSMQ**"，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="fad3a-220">To do so, open **Control Panel**, **Administrative Tools**, **Computer Management**, right-click **MSMQ**, and select **Properties**.</span></span> <span data-ttu-id="fad3a-221">选择 "**用户证书**" 选项卡，然后单击 "**续订**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="fad3a-221">Select the **User Certificate** tab and click the **Renew** button.</span></span>

<span data-ttu-id="fad3a-222">**问：** 当我使用发送消息 <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> 并指定要使用的证书时，会收到 "证书无效" 消息。</span><span class="sxs-lookup"><span data-stu-id="fad3a-222">**Q:** When I send a message using <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> and specify the certificate to use, I get an "Invalid certificate" message.</span></span> <span data-ttu-id="fad3a-223">如何修复此问题？</span><span class="sxs-lookup"><span data-stu-id="fad3a-223">How do I fix this?</span></span>

<span data-ttu-id="fad3a-224">**答：** 不能将本地计算机证书存储与证书模式一起使用。</span><span class="sxs-lookup"><span data-stu-id="fad3a-224">**A:** You cannot use a local machine certificate store with certificate mode.</span></span> <span data-ttu-id="fad3a-225">必须使用证书管理单元将证书从计算机证书存储区复制到当前用户存储区。</span><span class="sxs-lookup"><span data-stu-id="fad3a-225">You have to copy the certificate from the machine certificate store to the current user store using the Certificate snap-in.</span></span> <span data-ttu-id="fad3a-226">若要打开证书管理单元，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="fad3a-226">To get the Certificate snap-in:</span></span>

1. <span data-ttu-id="fad3a-227">单击 "**开始**"，选择 "**运行**"，键入 `mmc` ，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="fad3a-227">Click **Start**, select **Run**, type `mmc`, and click **OK**.</span></span>

2. <span data-ttu-id="fad3a-228">在**Microsoft 管理控制台**中，打开 "**文件**" 菜单，然后选择 "**添加/删除管理单元**"。</span><span class="sxs-lookup"><span data-stu-id="fad3a-228">In the **Microsoft Management Console**, open the **File** menu and select **Add/Remove Snap-in**.</span></span>

3. <span data-ttu-id="fad3a-229">在 "**添加/删除管理单元**" 对话框中，单击 "**添加**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="fad3a-229">In the **Add/Remove Snap-in** dialog box, click the **Add** button.</span></span>

4. <span data-ttu-id="fad3a-230">在 "**添加独立管理单元**" 对话框中，选择 "证书"，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="fad3a-230">In the **Add Standalone Snap-in** dialog box, select Certificates and click **Add**.</span></span>

5. <span data-ttu-id="fad3a-231">在 "**证书**管理单元" 对话框中，选择 "**我的用户帐户"，** 然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="fad3a-231">In the **Certificates** snap-in dialog box, select **My user account,** and click **Finish**.</span></span>

6. <span data-ttu-id="fad3a-232">接下来，使用前面的步骤添加另一个证书管理单元，但这次请选择 "**计算机帐户**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="fad3a-232">Next, add a second Certificates snap-in using the previous steps, but this time select **Computer account** and click **Next**.</span></span>

7. <span data-ttu-id="fad3a-233">选择“本地计算机”\*\*\*\*，然后单击“完成”\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fad3a-233">Select **Local Computer** and click **Finish**.</span></span> <span data-ttu-id="fad3a-234">现在，可以将证书从计算机证书存储区拖放到当前用户存储区。</span><span class="sxs-lookup"><span data-stu-id="fad3a-234">You can now drag and drop certificates from the machine certificate store to the current user store.</span></span>

<span data-ttu-id="fad3a-235">**问：** 当我的服务在工作组模式下从另一台计算机上的队列中读取时，出现 "拒绝访问" 异常。</span><span class="sxs-lookup"><span data-stu-id="fad3a-235">**Q:** When my service reads from a queue on another computer in workgroup mode, I get an "access denied" exception.</span></span>

<span data-ttu-id="fad3a-236">**答：** 在工作组模式下，对于远程应用程序，若要获取对队列的访问权限，该应用程序必须有权访问该队列。</span><span class="sxs-lookup"><span data-stu-id="fad3a-236">**A:** In workgroup mode, for a remote application to gain access to the queue, the application must have permission to access the queue.</span></span> <span data-ttu-id="fad3a-237">向队列的访问控制列表（ACL）添加 "匿名登录"，并向其授予 "读取" 权限。</span><span class="sxs-lookup"><span data-stu-id="fad3a-237">Add "Anonymous login" to the queue's access control list (ACL) and give it read permission.</span></span>

<span data-ttu-id="fad3a-238">**问：** 当网络服务客户端（或没有域帐户的任何客户端）发送排队消息时，发送将失败，并出现无效证书。</span><span class="sxs-lookup"><span data-stu-id="fad3a-238">**Q:** When a network service client (or any client that does not have a domain account) sends a queued message, the send fails with an invalid certificate.</span></span> <span data-ttu-id="fad3a-239">如何修复此问题？</span><span class="sxs-lookup"><span data-stu-id="fad3a-239">How do I fix this?</span></span>

<span data-ttu-id="fad3a-240">**答：** 检查绑定配置。</span><span class="sxs-lookup"><span data-stu-id="fad3a-240">**A:** Check the binding configuration.</span></span> <span data-ttu-id="fad3a-241">默认绑定会打开 MSMQ 传输安全以对消息进行签名。</span><span class="sxs-lookup"><span data-stu-id="fad3a-241">The default binding has MSMQ transport security turned on to sign the message.</span></span> <span data-ttu-id="fad3a-242">关闭该传输安全。</span><span class="sxs-lookup"><span data-stu-id="fad3a-242">Turn it off.</span></span>

### <a name="remote-transacted-receives"></a><span data-ttu-id="fad3a-243">远程事务处理接收</span><span class="sxs-lookup"><span data-stu-id="fad3a-243">Remote Transacted Receives</span></span>

<span data-ttu-id="fad3a-244">**问：** 当我在计算机 A 上有一个队列，而在计算机 B 上读取消息的 WCF 服务（远程事务处理接收方案）时，不会从队列中读取消息。</span><span class="sxs-lookup"><span data-stu-id="fad3a-244">**Q:** When I have a queue on machine A, and a WCF service that reads messages from a queue on machine B (the remote transacted receive scenario), messages are not read from the queue.</span></span> <span data-ttu-id="fad3a-245">跟踪信息指示接收失败，并显示消息 "无法导入事务"。</span><span class="sxs-lookup"><span data-stu-id="fad3a-245">Tracing information indicates the receive failed with the message "Transaction cannot be imported."</span></span> <span data-ttu-id="fad3a-246">如何进行修复？</span><span class="sxs-lookup"><span data-stu-id="fad3a-246">What can I do to fix this?</span></span>

<span data-ttu-id="fad3a-247">**答：** 有三个可能的原因：</span><span class="sxs-lookup"><span data-stu-id="fad3a-247">**A:** There are three possible reasons for this:</span></span>

- <span data-ttu-id="fad3a-248">如果处于域模式下，则远程事务处理接收要求 Microsoft 分布式事务协调器 (MSDTC) 网络访问。</span><span class="sxs-lookup"><span data-stu-id="fad3a-248">If you are in domain mode, remote transacted receive requires Microsoft Distributed Transaction Coordinator (MSDTC) network access.</span></span> <span data-ttu-id="fad3a-249">你可以使用 "**添加/删除组件**" 启用它。</span><span class="sxs-lookup"><span data-stu-id="fad3a-249">You can enable this using **Add/Remove Components**.</span></span>

  ![显示启用网络 DTC 访问的屏幕截图。](./media/troubleshooting-queued-messaging/enable-distributed-transaction-coordinator-access.jpg)

- <span data-ttu-id="fad3a-251">检查与事务管理器进行通信的身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="fad3a-251">Check the authentication mode for communicating with the transaction manager.</span></span> <span data-ttu-id="fad3a-252">如果处于工作组模式，则必须选择 "不要求进行身份验证"。</span><span class="sxs-lookup"><span data-stu-id="fad3a-252">If you are in workgroup mode, "No Authentication Required" must be selected.</span></span> <span data-ttu-id="fad3a-253">如果处于域模式下，则必须选择 "需要相互身份验证"。</span><span class="sxs-lookup"><span data-stu-id="fad3a-253">If you are in domain mode, then "Mutual Authentication Required" must be selected.</span></span>

  <span data-ttu-id="fad3a-254">![启用 XA 事务](media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")</span><span class="sxs-lookup"><span data-stu-id="fad3a-254">![Enabling XA transactions](media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")</span></span>

- <span data-ttu-id="fad3a-255">请确保 MSDTC 位于**Internet 连接防火墙**设置中的例外列表中。</span><span class="sxs-lookup"><span data-stu-id="fad3a-255">Make sure that MSDTC is in the list of exceptions in the **Internet Connection Firewall** settings.</span></span>

- <span data-ttu-id="fad3a-256">确保你使用的是 Windows Vista。</span><span class="sxs-lookup"><span data-stu-id="fad3a-256">Ensure that you are using Windows Vista.</span></span> <span data-ttu-id="fad3a-257">Windows Vista 上的 MSMQ 支持远程事务处理读取。</span><span class="sxs-lookup"><span data-stu-id="fad3a-257">MSMQ on Windows Vista supports remote transacted read.</span></span> <span data-ttu-id="fad3a-258">早期的 Windows 版本上的 MSMQ 不支持远程事务处理读取。</span><span class="sxs-lookup"><span data-stu-id="fad3a-258">MSMQ on earlier Windows releases does not support remote transacted read.</span></span>

<span data-ttu-id="fad3a-259">**问：** 如果从队列中读取的服务是一个网络服务，例如，在 Web 主机上，从队列中读取时，为什么会出现 "拒绝访问" 异常？</span><span class="sxs-lookup"><span data-stu-id="fad3a-259">**Q:** When the service reading from the queue is a network service, for example, in a Web host, why do I get an access-denied exception is raised when reading from the queue?</span></span>

<span data-ttu-id="fad3a-260">**答：** 必须将网络服务读取访问权限添加到队列 ACL，以确保网络服务可以从队列中读取。</span><span class="sxs-lookup"><span data-stu-id="fad3a-260">**A:** Network service read access must be added to the queue ACL to ensure that a network service can read from the queue.</span></span>

<span data-ttu-id="fad3a-261">**问：** 是否可以使用 MSMQ 激活服务根据远程计算机上的队列中的消息激活应用程序？</span><span class="sxs-lookup"><span data-stu-id="fad3a-261">**Q:** Can I use the MSMQ activation service to activate applications based on messages in a queue on a remote machine?</span></span>

<span data-ttu-id="fad3a-262">**答:** 是的。</span><span class="sxs-lookup"><span data-stu-id="fad3a-262">**A:** Yes.</span></span> <span data-ttu-id="fad3a-263">为此，您必须将 MSMQ 激活服务配置为以网络服务方式运行，并将网络服务访问权限添加到远程计算机上的队列中。</span><span class="sxs-lookup"><span data-stu-id="fad3a-263">To do this, you must configure the MSMQ activation service to run as a network service, and add network service access to the queue on the remote machine.</span></span>

## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a><span data-ttu-id="fad3a-264">使用已启用 ReceiveContext 的自定义 MSMQ 绑定</span><span class="sxs-lookup"><span data-stu-id="fad3a-264">Using Custom MSMQ Bindings with ReceiveContext Enabled</span></span>

<span data-ttu-id="fad3a-265">将自定义 MSMQ 绑定用于 <xref:System.ServiceModel.Channels.ReceiveContext> 启用后，处理传入消息将使用线程池线程，因为本机 MSMQ 不支持异步接收的 i/o 完成 <xref:System.ServiceModel.Channels.ReceiveContext> 。</span><span class="sxs-lookup"><span data-stu-id="fad3a-265">When using a custom MSMQ binding with <xref:System.ServiceModel.Channels.ReceiveContext> enabled, processing an incoming message uses a thread pool thread because native MSMQ doesn't support I/O completion for asynchronous <xref:System.ServiceModel.Channels.ReceiveContext> receives.</span></span> <span data-ttu-id="fad3a-266">这是因为处理此类消息对使用内部事务 <xref:System.ServiceModel.Channels.ReceiveContext> ，而 MSMQ 不支持异步处理。</span><span class="sxs-lookup"><span data-stu-id="fad3a-266">This is because processing such a message uses internal transactions for <xref:System.ServiceModel.Channels.ReceiveContext> and MSMQ doesn't support asynchronous processing.</span></span> <span data-ttu-id="fad3a-267">若要解决此问题，可将添加 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> 到终结点，以强制执行同步处理或将其设置 <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> 为1。</span><span class="sxs-lookup"><span data-stu-id="fad3a-267">To work around this issue, you can add a <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> to the endpoint to force synchronous processing or set <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> to 1.</span></span>
