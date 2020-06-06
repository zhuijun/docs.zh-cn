---
title: <Thread_UseAllCpuGroups> 元素
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115400"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="28228-102">\<Thread_UseAllCpuGroups> 元素</span><span class="sxs-lookup"><span data-stu-id="28228-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="28228-103">指定运行时是否跨所有 CPU 组分发托管的线程。</span><span class="sxs-lookup"><span data-stu-id="28228-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**  

## <a name="syntax"></a><span data-ttu-id="28228-104">语法</span><span class="sxs-lookup"><span data-stu-id="28228-104">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="28228-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="28228-105">Attributes and Elements</span></span>

<span data-ttu-id="28228-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="28228-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="28228-107">特性</span><span class="sxs-lookup"><span data-stu-id="28228-107">Attributes</span></span>

|<span data-ttu-id="28228-108">属性</span><span class="sxs-lookup"><span data-stu-id="28228-108">Attribute</span></span>|<span data-ttu-id="28228-109">说明</span><span class="sxs-lookup"><span data-stu-id="28228-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="28228-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="28228-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="28228-111">指定运行时是否跨所有 CPU 组分发托管的线程。</span><span class="sxs-lookup"><span data-stu-id="28228-111">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="28228-112">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="28228-112">enabled Attribute</span></span>

|<span data-ttu-id="28228-113">值</span><span class="sxs-lookup"><span data-stu-id="28228-113">Value</span></span>|<span data-ttu-id="28228-114">说明</span><span class="sxs-lookup"><span data-stu-id="28228-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="28228-115">运行时不会跨多个 CPU 组分发托管线程。</span><span class="sxs-lookup"><span data-stu-id="28228-115">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="28228-116">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="28228-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="28228-117">如果计算机具有多个 CPU 组并且元素已启用，则运行时将跨多个 CPU 组分发托管线程 [\<GCCpuGroup>](gccpugroup-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="28228-117">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="28228-118">子元素</span><span class="sxs-lookup"><span data-stu-id="28228-118">Child Elements</span></span>

<span data-ttu-id="28228-119">无。</span><span class="sxs-lookup"><span data-stu-id="28228-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="28228-120">父元素</span><span class="sxs-lookup"><span data-stu-id="28228-120">Parent Elements</span></span>

|<span data-ttu-id="28228-121">元素</span><span class="sxs-lookup"><span data-stu-id="28228-121">Element</span></span>|<span data-ttu-id="28228-122">描述</span><span class="sxs-lookup"><span data-stu-id="28228-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="28228-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="28228-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="28228-124">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="28228-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="28228-125">注解</span><span class="sxs-lookup"><span data-stu-id="28228-125">Remarks</span></span>

<span data-ttu-id="28228-126">如果计算机具有多个 CPU 组，则启用此元素会使运行时将托管线程分散到所有 CPU 组。</span><span class="sxs-lookup"><span data-stu-id="28228-126">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="28228-127">若要使用此功能，还必须启用 [\<GCCpuGroup>](gccpugroup-element.md) 元素，该元素将垃圾回收扩展到所有 CPU 组，并在创建和平衡堆时考虑所有核心。</span><span class="sxs-lookup"><span data-stu-id="28228-127">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="28228-128">启用 [\<GCCpuGroup>](gccpugroup-element.md) 元素需要启用 [\<gcServer>](gcserver-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="28228-128">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="28228-129">如果未启用这些元素，则启用 `<Thread_UseAllCpuGroups>` 元素不起作用。</span><span class="sxs-lookup"><span data-stu-id="28228-129">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="28228-130">示例</span><span class="sxs-lookup"><span data-stu-id="28228-130">Example</span></span>

<span data-ttu-id="28228-131">下面的示例演示如何启用对多个 CPU 组的支持。</span><span class="sxs-lookup"><span data-stu-id="28228-131">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="28228-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="28228-132">See also</span></span>

- [<span data-ttu-id="28228-133">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="28228-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="28228-134">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="28228-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="28228-135">\<GCCpuGroup>Element</span><span class="sxs-lookup"><span data-stu-id="28228-135">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
