---
title: 内存中数据库
ms.date: 12/13/2019
description: 了解如何使用内存中 SQLite 数据库。
ms.openlocfilehash: fbda5787d95a9ce462752b985f847af0b0551fa6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555362"
---
# <a name="in-memory-databases"></a><span data-ttu-id="0e365-103">内存中数据库</span><span class="sxs-lookup"><span data-stu-id="0e365-103">In-memory databases</span></span>

<span data-ttu-id="0e365-104">SQLite 内存中数据库是完全存储在内存中（而不是磁盘上）的数据库。</span><span class="sxs-lookup"><span data-stu-id="0e365-104">SQLite in-memory databases are databases stored entirely in memory, not on disk.</span></span> <span data-ttu-id="0e365-105">使用特殊数据源文件名 `:memory:` 可创建内存中数据库。</span><span class="sxs-lookup"><span data-stu-id="0e365-105">Use the special data source filename `:memory:` to create an in-memory database.</span></span> <span data-ttu-id="0e365-106">连接关闭后，数据库会被删除。</span><span class="sxs-lookup"><span data-stu-id="0e365-106">When the connection is closed, the database is deleted.</span></span> <span data-ttu-id="0e365-107">使用 `:memory:` 时，每个连接都会创建自己的数据库。</span><span class="sxs-lookup"><span data-stu-id="0e365-107">When using `:memory:`, each connection creates its own database.</span></span>

```connectionstring
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a><span data-ttu-id="0e365-108">可共享的内存中数据库</span><span class="sxs-lookup"><span data-stu-id="0e365-108">Shareable in-memory databases</span></span>

<span data-ttu-id="0e365-109">在连接字符串中使用 `Mode=Memory` 和 `Cache=Shared` 可以在多个连接之间共享内存中数据库。</span><span class="sxs-lookup"><span data-stu-id="0e365-109">In-memory databases can be shared between multiple connections by using `Mode=Memory` and `Cache=Shared` in the connection string.</span></span> <span data-ttu-id="0e365-110">`Data Source` 关键字用于为内存中数据库提供名称。</span><span class="sxs-lookup"><span data-stu-id="0e365-110">The `Data Source` keyword is used to give the in-memory database a name.</span></span> <span data-ttu-id="0e365-111">使用相同名称的连接字符串将访问相同的内存中数据库。</span><span class="sxs-lookup"><span data-stu-id="0e365-111">Connection strings using the same name will access the same in-memory database.</span></span> <span data-ttu-id="0e365-112">只要至少有一个与之相连的连接保持打开状态，数据库便会保持。</span><span class="sxs-lookup"><span data-stu-id="0e365-112">The database persists as long as at least one connection to it remains open.</span></span> <span data-ttu-id="0e365-113">GitHub 上提供了对此进行演示的[示例](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs)。</span><span class="sxs-lookup"><span data-stu-id="0e365-113">A [sample](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) demonstrating this is available on GitHub.</span></span>

```connectionstring
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
