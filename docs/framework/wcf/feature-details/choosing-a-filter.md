---
title: 选择筛选器
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: e951c472543239df0c01dcba3e46f120ced9e192
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587490"
---
# <a name="choosing-a-filter"></a><span data-ttu-id="7cef8-102">选择筛选器</span><span class="sxs-lookup"><span data-stu-id="7cef8-102">Choosing a Filter</span></span>
<span data-ttu-id="7cef8-103">配置路由服务时，选择正确的消息筛选器并将它们配置为允许您针对接收的消息进行完全匹配非常重要。</span><span class="sxs-lookup"><span data-stu-id="7cef8-103">When configuring the Routing Service, it is important to select correct message filters and configure them to allow you to make exact matches against the messages you receive.</span></span> <span data-ttu-id="7cef8-104">如果所选筛选器筛选出的匹配项太广或者配置不当，则消息会错误地进行路由。</span><span class="sxs-lookup"><span data-stu-id="7cef8-104">If the filters you select are overly broad in their matches or are incorrectly configured, messages are routed incorrectly.</span></span> <span data-ttu-id="7cef8-105">如果筛选器的筛选范围太窄，则某些消息可能没有任何可用的有效路由。</span><span class="sxs-lookup"><span data-stu-id="7cef8-105">If the filters are too restrictive, you may not have any valid routes available for some of your messages.</span></span>

## <a name="filter-types"></a><span data-ttu-id="7cef8-106">筛选器类型</span><span class="sxs-lookup"><span data-stu-id="7cef8-106">Filter Types</span></span>

<span data-ttu-id="7cef8-107">选择由路由服务使用的筛选器时，了解每个筛选器的工作方式以及哪些信息可以作为传入消息的一部分非常重要。</span><span class="sxs-lookup"><span data-stu-id="7cef8-107">When selecting the filters that are used by the Routing Service, it is important that you understand how each filter works as well as what information is available as part of the incoming messages.</span></span> <span data-ttu-id="7cef8-108">例如，如果所有消息都是通过同一终结点接收的，则 Address 和 EndpointName 筛选器可能没有用，因为所有消息都与这两个筛选器匹配。</span><span class="sxs-lookup"><span data-stu-id="7cef8-108">For instance, if all messages are received over the same endpoint, the Address and EndpointName filters are not useful because all messages match these filters.</span></span>

### <a name="action"></a><span data-ttu-id="7cef8-109">操作</span><span class="sxs-lookup"><span data-stu-id="7cef8-109">Action</span></span>

<span data-ttu-id="7cef8-110">Action 筛选器检查 <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="7cef8-110">The Action filter inspects the <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> property.</span></span> <span data-ttu-id="7cef8-111">如果消息中 Action 标头的内容与筛选器配置中指定的筛选器数据值相匹配，此筛选器将返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="7cef8-111">If the contents of the Action header in the message match the filter data value specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="7cef8-112">下面的示例定义一个 `FilterElement` ，它使用操作筛选器来匹配包含值为的操作标头的消息 `http://namespace/contract/operation/` 。</span><span class="sxs-lookup"><span data-stu-id="7cef8-112">The following example defines a `FilterElement` that uses the Action filter to match messages with an action header that contains a value of `http://namespace/contract/operation/`.</span></span>

```xml
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />
```

```csharp
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
```

<span data-ttu-id="7cef8-113">如果路由的消息包含唯一 Action 标头，则应使用此筛选器。</span><span class="sxs-lookup"><span data-stu-id="7cef8-113">This filter should be used when routing messages that contain a unique Action header.</span></span>

### <a name="endpointaddress"></a><span data-ttu-id="7cef8-114">EndpointAddress</span><span class="sxs-lookup"><span data-stu-id="7cef8-114">EndpointAddress</span></span>

