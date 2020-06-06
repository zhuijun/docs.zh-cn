---
title: <localServiceSettings> 元素
ms.date: 03/30/2017
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
ms.openlocfilehash: 4883fd563ecf989d67c369085df4fc43d0c5f078
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400302"
---
# <a name="localservicesettings-element"></a><span data-ttu-id="394b4-102">\<localServiceSettings> 元素</span><span class="sxs-lookup"><span data-stu-id="394b4-102">\<localServiceSettings> element</span></span>
<span data-ttu-id="394b4-103">指定此绑定的本地服务安全设置。</span><span class="sxs-lookup"><span data-stu-id="394b4-103">Specifies the security settings of a local service for this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localServiceSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="394b4-104">语法</span><span class="sxs-lookup"><span data-stu-id="394b4-104">Syntax</span></span>  
  
```xml  
<security>
  <localServiceSettings detectReplays="Boolean"
                        inactivityTimeout="TimeSpan"
                        issuedCookieLifeTime="TimeSpan"
                        maxCachedCookies="Integer"
                        maxClockSkew="TimeSpan"
                        maxPendingSessions="Integer"
                        maxStatefulNegotiations="Integer"
                        negotiationTimeout="TimeSpan"
                        reconnectTransportOnFailure="Boolean"
                        replayCacheSize="Integer"
                        replayWindow="TimeSpan"
                        sessionKeyRenewalInterval="TimeSpan"
                        sessionKeyRolloverInterval="TimeSpan"
                        timestampValidityDuration="TimeSpan" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="394b4-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="394b4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="394b4-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="394b4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="394b4-107">特性</span><span class="sxs-lookup"><span data-stu-id="394b4-107">Attributes</span></span>  
  
|<span data-ttu-id="394b4-108">属性</span><span class="sxs-lookup"><span data-stu-id="394b4-108">Attribute</span></span>|<span data-ttu-id="394b4-109">说明</span><span class="sxs-lookup"><span data-stu-id="394b4-109">Description</span></span>|  
|---------------|-----------------|  
|`detectReplays`|<span data-ttu-id="394b4-110">一个布尔值，指定是否自动检测和处理针对通道的重放攻击。</span><span class="sxs-lookup"><span data-stu-id="394b4-110">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="394b4-111">默认为 `false`。</span><span class="sxs-lookup"><span data-stu-id="394b4-111">The default is `false`.</span></span>|  
|`inactivityTimeout`|<span data-ttu-id="394b4-112">一个正值 <xref:System.TimeSpan> ，指定通道在超时之前等待的无活动持续时间。默认值为 "01:00:00"。</span><span class="sxs-lookup"><span data-stu-id="394b4-112">A positive <xref:System.TimeSpan> that specifies the duration of inactivity the channel waits before it times out. The default is "01:00:00".</span></span>|  
|`issuedCookieLifeTime`|<span data-ttu-id="394b4-113">一个 <xref:System.TimeSpan>，指定颁发给所有新安全 Cookie 的生存期。</span><span class="sxs-lookup"><span data-stu-id="394b4-113">A <xref:System.TimeSpan> that specifies the lifetime issued to all new security cookies.</span></span> <span data-ttu-id="394b4-114">超过生存期的 Cookie 会被回收，且需要再次对其进行协商。</span><span class="sxs-lookup"><span data-stu-id="394b4-114">Cookies that exceed their lifetime are recycled and need to be negotiated again.</span></span> <span data-ttu-id="394b4-115">默认值为“10:00:00”。</span><span class="sxs-lookup"><span data-stu-id="394b4-115">The default value is "10:00:00".</span></span>|  
|`maxCachedCookies`|<span data-ttu-id="394b4-116">一个正整数，指定可以缓存的最大 Cookie 数。</span><span class="sxs-lookup"><span data-stu-id="394b4-116">A positive integer that specifies the maximum number of cookies that can be cached.</span></span> <span data-ttu-id="394b4-117">默认值为 1000。</span><span class="sxs-lookup"><span data-stu-id="394b4-117">The default is 1000.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="394b4-118">一个 <xref:System.TimeSpan>，指定通信双方的系统时钟之间的最大时间差异。</span><span class="sxs-lookup"><span data-stu-id="394b4-118">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="394b4-119">默认值为“00:05:00”。</span><span class="sxs-lookup"><span data-stu-id="394b4-119">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="394b4-120">当此值被设置为默认值时，接收方所接受的消息的发送时间时间戳最多可比消息接收时间晚或早 5 分钟。</span><span class="sxs-lookup"><span data-stu-id="394b4-120">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="394b4-121">未通过发送时间测试的消息会被拒绝。</span><span class="sxs-lookup"><span data-stu-id="394b4-121">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="394b4-122">此设置与 `replayWindow` 属性结合使用。</span><span class="sxs-lookup"><span data-stu-id="394b4-122">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxPendingSessions`|<span data-ttu-id="394b4-123">一个正整数，指定服务支持的最大挂起安全会话数。</span><span class="sxs-lookup"><span data-stu-id="394b4-123">A positive integer that specifies the maximum number of pending security sessions that the service supports.</span></span> <span data-ttu-id="394b4-124">达到此限制时，所有新客户端都会接收到 SOAP 错误。</span><span class="sxs-lookup"><span data-stu-id="394b4-124">When this limit is reached, all new clients receive SOAP faults.</span></span> <span data-ttu-id="394b4-125">默认值为 1000。</span><span class="sxs-lookup"><span data-stu-id="394b4-125">The default value is 1000.</span></span>|  
|`maxStatefulNegotiations`|<span data-ttu-id="394b4-126">一个正整数，指定可以同时处于活动状态的最大安全协商数。</span><span class="sxs-lookup"><span data-stu-id="394b4-126">A positive integer that specifies the number of security negotiations that can be active concurrently.</span></span> <span data-ttu-id="394b4-127">超出此限制的协商会话需要排队，直到会话数低于限制值。</span><span class="sxs-lookup"><span data-stu-id="394b4-127">Negotiation sessions in excess of the limit are queued and can only be completed when a space below the limit becomes available.</span></span> <span data-ttu-id="394b4-128">默认值为 1024。</span><span class="sxs-lookup"><span data-stu-id="394b4-128">The default value is 1024.</span></span>|  
|`negotiationTimeout`|<span data-ttu-id="394b4-129">一个 <xref:System.TimeSpan>，指定通道使用的安全策略的生存期。</span><span class="sxs-lookup"><span data-stu-id="394b4-129">A <xref:System.TimeSpan> that specifies the lifetime of the security policy used by channel.</span></span> <span data-ttu-id="394b4-130">如果超过此时间，则通道将与客户端重新协商新的安全策略。</span><span class="sxs-lookup"><span data-stu-id="394b4-130">When the time expires, the channel renegotiates with the client for a new security policy.</span></span> <span data-ttu-id="394b4-131">默认值为“00:02:00”。</span><span class="sxs-lookup"><span data-stu-id="394b4-131">The default value is "00:02:00".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="394b4-132">一个布尔值，指定使用 WS-ReliableMessaging 的连接是否将在传输失败后尝试重新连接。</span><span class="sxs-lookup"><span data-stu-id="394b4-132">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="394b4-133">默认值为 `true`，表示将进行无限次重新连接尝试。</span><span class="sxs-lookup"><span data-stu-id="394b4-133">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="394b4-134">非活动超时能够打断此循环；非活动超时在无法重新连接通道时使其引发异常。</span><span class="sxs-lookup"><span data-stu-id="394b4-134">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="394b4-135">一个正整数，指定用于重播检测的缓存 Nonce 的数目。</span><span class="sxs-lookup"><span data-stu-id="394b4-135">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="394b4-136">如果超出此限制，则会移除最旧的 Nonce，并且为新消息创建一个新的 Nonce。</span><span class="sxs-lookup"><span data-stu-id="394b4-136">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="394b4-137">默认值为 500000。</span><span class="sxs-lookup"><span data-stu-id="394b4-137">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="394b4-138">一个 <xref:System.TimeSpan>，指定单个消息 Nonce 有效的持续时间。</span><span class="sxs-lookup"><span data-stu-id="394b4-138">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="394b4-139">在此持续时间之后，如果发送的消息与之前发送的消息具有相同的 Nonce，则该消息将被拒绝。</span><span class="sxs-lookup"><span data-stu-id="394b4-139">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="394b4-140">此属性与 `maxClockSkew` 属性结合使用，以防止遭受重放攻击。</span><span class="sxs-lookup"><span data-stu-id="394b4-140">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="394b4-141">攻击者可以在其重放时间窗口过期之后重放消息。</span><span class="sxs-lookup"><span data-stu-id="394b4-141">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="394b4-142">但是，该消息将无法通过 `maxClockSkew` 测试；如果消息的发送时间时间戳比消息接收时间晚或早指定的时间，则该测试会拒绝消息。</span><span class="sxs-lookup"><span data-stu-id="394b4-142">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="394b4-143">一个 <xref:System.TimeSpan>，指定一段持续时间，发起方在此段时间之后将续订安全会话的密钥。</span><span class="sxs-lookup"><span data-stu-id="394b4-143">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="394b4-144">默认值为“10:00:00”。</span><span class="sxs-lookup"><span data-stu-id="394b4-144">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="394b4-145">一个 <xref:System.TimeSpan>，指定在密钥续订期间，上一个会话密钥对于传入消息有效的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="394b4-145">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="394b4-146">默认值为“00:05:00”。</span><span class="sxs-lookup"><span data-stu-id="394b4-146">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="394b4-147">在密钥续订期间，客户端和服务器必须总是使用最新的可用密钥来发送消息。</span><span class="sxs-lookup"><span data-stu-id="394b4-147">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="394b4-148">在延期时间到期前，双方都可以接受以上一个会话密钥加密的传入消息。</span><span class="sxs-lookup"><span data-stu-id="394b4-148">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="394b4-149">一个值为正的 <xref:System.TimeSpan>，指定时间戳有效的持续时间。</span><span class="sxs-lookup"><span data-stu-id="394b4-149">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="394b4-150">默认值为“00:15:00”。</span><span class="sxs-lookup"><span data-stu-id="394b4-150">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="394b4-151">子元素</span><span class="sxs-lookup"><span data-stu-id="394b4-151">Child Elements</span></span>  
 <span data-ttu-id="394b4-152">无。</span><span class="sxs-lookup"><span data-stu-id="394b4-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="394b4-153">父元素</span><span class="sxs-lookup"><span data-stu-id="394b4-153">Parent Elements</span></span>  
  
