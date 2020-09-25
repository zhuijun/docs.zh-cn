---
title: 事务支持
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: 1449f4d10d0feeec47ac17ffda91acb3e0da17ea
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202196"
---
# <a name="transaction-support"></a><span data-ttu-id="52368-102">事务支持</span><span class="sxs-lookup"><span data-stu-id="52368-102">Transaction Support</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="52368-103">支持三种不同的事务模型。</span><span class="sxs-lookup"><span data-stu-id="52368-103">supports three distinct transaction models.</span></span> <span data-ttu-id="52368-104">下文按执行检查的顺序列出了这些模型。</span><span class="sxs-lookup"><span data-stu-id="52368-104">The following lists these models in the order of checks performed.</span></span>  
  
## <a name="explicit-local-transaction"></a><span data-ttu-id="52368-105">显式本地事务</span><span class="sxs-lookup"><span data-stu-id="52368-105">Explicit Local Transaction</span></span>  

 <span data-ttu-id="52368-106">调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时，如果 <xref:System.Data.Linq.DataContext.Transaction%2A> 属性设置为 (`IDbTransaction`) 事务，则在同一事务的上下文中执行 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 调用。</span><span class="sxs-lookup"><span data-stu-id="52368-106">When <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called, if the <xref:System.Data.Linq.DataContext.Transaction%2A> property is set to a (`IDbTransaction`) transaction, the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> call is executed in the context of the same transaction.</span></span>  
  
 <span data-ttu-id="52368-107">成功执行事务后，要由你来提交或回滚事务。</span><span class="sxs-lookup"><span data-stu-id="52368-107">It is your responsibility to commit or rollback the transaction after successful execution of the transaction.</span></span> <span data-ttu-id="52368-108">与事务对应的连接必须与用于构造 <xref:System.Data.Linq.DataContext> 的连接匹配。</span><span class="sxs-lookup"><span data-stu-id="52368-108">The connection corresponding to the transaction must match the connection used for constructing the <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="52368-109">如果使用其他连接，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="52368-109">An exception is thrown if a different connection is used.</span></span>  
  
## <a name="explicit-distributable-transaction"></a><span data-ttu-id="52368-110">显式可分发事务</span><span class="sxs-lookup"><span data-stu-id="52368-110">Explicit Distributable Transaction</span></span>  

 <span data-ttu-id="52368-111">可以在活动 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的作用域中调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> API（包括但不限于 <xref:System.Transactions.Transaction>）。</span><span class="sxs-lookup"><span data-stu-id="52368-111">You can call [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] APIs (including but not limited to <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) in the scope of an active <xref:System.Transactions.Transaction>.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="52368-112">检测到调用是在事务的作用域中，并且不会创建新的事务。</span><span class="sxs-lookup"><span data-stu-id="52368-112">detects that the call is in the scope of a transaction and does not create a new transaction.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="52368-113">在这种情况下，也可避免关闭连接。</span><span class="sxs-lookup"><span data-stu-id="52368-113">also avoids closing the connection in this case.</span></span> <span data-ttu-id="52368-114">您可以在此类事务的上下文中执行查询和 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 操作。</span><span class="sxs-lookup"><span data-stu-id="52368-114">You can perform query and <xref:System.Data.Linq.DataContext.SubmitChanges%2A> executions in the context of such a transaction.</span></span>  
  
## <a name="implicit-transaction"></a><span data-ttu-id="52368-115">隐式事务</span><span class="sxs-lookup"><span data-stu-id="52368-115">Implicit Transaction</span></span>  

 <span data-ttu-id="52368-116">当您调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会检查此调用是否在 <xref:System.Transactions.Transaction> 的作用域内或者 `Transaction` 属性 (`IDbTransaction`) 是否设置为由用户启动的本地事务。</span><span class="sxs-lookup"><span data-stu-id="52368-116">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] checks to see whether the call is in the scope of a <xref:System.Transactions.Transaction> or if the `Transaction` property (`IDbTransaction`) is set to a user-started local transaction.</span></span> <span data-ttu-id="52368-117">如果这两个事务均未找到，则 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 启动本地事务 (`IDbTransaction`)，并使用此事务执行所生成的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="52368-117">If it finds neither transaction, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a local transaction (`IDbTransaction`) and uses it to execute the generated SQL commands.</span></span> <span data-ttu-id="52368-118">当所有 SQL 命令均已成功执行完毕时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 提交本地事务并返回。</span><span class="sxs-lookup"><span data-stu-id="52368-118">When all SQL commands have been successfully completed, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] commits the local transaction and returns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52368-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="52368-119">See also</span></span>

- [<span data-ttu-id="52368-120">背景信息</span><span class="sxs-lookup"><span data-stu-id="52368-120">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="52368-121">如何：通过使用事务对数据提交进行分类</span><span class="sxs-lookup"><span data-stu-id="52368-121">How to: Bracket Data Submissions by Using Transactions</span></span>](how-to-bracket-data-submissions-by-using-transactions.md)
