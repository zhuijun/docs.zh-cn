---
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: 413eb6c6e61b509135601c65cf045eabd849e8b3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "74802113"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a><span data-ttu-id="6a8ca-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> 元素</span><span class="sxs-lookup"><span data-stu-id="6a8ca-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="6a8ca-103">指定运行时是否使用固定的内存量来计算 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法的哈希代码。</span><span class="sxs-lookup"><span data-stu-id="6a8ca-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**  

## <a name="syntax"></a><span data-ttu-id="6a8ca-104">语法</span><span class="sxs-lookup"><span data-stu-id="6a8ca-104">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a8ca-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6a8ca-105">Attributes and Elements</span></span>

<span data-ttu-id="6a8ca-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6a8ca-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a8ca-107">特性</span><span class="sxs-lookup"><span data-stu-id="6a8ca-107">Attributes</span></span>

|<span data-ttu-id="6a8ca-108">属性</span><span class="sxs-lookup"><span data-stu-id="6a8ca-108">Attribute</span></span>|<span data-ttu-id="6a8ca-109">说明</span><span class="sxs-lookup"><span data-stu-id="6a8ca-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="6a8ca-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="6a8ca-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="6a8ca-111">指定公共语言运行时是否在计算哈希代码时分配固定的内存量。</span><span class="sxs-lookup"><span data-stu-id="6a8ca-111">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="6a8ca-112">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="6a8ca-112">enabled Attribute</span></span>

|<span data-ttu-id="6a8ca-113">值</span><span class="sxs-lookup"><span data-stu-id="6a8ca-113">Value</span></span>|<span data-ttu-id="6a8ca-114">说明</span><span class="sxs-lookup"><span data-stu-id="6a8ca-114">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="6a8ca-115">0</span><span class="sxs-lookup"><span data-stu-id="6a8ca-115">0</span></span>|<span data-ttu-id="6a8ca-116">公共语言运行时为 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法分配可变的内存量来计算哈希代码。</span><span class="sxs-lookup"><span data-stu-id="6a8ca-116">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="6a8ca-117">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="6a8ca-117">This is the default.</span></span>|
|<span data-ttu-id="6a8ca-118">1</span><span class="sxs-lookup"><span data-stu-id="6a8ca-118">1</span></span>|<span data-ttu-id="6a8ca-119">公共语言运行时为 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法分配固定的内存量来计算哈希代码。</span><span class="sxs-lookup"><span data-stu-id="6a8ca-119">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6a8ca-120">子元素</span><span class="sxs-lookup"><span data-stu-id="6a8ca-120">Child Elements</span></span>

<span data-ttu-id="6a8ca-121">无。</span><span class="sxs-lookup"><span data-stu-id="6a8ca-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6a8ca-122">父元素</span><span class="sxs-lookup"><span data-stu-id="6a8ca-122">Parent Elements</span></span>

|<span data-ttu-id="6a8ca-123">元素</span><span class="sxs-lookup"><span data-stu-id="6a8ca-123">Element</span></span>|<span data-ttu-id="6a8ca-124">描述</span><span class="sxs-lookup"><span data-stu-id="6a8ca-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="6a8ca-125">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="6a8ca-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="6a8ca-126">包含有关运行时初始化选项的信息。</span><span class="sxs-lookup"><span data-stu-id="6a8ca-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6a8ca-127">注解</span><span class="sxs-lookup"><span data-stu-id="6a8ca-127">Remarks</span></span>

<span data-ttu-id="6a8ca-128">默认情况下，公共语言运行时将为 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法分配可变的内存量，当该方法尝试计算非常大的字符串（几百万个字符以上）的哈希代码时，会引发 <xref:System.ArgumentException> 。</span><span class="sxs-lookup"><span data-stu-id="6a8ca-128">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="6a8ca-129">通过将此元素添加到应用程序配置文件并将其 `enabled` 特性设置为“1”，你可以指定 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法使用可分配固定内存量以计算哈希代码的替代算法。</span><span class="sxs-lookup"><span data-stu-id="6a8ca-129">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6a8ca-130">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>`Windows 8 及更高版本中不使用元素。</span><span class="sxs-lookup"><span data-stu-id="6a8ca-130">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in Windows 8 and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a8ca-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6a8ca-131">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6a8ca-132">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="6a8ca-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6a8ca-133">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="6a8ca-133">Configuration File Schema</span></span>](../index.md)
