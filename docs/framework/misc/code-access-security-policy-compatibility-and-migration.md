---
title: 代码访问安全策略兼容性和迁移
description: 阅读摘要，查看有关 .NET 4 中的代码访问安全策略兼容性和迁移的链接。
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
ms.openlocfilehash: e5affd9d16635fa28342b5b7390a083185975f2b
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281727"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="225a3-103">代码访问安全策略兼容性和迁移</span><span class="sxs-lookup"><span data-stu-id="225a3-103">Code Access Security Policy Compatibility and Migration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="225a3-104">代码访问安全性 (CA) 的策略部分在 .NET Framework 4 中已过时。</span><span class="sxs-lookup"><span data-stu-id="225a3-104">The policy portion of code access security (CAS) has been made obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="225a3-105">因此，如果通过) 的其他类型和成员[显式](#explicit_use)或[隐式](#implicit_use)地 (调用过时的策略类型和成员，则可能会遇到编译警告和运行时异常。</span><span class="sxs-lookup"><span data-stu-id="225a3-105">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>

<span data-ttu-id="225a3-106">可以通过以下任一方法来避免这些警告和错误：</span><span class="sxs-lookup"><span data-stu-id="225a3-106">You can avoid the warnings and errors by either:</span></span>

- <span data-ttu-id="225a3-107">[迁移](#migration)到 .NET Framework 4 替换已过时的调用。</span><span class="sxs-lookup"><span data-stu-id="225a3-107">[Migrating](#migration) to the .NET Framework 4 replacements for the obsolete calls.</span></span>

   <span data-ttu-id="225a3-108">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="225a3-108">\- or -</span></span>

- <span data-ttu-id="225a3-109">使用[ \<NetFx40_LegacySecurityPolicy> 配置元素](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)选择使用旧的 CAS 策略行为。</span><span class="sxs-lookup"><span data-stu-id="225a3-109">Using the [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>

<span data-ttu-id="225a3-110">本主题包含以下各节：</span><span class="sxs-lookup"><span data-stu-id="225a3-110">This topic contains the following sections:</span></span>

- [<span data-ttu-id="225a3-111">显式使用</span><span class="sxs-lookup"><span data-stu-id="225a3-111">Explicit Use</span></span>](#explicit_use)

- [<span data-ttu-id="225a3-112">隐式使用</span><span class="sxs-lookup"><span data-stu-id="225a3-112">Implicit Use</span></span>](#implicit_use)

- [<span data-ttu-id="225a3-113">错误和警告</span><span class="sxs-lookup"><span data-stu-id="225a3-113">Errors and Warnings</span></span>](#errors_and_warnings)

- [<span data-ttu-id="225a3-114">迁移：替换已过时的调用</span><span class="sxs-lookup"><span data-stu-id="225a3-114">Migration: Replacement for Obsolete Calls</span></span>](#migration)

- [<span data-ttu-id="225a3-115">兼容性：使用 CAS 策略旧版选项</span><span class="sxs-lookup"><span data-stu-id="225a3-115">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a><span data-ttu-id="225a3-116">显式使用</span><span class="sxs-lookup"><span data-stu-id="225a3-116">Explicit Use</span></span>

<span data-ttu-id="225a3-117">直接操作安全策略或需要沙盒的 CAS 策略的成员已过时，并且默认情况下将产生错误。</span><span class="sxs-lookup"><span data-stu-id="225a3-117">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>

<span data-ttu-id="225a3-118">示例包括：</span><span class="sxs-lookup"><span data-stu-id="225a3-118">Examples of these are:</span></span>

- <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>

<a name="implicit_use"></a>

## <a name="implicit-use"></a><span data-ttu-id="225a3-119">隐式使用</span><span class="sxs-lookup"><span data-stu-id="225a3-119">Implicit Use</span></span>

<span data-ttu-id="225a3-120">由于若干程序集加载重载隐式使用 CAS 策略，因此它们产生错误。</span><span class="sxs-lookup"><span data-stu-id="225a3-120">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="225a3-121">这些重载采用用于解决 CAS 策略的 <xref:System.Security.Policy.Evidence> 参数，并为程序集提供权限授予集。</span><span class="sxs-lookup"><span data-stu-id="225a3-121">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>

<span data-ttu-id="225a3-122">下面是一些示例。</span><span class="sxs-lookup"><span data-stu-id="225a3-122">Here are some examples.</span></span> <span data-ttu-id="225a3-123">过时的重载是使用 <xref:System.Security.Policy.Evidence> 作为参数的重载：</span><span class="sxs-lookup"><span data-stu-id="225a3-123">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>

- <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

<a name="errors_and_warnings"></a>

## <a name="errors-and-warnings"></a><span data-ttu-id="225a3-124">错误和警告</span><span class="sxs-lookup"><span data-stu-id="225a3-124">Errors and Warnings</span></span>

<span data-ttu-id="225a3-125">当使用过时的类型和成员时，会产生下列错误消息。</span><span class="sxs-lookup"><span data-stu-id="225a3-125">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="225a3-126">请注意，<xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 类型本身并未过时。</span><span class="sxs-lookup"><span data-stu-id="225a3-126">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>

<span data-ttu-id="225a3-127">编译时警告：</span><span class="sxs-lookup"><span data-stu-id="225a3-127">Compile-time warning:</span></span>

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

<span data-ttu-id="225a3-128">运行时异常：</span><span class="sxs-lookup"><span data-stu-id="225a3-128">Run-time exception:</span></span>

<span data-ttu-id="225a3-129"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="225a3-129"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="225a3-130">迁移：替换已过时的调用</span><span class="sxs-lookup"><span data-stu-id="225a3-130">Migration: Replacement for Obsolete Calls</span></span>

### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="225a3-131">确定程序集的信任级别</span><span class="sxs-lookup"><span data-stu-id="225a3-131">Determining an Assembly’s Trust Level</span></span>

<span data-ttu-id="225a3-132">CAS 策略通常用于确定程序集或应用程序域的权限授予集或信任级别。</span><span class="sxs-lookup"><span data-stu-id="225a3-132">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="225a3-133">.NET Framework 4 公开了以下有用的属性，这些属性不需要解析安全策略：</span><span class="sxs-lookup"><span data-stu-id="225a3-133">The .NET Framework 4 exposes the following useful properties that do not need to resolve security policy:</span></span>

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a><span data-ttu-id="225a3-134">应用程序域沙盒</span><span class="sxs-lookup"><span data-stu-id="225a3-134">Application Domain Sandboxing</span></span>

<span data-ttu-id="225a3-135"><xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> 方法通常用于对应用程序域中的程序集进行沙盒处理。</span><span class="sxs-lookup"><span data-stu-id="225a3-135">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="225a3-136">.NET Framework 4 公开无需用于 <xref:System.Security.Policy.PolicyLevel> 此目的的成员。</span><span class="sxs-lookup"><span data-stu-id="225a3-136">The .NET Framework 4 exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="225a3-137">有关详细信息，请参阅[如何：在沙盒中运行部分受信任的代码](how-to-run-partially-trusted-code-in-a-sandbox.md)。</span><span class="sxs-lookup"><span data-stu-id="225a3-137">For more information, see [How to: Run Partially Trusted Code in a Sandbox](how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="225a3-138">确定部分受信任的代码的“安全”或“合理”权限集</span><span class="sxs-lookup"><span data-stu-id="225a3-138">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>

<span data-ttu-id="225a3-139">主机通常需要确定适用于沙盒处理托管代码的权限。</span><span class="sxs-lookup"><span data-stu-id="225a3-139">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="225a3-140">在 .NET Framework 4 之前，CAS 策略提供了一种方法来执行此操作 <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="225a3-140">Before the .NET Framework 4, CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="225a3-141">作为替代，.NET Framework 4 提供 <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> 方法，该方法为所提供的证据返回安全的标准权限集。</span><span class="sxs-lookup"><span data-stu-id="225a3-141">As a replacement, .NET Framework 4 provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="225a3-142">非沙盒处理方案：程序集加载的重载</span><span class="sxs-lookup"><span data-stu-id="225a3-142">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>

<span data-ttu-id="225a3-143">使用程序集加载重载的原因可能是为了使用不可通过其他方式使用的参数，而不是对程序集进行沙盒处理。</span><span class="sxs-lookup"><span data-stu-id="225a3-143">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="225a3-144">从 .NET Framework 4 开始，不需要对象作为参数的程序集加载重载， <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 例如， <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType> 启用此方案。</span><span class="sxs-lookup"><span data-stu-id="225a3-144">Starting with the .NET Framework 4, assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>

<span data-ttu-id="225a3-145">如果要对程序集进行沙盒处理，请使用 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> 重载。</span><span class="sxs-lookup"><span data-stu-id="225a3-145">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="225a3-146">兼容性：使用 CAS 策略旧版选项</span><span class="sxs-lookup"><span data-stu-id="225a3-146">Compatibility: Using the CAS Policy Legacy Option</span></span>

<span data-ttu-id="225a3-147">[ \<NetFx40_LegacySecurityPolicy> 配置元素](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)允许你指定进程或库使用旧版 CAS 策略。</span><span class="sxs-lookup"><span data-stu-id="225a3-147">The [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="225a3-148">启用此元素时，策略和证据重载将与其在 Framework 以前版本中进行的操作相同。</span><span class="sxs-lookup"><span data-stu-id="225a3-148">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>

> [!NOTE]
> <span data-ttu-id="225a3-149">CAS 策略行为是在运行时版本的基础上指定的，因此修改一个运行时版本的 CAS 策略不会影响另一个版本的 CAS 策略。</span><span class="sxs-lookup"><span data-stu-id="225a3-149">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="225a3-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="225a3-150">See also</span></span>

- [<span data-ttu-id="225a3-151">如何：运行沙盒中部分受信任的代码</span><span class="sxs-lookup"><span data-stu-id="225a3-151">How to: Run Partially Trusted Code in a Sandbox</span></span>](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="225a3-152">代码安全维护指南</span><span class="sxs-lookup"><span data-stu-id="225a3-152">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
