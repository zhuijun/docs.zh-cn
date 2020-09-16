---
title: 在 ASP.NET 中使用 System.Transactions
description: 在 ASP.NET 应用程序中使用 System.object。 启用分布式事务权限，并使用动态编译。
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: f8bf485389d9633a37201f6293fab8ccae7cf26f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544461"
---
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="64705-104">在 ASP.NET 中使用 System.Transactions</span><span class="sxs-lookup"><span data-stu-id="64705-104">Using System.Transactions in ASP.NET</span></span>
<span data-ttu-id="64705-105">本主题描述如何才能在 ASP.NET 应用程序中成功使用 <xref:System.Transactions>。</span><span class="sxs-lookup"><span data-stu-id="64705-105">This topic describes how you can successfully use <xref:System.Transactions> inside an ASP.NET application.</span></span>

## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="64705-106">在 ASP.NET 中启用 DistributedTransactionPermission</span><span class="sxs-lookup"><span data-stu-id="64705-106">Enable DistributedTransactionPermission in ASP.NET</span></span>
 <span data-ttu-id="64705-107"><xref:System.Transactions> 支持部分受信任的调用方，并用 `AllowPartiallyTrustedCallers` 特性标记 (APTCA) 。</span><span class="sxs-lookup"><span data-stu-id="64705-107"><xref:System.Transactions> supports partially trusted callers and is marked with the `AllowPartiallyTrustedCallers` attribute (APTCA).</span></span> <span data-ttu-id="64705-108">的信任级别 <xref:System.Transactions> 根据资源类型 (例如，系统内存、共享进程范围的资源、系统范围的资源以及公开的其他资源) <xref:System.Transactions> 以及访问这些资源所需的信任级别进行定义。</span><span class="sxs-lookup"><span data-stu-id="64705-108">The trust levels for <xref:System.Transactions> are defined based on the types of resources (for example, system memory, shared process-wide resources, system-wide resources, and other resources) that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="64705-109">在部分信任环境中，除非向非完全信任程序集授予 <xref:System.Transactions.DistributedTransactionPermission>，否则该程序集只能在应用程序域中使用事务（在这种情况下，只有系统内存才是受保护的资源）。</span><span class="sxs-lookup"><span data-stu-id="64705-109">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>

 <span data-ttu-id="64705-110">每当将事务管理升级为由 Microsoft 分布式事务协调器 (MSDTC) 进行管理时，都会要求<xref:System.Transactions.DistributedTransactionPermission> 。</span><span class="sxs-lookup"><span data-stu-id="64705-110"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="64705-111">这种方案使用的是进程范围的资源尤其是全局资源，全局资源是指 MSDTC 日志中的保留空间。</span><span class="sxs-lookup"><span data-stu-id="64705-111">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="64705-112">此用法的一个示例就是数据库或应用程序的 Web 前端，它使用数据库作为所提供服务的一部分。</span><span class="sxs-lookup"><span data-stu-id="64705-112">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>

 <span data-ttu-id="64705-113">ASP.NET 有自己的一组信任级别，并可通过策略文件将特定的权限集与这些信任级别关联。</span><span class="sxs-lookup"><span data-stu-id="64705-113">ASP.NET has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> <span data-ttu-id="64705-114">有关详细信息，请参阅 [ASP.NET 信任级别和策略文件](/previous-versions/aspnet/wyts434y(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="64705-114">For more information, see [ASP.NET Trust Levels and Policy Files](/previous-versions/aspnet/wyts434y(v=vs.100)).</span></span> <span data-ttu-id="64705-115">最初安装 Windows SDK 时，任何默认 ASP.NET 策略文件都不与关联 <xref:System.Transactions.DistributedTransactionPermission> 。</span><span class="sxs-lookup"><span data-stu-id="64705-115">When you initially install the Windows SDK, none of the default ASP.NET policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="64705-116">因此，当 ASP.NET 应用程序中的事务升级为由 MSDTC 管理时，升级就会失败，并引发有关要求 <xref:System.Security.SecurityException> 的 <xref:System.Transactions.DistributedTransactionPermission> 异常。</span><span class="sxs-lookup"><span data-stu-id="64705-116">As such, when your transaction in an ASP.NET application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="64705-117">若要在 ASP.NET 部分信任环境中启用事务升级，应该用与 <xref:System.Transactions.DistributedTransactionPermission> 相同的默认信任级别授予 <xref:System.Data.SqlClient.SqlClientPermission>。</span><span class="sxs-lookup"><span data-stu-id="64705-117">To enable transaction escalation in an ASP.NET partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="64705-118">你可以配置自己的自定义信任级别和策略文件来支持这一方法，也可以修改默认策略文件（即 **Web_hightrust.config** 和 **Web_mediumtrust.config**）。</span><span class="sxs-lookup"><span data-stu-id="64705-118">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>

 <span data-ttu-id="64705-119">若要修改策略文件，请将 `SecurityClass` 的元素添加 `DistributedTransactionPermission` 到元素下的 `SecurityClasses` 元素 `PolicyLevel` ，并在 ASP.NET 中添加对应的 `IPermission` 元素 `NamedPermissionSet` 。</span><span class="sxs-lookup"><span data-stu-id="64705-119">To modify the policy files, add a `SecurityClass` element for `DistributedTransactionPermission` to the `SecurityClasses` element under the `PolicyLevel` element and add a corresponding `IPermission` element under the ASP.NET `NamedPermissionSet` for System.Transactions.</span></span> <span data-ttu-id="64705-120">下面的配置文件演示了这一点。</span><span class="sxs-lookup"><span data-stu-id="64705-120">The following configuration file demonstrates this.</span></span>

```xml
<SecurityClasses>
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
...
</SecurityClasses>

<PermissionSet
  class="NamedPermissionSet"
  version="1"
  Name="ASP.Net">
     <IPermission
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
        version="1"
        Unrestricted="true"
     />
...
</PermissionSet>
```

 <span data-ttu-id="64705-121">有关 ASP.NET 安全策略的详细信息，请参阅 [Ws-securitypolicy 元素 (ASP.NET Settings Schema) ](/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="64705-121">For more information about ASP.NET security policy, see [securityPolicy Element (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).</span></span>

## <a name="dynamic-compilation"></a><span data-ttu-id="64705-122">动态编译</span><span class="sxs-lookup"><span data-stu-id="64705-122">Dynamic Compilation</span></span>
 <span data-ttu-id="64705-123">如果要在访问时动态编译的 ASP.NET 应用程序中导入和使用 <xref:System.Transactions>，则应将对该 <xref:System.Transactions> 程序集的引用放入配置文件中。</span><span class="sxs-lookup"><span data-stu-id="64705-123">If you want to import and use <xref:System.Transactions> in an ASP.NET application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="64705-124">具体而言，应将该引用添加到 `compilation/assemblies` 默认根 **Web.config** 配置文件或特定 Web 应用程序配置文件的部分下。</span><span class="sxs-lookup"><span data-stu-id="64705-124">Specifically, the reference should be added under the `compilation/assemblies` section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="64705-125">下面的示例演示这一操作。</span><span class="sxs-lookup"><span data-stu-id="64705-125">The following example demonstrates this.</span></span>

```xml
<configuration>
   <system.web>
      <compilation>
         <assemblies>
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
         </assemblies>
      </compilation>
   </system.web>
</configuration>
```

 <span data-ttu-id="64705-126">有关详细信息，请参阅 [Add Element for (汇编 for ASP.NET Settings Schema) ](/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="64705-126">For more information, see [add Element for assemblies for compilation (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="64705-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="64705-127">See also</span></span>

- <span data-ttu-id="64705-128">[ASP.NET 信任级别和策略文件](/previous-versions/aspnet/wyts434y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="64705-128">[ASP.NET Trust Levels and Policy Files](/previous-versions/aspnet/wyts434y(v=vs.100))</span></span>
- <span data-ttu-id="64705-129">[securityPolicy 元素（ASP.NET 设置架构）](/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="64705-129">[securityPolicy Element (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))</span></span>
- [<span data-ttu-id="64705-130">事务管理升级</span><span class="sxs-lookup"><span data-stu-id="64705-130">Transaction Management Escalation</span></span>](transaction-management-escalation.md)