<span data-ttu-id="7cef8-115">EndpointAddress 筛选器检查接收消息的 EndpointAddress。</span><span class="sxs-lookup"><span data-stu-id="7cef8-115">The EndpointAddress filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="7cef8-116">如果消息到达的地址与筛选器配置中指定的筛选器地址完全匹配，此筛选器将返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="7cef8-116">If the address that the message arrives at exactly matches the filter address specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="7cef8-117">下面的示例定义一个 `FilterElement` ，它使用地址筛选器来匹配发送到 "http:///vdir/s.svc/b" 的任何消息 \<hostname> 。</span><span class="sxs-lookup"><span data-stu-id="7cef8-117">The following example defines a `FilterElement` that uses the Address filter to match any messages addressed to "http://\<hostname>/vdir/s.svc/b".</span></span>

```xml
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> <span data-ttu-id="7cef8-118">需要特别注意的是，根据客户端使用的是完全限定域名、NetBIOS 名称、IP 地址还是其他名称，地址的主机名部分可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="7cef8-118">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="7cef8-119">由于不同值可以引用同一主机，因此在执行匹配时，此比较的默认行为是不使用地址的主机名部分。</span><span class="sxs-lookup"><span data-stu-id="7cef8-119">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>
>
> <span data-ttu-id="7cef8-120">可以对此行为进行修改，以便在以编程方式配置路由服务时允许比较操作计算主机名。</span><span class="sxs-lookup"><span data-stu-id="7cef8-120">This behavior can be modified to allow the comparison to evaluate the host name when configuring the Routing Service programmatically.</span></span>

<span data-ttu-id="7cef8-121">如果将传入消息发送到唯一地址，则应使用此筛选器。</span><span class="sxs-lookup"><span data-stu-id="7cef8-121">This filter should be used when the incoming messages are addressed to a unique address.</span></span>

### <a name="endpointaddressprefix"></a><span data-ttu-id="7cef8-122">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="7cef8-122">EndpointAddressPrefix</span></span>

<span data-ttu-id="7cef8-123">EndpointAddressPrefix 筛选器与 EndpointAddress 筛选器类似。</span><span class="sxs-lookup"><span data-stu-id="7cef8-123">The EndpointAddressPrefix filter is similar to the EndpointAddress filter.</span></span> <span data-ttu-id="7cef8-124">EndpointAddressPrefix 筛选器检查接收消息的 EndpointAddress。</span><span class="sxs-lookup"><span data-stu-id="7cef8-124">The EndpointAddressPrefix filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="7cef8-125">但是，EndpointAddressPrefix 筛选器在匹配以筛选器配置中指定的值开头的地址时用作通配符。</span><span class="sxs-lookup"><span data-stu-id="7cef8-125">However the EndpointAddressPrefix filter acts as a wildcard by matching addresses that begin with the value specified in the filter configuration.</span></span> <span data-ttu-id="7cef8-126">下面的示例定义一个 `FilterElement` ，它使用 EndpointAddressPrefix 筛选器来匹配发送到的所有消息 `http://<hostname>/vdir*` 。</span><span class="sxs-lookup"><span data-stu-id="7cef8-126">The following example defines a `FilterElement` that uses the EndpointAddressPrefix filter to match any messages addressed to `http://<hostname>/vdir*`.</span></span>

```xml
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />
```

```csharp
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
```

> [!NOTE]
> <span data-ttu-id="7cef8-127">需要特别注意的是，根据客户端使用的是完全限定域名、NetBIOS 名称、IP 地址还是其他名称，地址的主机名部分可能有所不同。</span><span class="sxs-lookup"><span data-stu-id="7cef8-127">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="7cef8-128">由于不同值可以引用同一主机，因此在执行匹配时，此比较的默认行为是不使用地址的主机名部分。</span><span class="sxs-lookup"><span data-stu-id="7cef8-128">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>

<span data-ttu-id="7cef8-129">如果要路由的传入消息都有一个相同的地址前缀，则应使用此筛选器。</span><span class="sxs-lookup"><span data-stu-id="7cef8-129">This filter should be used when routing incoming messages that share a common address prefix.</span></span>

