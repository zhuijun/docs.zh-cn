---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 8c15b06e60e4de6ede4c9a683a6701140533534c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204731"
---
# \<mexHttpBinding>

<span data-ttu-id="99c31-101">指定用于通过 HTTP 进行的 WS-MetadataExchange (WS-MEX) 消息交换的绑定的设置。</span><span class="sxs-lookup"><span data-stu-id="99c31-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="99c31-102">语法</span><span class="sxs-lookup"><span data-stu-id="99c31-102">Syntax</span></span>  
  
```xml  
<mexHttpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99c31-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="99c31-103">Attributes and Elements</span></span>  

 <span data-ttu-id="99c31-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="99c31-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99c31-105">特性</span><span class="sxs-lookup"><span data-stu-id="99c31-105">Attributes</span></span>  
  
|<span data-ttu-id="99c31-106">属性</span><span class="sxs-lookup"><span data-stu-id="99c31-106">Attribute</span></span>|<span data-ttu-id="99c31-107">描述</span><span class="sxs-lookup"><span data-stu-id="99c31-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="99c31-108">一个 <xref:System.TimeSpan> 值，指定为完成关闭操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="99c31-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="99c31-109">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="99c31-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="99c31-110">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="99c31-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="99c31-111">一个包含绑定的配置名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="99c31-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="99c31-112">因为此值用作绑定的标识，所以它应该是唯一的。</span><span class="sxs-lookup"><span data-stu-id="99c31-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="99c31-113">从 .NET Framework 4 开始，绑定和行为不需要具有名称。</span><span class="sxs-lookup"><span data-stu-id="99c31-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="99c31-114">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="99c31-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="99c31-115">一个 <xref:System.TimeSpan> 值，指定为完成打开操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="99c31-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="99c31-116">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="99c31-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="99c31-117">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="99c31-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="99c31-118">一个 <xref:System.TimeSpan> 值，指定为完成接收操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="99c31-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="99c31-119">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="99c31-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="99c31-120">默认值为 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="99c31-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="99c31-121">一个 <xref:System.TimeSpan> 值，指定为完成发送操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="99c31-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="99c31-122">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="99c31-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="99c31-123">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="99c31-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99c31-124">子元素</span><span class="sxs-lookup"><span data-stu-id="99c31-124">Child Elements</span></span>  

 <span data-ttu-id="99c31-125">无。</span><span class="sxs-lookup"><span data-stu-id="99c31-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99c31-126">父元素</span><span class="sxs-lookup"><span data-stu-id="99c31-126">Parent Elements</span></span>  
  
|<span data-ttu-id="99c31-127">元素</span><span class="sxs-lookup"><span data-stu-id="99c31-127">Element</span></span>|<span data-ttu-id="99c31-128">描述</span><span class="sxs-lookup"><span data-stu-id="99c31-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="99c31-129">此元素包含标准绑定和自定义绑定的集合。</span><span class="sxs-lookup"><span data-stu-id="99c31-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99c31-130">备注</span><span class="sxs-lookup"><span data-stu-id="99c31-130">Remarks</span></span>  

 <span data-ttu-id="99c31-131">此绑定实质上是一个禁用了安全性的 `WSHttpBinding` 绑定。</span><span class="sxs-lookup"><span data-stu-id="99c31-131">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="99c31-132">它支持大多数元数据请求。</span><span class="sxs-lookup"><span data-stu-id="99c31-132">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c31-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="99c31-133">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="99c31-134">如何：使用配置文件发布服务的元数据</span><span class="sxs-lookup"><span data-stu-id="99c31-134">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="99c31-135">通过自定义绑定发布和检索元数据</span><span class="sxs-lookup"><span data-stu-id="99c31-135">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- <span data-ttu-id="99c31-136">Metadata </span><span class="sxs-lookup"><span data-stu-id="99c31-136">[Metadata](../../../wcf/feature-details/metadata.md)</span></span>
- [<span data-ttu-id="99c31-137">绑定</span><span class="sxs-lookup"><span data-stu-id="99c31-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="99c31-138">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="99c31-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="99c31-139">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="99c31-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
