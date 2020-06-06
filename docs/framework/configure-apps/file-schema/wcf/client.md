---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7aa3755be97a839cb576d53852b75cfe50e39276
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "72773943"
---
# \<client>
<span data-ttu-id="8c199-101">`client` 元素定义客户端可以连接的终结点的列表。</span><span class="sxs-lookup"><span data-stu-id="8c199-101">The `client` element defines a list of endpoints that a client can connect to.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**

## <a name="syntax"></a><span data-ttu-id="8c199-102">语法</span><span class="sxs-lookup"><span data-stu-id="8c199-102">Syntax</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8c199-103">特性和元素</span><span class="sxs-lookup"><span data-stu-id="8c199-103">Attributes and Elements</span></span>
 <span data-ttu-id="8c199-104">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8c199-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8c199-105">特性</span><span class="sxs-lookup"><span data-stu-id="8c199-105">Attributes</span></span>
 <span data-ttu-id="8c199-106">无</span><span class="sxs-lookup"><span data-stu-id="8c199-106">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="8c199-107">子元素</span><span class="sxs-lookup"><span data-stu-id="8c199-107">Child Elements</span></span>

|<span data-ttu-id="8c199-108">元素</span><span class="sxs-lookup"><span data-stu-id="8c199-108">Element</span></span>|<span data-ttu-id="8c199-109">说明</span><span class="sxs-lookup"><span data-stu-id="8c199-109">Description</span></span>|
|-------------|-----------------|
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="8c199-110">包含终结点元素的集合，这些元素指定此客户端可以连接到的终结点。</span><span class="sxs-lookup"><span data-stu-id="8c199-110">Contains a collection of endpoint elements that specify the endpoints that this client can connect to.</span></span>|
|[\<metadata>](metadata.md)|<span data-ttu-id="8c199-111">包含用于处理元数据的设置。</span><span class="sxs-lookup"><span data-stu-id="8c199-111">Contains settings for processing metadata.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8c199-112">父元素</span><span class="sxs-lookup"><span data-stu-id="8c199-112">Parent Elements</span></span>

|<span data-ttu-id="8c199-113">元素</span><span class="sxs-lookup"><span data-stu-id="8c199-113">Element</span></span>|<span data-ttu-id="8c199-114">说明</span><span class="sxs-lookup"><span data-stu-id="8c199-114">Description</span></span>|
|-------------|-----------------|
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="8c199-115">所有 Windows Communication Foundation (WCF) 配置元素的根元素。</span><span class="sxs-lookup"><span data-stu-id="8c199-115">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8c199-116">注解</span><span class="sxs-lookup"><span data-stu-id="8c199-116">Remarks</span></span>
 <span data-ttu-id="8c199-117">`client` 节定义客户端可以连接的终结点的列表。</span><span class="sxs-lookup"><span data-stu-id="8c199-117">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="8c199-118">客户端节中列出的每个终结点都定义了它自己的绑定、行为和协定。</span><span class="sxs-lookup"><span data-stu-id="8c199-118">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="8c199-119">它由 `name` 和 `contract` 属性共同进行唯一标识。</span><span class="sxs-lookup"><span data-stu-id="8c199-119">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="8c199-120">客户端代码指定要连接到该客户端实现的服务终结点的 `name`。</span><span class="sxs-lookup"><span data-stu-id="8c199-120">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="8c199-121">如果省略 `name` 属性，则该终结点将作为其实现的协定的默认终结点。</span><span class="sxs-lookup"><span data-stu-id="8c199-121">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>

 <span data-ttu-id="8c199-122">此外，本节还指定了用于处理元数据的设置。</span><span class="sxs-lookup"><span data-stu-id="8c199-122">In addition, this section also specifies settings for processing metadata.</span></span>

## <a name="example"></a><span data-ttu-id="8c199-123">示例</span><span class="sxs-lookup"><span data-stu-id="8c199-123">Example</span></span>

```xml
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```

## <a name="see-also"></a><span data-ttu-id="8c199-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8c199-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="8c199-125">WCF 客户端配置</span><span class="sxs-lookup"><span data-stu-id="8c199-125">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="8c199-126">客户端</span><span class="sxs-lookup"><span data-stu-id="8c199-126">Clients</span></span>](../../../wcf/feature-details/clients.md)
