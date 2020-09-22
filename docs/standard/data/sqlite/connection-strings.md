---
title: 连接字符串
ms.date: 12/13/2019
description: 连接字符串的支持关键字和值。
ms.openlocfilehash: 3c50b31689abf6d47aa8f83a6f6f755bcfec0ea3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555388"
---
# <a name="connection-strings"></a><span data-ttu-id="98d4a-103">连接字符串</span><span class="sxs-lookup"><span data-stu-id="98d4a-103">Connection strings</span></span>

<span data-ttu-id="98d4a-104">用于指定如何连接到数据库的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="98d4a-104">A connection string is used to specify how to connect to the database.</span></span> <span data-ttu-id="98d4a-105">Microsoft.Data.Sqlite 中的连接字符串遵循标准 [ADO.NET 语法](../../../framework/data/adonet/connection-strings.md)，形成以分号分隔的关键字和值的列表。</span><span class="sxs-lookup"><span data-stu-id="98d4a-105">Connection strings in Microsoft.Data.Sqlite follow the standard [ADO.NET syntax](../../../framework/data/adonet/connection-strings.md) as a semicolon-separated list of keywords and values.</span></span>

## <a name="keywords"></a><span data-ttu-id="98d4a-106">关键字</span><span class="sxs-lookup"><span data-stu-id="98d4a-106">Keywords</span></span>

<span data-ttu-id="98d4a-107">以下连接字符串关键字可以与 Microsoft.Data.Sqlite 一起使用：</span><span class="sxs-lookup"><span data-stu-id="98d4a-107">The following connection string keywords can be used with Microsoft.Data.Sqlite:</span></span>

### <a name="data-source"></a><span data-ttu-id="98d4a-108">数据源</span><span class="sxs-lookup"><span data-stu-id="98d4a-108">Data source</span></span>

<span data-ttu-id="98d4a-109">数据库文件的路径。</span><span class="sxs-lookup"><span data-stu-id="98d4a-109">The path to the database file.</span></span> <span data-ttu-id="98d4a-110">DataSource  （不带空格）和 Filename  是此关键字的别名。</span><span class="sxs-lookup"><span data-stu-id="98d4a-110">*DataSource* (without a space) and *Filename* are aliases of this keyword.</span></span>

<span data-ttu-id="98d4a-111">SQLite 处理相对于当前工作目录的路径。</span><span class="sxs-lookup"><span data-stu-id="98d4a-111">SQLite treats paths relative to the current working directory.</span></span> <span data-ttu-id="98d4a-112">还可以指定绝对路径。</span><span class="sxs-lookup"><span data-stu-id="98d4a-112">Absolute paths can also be specified.</span></span>

<span data-ttu-id="98d4a-113">如果为空  ，则 SQLite 将创建一个临时磁盘数据库，该数据库会在连接关闭时删除。</span><span class="sxs-lookup"><span data-stu-id="98d4a-113">If **empty**, SQLite creates a temporary on-disk database that's deleted when the connection is closed.</span></span>

