---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 8d0ae2a1848eaf28c2e408542b8209cf968de4c1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430301"
---
# \<mexTcpBinding>
<span data-ttu-id="7337b-101">指定用于通过 TCP 进行的 WS-MetadataExchange (WS-MEX) 消息交换的绑定的设置。</span><span class="sxs-lookup"><span data-stu-id="7337b-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="7337b-102">语法</span><span class="sxs-lookup"><span data-stu-id="7337b-102">Syntax</span></span>  
  
```xml  
<mexTcpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7337b-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="7337b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7337b-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7337b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7337b-105">特性</span><span class="sxs-lookup"><span data-stu-id="7337b-105">Attributes</span></span>  
  
|<span data-ttu-id="7337b-106">属性</span><span class="sxs-lookup"><span data-stu-id="7337b-106">Attribute</span></span>|<span data-ttu-id="7337b-107">说明</span><span class="sxs-lookup"><span data-stu-id="7337b-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="7337b-108">一个 <xref:System.TimeSpan> 值，指定为完成关闭操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="7337b-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7337b-109">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="7337b-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7337b-110">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="7337b-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="7337b-111">一个包含绑定的配置名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="7337b-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="7337b-112">因为此值用作绑定的标识，所以它应该是唯一的。</span><span class="sxs-lookup"><span data-stu-id="7337b-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7337b-113">从 .NET Framework 4 开始，绑定和行为不需要具有名称。</span><span class="sxs-lookup"><span data-stu-id="7337b-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7337b-114">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="7337b-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="7337b-115">一个 <xref:System.TimeSpan> 值，指定为完成打开操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="7337b-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7337b-116">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="7337b-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7337b-117">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="7337b-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="7337b-118">一个 <xref:System.TimeSpan> 值，指定为完成接收操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="7337b-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7337b-119">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="7337b-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7337b-120">默认值为 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="7337b-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="7337b-121">一个 <xref:System.TimeSpan> 值，指定为完成发送操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="7337b-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7337b-122">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="7337b-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7337b-123">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="7337b-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7337b-124">子元素</span><span class="sxs-lookup"><span data-stu-id="7337b-124">Child Elements</span></span>  
 <span data-ttu-id="7337b-125">无。</span><span class="sxs-lookup"><span data-stu-id="7337b-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7337b-126">父元素</span><span class="sxs-lookup"><span data-stu-id="7337b-126">Parent Elements</span></span>  
  
|<span data-ttu-id="7337b-127">元素</span><span class="sxs-lookup"><span data-stu-id="7337b-127">Element</span></span>|<span data-ttu-id="7337b-128">描述</span><span class="sxs-lookup"><span data-stu-id="7337b-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="7337b-129">此元素包含标准绑定和自定义绑定的集合。</span><span class="sxs-lookup"><span data-stu-id="7337b-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7337b-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7337b-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="7337b-131">如何：使用配置文件发布服务的元数据</span><span class="sxs-lookup"><span data-stu-id="7337b-131">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="7337b-132">通过自定义绑定发布和检索元数据</span><span class="sxs-lookup"><span data-stu-id="7337b-132">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="7337b-133">元数据</span><span class="sxs-lookup"><span data-stu-id="7337b-133">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="7337b-134">绑定</span><span class="sxs-lookup"><span data-stu-id="7337b-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7337b-135">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="7337b-135">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7337b-136">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="7337b-136">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
