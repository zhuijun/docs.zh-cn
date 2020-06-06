---
title: GCLOHThreshold 元素
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74451322"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="d63f7-102">GCLOHThreshold 元素</span><span class="sxs-lookup"><span data-stu-id="d63f7-102">GCLOHThreshold element</span></span>

<span data-ttu-id="d63f7-103">指定导致垃圾回收器将对象置于大对象堆（LOH）上的阈值大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="d63f7-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold>

## <a name="syntax"></a><span data-ttu-id="d63f7-104">语法</span><span class="sxs-lookup"><span data-stu-id="d63f7-104">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="d63f7-105">特性</span><span class="sxs-lookup"><span data-stu-id="d63f7-105">Attributes</span></span>

|<span data-ttu-id="d63f7-106">属性</span><span class="sxs-lookup"><span data-stu-id="d63f7-106">Attribute</span></span>|<span data-ttu-id="d63f7-107">说明</span><span class="sxs-lookup"><span data-stu-id="d63f7-107">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="d63f7-108">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="d63f7-108">Required attribute.</span></span><br /><br /><span data-ttu-id="d63f7-109">指定导致对象在大型对象堆上的阈值大小。</span><span class="sxs-lookup"><span data-stu-id="d63f7-109">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="d63f7-110">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="d63f7-110">enabled attribute</span></span>

|<span data-ttu-id="d63f7-111">值</span><span class="sxs-lookup"><span data-stu-id="d63f7-111">Value</span></span>|<span data-ttu-id="d63f7-112">说明</span><span class="sxs-lookup"><span data-stu-id="d63f7-112">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="d63f7-113">导致对象在大型对象堆上的阈值大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="d63f7-113">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="d63f7-114">子元素</span><span class="sxs-lookup"><span data-stu-id="d63f7-114">Child elements</span></span>

<span data-ttu-id="d63f7-115">无。</span><span class="sxs-lookup"><span data-stu-id="d63f7-115">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="d63f7-116">父元素</span><span class="sxs-lookup"><span data-stu-id="d63f7-116">Parent elements</span></span>

|<span data-ttu-id="d63f7-117">元素</span><span class="sxs-lookup"><span data-stu-id="d63f7-117">Element</span></span>|<span data-ttu-id="d63f7-118">描述</span><span class="sxs-lookup"><span data-stu-id="d63f7-118">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="d63f7-119">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="d63f7-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="d63f7-120">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="d63f7-120">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d63f7-121">注解</span><span class="sxs-lookup"><span data-stu-id="d63f7-121">Remarks</span></span>

<span data-ttu-id="d63f7-122">.NET Framework 4.8 中引入了此设置。</span><span class="sxs-lookup"><span data-stu-id="d63f7-122">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="d63f7-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d63f7-123">See also</span></span>

- [<span data-ttu-id="d63f7-124">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="d63f7-124">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="d63f7-125">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="d63f7-125">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="d63f7-126">垃圾回收的基本知识</span><span class="sxs-lookup"><span data-stu-id="d63f7-126">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="d63f7-127">用于 GC 的 NET Core 运行时配置选项</span><span class="sxs-lookup"><span data-stu-id="d63f7-127">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)