|<span data-ttu-id="394b4-154">元素</span><span class="sxs-lookup"><span data-stu-id="394b4-154">Element</span></span>|<span data-ttu-id="394b4-155">描述</span><span class="sxs-lookup"><span data-stu-id="394b4-155">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="394b4-156">指定自定义绑定的安全选项。</span><span class="sxs-lookup"><span data-stu-id="394b4-156">Specifies the security options for a custom binding.</span></span>|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="394b4-157">指定用于启动安全对话服务的默认值。</span><span class="sxs-lookup"><span data-stu-id="394b4-157">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="394b4-158">注解</span><span class="sxs-lookup"><span data-stu-id="394b4-158">Remarks</span></span>  
 <span data-ttu-id="394b4-159">这些设置并非作为安全策略的组成部分而发布，而且不影响客户端绑定，因此是本地的。</span><span class="sxs-lookup"><span data-stu-id="394b4-159">The settings are local because they are not published as part of the security policy of the service and do not affect the client's binding.</span></span>  
  
 <span data-ttu-id="394b4-160">`localServiceSecuritySettings` 元素的下列属性有助于缓解拒绝服务 (DOS) 安全攻击：</span><span class="sxs-lookup"><span data-stu-id="394b4-160">The following attributes of the `localServiceSecuritySettings` element can help mitigate a denial-of-service (DOS) security attack:</span></span>  
  
