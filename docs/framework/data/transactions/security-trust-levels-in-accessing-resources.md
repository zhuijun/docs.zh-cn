---
title: 访问资源时的安全信任级别
description: 了解访问 .NET 中的资源时的安全信任级别。 对于系统事务，有3个主要信任级别。
ms.date: 03/30/2017
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
ms.openlocfilehash: cbae3e87fc11a4230ba8f62cdbc273677e220bfb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152905"
---
# <a name="security-trust-levels-in-accessing-resources"></a><span data-ttu-id="54b36-104">访问资源时的安全信任级别</span><span class="sxs-lookup"><span data-stu-id="54b36-104">Security Trust Levels in Accessing Resources</span></span>

<span data-ttu-id="54b36-105">本主题讨论如何限制对 <xref:System.Transactions> 所公开的资源类型的访问。</span><span class="sxs-lookup"><span data-stu-id="54b36-105">This topic discusses how access is restricted on the types of resources that <xref:System.Transactions> exposes.</span></span>  
  
 <span data-ttu-id="54b36-106"><xref:System.Transactions> 主要有三种信任级别。</span><span class="sxs-lookup"><span data-stu-id="54b36-106">There are three main levels of trust for <xref:System.Transactions>.</span></span> <span data-ttu-id="54b36-107">定义这些信任级别时根据的是 <xref:System.Transactions> 所公开的资源类型以及访问这些资源所需的信任级别。</span><span class="sxs-lookup"><span data-stu-id="54b36-107">The trust levels are defined based on the types of resources that <xref:System.Transactions> exposes, and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="54b36-108"><xref:System.Transactions> 可访问的资源有系统内存、共享进程范围的资源以及系统范围的资源。</span><span class="sxs-lookup"><span data-stu-id="54b36-108">The resources that <xref:System.Transactions> provides access to are system memory, shared process wide resources, and system wide resources.</span></span> <span data-ttu-id="54b36-109">级别包括：</span><span class="sxs-lookup"><span data-stu-id="54b36-109">The levels are:</span></span>  
  
- <span data-ttu-id="54b36-110">对于在单个应用程序域中使用事务的应用程序， **AllowPartiallyTrustedCallers** (APTCA) 。</span><span class="sxs-lookup"><span data-stu-id="54b36-110">**AllowPartiallyTrustedCallers** (APTCA) for applications using transactions within a single application domain.</span></span>  
  
- <span data-ttu-id="54b36-111">使用分布式事务的应用程序的**DistributedTransactionPermission** (DTP) 。</span><span class="sxs-lookup"><span data-stu-id="54b36-111">**DistributedTransactionPermission** (DTP) for applications using distributed transactions.</span></span>  
  
- <span data-ttu-id="54b36-112">完全信任，适用于持久资源、配置管理应用程序和旧版互操作应用程序。</span><span class="sxs-lookup"><span data-stu-id="54b36-112">Full trust for durable resources, configuration management applications, and legacy interop applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54b36-113">不能在模拟上下文中调用任何登记接口。</span><span class="sxs-lookup"><span data-stu-id="54b36-113">You should not call any of the enlistment interfaces with impersonated contexts.</span></span>  
  
## <a name="trust-levels"></a><span data-ttu-id="54b36-114">信任级别</span><span class="sxs-lookup"><span data-stu-id="54b36-114">Trust Levels</span></span>  
  
### <a name="aptca-partial-trust"></a><span data-ttu-id="54b36-115">APTCA（部分信任）</span><span class="sxs-lookup"><span data-stu-id="54b36-115">APTCA (Partial Trust)</span></span>  

 <span data-ttu-id="54b36-116">此 <xref:System.Transactions> 程序集可由部分受信任的代码调用，因为它已标记有 **AllowPartiallyTrustedCallers** 特性 (APTCA) 。</span><span class="sxs-lookup"><span data-stu-id="54b36-116">The <xref:System.Transactions> assembly can be called by partially trusted code because it has been marked with the **AllowPartiallyTrustedCallers** attribute (APTCA).</span></span> <span data-ttu-id="54b36-117">此属性实质上会删除 <xref:System.Security.Permissions.SecurityAction.LinkDemand> **FullTrust** 权限集的隐式，否则将自动在每个类型的每个可公开访问的方法上放置该权限集。</span><span class="sxs-lookup"><span data-stu-id="54b36-117">This attribute essentially removes the implicit <xref:System.Security.Permissions.SecurityAction.LinkDemand> for the **FullTrust** permission set that is otherwise automatically placed on each publicly accessible method in each type.</span></span> <span data-ttu-id="54b36-118">但是，某些类型和成员还是需要更强的权限。</span><span class="sxs-lookup"><span data-stu-id="54b36-118">However, some types and members still require stronger permissions.</span></span>  
  
 <span data-ttu-id="54b36-119">APTCA 特性使应用程序可以在单个应用程序域中以部分信任级别使用事务。</span><span class="sxs-lookup"><span data-stu-id="54b36-119">The APTCA attribute enables applications to use transactions in partial trust within a single application domain.</span></span> <span data-ttu-id="54b36-120">这会启用未升级的事务和可用于错误处理的可变登记。</span><span class="sxs-lookup"><span data-stu-id="54b36-120">This enables non-escalated transactions and volatile enlistments that can be used for error handling.</span></span> <span data-ttu-id="54b36-121">事务处理哈希表和使用它的应用程序就属于这种情况。</span><span class="sxs-lookup"><span data-stu-id="54b36-121">One example of this is a transacted hash table and an application that uses it.</span></span> <span data-ttu-id="54b36-122">可在单个事务下的哈希表中添加和移除数据。</span><span class="sxs-lookup"><span data-stu-id="54b36-122">Data can be added to and removed from the hash table under a single transaction.</span></span> <span data-ttu-id="54b36-123">如果以后回滚该事务，则对该事务下哈希表的所有更改都可撤消。</span><span class="sxs-lookup"><span data-stu-id="54b36-123">If the transaction is later rolled back, all of the changes made to the hash table under that transaction can be undone.</span></span>  
  
