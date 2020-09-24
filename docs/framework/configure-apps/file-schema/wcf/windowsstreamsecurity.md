---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: 3c82bd81bd0fabf10f2dd835188b346f62d038b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167075"
---
# \<windowsStreamSecurity>

<span data-ttu-id="3c885-101">指定自定义绑定的 Windows 流安全设置。</span><span class="sxs-lookup"><span data-stu-id="3c885-101">Specify Windows stream security settings of the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="3c885-102">语法</span><span class="sxs-lookup"><span data-stu-id="3c885-102">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c885-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="3c885-103">Attributes and Elements</span></span>  

 <span data-ttu-id="3c885-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3c885-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c885-105">特性</span><span class="sxs-lookup"><span data-stu-id="3c885-105">Attributes</span></span>  
  
|<span data-ttu-id="3c885-106">属性</span><span class="sxs-lookup"><span data-stu-id="3c885-106">Attribute</span></span>|<span data-ttu-id="3c885-107">描述</span><span class="sxs-lookup"><span data-stu-id="3c885-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c885-108">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="3c885-108">protectionLevel</span></span>|<span data-ttu-id="3c885-109">定义消息级安全性。</span><span class="sxs-lookup"><span data-stu-id="3c885-109">Defines message-level security.</span></span> <span data-ttu-id="3c885-110">消息签名降低了在消息传输过程中第三方对消息进行篡改的风险。</span><span class="sxs-lookup"><span data-stu-id="3c885-110">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="3c885-111">加密为传输过程提供了数据级保密功能。</span><span class="sxs-lookup"><span data-stu-id="3c885-111">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="3c885-112">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="3c885-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3c885-113">-None：无保护。</span><span class="sxs-lookup"><span data-stu-id="3c885-113">-   None: No protection.</span></span><br /><span data-ttu-id="3c885-114">-Sign：对消息进行签名。</span><span class="sxs-lookup"><span data-stu-id="3c885-114">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="3c885-115">-EncryptAndSign：对消息进行签名和加密。</span><span class="sxs-lookup"><span data-stu-id="3c885-115">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="3c885-116">默认值为 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="3c885-116">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="3c885-117">此属性的类型为 <xref:System.Net.Security.ProtectionLevel>。</span><span class="sxs-lookup"><span data-stu-id="3c885-117">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c885-118">子元素</span><span class="sxs-lookup"><span data-stu-id="3c885-118">Child Elements</span></span>  

 <span data-ttu-id="3c885-119">无</span><span class="sxs-lookup"><span data-stu-id="3c885-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c885-120">父元素</span><span class="sxs-lookup"><span data-stu-id="3c885-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3c885-121">元素</span><span class="sxs-lookup"><span data-stu-id="3c885-121">Element</span></span>|<span data-ttu-id="3c885-122">描述</span><span class="sxs-lookup"><span data-stu-id="3c885-122">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="3c885-123">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="3c885-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c885-124">备注</span><span class="sxs-lookup"><span data-stu-id="3c885-124">Remarks</span></span>  

 <span data-ttu-id="3c885-125">使用面向流协议（如 TCP 和命名管道）的传输支持基于流的传输升级。</span><span class="sxs-lookup"><span data-stu-id="3c885-125">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="3c885-126">特别是 WCF 提供了安全升级。</span><span class="sxs-lookup"><span data-stu-id="3c885-126">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="3c885-127">此传输安全的配置由此配置元素以及 [\<sslStreamSecurity>](sslstreamsecurity.md) 可配置并添加到自定义绑定中的进行封装</span><span class="sxs-lookup"><span data-stu-id="3c885-127">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c885-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="3c885-128">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="3c885-129">绑定</span><span class="sxs-lookup"><span data-stu-id="3c885-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3c885-130">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="3c885-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3c885-131">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="3c885-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
