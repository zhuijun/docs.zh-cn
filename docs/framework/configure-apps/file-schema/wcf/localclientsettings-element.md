---
title: <localClientSettings> 元素
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: 19eaea71fdaad1b945524cca5cf15634e0b0fa14
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158729"
---
# <a name="localclientsettings-element"></a><span data-ttu-id="0d75b-102">\<localClientSettings> 元素</span><span class="sxs-lookup"><span data-stu-id="0d75b-102">\<localClientSettings> element</span></span>

<span data-ttu-id="0d75b-103">指定此绑定的本地客户端安全设置。</span><span class="sxs-lookup"><span data-stu-id="0d75b-103">Specifies the security settings of a local client for this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="0d75b-104">语法</span><span class="sxs-lookup"><span data-stu-id="0d75b-104">Syntax</span></span>  
  
```xml  
<security>
   <localClientSettings cacheCookies="Boolean"
                        cookieRenewalThresholdPercentage="Integer"
                        detectReplays="Boolean"
                        maxClockSkew="TimeSpan"
                        maxCookieCachingTime="TimeSpan"
                        reconnectTransportOnFailure="Boolean"
                        replayCacheSize="Integer"
                        replayWindow="TimeSpan"
                        sessionKeyRenewalInterval="TimeSpan"
                        sessionKeyRolloverInterval="TimeSpan"
                        timestampValidityDuration="TimeSpan" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d75b-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0d75b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="0d75b-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0d75b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d75b-107">特性</span><span class="sxs-lookup"><span data-stu-id="0d75b-107">Attributes</span></span>  
  
|<span data-ttu-id="0d75b-108">属性</span><span class="sxs-lookup"><span data-stu-id="0d75b-108">Attribute</span></span>|<span data-ttu-id="0d75b-109">描述</span><span class="sxs-lookup"><span data-stu-id="0d75b-109">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="0d75b-110">一个布尔值，指定是否启用 Cookie 缓存。</span><span class="sxs-lookup"><span data-stu-id="0d75b-110">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="0d75b-111">默认为 `false`。</span><span class="sxs-lookup"><span data-stu-id="0d75b-111">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="0d75b-112">一个整数，指定可续订的最大 Cookie 百分比。</span><span class="sxs-lookup"><span data-stu-id="0d75b-112">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="0d75b-113">该值应介于 0 至 100 之间（包括这两个数）。</span><span class="sxs-lookup"><span data-stu-id="0d75b-113">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="0d75b-114">默认值为 90。</span><span class="sxs-lookup"><span data-stu-id="0d75b-114">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="0d75b-115">一个布尔值，指定是否自动检测和处理针对通道的重放攻击。</span><span class="sxs-lookup"><span data-stu-id="0d75b-115">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="0d75b-116">默认为 `false`。</span><span class="sxs-lookup"><span data-stu-id="0d75b-116">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="0d75b-117">一个 <xref:System.TimeSpan>，指定通信双方的系统时钟之间的最大时间差异。</span><span class="sxs-lookup"><span data-stu-id="0d75b-117">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="0d75b-118">默认值为“00:05:00”。</span><span class="sxs-lookup"><span data-stu-id="0d75b-118">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="0d75b-119">当此值被设置为默认值时，接收方所接受的消息的发送时间时间戳最多可比消息接收时间晚或早 5 分钟。</span><span class="sxs-lookup"><span data-stu-id="0d75b-119">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="0d75b-120">未通过发送时间测试的消息会被拒绝。</span><span class="sxs-lookup"><span data-stu-id="0d75b-120">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="0d75b-121">此设置与 `replayWindow` 属性结合使用。</span><span class="sxs-lookup"><span data-stu-id="0d75b-121">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="0d75b-122">一个 <xref:System.TimeSpan>，指定 Cookie 的最长生存期。</span><span class="sxs-lookup"><span data-stu-id="0d75b-122">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="0d75b-123">默认值为“10675199.02:48:05.4775807”。</span><span class="sxs-lookup"><span data-stu-id="0d75b-123">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="0d75b-124">一个布尔值，指定使用 WS-ReliableMessaging 的连接是否将在传输失败后尝试重新连接。</span><span class="sxs-lookup"><span data-stu-id="0d75b-124">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="0d75b-125">默认值为 `true`，表示将进行无限次重新连接尝试。</span><span class="sxs-lookup"><span data-stu-id="0d75b-125">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="0d75b-126">非活动超时能够打断此循环；非活动超时在无法重新连接通道时使其引发异常。</span><span class="sxs-lookup"><span data-stu-id="0d75b-126">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="0d75b-127">一个正整数，指定用于重播检测的缓存 Nonce 的数目。</span><span class="sxs-lookup"><span data-stu-id="0d75b-127">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="0d75b-128">如果超出此限制，则会移除最旧的 Nonce，并且为新消息创建一个新的 Nonce。</span><span class="sxs-lookup"><span data-stu-id="0d75b-128">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="0d75b-129">默认值为 500000。</span><span class="sxs-lookup"><span data-stu-id="0d75b-129">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="0d75b-130">一个 <xref:System.TimeSpan>，指定单个消息 Nonce 有效的持续时间。</span><span class="sxs-lookup"><span data-stu-id="0d75b-130">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="0d75b-131">在此持续时间之后，如果发送的消息与之前发送的消息具有相同的 Nonce，则该消息将被拒绝。</span><span class="sxs-lookup"><span data-stu-id="0d75b-131">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="0d75b-132">此属性与 `maxClockSkew` 属性结合使用，以防止遭受重放攻击。</span><span class="sxs-lookup"><span data-stu-id="0d75b-132">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="0d75b-133">攻击者可以在其重放时间窗口过期之后重放消息。</span><span class="sxs-lookup"><span data-stu-id="0d75b-133">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="0d75b-134">但是，该消息将无法通过 `maxClockSkew` 测试；如果消息的发送时间时间戳比消息接收时间晚或早指定的时间，则该测试会拒绝消息。</span><span class="sxs-lookup"><span data-stu-id="0d75b-134">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="0d75b-135">一个 <xref:System.TimeSpan>，指定一段持续时间，发起方在此段时间之后将续订安全会话的密钥。</span><span class="sxs-lookup"><span data-stu-id="0d75b-135">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="0d75b-136">默认值为“10:00:00”。</span><span class="sxs-lookup"><span data-stu-id="0d75b-136">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="0d75b-137">一个 <xref:System.TimeSpan>，指定在密钥续订期间，上一个会话密钥对于传入消息有效的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="0d75b-137">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="0d75b-138">默认值为“00:05:00”。</span><span class="sxs-lookup"><span data-stu-id="0d75b-138">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="0d75b-139">在密钥续订期间，客户端和服务器必须总是使用最新的可用密钥来发送消息。</span><span class="sxs-lookup"><span data-stu-id="0d75b-139">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="0d75b-140">在延期时间到期前，双方都可以接受以上一个会话密钥加密的传入消息。</span><span class="sxs-lookup"><span data-stu-id="0d75b-140">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="0d75b-141">一个值为正的 <xref:System.TimeSpan>，指定时间戳有效的持续时间。</span><span class="sxs-lookup"><span data-stu-id="0d75b-141">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="0d75b-142">默认值为“00:15:00”。</span><span class="sxs-lookup"><span data-stu-id="0d75b-142">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d75b-143">子元素</span><span class="sxs-lookup"><span data-stu-id="0d75b-143">Child Elements</span></span>  

 <span data-ttu-id="0d75b-144">无</span><span class="sxs-lookup"><span data-stu-id="0d75b-144">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d75b-145">父元素</span><span class="sxs-lookup"><span data-stu-id="0d75b-145">Parent Elements</span></span>  
  
|<span data-ttu-id="0d75b-146">元素</span><span class="sxs-lookup"><span data-stu-id="0d75b-146">Element</span></span>|<span data-ttu-id="0d75b-147">描述</span><span class="sxs-lookup"><span data-stu-id="0d75b-147">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="0d75b-148">指定自定义绑定的安全选项。</span><span class="sxs-lookup"><span data-stu-id="0d75b-148">Specifies the security options for a custom binding.</span></span>|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="0d75b-149">指定用于启动安全对话服务的默认值。</span><span class="sxs-lookup"><span data-stu-id="0d75b-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d75b-150">备注</span><span class="sxs-lookup"><span data-stu-id="0d75b-150">Remarks</span></span>  

 <span data-ttu-id="0d75b-151">这些设置不是从服务的安全策略派生而来的，从这个意义上说，它们是本地的。</span><span class="sxs-lookup"><span data-stu-id="0d75b-151">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d75b-152">请参阅</span><span class="sxs-lookup"><span data-stu-id="0d75b-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="0d75b-153">绑定</span><span class="sxs-lookup"><span data-stu-id="0d75b-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0d75b-154">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="0d75b-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0d75b-155">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="0d75b-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="0d75b-156">如何：使用 SecurityBindingElement 创建自定义绑定</span><span class="sxs-lookup"><span data-stu-id="0d75b-156">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="0d75b-157">自定义绑定安全性</span><span class="sxs-lookup"><span data-stu-id="0d75b-157">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
