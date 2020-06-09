---
title: 如何：在可靠会话内保护消息
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: 306d0f96b5163fe5c24d270b4b9a7c1d3f499e7e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596950"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="074b9-102">如何：在可靠会话内保护消息</span><span class="sxs-lookup"><span data-stu-id="074b9-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="074b9-103">本主题概述了使用系统提供的绑定之一来启用在可靠会话内交换的消息的消息级安全所需的步骤。这些绑定支持这种会话，但默认情况下不支持。</span><span class="sxs-lookup"><span data-stu-id="074b9-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="074b9-104">通过使用代码或在配置文件中以声明方式强制启用安全、可靠的会话。</span><span class="sxs-lookup"><span data-stu-id="074b9-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="074b9-105">此过程使用客户端和服务配置文件来启用安全的可靠会话。</span><span class="sxs-lookup"><span data-stu-id="074b9-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="074b9-106">此过程由以下三个关键任务组成：</span><span class="sxs-lookup"><span data-stu-id="074b9-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="074b9-107">指定客户端和服务在可靠会话内交换消息。</span><span class="sxs-lookup"><span data-stu-id="074b9-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="074b9-108">在可靠会话内要求消息级安全。</span><span class="sxs-lookup"><span data-stu-id="074b9-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="074b9-109">指定客户端必须用来向服务进行身份验证的客户端凭据类型。</span><span class="sxs-lookup"><span data-stu-id="074b9-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="074b9-110">在第一个任务中，终结点配置元素包含 `bindingConfiguration` 引用名为的绑定配置的特性（在本示例中为），这一点很重要 `MessageSecurity` 。</span><span class="sxs-lookup"><span data-stu-id="074b9-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="074b9-111">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)然后，配置元素引用此名称，通过将元素的属性设置 `enabled` [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) 为来启用可靠会话 `true` 。</span><span class="sxs-lookup"><span data-stu-id="074b9-111">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="074b9-112">通过将 `ordered` 属性设置为 `true`，可以要求可靠会话内的有序传送保证。</span><span class="sxs-lookup"><span data-stu-id="074b9-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="074b9-113">对于此配置过程所基于的示例的源副本，请参阅[WS 可靠会话](../samples/ws-reliable-session.md)。</span><span class="sxs-lookup"><span data-stu-id="074b9-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="074b9-114">第二个任务的基本项是通过将 `mode` **\<security>** 客户端和服务的元素中包含的元素的属性设置 **\<binding>** 为来完成的 `Message` 。</span><span class="sxs-lookup"><span data-stu-id="074b9-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="074b9-115">第三项任务的基本项是通过将 `clientCredentialType` **\<message>** 客户端和服务的元素中包含的元素的属性设置 **\<security>** 为来完成的 `Certificate` 。</span><span class="sxs-lookup"><span data-stu-id="074b9-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="074b9-116">如果在可靠会话中使用消息安全，则在发生超时而不是在第一次失败时引发异常的情况下，可靠的消息传送将尝试对未经身份验证的客户端</span><span class="sxs-lookup"><span data-stu-id="074b9-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="074b9-117">使用 WSHttpBinding 配置服务以使用可靠会话</span><span class="sxs-lookup"><span data-stu-id="074b9-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="074b9-118">[如何：在可靠会话内交换消息](how-to-exchange-messages-within-a-reliable-session.md)中介绍了此过程。</span><span class="sxs-lookup"><span data-stu-id="074b9-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="074b9-119">使用 WSHttpBinding 配置客户端以使用可靠会话</span><span class="sxs-lookup"><span data-stu-id="074b9-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="074b9-120">[如何：在可靠会话内交换消息](how-to-exchange-messages-within-a-reliable-session.md)中介绍了此过程。</span><span class="sxs-lookup"><span data-stu-id="074b9-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="074b9-121">在配置中设置模式和 ClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="074b9-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="074b9-122">将相应的绑定元素添加到 [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) 配置文件的元素中。</span><span class="sxs-lookup"><span data-stu-id="074b9-122">Add an appropriate binding element to the [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="074b9-123">下面的示例添加一个 [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="074b9-123">The following example adds a [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="074b9-124">添加 **\<binding>** 元素，并将其 `name` 属性设置为合适的值。</span><span class="sxs-lookup"><span data-stu-id="074b9-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="074b9-125">该示例使用名称 `MessageSecurity` 。</span><span class="sxs-lookup"><span data-stu-id="074b9-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="074b9-126">添加一个 **\<security>** 元素，并将 `mode` 属性设置为 `Message` 。</span><span class="sxs-lookup"><span data-stu-id="074b9-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="074b9-127">在 **\<security>** 元素中，添加一个 **\<message>** 元素，并将 `clientCredentialType` 特性设置为 `Certificate` 。</span><span class="sxs-lookup"><span data-stu-id="074b9-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
