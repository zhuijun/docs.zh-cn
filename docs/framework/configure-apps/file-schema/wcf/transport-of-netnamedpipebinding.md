---
title: <transport> 的 <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: d40178e59b89c2912123e1927e9e960f6d880871
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735958"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="0dc65-102">\<transport> 的 \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="0dc65-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="0dc65-103">定义命名管道的传输安全设置。</span><span class="sxs-lookup"><span data-stu-id="0dc65-103">Defines the transport security settings for a named pipe.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="0dc65-104">语法</span><span class="sxs-lookup"><span data-stu-id="0dc65-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0dc65-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="0dc65-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0dc65-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0dc65-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0dc65-107">特性</span><span class="sxs-lookup"><span data-stu-id="0dc65-107">Attributes</span></span>  
  
|<span data-ttu-id="0dc65-108">属性</span><span class="sxs-lookup"><span data-stu-id="0dc65-108">Attribute</span></span>|<span data-ttu-id="0dc65-109">说明</span><span class="sxs-lookup"><span data-stu-id="0dc65-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0dc65-110">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="0dc65-110">protectionLevel</span></span>|<span data-ttu-id="0dc65-111">定义命名管道的保护级别。</span><span class="sxs-lookup"><span data-stu-id="0dc65-111">Defines protection level of the named pipe.</span></span> <span data-ttu-id="0dc65-112">消息签名降低了在消息传输过程中第三方对消息进行篡改的风险。</span><span class="sxs-lookup"><span data-stu-id="0dc65-112">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="0dc65-113">加密为传输过程提供了数据级保密功能。</span><span class="sxs-lookup"><span data-stu-id="0dc65-113">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="0dc65-114">有效值包括以下值：</span><span class="sxs-lookup"><span data-stu-id="0dc65-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0dc65-115">-None：无保护。</span><span class="sxs-lookup"><span data-stu-id="0dc65-115">-   None: No protection.</span></span><br /><span data-ttu-id="0dc65-116">-Sign：对消息进行签名。</span><span class="sxs-lookup"><span data-stu-id="0dc65-116">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="0dc65-117">-EncryptAndSign：对消息进行加密和签名。</span><span class="sxs-lookup"><span data-stu-id="0dc65-117">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="0dc65-118">默认值为 EncryptAndSign。</span><span class="sxs-lookup"><span data-stu-id="0dc65-118">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0dc65-119">子元素</span><span class="sxs-lookup"><span data-stu-id="0dc65-119">Child Elements</span></span>  
 <span data-ttu-id="0dc65-120">无</span><span class="sxs-lookup"><span data-stu-id="0dc65-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0dc65-121">父元素</span><span class="sxs-lookup"><span data-stu-id="0dc65-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0dc65-122">元素</span><span class="sxs-lookup"><span data-stu-id="0dc65-122">Element</span></span>|<span data-ttu-id="0dc65-123">描述</span><span class="sxs-lookup"><span data-stu-id="0dc65-123">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="0dc65-124">定义绑定的安全设置。</span><span class="sxs-lookup"><span data-stu-id="0dc65-124">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0dc65-125">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0dc65-125">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="0dc65-126">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="0dc65-126">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0dc65-127">绑定</span><span class="sxs-lookup"><span data-stu-id="0dc65-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0dc65-128">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="0dc65-128">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0dc65-129">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="0dc65-129">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
