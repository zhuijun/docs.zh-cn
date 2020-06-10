---
title: 审核安全事件
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: b130ed57ba086535122c8c8795c42863348870d0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597652"
---
# <a name="auditing-security-events"></a><span data-ttu-id="f2d38-102">审核安全事件</span><span class="sxs-lookup"><span data-stu-id="f2d38-102">Auditing Security Events</span></span>
<span data-ttu-id="f2d38-103">用 Windows Communication Foundation （WCF）创建的应用程序可以通过审核功能记录安全事件（成功和/或失败）。</span><span class="sxs-lookup"><span data-stu-id="f2d38-103">Applications created with Windows Communication Foundation (WCF) can log security events (either success, failure, or both) with the auditing feature.</span></span> <span data-ttu-id="f2d38-104">这些事件被写入 Windows 系统事件日志，并且可以使用事件查看器进行检查。</span><span class="sxs-lookup"><span data-stu-id="f2d38-104">The events are written to the Windows system event log and can be examined using the Event Viewer.</span></span>  
  
 <span data-ttu-id="f2d38-105">审核为管理员提供了一种检测已经发生或正在发生的攻击的方式。</span><span class="sxs-lookup"><span data-stu-id="f2d38-105">Auditing provides a way for an administrator to detect an attack that has already occurred or is in progress.</span></span> <span data-ttu-id="f2d38-106">此外，审核有助于开发人员调试与安全相关的问题。</span><span class="sxs-lookup"><span data-stu-id="f2d38-106">In addition, auditing can help a developer to debug security-related problems.</span></span> <span data-ttu-id="f2d38-107">例如，如果授权或检查策略配置中的错误意外拒绝授权用户进行访问，开发人员可以通过检查事件日志迅速发现并隔离此错误的原因。</span><span class="sxs-lookup"><span data-stu-id="f2d38-107">For example, if an error in the configuration of the authorization or checking policy accidentally denies access to an authorized user, a developer can quickly discover and isolate the cause of this error by examining the event log.</span></span>  
  
 <span data-ttu-id="f2d38-108">有关 WCF 安全的详细信息，请参阅[安全性概述](security-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f2d38-108">For more information about WCF security, see [Security Overview](security-overview.md).</span></span> <span data-ttu-id="f2d38-109">有关编程 WCF 的详细信息，请参阅[基本 Wcf 编程](../basic-wcf-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="f2d38-109">For more information about programming WCF, see [Basic WCF Programming](../basic-wcf-programming.md).</span></span>  
  
## <a name="audit-level-and-behavior"></a><span data-ttu-id="f2d38-110">审核级别和行为</span><span class="sxs-lookup"><span data-stu-id="f2d38-110">Audit Level and Behavior</span></span>  
 <span data-ttu-id="f2d38-111">存在两个安全审核级别：</span><span class="sxs-lookup"><span data-stu-id="f2d38-111">Two levels of security audits exist:</span></span>  
  
- <span data-ttu-id="f2d38-112">服务授权级别，在该级别对调用方进行授权。</span><span class="sxs-lookup"><span data-stu-id="f2d38-112">Service authorization level, in which a caller is authorized.</span></span>  
  
- <span data-ttu-id="f2d38-113">消息级别，WCF 检查消息有效性并对调用方进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="f2d38-113">Message level, in which WCF checks for message validity and authenticates the caller.</span></span>  
  
 <span data-ttu-id="f2d38-114">您可以检查审核级别的成功或失败情况，这称为*审核行为*。</span><span class="sxs-lookup"><span data-stu-id="f2d38-114">You can check both audit levels for success or failure, which is known as the *audit behavior*.</span></span>  
  
## <a name="audit-log-location"></a><span data-ttu-id="f2d38-115">审核日志位置</span><span class="sxs-lookup"><span data-stu-id="f2d38-115">Audit Log Location</span></span>  
 <span data-ttu-id="f2d38-116">一旦确定审核级别和行为，您（或管理员）就可指定审核日志的位置。</span><span class="sxs-lookup"><span data-stu-id="f2d38-116">Once you determine an audit level and behavior, you (or an administrator) can specify a location for the audit log.</span></span> <span data-ttu-id="f2d38-117">有以下三种选择：Default、Application 和 Security。</span><span class="sxs-lookup"><span data-stu-id="f2d38-117">The three choices include: Default, Application, and Security.</span></span> <span data-ttu-id="f2d38-118">当指定“默认值”时，实际日志取决于所使用的系统以及该系统是否支持写入安全日志。</span><span class="sxs-lookup"><span data-stu-id="f2d38-118">When you specify Default, the actual log depends on which system you are using and whether the system supports writing to the security log.</span></span> <span data-ttu-id="f2d38-119">有关详细信息，请参阅本主题后面的 "操作系统" 部分。</span><span class="sxs-lookup"><span data-stu-id="f2d38-119">For more information, see the "Operating System" section later in this topic.</span></span>  
  
 <span data-ttu-id="f2d38-120">写入 Security 日志要求具有 `SeAuditPrivilege`。</span><span class="sxs-lookup"><span data-stu-id="f2d38-120">To write to the Security log requires the `SeAuditPrivilege`.</span></span> <span data-ttu-id="f2d38-121">默认情况下，只有“本地系统”和“网络服务”帐户具有此特权。</span><span class="sxs-lookup"><span data-stu-id="f2d38-121">By default, only Local System and Network Service accounts have this privilege.</span></span> <span data-ttu-id="f2d38-122">管理 Security 日志功能 `read` 和 `delete` 要求具有 `SeSecurityPrivilege`。</span><span class="sxs-lookup"><span data-stu-id="f2d38-122">To manage the Security log functions `read` and `delete` requires the `SeSecurityPrivilege`.</span></span> <span data-ttu-id="f2d38-123">默认情况下，只有管理员具有此特权。</span><span class="sxs-lookup"><span data-stu-id="f2d38-123">By default, only administrators have this privilege.</span></span>  
  
 <span data-ttu-id="f2d38-124">与此相反，经过身份验证的用户可以读取和写入应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="f2d38-124">In contrast, authenticated users can read and write to the Application log.</span></span> <span data-ttu-id="f2d38-125">默认情况下，Windows XP 将审核事件写入应用程序日志。</span><span class="sxs-lookup"><span data-stu-id="f2d38-125">Windows XP writes audit events to the Application log by default.</span></span> <span data-ttu-id="f2d38-126">该日志还包含对所有通过身份验证的用户可见的个人信息。</span><span class="sxs-lookup"><span data-stu-id="f2d38-126">The log can also contain personal information that is visible to all authenticated users.</span></span>  
  
## <a name="suppressing-audit-failures"></a><span data-ttu-id="f2d38-127">禁止显示审核失败</span><span class="sxs-lookup"><span data-stu-id="f2d38-127">Suppressing Audit Failures</span></span>  
 <span data-ttu-id="f2d38-128">审核过程中的另一个选择为是否禁止显示任何审核失败。</span><span class="sxs-lookup"><span data-stu-id="f2d38-128">Another option during auditing is whether to suppress any audit failure.</span></span> <span data-ttu-id="f2d38-129">默认情况下，审核失败不会影响应用程序。</span><span class="sxs-lookup"><span data-stu-id="f2d38-129">By default, an audit failure does not affect an application.</span></span> <span data-ttu-id="f2d38-130">但是，如若需要，可将此选项设置为 `false`，这将导致引发异常。</span><span class="sxs-lookup"><span data-stu-id="f2d38-130">If required, however, you can set the option to `false`, which causes an exception to be thrown.</span></span>  
  
## <a name="programming-auditing"></a><span data-ttu-id="f2d38-131">审核编程</span><span class="sxs-lookup"><span data-stu-id="f2d38-131">Programming Auditing</span></span>  
 <span data-ttu-id="f2d38-132">可以通过编程或通过配置来指定审核行为。</span><span class="sxs-lookup"><span data-stu-id="f2d38-132">You can specify auditing behavior either programmatically or through configuration.</span></span>  
  
### <a name="auditing-classes"></a><span data-ttu-id="f2d38-133">审核类</span><span class="sxs-lookup"><span data-stu-id="f2d38-133">Auditing Classes</span></span>  
 <span data-ttu-id="f2d38-134">下表描述了用于对审核行为进行编程的类和属性。</span><span class="sxs-lookup"><span data-stu-id="f2d38-134">The following table describes the classes and properties used to program auditing behavior.</span></span>  
  
|<span data-ttu-id="f2d38-135">类</span><span class="sxs-lookup"><span data-stu-id="f2d38-135">Class</span></span>|<span data-ttu-id="f2d38-136">描述</span><span class="sxs-lookup"><span data-stu-id="f2d38-136">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|<span data-ttu-id="f2d38-137">将设置审核选项作为服务行为启用。</span><span class="sxs-lookup"><span data-stu-id="f2d38-137">Enables setting options for auditing as a service behavior.</span></span>|  
|<xref:System.ServiceModel.AuditLogLocation>|<span data-ttu-id="f2d38-138">枚举值，用于指定要写入的日志。</span><span class="sxs-lookup"><span data-stu-id="f2d38-138">Enumeration to specify which log to write to.</span></span> <span data-ttu-id="f2d38-139">可能的值为 Default、Application 和 Security。</span><span class="sxs-lookup"><span data-stu-id="f2d38-139">The possible values are Default, Application, and Security.</span></span> <span data-ttu-id="f2d38-140">选择 Default 时，操作系统将确定实际日志位置。</span><span class="sxs-lookup"><span data-stu-id="f2d38-140">When you select Default, the operating system determines the actual log location.</span></span> <span data-ttu-id="f2d38-141">请参见本主题后面的“Application 或 Security 事件日志选择”部分。</span><span class="sxs-lookup"><span data-stu-id="f2d38-141">See the "Application or Security Event Log Choice" section later in this topic.</span></span>|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|<span data-ttu-id="f2d38-142">指定在消息级别审核哪些类型的消息身份验证事件。</span><span class="sxs-lookup"><span data-stu-id="f2d38-142">Specifies which types of message authentication events are audited at the message level.</span></span> <span data-ttu-id="f2d38-143">选择包括 `None`、`Failure`、`Success` 和 `SuccessOrFailure`。</span><span class="sxs-lookup"><span data-stu-id="f2d38-143">The choices are `None`, `Failure`, `Success`, and `SuccessOrFailure`.</span></span>|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|<span data-ttu-id="f2d38-144">指定在服务级别审核哪些类型的服务授权事件。</span><span class="sxs-lookup"><span data-stu-id="f2d38-144">Specifies which types of service authorization events are audited at the service level.</span></span> <span data-ttu-id="f2d38-145">选择包括 `None`、`Failure`、`Success` 和 `SuccessOrFailure`。</span><span class="sxs-lookup"><span data-stu-id="f2d38-145">The choices are `None`, `Failure`, `Success`, and `SuccessOrFailure`.</span></span>|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|<span data-ttu-id="f2d38-146">指定在审核失败时如何处理客户端请求。</span><span class="sxs-lookup"><span data-stu-id="f2d38-146">Specifies what happens to the client request when auditing fails.</span></span> <span data-ttu-id="f2d38-147">例如，当服务尝试写入 Security 日志但不具有 `SeAuditPrivilege` 时。</span><span class="sxs-lookup"><span data-stu-id="f2d38-147">For example, when the service attempts to write to the security log, but does not have `SeAuditPrivilege`.</span></span> <span data-ttu-id="f2d38-148">默认值 `true` 指示忽略失败，因此将正常处理客户端请求。</span><span class="sxs-lookup"><span data-stu-id="f2d38-148">The default value of `true` indicates that failures are ignored, and the client request is processed normally.</span></span>|  
  
 <span data-ttu-id="f2d38-149">有关设置应用程序以记录审核事件的示例，请参阅[如何：审核安全事件](how-to-audit-wcf-security-events.md)。</span><span class="sxs-lookup"><span data-stu-id="f2d38-149">For an example of setting up an application to log audit events, see [How to: Audit Security Events](how-to-audit-wcf-security-events.md).</span></span>  
  
### <a name="configuration"></a><span data-ttu-id="f2d38-150">Configuration</span><span class="sxs-lookup"><span data-stu-id="f2d38-150">Configuration</span></span>  
 <span data-ttu-id="f2d38-151">通过在下添加，还可以使用配置来指定审核行为 [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) 。</span><span class="sxs-lookup"><span data-stu-id="f2d38-151">You can also use configuration to specify auditing behavior by adding a [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) under the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md).</span></span> <span data-ttu-id="f2d38-152">必须在下添加元素 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) ，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="f2d38-152">You must add the element under a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) as shown in the following code.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <behavior>  
        <!-- auditLogLocation="Application" or "Security" -->  
        <serviceSecurityAudit  
                  auditLogLocation="Application"  
                  suppressAuditFailure="true"  
                  serviceAuthorizationAuditLevel="Failure"  
                  messageAuthenticationAuditLevel="SuccessOrFailure" />
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="f2d38-153">如果启用了审核但未指定 `auditLogLocation`，则对于支持写入 Security 日志的平台来说，默认日志名称为“Security”日志；否则为“Application”日志。</span><span class="sxs-lookup"><span data-stu-id="f2d38-153">If auditing is enabled and an `auditLogLocation` is not specified, the default log name is "Security" log for the platform supporting writing to the Security log; otherwise, it is "Application" log.</span></span> <span data-ttu-id="f2d38-154">只有 Windows Server 2003 和 Windows Vista 操作系统才支持写入安全日志。</span><span class="sxs-lookup"><span data-stu-id="f2d38-154">Only the Windows Server 2003 and Windows Vista operating systems support writing to the Security log.</span></span> <span data-ttu-id="f2d38-155">有关详细信息，请参阅本主题后面的 "操作系统" 部分。</span><span class="sxs-lookup"><span data-stu-id="f2d38-155">For more information, see the "Operating System" section later in this topic.</span></span>  
  
