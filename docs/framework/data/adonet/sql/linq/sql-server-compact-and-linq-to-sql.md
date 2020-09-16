---
title: SQL Server Compact 与 LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: bdd1237a8eac1c278e7704f3fbf0ae8b1deeff42
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541358"
---
# <a name="sql-server-compact-and-linq-to-sql"></a><span data-ttu-id="8007b-102">SQL Server Compact 与 LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8007b-102">SQL Server Compact and LINQ to SQL</span></span>
<span data-ttu-id="8007b-103">SQL Server Compact 是随 Visual Studio 一起安装的默认数据库。</span><span class="sxs-lookup"><span data-stu-id="8007b-103">SQL Server Compact is the default database installed with Visual Studio.</span></span> <span data-ttu-id="8007b-104">有关详细信息，请参阅 [ (Visual Studio) 使用 SQL Server Compact ](/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110))。</span><span class="sxs-lookup"><span data-stu-id="8007b-104">For more information, see [Using SQL Server Compact (Visual Studio)](/previous-versions/visualstudio/visual-studio-2012/aa983321(v=vs.110)).</span></span>  
  
 <span data-ttu-id="8007b-105">本主题概述了使用情况、配置、功能集和支持范围的主要区别 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8007b-105">This topic outlines the key differences in usage, configuration, feature sets, and scope of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a><span data-ttu-id="8007b-106">SQL Server Compact 相对于 LINQ to SQL 的特性</span><span class="sxs-lookup"><span data-stu-id="8007b-106">Characteristics of SQL Server Compact in Relation to LINQ to SQL</span></span>  
 <span data-ttu-id="8007b-107">默认情况下，为所有 Visual Studio 版本安装 SQL Server Compact，因此在开发计算机上可用于的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8007b-107">By default, SQL Server Compact is installed for all Visual Studio editions, and is therefore available on the development computer for use with [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="8007b-108">但是，部署使用 SQL Server Compact 和的应用程序 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不同于 SQL Server 应用程序的应用程序。</span><span class="sxs-lookup"><span data-stu-id="8007b-108">But deployment of an application that uses SQL Server Compact and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] differs from that for a SQL Server application.</span></span> <span data-ttu-id="8007b-109">SQL Server Compact 不是 .NET Framework 的一部分，因此必须与应用程序一起打包或单独从 Microsoft 网站下载。</span><span class="sxs-lookup"><span data-stu-id="8007b-109">SQL Server Compact is not a part of the .NET Framework, and therefore must be packaged with the application or downloaded separately from the Microsoft site.</span></span>  
  
 <span data-ttu-id="8007b-110">请注意下列特性：</span><span class="sxs-lookup"><span data-stu-id="8007b-110">Note the following characteristics:</span></span>  
  
- <span data-ttu-id="8007b-111">SQL Server Compact 打包为可直接对数据库文件（扩展名为 .sdf）使用的 DLL。</span><span class="sxs-lookup"><span data-stu-id="8007b-111">SQL Server Compact is packaged as a DLL that can be used against database files (.sdf extension) directly.</span></span>  
  
- <span data-ttu-id="8007b-112">SQL Server Compact 与客户端应用程序在同一进程中运行。</span><span class="sxs-lookup"><span data-stu-id="8007b-112">SQL Server Compact runs in the same process as the client application.</span></span> <span data-ttu-id="8007b-113">因此，与 SQL Server Compact 通信相比，可以大大提高与 SQL Server 通信的效率。</span><span class="sxs-lookup"><span data-stu-id="8007b-113">The efficiency of communication with SQL Server Compact can therefore be significantly higher than communicating with SQL Server.</span></span> <span data-ttu-id="8007b-114">另一方面，SQL Server Compact 确实需要托管代码和非托管代码之间的互操作性，而这也会带来开销。</span><span class="sxs-lookup"><span data-stu-id="8007b-114">On the other hand, SQL Server Compact does require interoperability between managed and unmanaged code with its attendant costs.</span></span>  
  
- <span data-ttu-id="8007b-115">SQL Server Compact DLL 很小。</span><span class="sxs-lookup"><span data-stu-id="8007b-115">The size of the SQL Server Compact DLL is small.</span></span> <span data-ttu-id="8007b-116">这一特征减小了应用程序的总大小。</span><span class="sxs-lookup"><span data-stu-id="8007b-116">This feature reduces the overall application size.</span></span>  
  
- <span data-ttu-id="8007b-117">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 运行时和 SQLMetal 命令行工具支持 SQL Server Compact。</span><span class="sxs-lookup"><span data-stu-id="8007b-117">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime and the SQLMetal command-line tool support SQL Server Compact.</span></span>  
  
- <span data-ttu-id="8007b-118">对象关系设计器不支持 SQL Server Compact。</span><span class="sxs-lookup"><span data-stu-id="8007b-118">The Object Relational Designer does not support SQL Server Compact.</span></span>  
  
## <a name="feature-set"></a><span data-ttu-id="8007b-119">功能集</span><span class="sxs-lookup"><span data-stu-id="8007b-119">Feature Set</span></span>  
 <span data-ttu-id="8007b-120">SQL Server Compact 功能集比 SQL Server 功能集简单得多，这种方法可影响 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 应用程序：</span><span class="sxs-lookup"><span data-stu-id="8007b-120">The SQL Server Compact feature set is much simpler than the feature set of SQL Server in the following ways that can affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications :</span></span>  
  
- <span data-ttu-id="8007b-121">SQL Server Compact 不支持存储过程或视图。</span><span class="sxs-lookup"><span data-stu-id="8007b-121">SQL Server Compact does not support stored procedures or views.</span></span>  
  
- <span data-ttu-id="8007b-122">SQL Server Compact 仅支持部分数据类型和 SQL 函数。</span><span class="sxs-lookup"><span data-stu-id="8007b-122">SQL Server Compact supports only a subset of data types and SQL functions.</span></span>  
  
- <span data-ttu-id="8007b-123">SQL Server Compact 仅支持部分 SQL 构造。</span><span class="sxs-lookup"><span data-stu-id="8007b-123">SQL Server Compact supports only a subset of SQL constructs.</span></span>  
  
- <span data-ttu-id="8007b-124">SQL Server Compact 仅提供具有最基本功能的优化器。</span><span class="sxs-lookup"><span data-stu-id="8007b-124">SQL Server Compact provides only a minimal optimizer.</span></span> <span data-ttu-id="8007b-125">有些查询可能会超时。</span><span class="sxs-lookup"><span data-stu-id="8007b-125">It is possible that some queries might time out.</span></span>  
  
- <span data-ttu-id="8007b-126">SQL Server Compact 不支持部分信任。</span><span class="sxs-lookup"><span data-stu-id="8007b-126">SQL Server Compact does not support partial trust.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8007b-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="8007b-127">See also</span></span>

- [<span data-ttu-id="8007b-128">引用</span><span class="sxs-lookup"><span data-stu-id="8007b-128">Reference</span></span>](reference.md)
