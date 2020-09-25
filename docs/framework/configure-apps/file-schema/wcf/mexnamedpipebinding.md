---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 64e250ae5ccb30da3f8857b94628b85b8c237a03
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204705"
---
# \<mexNamedPipeBinding>

<span data-ttu-id="1ae79-101">指定用于通过命名管道进行的 WS-MetadataExchange (WS-MEX) 消息交换的绑定的设置。</span><span class="sxs-lookup"><span data-stu-id="1ae79-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexNamedPipeBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="1ae79-102">语法</span><span class="sxs-lookup"><span data-stu-id="1ae79-102">Syntax</span></span>  
  
```xml  
<mexNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ae79-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1ae79-103">Attributes and Elements</span></span>  

 <span data-ttu-id="1ae79-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1ae79-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ae79-105">特性</span><span class="sxs-lookup"><span data-stu-id="1ae79-105">Attributes</span></span>  
  
|<span data-ttu-id="1ae79-106">属性</span><span class="sxs-lookup"><span data-stu-id="1ae79-106">Attribute</span></span>|<span data-ttu-id="1ae79-107">描述</span><span class="sxs-lookup"><span data-stu-id="1ae79-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="1ae79-108">一个 <xref:System.TimeSpan> 值，指定为完成关闭操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1ae79-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1ae79-109">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1ae79-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1ae79-110">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1ae79-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="1ae79-111">一个包含绑定的配置名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="1ae79-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="1ae79-112">因为此值用作绑定的标识，所以它应该是唯一的。</span><span class="sxs-lookup"><span data-stu-id="1ae79-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="1ae79-113">从 .NET Framework 4 开始，绑定和行为不需要具有名称。</span><span class="sxs-lookup"><span data-stu-id="1ae79-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1ae79-114">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="1ae79-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="1ae79-115">一个 <xref:System.TimeSpan> 值，指定为完成打开操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1ae79-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1ae79-116">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1ae79-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1ae79-117">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1ae79-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="1ae79-118">一个 <xref:System.TimeSpan> 值，指定为完成接收操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1ae79-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1ae79-119">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1ae79-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1ae79-120">默认值为 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="1ae79-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="1ae79-121">一个 <xref:System.TimeSpan> 值，指定为完成发送操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1ae79-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1ae79-122">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1ae79-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1ae79-123">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1ae79-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ae79-124">子元素</span><span class="sxs-lookup"><span data-stu-id="1ae79-124">Child Elements</span></span>  

 <span data-ttu-id="1ae79-125">无。</span><span class="sxs-lookup"><span data-stu-id="1ae79-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ae79-126">父元素</span><span class="sxs-lookup"><span data-stu-id="1ae79-126">Parent Elements</span></span>  
  
|<span data-ttu-id="1ae79-127">元素</span><span class="sxs-lookup"><span data-stu-id="1ae79-127">Element</span></span>|<span data-ttu-id="1ae79-128">描述</span><span class="sxs-lookup"><span data-stu-id="1ae79-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="1ae79-129">此元素包含标准绑定和自定义绑定的集合。</span><span class="sxs-lookup"><span data-stu-id="1ae79-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ae79-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="1ae79-130">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="1ae79-131">如何：使用配置文件发布服务的元数据</span><span class="sxs-lookup"><span data-stu-id="1ae79-131">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="1ae79-132">通过自定义绑定发布和检索元数据</span><span class="sxs-lookup"><span data-stu-id="1ae79-132">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- <span data-ttu-id="1ae79-133">Metadata </span><span class="sxs-lookup"><span data-stu-id="1ae79-133">[Metadata](../../../wcf/feature-details/metadata.md)</span></span>
- [<span data-ttu-id="1ae79-134">绑定</span><span class="sxs-lookup"><span data-stu-id="1ae79-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1ae79-135">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="1ae79-135">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1ae79-136">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="1ae79-136">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