### <a name="distributedtransactionpermission-dtp"></a><span data-ttu-id="54b36-124">DistributedTransactionPermission (DTP)</span><span class="sxs-lookup"><span data-stu-id="54b36-124">DistributedTransactionPermission (DTP)</span></span>  

 <span data-ttu-id="54b36-125">当 <xref:System.Transactions> 事务升级为由 MSDTC 进行管理时，<xref:System.Transactions> 会要求提供 <xref:System.Transactions.DistributedTransactionPermission> (DTP) 以创建分布式事务。</span><span class="sxs-lookup"><span data-stu-id="54b36-125">When a <xref:System.Transactions> transaction is escalated to be managed by MSDTC, <xref:System.Transactions> demands the <xref:System.Transactions.DistributedTransactionPermission> (DTP) to create the distributed transaction.</span></span> <span data-ttu-id="54b36-126">这意味着需要向用于使事务升级（例如，通过序列化或其他持久登记）的代码授予 DTP。</span><span class="sxs-lookup"><span data-stu-id="54b36-126">This means that the code that causes the transaction to be escalated (such as through serialization or additional durable enlistments) would need to be granted DTP.</span></span> <span data-ttu-id="54b36-127">最初创建了 <xref:System.Transactions> 事务的代码无需拥有此权限。</span><span class="sxs-lookup"><span data-stu-id="54b36-127">The code that originally created the <xref:System.Transactions> transaction does not necessarily need to possess this permission.</span></span>  
  
### <a name="fulltrust-link-demands"></a><span data-ttu-id="54b36-128">FullTrust 链接要求</span><span class="sxs-lookup"><span data-stu-id="54b36-128">FullTrust Link Demands</span></span>  

 <span data-ttu-id="54b36-129">此权限级别旨在限制要写入持久资源的应用程序。</span><span class="sxs-lookup"><span data-stu-id="54b36-129">This permission level is intended to restrict applications that are writing to durable resources.</span></span> <span data-ttu-id="54b36-130">在出现故障时，应用程序需要能够使用事务管理器进行恢复，以确定事务的最终结果，从而可以更新永久数据。</span><span class="sxs-lookup"><span data-stu-id="54b36-130">Upon failure, the application needs to be able to recover with the transaction manager to determine the final outcome of the transaction, so that it can update permanent data.</span></span> <span data-ttu-id="54b36-131">这种应用程序称为持久源管理器。</span><span class="sxs-lookup"><span data-stu-id="54b36-131">This type of application is known as a durable source manager.</span></span> <span data-ttu-id="54b36-132">SQL 就是这种应用程序的典型示例。</span><span class="sxs-lookup"><span data-stu-id="54b36-132">A classic example of this type of application is SQL.</span></span>  
  
 <span data-ttu-id="54b36-133">若要启用恢复功能，这种应用程序应具备永久使用系统资源的能力。</span><span class="sxs-lookup"><span data-stu-id="54b36-133">To enable recovery, this type of application has the ability to permanently consume system resources.</span></span> <span data-ttu-id="54b36-134">这是因为可恢复的事务管理器必须记住已提交的事务，直到它可确认参与事务的所有持久资源管理器都已接收到结果。</span><span class="sxs-lookup"><span data-stu-id="54b36-134">This is because the recoverable transaction manager must remember transactions that have committed until it can confirm that all durable resource managers that are participating in the transaction have received the outcome.</span></span> <span data-ttu-id="54b36-135">因此，这种应用程序要求完全信任权限，因此它只有在已被授予该信任级别的情况下才能运行。</span><span class="sxs-lookup"><span data-stu-id="54b36-135">Therefore, this type of application requires full trust and should not be run unless that level of trust has been granted.</span></span>  
  
 <span data-ttu-id="54b36-136">有关持久登记和恢复的详细信息，请参阅在 [事务中将资源登记为参与者](enlisting-resources-as-participants-in-a-transaction.md) 和 [执行恢复](performing-recovery.md) 主题。</span><span class="sxs-lookup"><span data-stu-id="54b36-136">For more information on durable enlistments and recovery, see the [Enlisting Resources as Participants in a Transaction](enlisting-resources-as-participants-in-a-transaction.md) and [Performing Recovery](performing-recovery.md) topics.</span></span>  
  
 <span data-ttu-id="54b36-137">此外，使用 COM+ 执行旧版互操作的应用程序也需要具有完全信任级别。</span><span class="sxs-lookup"><span data-stu-id="54b36-137">Applications that perform legacy interop work with COM+ are also required to have full trust.</span></span>  
  
 <span data-ttu-id="54b36-138">下面是部分受信任代码无法调用的类型和成员列表，因为这些类型和成员是使用 **FullTrust** 声明性安全特性修饰的：</span><span class="sxs-lookup"><span data-stu-id="54b36-138">The following is a list of types and members that are not callable by partially trusted code because they are decorated with the **FullTrust** declarative security attribute:</span></span>  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
- <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
- <xref:System.Transactions.TransactionInterop>  
  
- <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
- <xref:System.Transactions.HostCurrentTransactionCallback>  
  
- <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
- <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
- <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 <span data-ttu-id="54b36-139">只有直接调用方才能拥有 **FullTrust** 权限集来使用以上类型或方法。</span><span class="sxs-lookup"><span data-stu-id="54b36-139">Only the immediate caller is required to possess the **FullTrust** permission set to use the above types or methods.</span></span>