### <a name="and"></a><span data-ttu-id="7cef8-130">AND</span><span class="sxs-lookup"><span data-stu-id="7cef8-130">AND</span></span>

<span data-ttu-id="7cef8-131">AND 筛选器不直接筛选消息中的值，但允许您组合两个其他筛选器来创建 `AND` 条件，其中，这两个筛选器必须匹配消息，AND 筛选器的计算结果才会为 `true`。</span><span class="sxs-lookup"><span data-stu-id="7cef8-131">The AND filter does not directly filter on a value within a message, but allows you to combine two other filters to create an `AND` condition where both filters must match the message before the AND filter evaluates to `true`.</span></span> <span data-ttu-id="7cef8-132">这样，您可以创建仅当所有子筛选器都匹配时才匹配的复杂筛选器。</span><span class="sxs-lookup"><span data-stu-id="7cef8-132">This allows you to create complex filters that only match if all the sub-filters match.</span></span> <span data-ttu-id="7cef8-133">下面的示例定义一个 Address 筛选器和一个 Action 筛选器，然后定义一个根据 Address 筛选器和 Action 筛选器来计算消息的 AND 筛选器。</span><span class="sxs-lookup"><span data-stu-id="7cef8-133">The following example defines an address filter and an action filter, and then defines an AND filter that evaluates a message against both the address and action filters.</span></span> <span data-ttu-id="7cef8-134">如果 Address 筛选器和 Action 筛选器都匹配，AND 筛选器将返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="7cef8-134">If both the address and the action filters match, then the AND filter returns `true`.</span></span>

```xml
<filter name="address1" filterType="AddressPrefix" filterData="http://host/vdir"/>
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/"/>
<filter name="and1" filterType="And" filter1="address1" filter2="action1" />
```

```csharp
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });
StrictAndMessageFilter and1=new StrictAndMessageFilter(address1, action1);
```

<span data-ttu-id="7cef8-135">如果您必须组合多个筛选器中的逻辑来确定应进行匹配的条件，则应使用此筛选器。</span><span class="sxs-lookup"><span data-stu-id="7cef8-135">This filter should be used when you must combine the logic from multiple filters to determine when a match should be made.</span></span> <span data-ttu-id="7cef8-136">例如，如果您有多个目标，而这些目标只能接收发送到特定地址的操作和消息的某些组合，则可以使用 AND 筛选器组合必要的 Action 筛选器和 Address 筛选器。</span><span class="sxs-lookup"><span data-stu-id="7cef8-136">For example, if you have multiple destinations that must receive only certain combinations of actions and messages to particular addresses, you can use an AND filter to combine the necessary Action and Address filters.</span></span>

### <a name="custom"></a><span data-ttu-id="7cef8-137">自定义</span><span class="sxs-lookup"><span data-stu-id="7cef8-137">Custom</span></span>

<span data-ttu-id="7cef8-138">选择自定义筛选器类型时，必须提供一个 customType 值，该值包含包含要用于此筛选器的**MessageFilter**实现的程序集的类型。</span><span class="sxs-lookup"><span data-stu-id="7cef8-138">When selecting the Custom filter type, you must provide a customType value that contains the type of the assembly that contains the **MessageFilter** implementation to be used for this filter.</span></span> <span data-ttu-id="7cef8-139">此外，filterData 必须包含自定义筛选器在计算消息时可能需要的任何值。</span><span class="sxs-lookup"><span data-stu-id="7cef8-139">Additionally, filterData must contain any values that the custom filter may require in its evaluation of messages.</span></span> <span data-ttu-id="7cef8-140">下面的示例定义一个 `FilterElement`，它使用 `CustomAssembly.MyCustomMsgFilter` MessageFilter 实现。</span><span class="sxs-lookup"><span data-stu-id="7cef8-140">The following example defines a `FilterElement` that uses the `CustomAssembly.MyCustomMsgFilter` MessageFilter implementation.</span></span>

```xml
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />
```

```csharp
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");
```