- <span data-ttu-id="394b4-161">`maxCachedCookies`：控制在执行 SPNEGO 或 SSL 协商之后服务器所缓存的有时限的 SecurityContextToken 的最大数目。</span><span class="sxs-lookup"><span data-stu-id="394b4-161">`maxCachedCookies`: controls the maximum number of time-bounded SecurityContextTokens that are cached by the server after doing SPNEGO or SSL negotiation.</span></span>  
  
- <span data-ttu-id="394b4-162">`issuedCookieLifetime`：控制在进行 SPNEGO 或 SSL 协商之后服务器所发布的 SecurityContextToken 的生命周期。</span><span class="sxs-lookup"><span data-stu-id="394b4-162">`issuedCookieLifetime`: controls the lifetime of the SecurityContextTokens that are issued by the server following SPNEGO or SSL negotiation.</span></span> <span data-ttu-id="394b4-163">服务器在此段时间之内缓存 SecurityContextToken。</span><span class="sxs-lookup"><span data-stu-id="394b4-163">The server caches the SecurityContextTokens for this period of time.</span></span>  
  
- <span data-ttu-id="394b4-164">`maxPendingSessions`：控制在服务器上建立但尚未针为其处理任何应用程序消息的安全对话的最大数目。</span><span class="sxs-lookup"><span data-stu-id="394b4-164">`maxPendingSessions`: controls the maximum number of secure conversations that are established at the server but for which no application messages have been processed.</span></span> <span data-ttu-id="394b4-165">此配额可防止客户端在服务上建立安全对话而导致服务维护每个客户端的状态，但是从不使用这些状态。</span><span class="sxs-lookup"><span data-stu-id="394b4-165">This quota prevents clients from establishing secure conversations at the service, thereby causing the service to maintain state for each client, but never using them.</span></span>  
  
