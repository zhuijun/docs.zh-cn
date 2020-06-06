---
title: <GCCpuGroup> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102887"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="b2b4b-102">\<GCCpuGroup> 元素</span><span class="sxs-lookup"><span data-stu-id="b2b4b-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="b2b4b-103">指定垃圾回收是否支持多个 CPU 组。</span><span class="sxs-lookup"><span data-stu-id="b2b4b-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**

## <a name="syntax"></a><span data-ttu-id="b2b4b-104">语法</span><span class="sxs-lookup"><span data-stu-id="b2b4b-104">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2b4b-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b2b4b-105">Attributes and Elements</span></span>

<span data-ttu-id="b2b4b-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b2b4b-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2b4b-107">特性</span><span class="sxs-lookup"><span data-stu-id="b2b4b-107">Attributes</span></span>

|<span data-ttu-id="b2b4b-108">属性</span><span class="sxs-lookup"><span data-stu-id="b2b4b-108">Attribute</span></span>|<span data-ttu-id="b2b4b-109">说明</span><span class="sxs-lookup"><span data-stu-id="b2b4b-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="b2b4b-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="b2b4b-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="b2b4b-111">指定垃圾回收是否支持多个 CPU 组。</span><span class="sxs-lookup"><span data-stu-id="b2b4b-111">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="b2b4b-112">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="b2b4b-112">enabled Attribute</span></span>

|<span data-ttu-id="b2b4b-113">值</span><span class="sxs-lookup"><span data-stu-id="b2b4b-113">Value</span></span>|<span data-ttu-id="b2b4b-114">说明</span><span class="sxs-lookup"><span data-stu-id="b2b4b-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="b2b4b-115">垃圾回收不支持多个 CPU 组。</span><span class="sxs-lookup"><span data-stu-id="b2b4b-115">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="b2b4b-116">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="b2b4b-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="b2b4b-117">如果启用了服务器垃圾回收，则垃圾回收支持多个 CPU 组。</span><span class="sxs-lookup"><span data-stu-id="b2b4b-117">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b2b4b-118">子元素</span><span class="sxs-lookup"><span data-stu-id="b2b4b-118">Child Elements</span></span>

<span data-ttu-id="b2b4b-119">无。</span><span class="sxs-lookup"><span data-stu-id="b2b4b-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b2b4b-120">父元素</span><span class="sxs-lookup"><span data-stu-id="b2b4b-120">Parent Elements</span></span>

|<span data-ttu-id="b2b4b-121">元素</span><span class="sxs-lookup"><span data-stu-id="b2b4b-121">Element</span></span>|<span data-ttu-id="b2b4b-122">描述</span><span class="sxs-lookup"><span data-stu-id="b2b4b-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="b2b4b-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="b2b4b-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="b2b4b-124">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="b2b4b-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b2b4b-125">注解</span><span class="sxs-lookup"><span data-stu-id="b2b4b-125">Remarks</span></span>

<span data-ttu-id="b2b4b-126">如果计算机具有多个 CPU 组并且启用了服务器垃圾回收（请参阅 [\<gcServer>](gcserver-element.md) 元素），则启用此元素会在所有 CPU 组之间扩展垃圾回收，并在创建和平衡堆时考虑所有核心。</span><span class="sxs-lookup"><span data-stu-id="b2b4b-126">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="b2b4b-127">此元素仅适用于垃圾回收线程。</span><span class="sxs-lookup"><span data-stu-id="b2b4b-127">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="b2b4b-128">若要使运行时能够在所有 CPU 组之间分配用户线程，还必须启用该 [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="b2b4b-128">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="b2b4b-129">示例</span><span class="sxs-lookup"><span data-stu-id="b2b4b-129">Example</span></span>

<span data-ttu-id="b2b4b-130">下面的示例演示如何为多个 CPU 组启用垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="b2b4b-130">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="b2b4b-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2b4b-131">See also</span></span>

- [<span data-ttu-id="b2b4b-132">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="b2b4b-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b2b4b-133">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="b2b4b-133">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b2b4b-134">禁用并发垃圾回收</span><span class="sxs-lookup"><span data-stu-id="b2b4b-134">Disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="b2b4b-135">工作站和服务器垃圾回收</span><span class="sxs-lookup"><span data-stu-id="b2b4b-135">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/workstation-server-gc.md)