<span data-ttu-id="7cef8-141">如果需要对随提供的筛选器未涵盖的消息执行自定义匹配逻辑 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] ，则必须创建作为**MessageFilter**类的实现的自定义筛选器。</span><span class="sxs-lookup"><span data-stu-id="7cef8-141">If you need to perform custom matching logic against a message that is not covered by the filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], you must create a custom filter that is an implementation of the **MessageFilter** class.</span></span> <span data-ttu-id="7cef8-142">例如，您可以创建这样的自定义筛选器：比较传入消息中的字段与作为配置提供给该筛选器的已知值列表，或者对特定消息元素进行哈希处理然后检查该值以确定该筛选器应返回 `true` 还是 `false`。</span><span class="sxs-lookup"><span data-stu-id="7cef8-142">For example, you might create a custom filter that compares a field in the incoming message against a list of known values given to the filter as configuration, or that hashes a particular message element and then examines that value to determine whether the filter should return `true` or `false`.</span></span>

### <a name="endpointname"></a><span data-ttu-id="7cef8-143">EndpointName</span><span class="sxs-lookup"><span data-stu-id="7cef8-143">EndpointName</span></span>

<span data-ttu-id="7cef8-144">EndpointName 筛选器检查接收消息的终结点的名称。</span><span class="sxs-lookup"><span data-stu-id="7cef8-144">The EndpointName filter inspects the name of the endpoint that received the message.</span></span> <span data-ttu-id="7cef8-145">下面的示例定义一个 `FilterElement` ，它使用终结点筛选器来路由 "SvcEndpoint" 上收到的消息。</span><span class="sxs-lookup"><span data-stu-id="7cef8-145">The following example defines a `FilterElement` that uses the EndpointName filter to route messages received on the "SvcEndpoint".</span></span>

```xml
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />
```

```csharp
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");
```

<span data-ttu-id="7cef8-146">如果路由服务公开多个指定的服务终结点，则此筛选器非常有用。</span><span class="sxs-lookup"><span data-stu-id="7cef8-146">This filter is useful when the Routing Service exposes more than one named service endpoint.</span></span> <span data-ttu-id="7cef8-147">例如，您可能公开了路由服务用来接收消息的两个终结点；一个终结点由需要实时处理其消息的优先级客户使用，而另一个终结点接收不具有时效性的消息。</span><span class="sxs-lookup"><span data-stu-id="7cef8-147">For example, you might expose two endpoints that the Routing Service uses to receive messages; one is used by priority customers who require real-time processing of their messages, while the other endpoint receives messages that are not time sensitive.</span></span>

<span data-ttu-id="7cef8-148">虽然您可能经常使用完整地址匹配来确定接收消息的终结点，但是改为使用定义的终结点名称后，会非常简便快捷而且通常不容易出错，尤其在使用配置文件配置路由服务时（此时终结点名称是必需的特性）。</span><span class="sxs-lookup"><span data-stu-id="7cef8-148">While you can often use full address matching to determine which endpoint a message was received on, using the defined endpoint name instead is a convenient shortcut that is often less error prone, especially when configuring a Routing Service using a configuration file (where endpoint names are a required attribute).</span></span>

### <a name="matchall"></a><span data-ttu-id="7cef8-149">MatchAll</span><span class="sxs-lookup"><span data-stu-id="7cef8-149">MatchAll</span></span>

<span data-ttu-id="7cef8-150">MatchAll 筛选器匹配所有接收的消息。</span><span class="sxs-lookup"><span data-stu-id="7cef8-150">The MatchAll filter matches any received message.</span></span> <span data-ttu-id="7cef8-151">如果您必须始终将所有接收的消息路由到特定终结点（例如存储所有已接收消息的副本的日志记录服务），则此筛选器非常有用。</span><span class="sxs-lookup"><span data-stu-id="7cef8-151">It is useful if you must always route all received messages to a specific endpoint, such as a logging service that stores a copy of all received messages.</span></span> <span data-ttu-id="7cef8-152">下面的示例定义一个 `FilterElement`，它使用 MatchAll 筛选器。</span><span class="sxs-lookup"><span data-stu-id="7cef8-152">The following example defines a `FilterElement` that uses the MatchAll filter.</span></span>

