---
title: Oracle 分布式事务
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: a21134c3283d3d9d8d7660eecaaf74d60ecf6662
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166516"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="4a586-102">Oracle 分布式事务</span><span class="sxs-lookup"><span data-stu-id="4a586-102">Oracle Distributed Transactions</span></span>

<span data-ttu-id="4a586-103"><xref:System.Data.OracleClient.OracleConnection> 对象自动在现有分布式事务中登记（如果确定某个事务是活动的）。</span><span class="sxs-lookup"><span data-stu-id="4a586-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="4a586-104">如果连接从连接池中打开或检索，将自动登记事务。</span><span class="sxs-lookup"><span data-stu-id="4a586-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="4a586-105">可以禁用现有事务中的自动登记，方法是将</span><span class="sxs-lookup"><span data-stu-id="4a586-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```csharp  
Enlist=false  
```  
  
 <span data-ttu-id="4a586-106">指定为 <xref:System.Data.OracleClient.OracleConnection> 的连接字符串参数。</span><span class="sxs-lookup"><span data-stu-id="4a586-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a586-107">请参阅</span><span class="sxs-lookup"><span data-stu-id="4a586-107">See also</span></span>

- [<span data-ttu-id="4a586-108">Oracle 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4a586-108">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="4a586-109">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="4a586-109">ADO.NET Overview</span></span>](ado-net-overview.md)
