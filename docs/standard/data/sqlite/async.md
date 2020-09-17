---
title: 异步限制
ms.date: 09/04/2020
description: 说明异步 API 的限制以及可以使用的一些替代方法。
ms.openlocfilehash: 8b14fcfeb12d331d8d43ca6d77332007a12ae5dc
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2020
ms.locfileid: "89515990"
---
# <a name="async-limitations"></a><span data-ttu-id="ab8e9-103">异步限制</span><span class="sxs-lookup"><span data-stu-id="ab8e9-103">Async limitations</span></span>

<span data-ttu-id="ab8e9-104">SQLite 不支持异步 I/O。</span><span class="sxs-lookup"><span data-stu-id="ab8e9-104">SQLite doesn't support asynchronous I/O.</span></span> <span data-ttu-id="ab8e9-105">异步 ADO.NET 方法将在 Microsoft.Data.Sqlite 中同步执行。</span><span class="sxs-lookup"><span data-stu-id="ab8e9-105">Async ADO.NET methods will execute synchronously in Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="ab8e9-106">请避免调用它们。</span><span class="sxs-lookup"><span data-stu-id="ab8e9-106">Avoid calling them.</span></span>

<span data-ttu-id="ab8e9-107">请改用[共享缓存](connection-strings.md#cache)和[预写日志记录](https://www.sqlite.org/wal.html)，以提高性能和并发性。</span><span class="sxs-lookup"><span data-stu-id="ab8e9-107">Instead, use a [shared cache](connection-strings.md#cache) and [write-ahead logging](https://www.sqlite.org/wal.html) to improve performance and concurrency.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/AsyncSample/Program.cs?name=snippet_WAL)]

> [!TIP]
> <span data-ttu-id="ab8e9-108">默认情况下，在使用 [Entity Framework Core](/ef/core/) 创建的数据库上启用预写日志记录。</span><span class="sxs-lookup"><span data-stu-id="ab8e9-108">Write-ahead logging is enabled by default on databases created using [Entity Framework Core](/ef/core/).</span></span>
