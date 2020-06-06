---
title: <add> 的 <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: a0f68717f765482f53e675458fae63d1a374d6fb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850327"
---
# <a name="add-of-serviceactivations"></a><span data-ttu-id="ec9a4-102">\<add> 的 \<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="ec9a4-102">\<add> of \<serviceActivations></span></span>

<span data-ttu-id="ec9a4-103">一个配置元素，允许您定义映射到 Windows Communication Foundation （WCF）服务类型的虚拟服务激活设置。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-103">A configuration element that allows you to define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="ec9a4-104">使用此配置元素可以在不使用 .svc 文件的情况下激活承载在 WAS/IIS 中的服务。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="ec9a4-105">语法</span><span class="sxs-lookup"><span data-stu-id="ec9a4-105">Syntax</span></span>

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ec9a4-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="ec9a4-106">Attributes and Elements</span></span>

<span data-ttu-id="ec9a4-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ec9a4-108">特性</span><span class="sxs-lookup"><span data-stu-id="ec9a4-108">Attributes</span></span>

|<span data-ttu-id="ec9a4-109">属性</span><span class="sxs-lookup"><span data-stu-id="ec9a4-109">Attribute</span></span>|<span data-ttu-id="ec9a4-110">说明</span><span class="sxs-lookup"><span data-stu-id="ec9a4-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="ec9a4-111">工厂</span><span class="sxs-lookup"><span data-stu-id="ec9a4-111">factory</span></span>|<span data-ttu-id="ec9a4-112">一个字符串，指定生成服务激活元素的工厂的 CLR 类型名称。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-112">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|
|<span data-ttu-id="ec9a4-113">服务</span><span class="sxs-lookup"><span data-stu-id="ec9a4-113">service</span></span>|<span data-ttu-id="ec9a4-114">实现服务的 ServiceType（完全限定的 Typename 或短的 Typename（将它置于 App_Code 文件夹中时））。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-114">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|
|<span data-ttu-id="ec9a4-115">relativeAddress</span><span class="sxs-lookup"><span data-stu-id="ec9a4-115">relativeAddress</span></span>|<span data-ttu-id="ec9a4-116">当前 IIS 应用程序内的相对地址，例如“Service.svc”。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-116">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="ec9a4-117">在 WCF 4.0 中，此相对地址必须包含其中一个已知文件扩展名（.svc，. .xamlx，...）。RelativeUrl 不存在物理文件</span><span class="sxs-lookup"><span data-stu-id="ec9a4-117">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ec9a4-118">子元素</span><span class="sxs-lookup"><span data-stu-id="ec9a4-118">Child Elements</span></span>

<span data-ttu-id="ec9a4-119">无。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ec9a4-120">父元素</span><span class="sxs-lookup"><span data-stu-id="ec9a4-120">Parent Elements</span></span>

|<span data-ttu-id="ec9a4-121">元素</span><span class="sxs-lookup"><span data-stu-id="ec9a4-121">Element</span></span>|<span data-ttu-id="ec9a4-122">描述</span><span class="sxs-lookup"><span data-stu-id="ec9a4-122">Description</span></span>|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="ec9a4-123">一个描述激活设置的配置节。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-123">A configuration section that describes activation settings.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ec9a4-124">注解</span><span class="sxs-lookup"><span data-stu-id="ec9a4-124">Remarks</span></span>

<span data-ttu-id="ec9a4-125">下面的示例演示如何在 web.config 文件中配置激活设置。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-125">The following example shows how to configure activation settings within your web.config file.</span></span>

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

<span data-ttu-id="ec9a4-126">使用此配置，您可以在不使用 .svc 文件的情况下激活 GreetingService。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-126">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="ec9a4-127">请注意，`<serviceHostingEnvironment>` 是应用程序级配置。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-127">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="ec9a4-128">必须将包含此配置的 `web.config` 放置到虚拟应用程序的根目录下。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-128">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="ec9a4-129">此外， `serviceHostingEnvironment` 是 machineToApplication 可继承部分。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-129">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="ec9a4-130">如果在计算机的根目录中注册了一个服务，应用程序中的每个服务都将继承此服务。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-130">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="ec9a4-131">基于配置的激活支持通过 http 协议和非 http 协议进行激活。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-131">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="ec9a4-132">它需要 relativeAddress 中的扩展，即 xoml 或 .xamlx。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-132">It requires extensions in the relativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="ec9a4-133">您可以将自己的扩展名映射到已知的 buildProviders，然后就可以通过任意扩展名激活服务。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-133">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="ec9a4-134">如果发生冲突，`<serviceActivations>` 节将重写 .svc 注册。</span><span class="sxs-lookup"><span data-stu-id="ec9a4-134">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec9a4-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ec9a4-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
