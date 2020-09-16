---
title: <generatePublisherEvidence> 元素
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 11592b055641c0fa2d2b968547dcc5aa40c94600
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541779"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="9125a-102">\<generatePublisherEvidence> 元素</span><span class="sxs-lookup"><span data-stu-id="9125a-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="9125a-103">指定运行时是否 <xref:System.Security.Policy.Publisher> 为代码访问安全性 (CAS) 创建证据。</span><span class="sxs-lookup"><span data-stu-id="9125a-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
## <a name="syntax"></a><span data-ttu-id="9125a-104">语法</span><span class="sxs-lookup"><span data-stu-id="9125a-104">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9125a-105">特性和元素</span><span class="sxs-lookup"><span data-stu-id="9125a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9125a-106">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9125a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9125a-107">特性</span><span class="sxs-lookup"><span data-stu-id="9125a-107">Attributes</span></span>  
  
|<span data-ttu-id="9125a-108">属性</span><span class="sxs-lookup"><span data-stu-id="9125a-108">Attribute</span></span>|<span data-ttu-id="9125a-109">描述</span><span class="sxs-lookup"><span data-stu-id="9125a-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="9125a-110">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="9125a-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="9125a-111">指定运行时是否创建 <xref:System.Security.Policy.Publisher> 证据。</span><span class="sxs-lookup"><span data-stu-id="9125a-111">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9125a-112">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="9125a-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="9125a-113">“值”</span><span class="sxs-lookup"><span data-stu-id="9125a-113">Value</span></span>|<span data-ttu-id="9125a-114">说明</span><span class="sxs-lookup"><span data-stu-id="9125a-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="9125a-115">不创建 <xref:System.Security.Policy.Publisher> 证据。</span><span class="sxs-lookup"><span data-stu-id="9125a-115">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="9125a-116">创建 <xref:System.Security.Policy.Publisher> 证据。</span><span class="sxs-lookup"><span data-stu-id="9125a-116">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="9125a-117">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="9125a-117">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9125a-118">子元素</span><span class="sxs-lookup"><span data-stu-id="9125a-118">Child Elements</span></span>  
 <span data-ttu-id="9125a-119">无。</span><span class="sxs-lookup"><span data-stu-id="9125a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9125a-120">父元素</span><span class="sxs-lookup"><span data-stu-id="9125a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9125a-121">元素</span><span class="sxs-lookup"><span data-stu-id="9125a-121">Element</span></span>|<span data-ttu-id="9125a-122">说明</span><span class="sxs-lookup"><span data-stu-id="9125a-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9125a-123">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="9125a-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9125a-124">包含有关运行时初始化选项的信息。</span><span class="sxs-lookup"><span data-stu-id="9125a-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9125a-125">备注</span><span class="sxs-lookup"><span data-stu-id="9125a-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9125a-126">在 .NET Framework 4 及更高版本中，此元素对程序集加载时间没有影响。</span><span class="sxs-lookup"><span data-stu-id="9125a-126">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="9125a-127">有关详细信息，请参阅 [安全更改](/previous-versions/dotnet/framework/security/security-changes)中的 "安全策略简化" 部分。</span><span class="sxs-lookup"><span data-stu-id="9125a-127">For more information, see the "Security Policy Simplification" section in [Security Changes](/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="9125a-128">公共语言运行时 (CLR) 尝试在加载时验证 Authenticode 签名，以创建 <xref:System.Security.Policy.Publisher> 程序集的证据。</span><span class="sxs-lookup"><span data-stu-id="9125a-128">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="9125a-129">但是，默认情况下，大多数应用程序不需要 <xref:System.Security.Policy.Publisher> 证据。</span><span class="sxs-lookup"><span data-stu-id="9125a-129">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="9125a-130">标准 CAS 策略不依赖于 <xref:System.Security.Policy.PublisherMembershipCondition> 。</span><span class="sxs-lookup"><span data-stu-id="9125a-130">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="9125a-131">除非你的应用程序在具有自定义 CAS 策略的计算机上执行，或者要 <xref:System.Security.Permissions.PublisherIdentityPermission> 在部分信任环境中满足的要求，否则，应避免与验证发行者签名相关的不必要的启动成本。</span><span class="sxs-lookup"><span data-stu-id="9125a-131">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="9125a-132">在完全信任的环境中，标识权限的 (要求始终成功。 ) </span><span class="sxs-lookup"><span data-stu-id="9125a-132">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9125a-133">建议服务使用 `<generatePublisherEvidence>` 元素以提高启动性能。</span><span class="sxs-lookup"><span data-stu-id="9125a-133">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="9125a-134">使用此元素还有助于避免可能导致超时和取消服务启动的延迟。</span><span class="sxs-lookup"><span data-stu-id="9125a-134">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="9125a-135">配置文件</span><span class="sxs-lookup"><span data-stu-id="9125a-135">Configuration File</span></span>  
 <span data-ttu-id="9125a-136">此元素只能在应用程序配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="9125a-136">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9125a-137">示例</span><span class="sxs-lookup"><span data-stu-id="9125a-137">Example</span></span>  
 <span data-ttu-id="9125a-138">下面的示例演示如何使用 `<generatePublisherEvidence>` 元素禁用应用程序的 CAS 发行者策略检查。</span><span class="sxs-lookup"><span data-stu-id="9125a-138">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9125a-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="9125a-139">See also</span></span>

- [<span data-ttu-id="9125a-140">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="9125a-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9125a-141">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="9125a-141">Configuration File Schema</span></span>](../index.md)
