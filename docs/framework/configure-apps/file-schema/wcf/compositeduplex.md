---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: a5209efddd489f8cb04b3266e6ba0bb033eeae6c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176014"
---
# \<compositeDuplex>

<span data-ttu-id="a7274-101">定义绑定元素，客户端在必须公开一个终结点以使服务可以将消息发送回客户端时使用此元素。</span><span class="sxs-lookup"><span data-stu-id="a7274-101">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**  
  
## <a name="syntax"></a><span data-ttu-id="a7274-102">语法</span><span class="sxs-lookup"><span data-stu-id="a7274-102">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7274-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a7274-103">Attributes and Elements</span></span>  

 <span data-ttu-id="a7274-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a7274-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7274-105">特性</span><span class="sxs-lookup"><span data-stu-id="a7274-105">Attributes</span></span>  
  
|<span data-ttu-id="a7274-106">属性</span><span class="sxs-lookup"><span data-stu-id="a7274-106">Attribute</span></span>|<span data-ttu-id="a7274-107">描述</span><span class="sxs-lookup"><span data-stu-id="a7274-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7274-108">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="a7274-108">clientBaseAddress</span></span>|<span data-ttu-id="a7274-109">一个在双工模式下设置反向通道地址的 URI。</span><span class="sxs-lookup"><span data-stu-id="a7274-109">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="a7274-110">服务使用该地址与客户端进行联系和建立连接。</span><span class="sxs-lookup"><span data-stu-id="a7274-110">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="a7274-111">如果未设置此属性，则生成默认地址 " `full qualified name+default port\TemporaryIndigoAddress\guid` "。</span><span class="sxs-lookup"><span data-stu-id="a7274-111">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="a7274-112">默认为 `null`。</span><span class="sxs-lookup"><span data-stu-id="a7274-112">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7274-113">子元素</span><span class="sxs-lookup"><span data-stu-id="a7274-113">Child Elements</span></span>  

 <span data-ttu-id="a7274-114">无</span><span class="sxs-lookup"><span data-stu-id="a7274-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7274-115">父元素</span><span class="sxs-lookup"><span data-stu-id="a7274-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a7274-116">元素</span><span class="sxs-lookup"><span data-stu-id="a7274-116">Element</span></span>|<span data-ttu-id="a7274-117">描述</span><span class="sxs-lookup"><span data-stu-id="a7274-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="a7274-118">定义自定义绑定的所有绑定功能。</span><span class="sxs-lookup"><span data-stu-id="a7274-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7274-119">备注</span><span class="sxs-lookup"><span data-stu-id="a7274-119">Remarks</span></span>  

 <span data-ttu-id="a7274-120">此配置元素与本身不允许进行双工通信的传输（例如，HTTP）一起使用。</span><span class="sxs-lookup"><span data-stu-id="a7274-120">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="a7274-121">与此相反，TCP 本身允许进行双工通信，并且不要求服务在将消息发送回客户端时使用此绑定元素。</span><span class="sxs-lookup"><span data-stu-id="a7274-121">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="a7274-122">客户端必须公开一个地址，以便服务进行联系和建立连接。</span><span class="sxs-lookup"><span data-stu-id="a7274-122">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="a7274-123">此客户端地址由 `clientBaseAddress` 属性提供。</span><span class="sxs-lookup"><span data-stu-id="a7274-123">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="a7274-124">请注意，如果用户未显式设置 ClientBaseAddress，则 Windows Communication Foundation (WCF) 将自动生成一个 ClientBaseAddress。</span><span class="sxs-lookup"><span data-stu-id="a7274-124">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7274-125">示例</span><span class="sxs-lookup"><span data-stu-id="a7274-125">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="a7274-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="a7274-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a7274-127">绑定</span><span class="sxs-lookup"><span data-stu-id="a7274-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a7274-128">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="a7274-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a7274-129">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="a7274-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
