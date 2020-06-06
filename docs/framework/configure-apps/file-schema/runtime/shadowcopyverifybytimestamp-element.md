---
title: <shadowCopyVerifyByTimestamp> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
ms.openlocfilehash: 160f14c856735e1ceac8635506aea52454faea43
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115730"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="c6f9c-102">\<shadowCopyVerifyByTimestamp> 元素</span><span class="sxs-lookup"><span data-stu-id="c6f9c-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="c6f9c-103">指定卷影复制是否使用 .NET Framework 4 中引入的默认启动行为，或恢复为 .NET Framework 早期版本的启动行为。</span><span class="sxs-lookup"><span data-stu-id="c6f9c-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**  
  
## <a name="syntax"></a><span data-ttu-id="c6f9c-104">语法</span><span class="sxs-lookup"><span data-stu-id="c6f9c-104">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6f9c-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="c6f9c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c6f9c-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c6f9c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6f9c-107">特性</span><span class="sxs-lookup"><span data-stu-id="c6f9c-107">Attributes</span></span>  
  
|<span data-ttu-id="c6f9c-108">属性</span><span class="sxs-lookup"><span data-stu-id="c6f9c-108">Attribute</span></span>|<span data-ttu-id="c6f9c-109">说明</span><span class="sxs-lookup"><span data-stu-id="c6f9c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6f9c-110">已启用</span><span class="sxs-lookup"><span data-stu-id="c6f9c-110">enabled</span></span>|<span data-ttu-id="c6f9c-111">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="c6f9c-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="c6f9c-112">指定在启动时，使用卷影复制的应用程序域是否对程序集时间戳进行比较，以确定在卷影复制程序集之前是否更新了程序集。</span><span class="sxs-lookup"><span data-stu-id="c6f9c-112">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c6f9c-113">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="c6f9c-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="c6f9c-114">值</span><span class="sxs-lookup"><span data-stu-id="c6f9c-114">Value</span></span>|<span data-ttu-id="c6f9c-115">说明</span><span class="sxs-lookup"><span data-stu-id="c6f9c-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c6f9c-116">true</span><span class="sxs-lookup"><span data-stu-id="c6f9c-116">true</span></span>|<span data-ttu-id="c6f9c-117">在启动时，仅复制自上次复制到卷影复制目录以来已更新的程序集。</span><span class="sxs-lookup"><span data-stu-id="c6f9c-117">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="c6f9c-118">这是 .NET Framework 4 的默认值。</span><span class="sxs-lookup"><span data-stu-id="c6f9c-118">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="c6f9c-119">false</span><span class="sxs-lookup"><span data-stu-id="c6f9c-119">false</span></span>|<span data-ttu-id="c6f9c-120">恢复到 .NET Framework 以前版本的启动行为，该行为是在启动时复制所有文件。</span><span class="sxs-lookup"><span data-stu-id="c6f9c-120">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6f9c-121">子元素</span><span class="sxs-lookup"><span data-stu-id="c6f9c-121">Child Elements</span></span>  
 <span data-ttu-id="c6f9c-122">无。</span><span class="sxs-lookup"><span data-stu-id="c6f9c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6f9c-123">父元素</span><span class="sxs-lookup"><span data-stu-id="c6f9c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c6f9c-124">元素</span><span class="sxs-lookup"><span data-stu-id="c6f9c-124">Element</span></span>|<span data-ttu-id="c6f9c-125">描述</span><span class="sxs-lookup"><span data-stu-id="c6f9c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c6f9c-126">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="c6f9c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c6f9c-127">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="c6f9c-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6f9c-128">注解</span><span class="sxs-lookup"><span data-stu-id="c6f9c-128">Remarks</span></span>  
 <span data-ttu-id="c6f9c-129">从 .NET Framework 4 开始，仅当程序集的时间戳指示它们自上次复制到卷影复制目录后发生了更改时，才会对程序集进行卷影复制。</span><span class="sxs-lookup"><span data-stu-id="c6f9c-129">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="c6f9c-130">这会缩短使用卷影复制的许多应用程序的启动时间，如[卷影复制程序集](../../../app-domains/shadow-copy-assemblies.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="c6f9c-130">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="c6f9c-131">对于程序集更新百分比和频率都很高的应用程序，可能不会从此行为改变中获益。</span><span class="sxs-lookup"><span data-stu-id="c6f9c-131">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="c6f9c-132">在此情况下，可以使用此元素存储 .NET Framework 早先版本的行为。</span><span class="sxs-lookup"><span data-stu-id="c6f9c-132">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6f9c-133">示例</span><span class="sxs-lookup"><span data-stu-id="c6f9c-133">Example</span></span>  
 <span data-ttu-id="c6f9c-134">下面的示例演示如何在 .NET Framework 4 中禁用卷影复制的默认启动行为，并还原为以前版本的 .NET Framework 的启动行为。</span><span class="sxs-lookup"><span data-stu-id="c6f9c-134">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6f9c-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c6f9c-135">See also</span></span>

- [<span data-ttu-id="c6f9c-136">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="c6f9c-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c6f9c-137">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="c6f9c-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c6f9c-138">卷影复制程序集</span><span class="sxs-lookup"><span data-stu-id="c6f9c-138">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