- <span data-ttu-id="394b4-166">`inactivityTimeout`：控制服务使安全对话保持活动状态（但不接收服务上的应用程序消息）的最长时间。</span><span class="sxs-lookup"><span data-stu-id="394b4-166">`inactivityTimeout`: controls the maximum time that the service keeps a secure conversation alive without ever receiving an application message on it.</span></span> <span data-ttu-id="394b4-167">此配额可防止客户端在服务上建立安全对话而导致服务维护每个客户端的状态，但是从不使用这些状态。</span><span class="sxs-lookup"><span data-stu-id="394b4-167">This quota prevents clients from establishing secure conversations at the service, thereby causing the service to maintain state for each client, but never using them.</span></span>  
  
 <span data-ttu-id="394b4-168">请注意，在安全对话会话中，绑定上的 `inactivityTimeout` 和 `receiveTimeout` 属性将影响会话超时。</span><span class="sxs-lookup"><span data-stu-id="394b4-168">In a secure conversation session, note that both `inactivityTimeout` and the `receiveTimeout` attributes on the binding affect session timeout.</span></span> <span data-ttu-id="394b4-169">两个属性中时间较短者将确定何时发生超时。</span><span class="sxs-lookup"><span data-stu-id="394b4-169">The shorter of the two determines when timeouts occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="394b4-170">另请参阅</span><span class="sxs-lookup"><span data-stu-id="394b4-170">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="394b4-171">绑定</span><span class="sxs-lookup"><span data-stu-id="394b4-171">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="394b4-172">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="394b4-172">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="394b4-173">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="394b4-173">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="394b4-174">如何：使用 SecurityBindingElement 创建自定义绑定</span><span class="sxs-lookup"><span data-stu-id="394b4-174">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="394b4-175">自定义绑定安全性</span><span class="sxs-lookup"><span data-stu-id="394b4-175">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