<span data-ttu-id="98d4a-114">如果为 `:memory:`，则使用内存数据库。</span><span class="sxs-lookup"><span data-stu-id="98d4a-114">If `:memory:`, an in-memory database is used.</span></span> <span data-ttu-id="98d4a-115">有关详细信息，请参阅[内存数据库](in-memory-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-115">For more information, see [In-Memory databases](in-memory-databases.md).</span></span>

<span data-ttu-id="98d4a-116">以 `|DataDirectory|` 替换字符串开头的路径被视作与相对路径相同。</span><span class="sxs-lookup"><span data-stu-id="98d4a-116">Paths that start with the `|DataDirectory|` substitution string are treated the same as relative paths.</span></span> <span data-ttu-id="98d4a-117">如果设置，路径是相对于 DataDirectory 应用程序域属性值进行设置的。</span><span class="sxs-lookup"><span data-stu-id="98d4a-117">If set, paths are made relative to the DataDirectory application domain property value.</span></span>

<span data-ttu-id="98d4a-118">此关键字还支持 [URI 文件名](https://www.sqlite.org/uri.html)。</span><span class="sxs-lookup"><span data-stu-id="98d4a-118">This keyword also supports [URI Filenames](https://www.sqlite.org/uri.html).</span></span>

### <a name="mode"></a><span data-ttu-id="98d4a-119">模式</span><span class="sxs-lookup"><span data-stu-id="98d4a-119">Mode</span></span>

<span data-ttu-id="98d4a-120">连接模式。</span><span class="sxs-lookup"><span data-stu-id="98d4a-120">The connection mode.</span></span>

| <span data-ttu-id="98d4a-121">“值”</span><span class="sxs-lookup"><span data-stu-id="98d4a-121">Value</span></span>           | <span data-ttu-id="98d4a-122">描述</span><span class="sxs-lookup"><span data-stu-id="98d4a-122">Description</span></span>                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="98d4a-123">ReadWriteCreate</span><span class="sxs-lookup"><span data-stu-id="98d4a-123">ReadWriteCreate</span></span> | <span data-ttu-id="98d4a-124">打开数据库以进行读取和写入，如果数据库不存在，则创建数据库。</span><span class="sxs-lookup"><span data-stu-id="98d4a-124">Opens the database for reading and writing, and creates it if it doesn't exist.</span></span> <span data-ttu-id="98d4a-125">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="98d4a-125">This is the default.</span></span> |
| <span data-ttu-id="98d4a-126">ReadWrite</span><span class="sxs-lookup"><span data-stu-id="98d4a-126">ReadWrite</span></span>       | <span data-ttu-id="98d4a-127">打开数据库以进行读取和写入。</span><span class="sxs-lookup"><span data-stu-id="98d4a-127">Opens the database for reading and writing.</span></span>                                                        |
| <span data-ttu-id="98d4a-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="98d4a-128">ReadOnly</span></span>        | <span data-ttu-id="98d4a-129">以只读模式打开数据库。</span><span class="sxs-lookup"><span data-stu-id="98d4a-129">Opens the database in read-only mode.</span></span>                                                              |
| <span data-ttu-id="98d4a-130">内存</span><span class="sxs-lookup"><span data-stu-id="98d4a-130">Memory</span></span>          | <span data-ttu-id="98d4a-131">打开内存数据库。</span><span class="sxs-lookup"><span data-stu-id="98d4a-131">Opens an in-memory database.</span></span>                                                                       |

### <a name="cache"></a><span data-ttu-id="98d4a-132">缓存</span><span class="sxs-lookup"><span data-stu-id="98d4a-132">Cache</span></span>

<span data-ttu-id="98d4a-133">连接使用的缓存模式。</span><span class="sxs-lookup"><span data-stu-id="98d4a-133">The caching mode used by the connection.</span></span>

| <span data-ttu-id="98d4a-134">“值”</span><span class="sxs-lookup"><span data-stu-id="98d4a-134">Value</span></span>   | <span data-ttu-id="98d4a-135">描述</span><span class="sxs-lookup"><span data-stu-id="98d4a-135">Description</span></span>                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| <span data-ttu-id="98d4a-136">默认</span><span class="sxs-lookup"><span data-stu-id="98d4a-136">Default</span></span> | <span data-ttu-id="98d4a-137">使用基础 SQLite 库的默认模式。</span><span class="sxs-lookup"><span data-stu-id="98d4a-137">Uses the default mode of the underlying SQLite library.</span></span> <span data-ttu-id="98d4a-138">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="98d4a-138">This is the default.</span></span>                   |
| <span data-ttu-id="98d4a-139">Private</span><span class="sxs-lookup"><span data-stu-id="98d4a-139">Private</span></span> | <span data-ttu-id="98d4a-140">每个连接使用一个专用缓存。</span><span class="sxs-lookup"><span data-stu-id="98d4a-140">Each connection uses a private cache.</span></span>                                                          |
| <span data-ttu-id="98d4a-141">Shared</span><span class="sxs-lookup"><span data-stu-id="98d4a-141">Shared</span></span>  | <span data-ttu-id="98d4a-142">连接共享一个缓存。</span><span class="sxs-lookup"><span data-stu-id="98d4a-142">Connections share a cache.</span></span> <span data-ttu-id="98d4a-143">此模式可更改事务和表锁定的行为。</span><span class="sxs-lookup"><span data-stu-id="98d4a-143">This mode can change the behavior of transaction and table locking.</span></span> |

### <a name="password"></a><span data-ttu-id="98d4a-144">Password</span><span class="sxs-lookup"><span data-stu-id="98d4a-144">Password</span></span>

<span data-ttu-id="98d4a-145">加密密钥。</span><span class="sxs-lookup"><span data-stu-id="98d4a-145">The encryption key.</span></span> <span data-ttu-id="98d4a-146">指定后，打开连接后会立即发送 `PRAGMA key`。</span><span class="sxs-lookup"><span data-stu-id="98d4a-146">When specified, `PRAGMA key` is sent immediately after opening the connection.</span></span>

> [!WARNING]
> <span data-ttu-id="98d4a-147">当本机 SQLite 库不支持加密时，密码不起作用。</span><span class="sxs-lookup"><span data-stu-id="98d4a-147">Password has no effect when encryption isn't supported by the native SQLite library.</span></span>

### <a name="foreign-keys"></a><span data-ttu-id="98d4a-148">Foreign Keys</span><span class="sxs-lookup"><span data-stu-id="98d4a-148">Foreign Keys</span></span>

<span data-ttu-id="98d4a-149">一个指示是否启用外键约束的值。</span><span class="sxs-lookup"><span data-stu-id="98d4a-149">A value indicating whether to enable foreign key constraints.</span></span>

| <span data-ttu-id="98d4a-150">“值”</span><span class="sxs-lookup"><span data-stu-id="98d4a-150">Value</span></span>   | <span data-ttu-id="98d4a-151">描述</span><span class="sxs-lookup"><span data-stu-id="98d4a-151">Description</span></span>
| ------- | --- |
| <span data-ttu-id="98d4a-152">True</span><span class="sxs-lookup"><span data-stu-id="98d4a-152">True</span></span>    | <span data-ttu-id="98d4a-153">打开连接后会立即发送 `PRAGMA foreign_keys = 1`。</span><span class="sxs-lookup"><span data-stu-id="98d4a-153">Sends `PRAGMA foreign_keys = 1` immediately after opening the connection.</span></span>
| <span data-ttu-id="98d4a-154">False</span><span class="sxs-lookup"><span data-stu-id="98d4a-154">False</span></span>   | <span data-ttu-id="98d4a-155">打开连接后会立即发送 `PRAGMA foreign_keys = 0`。</span><span class="sxs-lookup"><span data-stu-id="98d4a-155">Sends `PRAGMA foreign_keys = 0` immediately after opening the connection.</span></span>
| <span data-ttu-id="98d4a-156">（空）</span><span class="sxs-lookup"><span data-stu-id="98d4a-156">(empty)</span></span> | <span data-ttu-id="98d4a-157">不发送 `PRAGMA foreign_keys`。</span><span class="sxs-lookup"><span data-stu-id="98d4a-157">Doesn't send `PRAGMA foreign_keys`.</span></span> <span data-ttu-id="98d4a-158">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="98d4a-158">This is the default.</span></span> |

<span data-ttu-id="98d4a-159">如果在 e_sqlite3 中，SQLITE_DEFAULT_FOREIGN_KEYS 用于编译本机 SQLite 库，那么就不需要启用外键。</span><span class="sxs-lookup"><span data-stu-id="98d4a-159">There's no need enable foreign keys if, like in e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS was used to compile the native SQLite library.</span></span>

### <a name="recursive-triggers"></a><span data-ttu-id="98d4a-160">递归触发器</span><span class="sxs-lookup"><span data-stu-id="98d4a-160">Recursive triggers</span></span>

<span data-ttu-id="98d4a-161">一个指示是否启用递归触发器的值。</span><span class="sxs-lookup"><span data-stu-id="98d4a-161">A value that indicates whether to enable recursive triggers.</span></span>

| <span data-ttu-id="98d4a-162">“值”</span><span class="sxs-lookup"><span data-stu-id="98d4a-162">Value</span></span> | <span data-ttu-id="98d4a-163">描述</span><span class="sxs-lookup"><span data-stu-id="98d4a-163">Description</span></span>                                                                 |
| ----- | --------------------------------------------------------------------------- |
| <span data-ttu-id="98d4a-164">True</span><span class="sxs-lookup"><span data-stu-id="98d4a-164">True</span></span>  | <span data-ttu-id="98d4a-165">打开连接后会立即发送 `PRAGMA recursive_triggers`。</span><span class="sxs-lookup"><span data-stu-id="98d4a-165">Sends `PRAGMA recursive_triggers` immediately after opening the connection.</span></span> |
| <span data-ttu-id="98d4a-166">False</span><span class="sxs-lookup"><span data-stu-id="98d4a-166">False</span></span> | <span data-ttu-id="98d4a-167">不发送 `PRAGMA recursive_triggers`。</span><span class="sxs-lookup"><span data-stu-id="98d4a-167">Doesn't send `PRAGMA recursive_triggers`.</span></span> <span data-ttu-id="98d4a-168">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="98d4a-168">This is the default.</span></span>              |

## <a name="connection-string-builder"></a><span data-ttu-id="98d4a-169">连接字符串生成器</span><span class="sxs-lookup"><span data-stu-id="98d4a-169">Connection string builder</span></span>

<span data-ttu-id="98d4a-170">可以使用 <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> 作为创建连接字符串的强类型方式。</span><span class="sxs-lookup"><span data-stu-id="98d4a-170">You can use <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> as a strongly typed way of creating connection strings.</span></span> <span data-ttu-id="98d4a-171">它还可以用于防御连接字符串注入攻击。</span><span class="sxs-lookup"><span data-stu-id="98d4a-171">It can also be used to prevent connection string injection attacks.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a><span data-ttu-id="98d4a-172">示例</span><span class="sxs-lookup"><span data-stu-id="98d4a-172">Examples</span></span>

### <a name="basic"></a><span data-ttu-id="98d4a-173">Basic</span><span class="sxs-lookup"><span data-stu-id="98d4a-173">Basic</span></span>

<span data-ttu-id="98d4a-174">一个包含共享缓存的基本连接字符串，用于提高并发。</span><span class="sxs-lookup"><span data-stu-id="98d4a-174">A basic connection string with a shared cache for improved concurrency.</span></span>

```connectionstring
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a><span data-ttu-id="98d4a-175">加密</span><span class="sxs-lookup"><span data-stu-id="98d4a-175">Encrypted</span></span>

<span data-ttu-id="98d4a-176">一个加密的数据库。</span><span class="sxs-lookup"><span data-stu-id="98d4a-176">An encrypted database.</span></span>

```connectionstring
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a><span data-ttu-id="98d4a-177">只读</span><span class="sxs-lookup"><span data-stu-id="98d4a-177">Read-only</span></span>

<span data-ttu-id="98d4a-178">一个应用无法修改的只读数据库。</span><span class="sxs-lookup"><span data-stu-id="98d4a-178">A read-only database that cannot be modified by the app.</span></span>

```connectionstring
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a><span data-ttu-id="98d4a-179">内存中</span><span class="sxs-lookup"><span data-stu-id="98d4a-179">In-memory</span></span>

<span data-ttu-id="98d4a-180">一个专用的内存数据库。</span><span class="sxs-lookup"><span data-stu-id="98d4a-180">A private, in-memory database.</span></span>

```connectionstring
Data Source=:memory:
```

### <a name="sharable-in-memory"></a><span data-ttu-id="98d4a-181">可共享的内存</span><span class="sxs-lookup"><span data-stu-id="98d4a-181">Sharable in-memory</span></span>

<span data-ttu-id="98d4a-182">一个标识有“Sharable”  名称的可共享内存数据库。</span><span class="sxs-lookup"><span data-stu-id="98d4a-182">A sharable, in-memory database identified by the name *Sharable*.</span></span>

```connectionstring
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a><span data-ttu-id="98d4a-183">请参阅</span><span class="sxs-lookup"><span data-stu-id="98d4a-183">See also</span></span>

* [<span data-ttu-id="98d4a-184">ADO.NET 中的连接字符串</span><span class="sxs-lookup"><span data-stu-id="98d4a-184">Connection Strings in ADO.NET</span></span>](../../../framework/data/adonet/connection-strings.md)
* [<span data-ttu-id="98d4a-185">内存数据库</span><span class="sxs-lookup"><span data-stu-id="98d4a-185">In-Memory databases</span></span>](in-memory-databases.md)
* [<span data-ttu-id="98d4a-186">事务</span><span class="sxs-lookup"><span data-stu-id="98d4a-186">Transactions</span></span>](transactions.md)
