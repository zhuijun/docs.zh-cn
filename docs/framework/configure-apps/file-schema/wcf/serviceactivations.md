---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 64ae0bfd90ae941fc78515c7936c998201c87485
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855135"
---
# \<serviceActivations>

<span data-ttu-id="e6c8d-101">一个配置元素，允许您添加用于定义映射到 Windows Communication Foundation （WCF）服务类型的虚拟服务激活设置的设置。</span><span class="sxs-lookup"><span data-stu-id="e6c8d-101">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="e6c8d-102">使用此配置元素可以在不使用 .svc 文件的情况下激活承载在 WAS/IIS 中的服务。</span><span class="sxs-lookup"><span data-stu-id="e6c8d-102">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceActivations>**  

## <a name="syntax"></a><span data-ttu-id="e6c8d-103">语法</span><span class="sxs-lookup"><span data-stu-id="e6c8d-103">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e6c8d-104">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e6c8d-104">Attributes and Elements</span></span>

<span data-ttu-id="e6c8d-105">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e6c8d-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e6c8d-106">特性</span><span class="sxs-lookup"><span data-stu-id="e6c8d-106">Attributes</span></span>

<span data-ttu-id="e6c8d-107">无。</span><span class="sxs-lookup"><span data-stu-id="e6c8d-107">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e6c8d-108">子元素</span><span class="sxs-lookup"><span data-stu-id="e6c8d-108">Child Elements</span></span>

|<span data-ttu-id="e6c8d-109">元素</span><span class="sxs-lookup"><span data-stu-id="e6c8d-109">Element</span></span>|<span data-ttu-id="e6c8d-110">说明</span><span class="sxs-lookup"><span data-stu-id="e6c8d-110">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-serviceactivations.md)|<span data-ttu-id="e6c8d-111">添加一个指定激活服务应用程序的配置元素。</span><span class="sxs-lookup"><span data-stu-id="e6c8d-111">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e6c8d-112">父元素</span><span class="sxs-lookup"><span data-stu-id="e6c8d-112">Parent Elements</span></span>

|<span data-ttu-id="e6c8d-113">元素</span><span class="sxs-lookup"><span data-stu-id="e6c8d-113">Element</span></span>|<span data-ttu-id="e6c8d-114">说明</span><span class="sxs-lookup"><span data-stu-id="e6c8d-114">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="e6c8d-115">定义服务承载环境要为特定传输实例化的类型。</span><span class="sxs-lookup"><span data-stu-id="e6c8d-115">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e6c8d-116">注解</span><span class="sxs-lookup"><span data-stu-id="e6c8d-116">Remarks</span></span>

<span data-ttu-id="e6c8d-117">下面的示例演示如何在 web.config 文件中配置激活设置。</span><span class="sxs-lookup"><span data-stu-id="e6c8d-117">The following example shows how to configure activation settings within your web.config file.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="e6c8d-118">使用此配置，您可以在不使用 .svc 文件的情况下激活 GreetingService。</span><span class="sxs-lookup"><span data-stu-id="e6c8d-118">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="e6c8d-119">请注意，`<serviceHostingEnvironment>` 是应用程序级配置。</span><span class="sxs-lookup"><span data-stu-id="e6c8d-119">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="e6c8d-120">必须将包含此配置的 `web.config` 放置到虚拟应用程序的根目录下。</span><span class="sxs-lookup"><span data-stu-id="e6c8d-120">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="e6c8d-121">此外， `serviceHostingEnvironment` 是 machineToApplication 可继承部分。</span><span class="sxs-lookup"><span data-stu-id="e6c8d-121">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="e6c8d-122">如果在计算机的根目录中注册了一个服务，应用程序中的每个服务都将继承此服务。</span><span class="sxs-lookup"><span data-stu-id="e6c8d-122">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="e6c8d-123">基于配置的激活支持通过 http 协议和非 http 协议进行激活。</span><span class="sxs-lookup"><span data-stu-id="e6c8d-123">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="e6c8d-124">它需要 relativeAddress 中的扩展，如 xoml 或 .xamlx。</span><span class="sxs-lookup"><span data-stu-id="e6c8d-124">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="e6c8d-125">您可以将自己的扩展名映射到已知的 buildProviders，然后就可以通过任意扩展名激活服务。</span><span class="sxs-lookup"><span data-stu-id="e6c8d-125">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="e6c8d-126">如果发生冲突，`<serviceActivations>` 节将重写 .svc 注册。</span><span class="sxs-lookup"><span data-stu-id="e6c8d-126">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6c8d-127">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e6c8d-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
