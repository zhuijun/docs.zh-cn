---
title: 参数
ms.date: 12/13/2019
description: 了解如何使用 SQL 参数。
ms.openlocfilehash: b24610a5cb65e2b24171452acef9bf55b4995431
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768945"
---
# <a name="parameters"></a><span data-ttu-id="c4e3f-103">参数</span><span class="sxs-lookup"><span data-stu-id="c4e3f-103">Parameters</span></span>

<span data-ttu-id="c4e3f-104">可以使用参数来防范 SQL 注入攻击。</span><span class="sxs-lookup"><span data-stu-id="c4e3f-104">Parameters are used to protect against SQL injection attacks.</span></span> <span data-ttu-id="c4e3f-105">与其将用户输入与 SQL 语句连接起来，不如使用参数来确保输入只被视为文本值，而不会执行。</span><span class="sxs-lookup"><span data-stu-id="c4e3f-105">Instead of concatenating user input with SQL statements, use parameters to ensure input is only ever treated as a literal value and never executed.</span></span> <span data-ttu-id="c4e3f-106">在 SQLite 中，通常允许在 SQL 语句中允许文本的任何位置使用参数。</span><span class="sxs-lookup"><span data-stu-id="c4e3f-106">In SQLite, parameters are typically allowed anywhere a literal is allowed in SQL statements.</span></span>

<span data-ttu-id="c4e3f-107">参数可以使用 `:`、`@` 或 `$` 作为前缀。</span><span class="sxs-lookup"><span data-stu-id="c4e3f-107">Parameters can be prefixed with either `:`, `@`, or `$`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

<span data-ttu-id="c4e3f-108">若要详细了解如何将 .NET 值映射到 SQLite 值，请参阅[数据类型](types.md)。</span><span class="sxs-lookup"><span data-stu-id="c4e3f-108">See [Data types](types.md) for details about how .NET values are mapped to SQLite values.</span></span>

## <a name="truncation"></a><span data-ttu-id="c4e3f-109">截断</span><span class="sxs-lookup"><span data-stu-id="c4e3f-109">Truncation</span></span>

<span data-ttu-id="c4e3f-110">使用 <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> 属性可截断 TEXT 和 BLOB 值。</span><span class="sxs-lookup"><span data-stu-id="c4e3f-110">Use the <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> property to truncate TEXT and BLOB values.</span></span>

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Size = 30;
```

## <a name="alternative-types"></a><span data-ttu-id="c4e3f-111">替代类型</span><span class="sxs-lookup"><span data-stu-id="c4e3f-111">Alternative types</span></span>

<span data-ttu-id="c4e3f-112">有时，你可能想要使用替代的 SQLite 类型。</span><span class="sxs-lookup"><span data-stu-id="c4e3f-112">Sometimes, you may want to use an alternative SQLite type.</span></span> <span data-ttu-id="c4e3f-113">通过设置 <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> 属性可实现此目的。</span><span class="sxs-lookup"><span data-stu-id="c4e3f-113">Do this by setting the <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> property.</span></span>

<span data-ttu-id="c4e3f-114">可以使用以下替代类型映射。</span><span class="sxs-lookup"><span data-stu-id="c4e3f-114">The following alternative type mappings can be used.</span></span> <span data-ttu-id="c4e3f-115">有关默认映射，请参阅[数据类型](types.md)。</span><span class="sxs-lookup"><span data-stu-id="c4e3f-115">For the default mappings, see [Data types](types.md).</span></span>

| <span data-ttu-id="c4e3f-116">“值”</span><span class="sxs-lookup"><span data-stu-id="c4e3f-116">Value</span></span>          | <span data-ttu-id="c4e3f-117">SqliteType</span><span class="sxs-lookup"><span data-stu-id="c4e3f-117">SqliteType</span></span> | <span data-ttu-id="c4e3f-118">备注</span><span class="sxs-lookup"><span data-stu-id="c4e3f-118">Remarks</span></span>          |
| -------------- | ---------- | ---------------- |
| <span data-ttu-id="c4e3f-119">Char</span><span class="sxs-lookup"><span data-stu-id="c4e3f-119">Char</span></span>           | <span data-ttu-id="c4e3f-120">整数</span><span class="sxs-lookup"><span data-stu-id="c4e3f-120">Integer</span></span>    | <span data-ttu-id="c4e3f-121">UTF-16</span><span class="sxs-lookup"><span data-stu-id="c4e3f-121">UTF-16</span></span>           |
| <span data-ttu-id="c4e3f-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="c4e3f-122">DateTime</span></span>       | <span data-ttu-id="c4e3f-123">Real</span><span class="sxs-lookup"><span data-stu-id="c4e3f-123">Real</span></span>       | <span data-ttu-id="c4e3f-124">儒略日值</span><span class="sxs-lookup"><span data-stu-id="c4e3f-124">Julian day value</span></span> |
| <span data-ttu-id="c4e3f-125">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="c4e3f-125">DateTimeOffset</span></span> | <span data-ttu-id="c4e3f-126">Real</span><span class="sxs-lookup"><span data-stu-id="c4e3f-126">Real</span></span>       | <span data-ttu-id="c4e3f-127">儒略日值</span><span class="sxs-lookup"><span data-stu-id="c4e3f-127">Julian day value</span></span> |
| <span data-ttu-id="c4e3f-128">GUID</span><span class="sxs-lookup"><span data-stu-id="c4e3f-128">Guid</span></span>           | <span data-ttu-id="c4e3f-129">Blob</span><span class="sxs-lookup"><span data-stu-id="c4e3f-129">Blob</span></span>       |                  |
| <span data-ttu-id="c4e3f-130">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="c4e3f-130">TimeSpan</span></span>       | <span data-ttu-id="c4e3f-131">Real</span><span class="sxs-lookup"><span data-stu-id="c4e3f-131">Real</span></span>       | <span data-ttu-id="c4e3f-132">以天为单位</span><span class="sxs-lookup"><span data-stu-id="c4e3f-132">In days</span></span>          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a><span data-ttu-id="c4e3f-133">输出参数</span><span class="sxs-lookup"><span data-stu-id="c4e3f-133">Output parameters</span></span>

<span data-ttu-id="c4e3f-134">SQLite 不支持输出参数。</span><span class="sxs-lookup"><span data-stu-id="c4e3f-134">SQLite doesn't support output parameters.</span></span> <span data-ttu-id="c4e3f-135">改为返回查询结果中的值。</span><span class="sxs-lookup"><span data-stu-id="c4e3f-135">Return values in the query results instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4e3f-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="c4e3f-136">See also</span></span>

* [<span data-ttu-id="c4e3f-137">数据类型</span><span class="sxs-lookup"><span data-stu-id="c4e3f-137">Data types</span></span>](types.md)
