---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 6167a4ad56a9481a9f695b770605991a0a88d2d9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399404"
---
# \<transactedBatching>

<span data-ttu-id="629d4-101">指定接收操作是否支持事务批处理。</span><span class="sxs-lookup"><span data-stu-id="629d4-101">Specifies whether transaction batching is supported for receive operations.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactedBatching>**  

## <a name="syntax"></a><span data-ttu-id="629d4-102">语法</span><span class="sxs-lookup"><span data-stu-id="629d4-102">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="629d4-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="629d4-103">Attributes and Elements</span></span>

<span data-ttu-id="629d4-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="629d4-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="629d4-105">特性</span><span class="sxs-lookup"><span data-stu-id="629d4-105">Attributes</span></span>

|<span data-ttu-id="629d4-106">属性</span><span class="sxs-lookup"><span data-stu-id="629d4-106">Attribute</span></span>|<span data-ttu-id="629d4-107">说明</span><span class="sxs-lookup"><span data-stu-id="629d4-107">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="629d4-108">一个整数，指定可一起成批归入到一个事务中的最大接收操作数。</span><span class="sxs-lookup"><span data-stu-id="629d4-108">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="629d4-109">默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="629d4-109">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="629d4-110">子元素</span><span class="sxs-lookup"><span data-stu-id="629d4-110">Child Elements</span></span>

<span data-ttu-id="629d4-111">无。</span><span class="sxs-lookup"><span data-stu-id="629d4-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="629d4-112">父元素</span><span class="sxs-lookup"><span data-stu-id="629d4-112">Parent Elements</span></span>

|<span data-ttu-id="629d4-113">元素</span><span class="sxs-lookup"><span data-stu-id="629d4-113">Element</span></span>|<span data-ttu-id="629d4-114">描述</span><span class="sxs-lookup"><span data-stu-id="629d4-114">Description</span></span>|
|-------------|-----------------|
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="629d4-115">指定终结点行为。</span><span class="sxs-lookup"><span data-stu-id="629d4-115">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="629d4-116">注解</span><span class="sxs-lookup"><span data-stu-id="629d4-116">Remarks</span></span>

<span data-ttu-id="629d4-117">采用事务批处理配置的传输尝试将若干接收操作成批归入到一个事务中。</span><span class="sxs-lookup"><span data-stu-id="629d4-117">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="629d4-118">这样做可以避免因创建事务以及在每个接收操作中提交事务所产生的相对较高的成本。</span><span class="sxs-lookup"><span data-stu-id="629d4-118">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="629d4-119">示例</span><span class="sxs-lookup"><span data-stu-id="629d4-119">Example</span></span>

<span data-ttu-id="629d4-120">下面的示例演示如何将事务处理批处理行为添加到配置文件中的服务。</span><span class="sxs-lookup"><span data-stu-id="629d4-120">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamples"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IQueueCalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <behaviors>
    <endpointBehaviors>
      <behavior name="endpointBehavior">
        <transactedBatching maxBatchSize="10" />
      </behavior>
    </endpointBehaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="true" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```

## <a name="see-also"></a><span data-ttu-id="629d4-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="629d4-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