```xml
<filter name="matchAll1" filterType="MatchAll" />
```

```csharp
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();
```

### <a name="xpath"></a><span data-ttu-id="7cef8-153">XPath</span><span class="sxs-lookup"><span data-stu-id="7cef8-153">XPath</span></span>

<span data-ttu-id="7cef8-154">使用 XPath 筛选器可以指定用于检查消息中的特定元素的 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="7cef8-154">The XPath filter allows you to specify an XPath query that is used to inspect a specific element within the message.</span></span> <span data-ttu-id="7cef8-155">XPath 筛选是一个功能强大的筛选选项，通过它可以直接检查消息中的任何 XML 可寻址条目；但是该筛选要求您非常了解要接收的消息的结构。</span><span class="sxs-lookup"><span data-stu-id="7cef8-155">XPath filtering is a powerful filtering option that allows you to directly inspect any XML addressable entry within the message; however it requires that you have specific knowledge of the structure of the messages that you are receiving.</span></span> <span data-ttu-id="7cef8-156">下面的示例定义一个 `FilterElement` ，它使用 XPath 筛选器来检查消息中是否有 "ns" 命名空间前缀所引用的命名空间中名为 "element" 的元素。</span><span class="sxs-lookup"><span data-stu-id="7cef8-156">The following example defines a `FilterElement` that uses the XPath filter to inspect the message for an element named "element" within the namespace referenced by the "ns" namespace prefix.</span></span>

```xml
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />
```

```csharp
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");
```

<span data-ttu-id="7cef8-157">如果您知道要接收的消息包含特定值，则此筛选器非常有用。</span><span class="sxs-lookup"><span data-stu-id="7cef8-157">This filter is useful if you know that the messages you are receiving contain a specific value.</span></span> <span data-ttu-id="7cef8-158">例如，如果您要承载同一服务的两个版本，并且知道发送到较新版本服务的消息在自定义标头中包含唯一值，则您可以创建这样的筛选器：使用 XPath 导航到此标头，并比较标头中存在的值与筛选器配置中指定的另一个值来确定筛选器是否匹配。</span><span class="sxs-lookup"><span data-stu-id="7cef8-158">For example, if you are hosting two versions of the same service and you know that messages addressed to the newer version of the service contain a unique value in a custom header, you can create a filter that uses XPath to navigate to this header and compares the value present in the header to another given in the filter configuration to determine if the filter matches.</span></span>

<span data-ttu-id="7cef8-159">由于 XPath 查询通常包含唯一命名空间（通常为很长或复杂的字符串值），因此 XPath 筛选器允许您使用命名空间表来定义命名空间的唯一前缀。</span><span class="sxs-lookup"><span data-stu-id="7cef8-159">Because XPath queries often contain unique namespaces, which are often lengthy or complex string values, the XPath filter allows you to use the namespace table to define unique prefixes for your namespaces.</span></span> <span data-ttu-id="7cef8-160">有关命名空间表的详细信息，请参阅[消息筛选器](message-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="7cef8-160">For more information about the namespace table, see [Message Filters](message-filters.md).</span></span>

<span data-ttu-id="7cef8-161">有关设计 XPath 查询的详细信息，请参阅[Xpath 语法](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256471(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="7cef8-161">For more information about designing XPath queries, see [XPath Syntax](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256471(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="7cef8-162">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7cef8-162">See also</span></span>

- [<span data-ttu-id="7cef8-163">消息筛选器</span><span class="sxs-lookup"><span data-stu-id="7cef8-163">Message Filters</span></span>](message-filters.md)
- [<span data-ttu-id="7cef8-164">如何：使用筛选器</span><span class="sxs-lookup"><span data-stu-id="7cef8-164">How To: Use Filters</span></span>](how-to-use-filters.md)