## <a name="security-considerations"></a><span data-ttu-id="f2d38-156">安全注意事项</span><span class="sxs-lookup"><span data-stu-id="f2d38-156">Security Considerations</span></span>  
 <span data-ttu-id="f2d38-157">如果恶意用户了解到审核功能处于启用状态，攻击者可能会发送将导致写入审核项的无效消息。</span><span class="sxs-lookup"><span data-stu-id="f2d38-157">If a malicious user knows that auditing is enabled, that attacker can send invalid messages that cause audit entries to be written.</span></span> <span data-ttu-id="f2d38-158">如果以这种方式填充审核日志，则审核系统会出现故障。</span><span class="sxs-lookup"><span data-stu-id="f2d38-158">If the audit log is filled in this manner, the auditing system fails.</span></span> <span data-ttu-id="f2d38-159">为了缓解此问题，请将 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> 属性设置为 `true`，然后使用事件查看器的属性来控制审核行为。</span><span class="sxs-lookup"><span data-stu-id="f2d38-159">To mitigate this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true` and use the properties of the Event Viewer to control the auditing behavior.</span></span>  
  
 <span data-ttu-id="f2d38-160">写入到 Windows XP 上的应用程序日志的审核事件对任何经过身份验证的用户可见。</span><span class="sxs-lookup"><span data-stu-id="f2d38-160">Audit events that are written to the Application Log on Windows XP are visible to any authenticated user.</span></span>  
  
## <a name="choosing-between-application-and-security-event-logs"></a><span data-ttu-id="f2d38-161">选择 Application 或 Security 事件日志</span><span class="sxs-lookup"><span data-stu-id="f2d38-161">Choosing Between Application and Security Event Logs</span></span>  
 <span data-ttu-id="f2d38-162">下表提供的信息有助于您选择是记录到 Application 事件日志中还是记录到 Security 事件日志中。</span><span class="sxs-lookup"><span data-stu-id="f2d38-162">The following tables provide information to help you choose whether to log into the Application or the Security event log.</span></span>  
  
#### <a name="operating-system"></a><span data-ttu-id="f2d38-163">操作系统</span><span class="sxs-lookup"><span data-stu-id="f2d38-163">Operating System</span></span>  
  
|<span data-ttu-id="f2d38-164">系统</span><span class="sxs-lookup"><span data-stu-id="f2d38-164">System</span></span>|<span data-ttu-id="f2d38-165">应用程序日志</span><span class="sxs-lookup"><span data-stu-id="f2d38-165">Application log</span></span>|<span data-ttu-id="f2d38-166">安全日志</span><span class="sxs-lookup"><span data-stu-id="f2d38-166">Security log</span></span>|  
|------------|---------------------|------------------|  
|<span data-ttu-id="f2d38-167">Windows XP SP2 或更高版本</span><span class="sxs-lookup"><span data-stu-id="f2d38-167">Windows XP SP2 or later</span></span>|<span data-ttu-id="f2d38-168">支持</span><span class="sxs-lookup"><span data-stu-id="f2d38-168">Supported</span></span>|<span data-ttu-id="f2d38-169">不支持</span><span class="sxs-lookup"><span data-stu-id="f2d38-169">Not supported</span></span>|  
|<span data-ttu-id="f2d38-170">Windows Server 2003 SP1 和 Windows Vista</span><span class="sxs-lookup"><span data-stu-id="f2d38-170">Windows Server 2003 SP1 and Windows Vista</span></span>|<span data-ttu-id="f2d38-171">支持</span><span class="sxs-lookup"><span data-stu-id="f2d38-171">Supported</span></span>|<span data-ttu-id="f2d38-172">线程上下文必须具有 `SeAuditPrivilege`</span><span class="sxs-lookup"><span data-stu-id="f2d38-172">Thread context must possess `SeAuditPrivilege`</span></span>|  
  
#### <a name="other-factors"></a><span data-ttu-id="f2d38-173">其他因素</span><span class="sxs-lookup"><span data-stu-id="f2d38-173">Other Factors</span></span>  
 <span data-ttu-id="f2d38-174">除操作系统以外，下表描述了其他用于控制是否启用日志记录的设置。</span><span class="sxs-lookup"><span data-stu-id="f2d38-174">In addition to the operating system, the following table describes other settings that control the enablement of logging.</span></span>  
  
|<span data-ttu-id="f2d38-175">因素</span><span class="sxs-lookup"><span data-stu-id="f2d38-175">Factor</span></span>|<span data-ttu-id="f2d38-176">应用程序日志</span><span class="sxs-lookup"><span data-stu-id="f2d38-176">Application log</span></span>|<span data-ttu-id="f2d38-177">安全日志</span><span class="sxs-lookup"><span data-stu-id="f2d38-177">Security log</span></span>|  
|------------|---------------------|------------------|  
|<span data-ttu-id="f2d38-178">审核策略管理</span><span class="sxs-lookup"><span data-stu-id="f2d38-178">Audit policy management</span></span>|<span data-ttu-id="f2d38-179">不适用。</span><span class="sxs-lookup"><span data-stu-id="f2d38-179">Not applicable.</span></span>|<span data-ttu-id="f2d38-180">除配置以外，Security 日志还受到本地安全机构 (LSA) 策略的控制。</span><span class="sxs-lookup"><span data-stu-id="f2d38-180">Along with configuration, the Security log is also controlled by the local security authority (LSA) policy.</span></span> <span data-ttu-id="f2d38-181">还必须启用“审核对象访问”类别。</span><span class="sxs-lookup"><span data-stu-id="f2d38-181">The "Audit object access" category must also be enabled.</span></span>|  
|<span data-ttu-id="f2d38-182">默认用户体验</span><span class="sxs-lookup"><span data-stu-id="f2d38-182">Default user experience</span></span>|<span data-ttu-id="f2d38-183">所有通过身份验证的用户都可以写入 Application 日志，因此对于应用程序进程，不需要执行其他权限步骤。</span><span class="sxs-lookup"><span data-stu-id="f2d38-183">All authenticated users can write to the Application log, so no additional permission step is needed for application processes.</span></span>|<span data-ttu-id="f2d38-184">应用程序进程（上下文）必须具有 `SeAuditPrivilege`。</span><span class="sxs-lookup"><span data-stu-id="f2d38-184">The application process (context) must have `SeAuditPrivilege`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2d38-185">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f2d38-185">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [<span data-ttu-id="f2d38-186">安全性概述</span><span class="sxs-lookup"><span data-stu-id="f2d38-186">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="f2d38-187">基本 WCF 编程</span><span class="sxs-lookup"><span data-stu-id="f2d38-187">Basic WCF Programming</span></span>](../basic-wcf-programming.md)
- [<span data-ttu-id="f2d38-188">如何：审核安全事件</span><span class="sxs-lookup"><span data-stu-id="f2d38-188">How to: Audit Security Events</span></span>](how-to-audit-wcf-security-events.md)
- [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md)
- [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md)
- <span data-ttu-id="f2d38-189">[Windows Server App Fabric 的安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f2d38-189">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
