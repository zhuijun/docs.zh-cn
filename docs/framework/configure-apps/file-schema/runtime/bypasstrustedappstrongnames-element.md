---
title: <bypassTrustedAppStrongNames> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: 96361a6742d1d2f76cb237344189d3277d7c8069
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739094"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="a4252-102">\<bypassTrustedAppStrongNames> 元素</span><span class="sxs-lookup"><span data-stu-id="a4252-102">\<bypassTrustedAppStrongNames> Element</span></span>

<span data-ttu-id="a4252-103">指定是否在加载到完全信任的完全信任程序集上绕过强名称验证 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="a4252-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**

## <a name="syntax"></a><span data-ttu-id="a4252-104">语法</span><span class="sxs-lookup"><span data-stu-id="a4252-104">Syntax</span></span>

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a4252-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="a4252-105">Attributes and Elements</span></span>

<span data-ttu-id="a4252-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a4252-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a4252-107">特性</span><span class="sxs-lookup"><span data-stu-id="a4252-107">Attributes</span></span>

|<span data-ttu-id="a4252-108">属性</span><span class="sxs-lookup"><span data-stu-id="a4252-108">Attribute</span></span>|<span data-ttu-id="a4252-109">说明</span><span class="sxs-lookup"><span data-stu-id="a4252-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="a4252-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="a4252-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="a4252-111">指定是否启用回避功能，以避免为完全信任程序集验证强名称。</span><span class="sxs-lookup"><span data-stu-id="a4252-111">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="a4252-112">当启用此功能时，加载程序集时，不会验证强名称是否正确。</span><span class="sxs-lookup"><span data-stu-id="a4252-112">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="a4252-113">默认为 `true`。</span><span class="sxs-lookup"><span data-stu-id="a4252-113">The default is `true`.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="a4252-114">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="a4252-114">enabled Attribute</span></span>

|<span data-ttu-id="a4252-115">值</span><span class="sxs-lookup"><span data-stu-id="a4252-115">Value</span></span>|<span data-ttu-id="a4252-116">说明</span><span class="sxs-lookup"><span data-stu-id="a4252-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="a4252-117">将程序集加载到完全信任时，不会验证完全信任程序集上的强名称签名 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="a4252-117">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="a4252-118">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="a4252-118">This is the default.</span></span>|
|`false`|<span data-ttu-id="a4252-119">将程序集加载到完全信任时，会验证完全信任程序集上的强名称签名 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="a4252-119">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="a4252-120">仅对签名正确性检查强名称签名;与另一个匹配的强名称没有比较。</span><span class="sxs-lookup"><span data-stu-id="a4252-120">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a4252-121">子元素</span><span class="sxs-lookup"><span data-stu-id="a4252-121">Child Elements</span></span>

<span data-ttu-id="a4252-122">无。</span><span class="sxs-lookup"><span data-stu-id="a4252-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a4252-123">父元素</span><span class="sxs-lookup"><span data-stu-id="a4252-123">Parent Elements</span></span>

|<span data-ttu-id="a4252-124">元素</span><span class="sxs-lookup"><span data-stu-id="a4252-124">Element</span></span>|<span data-ttu-id="a4252-125">描述</span><span class="sxs-lookup"><span data-stu-id="a4252-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="a4252-126">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="a4252-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="a4252-127">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="a4252-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a4252-128">注解</span><span class="sxs-lookup"><span data-stu-id="a4252-128">Remarks</span></span>

<span data-ttu-id="a4252-129">强名称跳过功能可避免完全信任程序集的强名称签名验证的系统开销。</span><span class="sxs-lookup"><span data-stu-id="a4252-129">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>

<span data-ttu-id="a4252-130">跳过功能适用于使用强名称进行签名及具有以下特征的任何程序集：</span><span class="sxs-lookup"><span data-stu-id="a4252-130">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>

- <span data-ttu-id="a4252-131">完全受信任，无需 <xref:System.Security.Policy.StrongName> 证据（如具有 `MyComputer` 区域证据）。</span><span class="sxs-lookup"><span data-stu-id="a4252-131">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>

- <span data-ttu-id="a4252-132">加载到完全受信任的 <xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="a4252-132">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="a4252-133">加载自该 <xref:System.AppDomain> 的 <xref:System.AppDomainSetup.ApplicationBase%2A> 属性下的某个位置。</span><span class="sxs-lookup"><span data-stu-id="a4252-133">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="a4252-134">签名没有延迟。</span><span class="sxs-lookup"><span data-stu-id="a4252-134">Not delay-signed.</span></span>

> [!NOTE]
> <span data-ttu-id="a4252-135">如果对计算机上的所有应用程序使用注册表项关闭了绕过功能，则此配置文件设置将不起作用。</span><span class="sxs-lookup"><span data-stu-id="a4252-135">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="a4252-136">有关详细信息，请参阅[如何：禁用强名称跳过功能](../../../../standard/assembly/disable-strong-name-bypass-feature.md)。</span><span class="sxs-lookup"><span data-stu-id="a4252-136">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span></span>

## <a name="example"></a><span data-ttu-id="a4252-137">示例</span><span class="sxs-lookup"><span data-stu-id="a4252-137">Example</span></span>

<span data-ttu-id="a4252-138">下面的示例演示如何指定对完全信任程序集的强名称签名进行验证的行为。</span><span class="sxs-lookup"><span data-stu-id="a4252-138">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a4252-139">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a4252-139">See also</span></span>

- [<span data-ttu-id="a4252-140">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="a4252-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a4252-141">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="a4252-141">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a4252-142">如何：禁用强名称跳过功能</span><span class="sxs-lookup"><span data-stu-id="a4252-142">How to: Disable the strong-name bypass feature</span></span>](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
