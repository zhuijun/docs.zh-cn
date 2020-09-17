---
title: 自定义 SQLite 版本
ms.date: 09/04/2020
description: 了解如何使用本机 SQLite 库的自定义版本。
ms.openlocfilehash: fbf4b4cd33e6e890ce0c0cfe0b7688487b94b4a3
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2020
ms.locfileid: "89516133"
---
# <a name="custom-sqlite-versions"></a><span data-ttu-id="e1b67-103">自定义 SQLite 版本</span><span class="sxs-lookup"><span data-stu-id="e1b67-103">Custom SQLite versions</span></span>

<span data-ttu-id="e1b67-104">`Microsoft.Data.Sqlite` 是在 `SQLitePCLRaw` 基础上生成的。</span><span class="sxs-lookup"><span data-stu-id="e1b67-104">`Microsoft.Data.Sqlite` is built on top of `SQLitePCLRaw`.</span></span> <span data-ttu-id="e1b67-105">可以通过使用捆绑或配置 `SQLitePCLRaw` 提供程序来使用本机 SQLite 库的自定义版本。</span><span class="sxs-lookup"><span data-stu-id="e1b67-105">You can use custom versions of the native SQLite library by using a bundle or by configuring a `SQLitePCLRaw` provider.</span></span>

## <a name="bundles"></a><span data-ttu-id="e1b67-106">捆绑</span><span class="sxs-lookup"><span data-stu-id="e1b67-106">Bundles</span></span>

<span data-ttu-id="e1b67-107">`SQLitePCLRaw` 提供了方便的捆绑包，使你可以轻松地在不同平台间引入正确的依赖项。</span><span class="sxs-lookup"><span data-stu-id="e1b67-107">`SQLitePCLRaw` provides convenience-based bundle packages, that make it easy to bring in the right dependencies across different platforms.</span></span> <span data-ttu-id="e1b67-108">默认情况下，主 `Microsoft.Data.Sqlite` 包引入 `SQLitePCLRaw.bundle_e_sqlite3`。</span><span class="sxs-lookup"><span data-stu-id="e1b67-108">The main `Microsoft.Data.Sqlite` package brings in `SQLitePCLRaw.bundle_e_sqlite3` by default.</span></span> <span data-ttu-id="e1b67-109">若要使用不同的捆绑，请改为安装 `Microsoft.Data.Sqlite.Core` 包以及要使用的捆绑包。</span><span class="sxs-lookup"><span data-stu-id="e1b67-109">To use a different bundle, install the `Microsoft.Data.Sqlite.Core` package instead along with the bundle package you want to use.</span></span> <span data-ttu-id="e1b67-110">捆绑由 `Microsoft.Data.Sqlite` 自动初始化。</span><span class="sxs-lookup"><span data-stu-id="e1b67-110">Bundles are automatically initialized by `Microsoft.Data.Sqlite`.</span></span>

| <span data-ttu-id="e1b67-111">捆绑</span><span class="sxs-lookup"><span data-stu-id="e1b67-111">Bundle</span></span> | <span data-ttu-id="e1b67-112">描述</span><span class="sxs-lookup"><span data-stu-id="e1b67-112">Description</span></span> |
|--|--|
| [<span data-ttu-id="e1b67-113">SQLitePCLRaw.bundle_e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="e1b67-113">SQLitePCLRaw.bundle_e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlite3) | <span data-ttu-id="e1b67-114">在所有平台上提供一致版本的 SQLite。</span><span class="sxs-lookup"><span data-stu-id="e1b67-114">Provides a consistent version of SQLite on all platforms.</span></span> <span data-ttu-id="e1b67-115">包括 FTS4、FTS5、JSON1 和 R\* 树扩展。</span><span class="sxs-lookup"><span data-stu-id="e1b67-115">Includes the FTS4, FTS5, JSON1, and R\*Tree extensions.</span></span> <span data-ttu-id="e1b67-116">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="e1b67-116">This is the default.</span></span> |
| [<span data-ttu-id="e1b67-117">SQLitePCLRaw.bundle_e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="e1b67-117">SQLitePCLRaw.bundle_e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_e_sqlcipher) | <span data-ttu-id="e1b67-118">提供 `SQLCipher` 的非官方开放源代码内部版本。</span><span class="sxs-lookup"><span data-stu-id="e1b67-118">Provides an unofficial, open-source build of `SQLCipher`.</span></span> |
| [<span data-ttu-id="e1b67-119">SQLitePCLRaw.bundle_green</span><span class="sxs-lookup"><span data-stu-id="e1b67-119">SQLitePCLRaw.bundle_green</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_green) | <span data-ttu-id="e1b67-120">与 `bundle_e_sqlite3` 相同，不同之处是在 iOS 上使用系统 SQLite 库。</span><span class="sxs-lookup"><span data-stu-id="e1b67-120">Same as `bundle_e_sqlite3`, except on iOS where it uses the system SQLite library.</span></span> |
| [<span data-ttu-id="e1b67-121">SQLitePCLRaw.bundle_sqlite3</span><span class="sxs-lookup"><span data-stu-id="e1b67-121">SQLitePCLRaw.bundle_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_sqlite3) | <span data-ttu-id="e1b67-122">使用系统 SQLite 库。</span><span class="sxs-lookup"><span data-stu-id="e1b67-122">Uses the system SQLite library.</span></span> |
| [<span data-ttu-id="e1b67-123">SQLitePCLRaw.bundle_winsqlite3</span><span class="sxs-lookup"><span data-stu-id="e1b67-123">SQLitePCLRaw.bundle_winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_winsqlite3) | <span data-ttu-id="e1b67-124">使用 `winsqlite3.dll`（Windows 10 上的系统 SQLite 库）。</span><span class="sxs-lookup"><span data-stu-id="e1b67-124">Uses `winsqlite3.dll`, the system SQLite library on Windows 10.</span></span> |
| [<span data-ttu-id="e1b67-125">SQLitePCLRaw.bundle_zetetic</span><span class="sxs-lookup"><span data-stu-id="e1b67-125">SQLitePCLRaw.bundle_zetetic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.bundle_zetetic) | <span data-ttu-id="e1b67-126">使用 Zetetic 提供的官方 `SQLCipher` 内部版本（不包括在内）。</span><span class="sxs-lookup"><span data-stu-id="e1b67-126">Uses the official `SQLCipher` builds from Zetetic (not included).</span></span> |

<span data-ttu-id="e1b67-127">例如，若要使用 `SQLCipher` 的非官方开放源代码内部版本，请使用以下命令。</span><span class="sxs-lookup"><span data-stu-id="e1b67-127">For example, to use the unofficial, open-source build of `SQLCipher` use the following commands.</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="e1b67-128">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="e1b67-128">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[<span data-ttu-id="e1b67-129">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e1b67-129">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-available-providers"></a><span data-ttu-id="e1b67-130">SQLitePCLRaw 可用的提供程序</span><span class="sxs-lookup"><span data-stu-id="e1b67-130">SQLitePCLRaw available providers</span></span>

<span data-ttu-id="e1b67-131">当不依赖于捆绑时，可以将 SQLite 可用的提供程序用于核心程序集。</span><span class="sxs-lookup"><span data-stu-id="e1b67-131">When not relying on a bundle, you can use the available providers of SQLite with the core assembly.</span></span>

| <span data-ttu-id="e1b67-132">提供程序</span><span class="sxs-lookup"><span data-stu-id="e1b67-132">Provider</span></span> | <span data-ttu-id="e1b67-133">描述</span><span class="sxs-lookup"><span data-stu-id="e1b67-133">Description</span></span> |
|--|--|
| [<span data-ttu-id="e1b67-134">SQLitePCLRaw.provider.dynamic</span><span class="sxs-lookup"><span data-stu-id="e1b67-134">SQLitePCLRaw.provider.dynamic</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.dynamic) | <span data-ttu-id="e1b67-135">`dynamic` 提供程序加载本机库，而不是使用 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> 属性。</span><span class="sxs-lookup"><span data-stu-id="e1b67-135">The `dynamic` provider loads the native library instead of using <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType> attributes.</span></span> <span data-ttu-id="e1b67-136">有关使用此提供程序的详细信息，请参阅[使用动态提供程序](#use-the-dynamic-provider)。</span><span class="sxs-lookup"><span data-stu-id="e1b67-136">For more information on using this provider, see [use the dynamic provider](#use-the-dynamic-provider).</span></span> |
| [<span data-ttu-id="e1b67-137">SQLitePCLRaw.provider.e_sqlite3</span><span class="sxs-lookup"><span data-stu-id="e1b67-137">SQLitePCLRaw.provider.e_sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlite3) | <span data-ttu-id="e1b67-138">`e_sqlite3` 是默认提供程序。</span><span class="sxs-lookup"><span data-stu-id="e1b67-138">The `e_sqlite3` is the default provider.</span></span> |
| [<span data-ttu-id="e1b67-139">SQLitePCLRaw.provider.e_sqlcipher</span><span class="sxs-lookup"><span data-stu-id="e1b67-139">SQLitePCLRaw.provider.e_sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.e_sqlcipher) | <span data-ttu-id="e1b67-140">`e_sqlcipher` 提供程序是非官方且不受支持的 `SQLCipher`。</span><span class="sxs-lookup"><span data-stu-id="e1b67-140">The `e_sqlcipher` provider is the unofficial and unsupported `SQLCipher`.</span></span> |
| [<span data-ttu-id="e1b67-141">SQLitePCLRaw.provider.sqlite3</span><span class="sxs-lookup"><span data-stu-id="e1b67-141">SQLitePCLRaw.provider.sqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlite3) | <span data-ttu-id="e1b67-142">`sqlite3` 提供程序是系统提供的适用于 iOS、macOS 和 Linux 的 `SQLite`。</span><span class="sxs-lookup"><span data-stu-id="e1b67-142">The `sqlite3` provider is a system-provided `SQLite` for iOS, macOS, and Linux.</span></span> |
| [<span data-ttu-id="e1b67-143">SQLitePCLRaw.provider.sqlcipher</span><span class="sxs-lookup"><span data-stu-id="e1b67-143">SQLitePCLRaw.provider.sqlcipher</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.sqlcipher) | <span data-ttu-id="e1b67-144">`sqlcipher` 提供程序适用于来自 `Zetetic` 的官方 `SQLCipher` 内部版本。</span><span class="sxs-lookup"><span data-stu-id="e1b67-144">The `sqlcipher` provider is for official `SQLCipher` builds from `Zetetic`.</span></span> |
| [<span data-ttu-id="e1b67-145">SQLitePCLRaw.provider.winsqlite3</span><span class="sxs-lookup"><span data-stu-id="e1b67-145">SQLitePCLRaw.provider.winsqlite3</span></span>](https://www.nuget.org/packages/SQLitePCLRaw.provider.winsqlite3) | <span data-ttu-id="e1b67-146">`winsqlite3` 提供程序适用于 Windows 10 环境。</span><span class="sxs-lookup"><span data-stu-id="e1b67-146">The `winsqlite3` provider is for Windows 10 environments.</span></span> |

<span data-ttu-id="e1b67-147">若要使用 `sqlite3` 提供程序，请使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="e1b67-147">To use the `sqlite3` provider use the following commands:</span></span>

### <a name="net-core-cli"></a>[<span data-ttu-id="e1b67-148">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="e1b67-148">.NET Core CLI</span></span>](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.core
dotnet add package SQLitePCLRaw.provider.sqlite3
```

### <a name="visual-studio"></a>[<span data-ttu-id="e1b67-149">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e1b67-149">Visual Studio</span></span>](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.core
Install-Package SQLitePCLRaw.provider.sqlite3
```

---

<span data-ttu-id="e1b67-150">安装包后，你可以将提供程序设置为 `sqlite3` 实例。</span><span class="sxs-lookup"><span data-stu-id="e1b67-150">With the packages installed, you then set the provider to the `sqlite3` instance.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SqliteProviderSample/Program.cs)]

## <a name="use-the-dynamic-provider"></a><span data-ttu-id="e1b67-151">使用动态提供程序</span><span class="sxs-lookup"><span data-stu-id="e1b67-151">Use the dynamic provider</span></span>

<span data-ttu-id="e1b67-152">通过利用 `SQLitePCLRaw.provider.dynamic_cdecl` 包，可以使用自己的 SQLite 内部版本。</span><span class="sxs-lookup"><span data-stu-id="e1b67-152">You can use your own build of SQLite by leveraging the `SQLitePCLRaw.provider.dynamic_cdecl` package.</span></span> <span data-ttu-id="e1b67-153">在这种情况下，由你负责随应用部署本机库。</span><span class="sxs-lookup"><span data-stu-id="e1b67-153">In this case, you're responsible for deploying the native library with your app.</span></span> <span data-ttu-id="e1b67-154">请注意，根据所使用的 .NET 平台和运行时，随应用部署本机库的详细信息差异很大。</span><span class="sxs-lookup"><span data-stu-id="e1b67-154">Note, the details of deploying native libraries with your app vary considerably depending on which .NET platform and runtime you're using.</span></span>

<span data-ttu-id="e1b67-155">首先，需要实现 `IGetFunctionPointer`。</span><span class="sxs-lookup"><span data-stu-id="e1b67-155">First, you'll need to implement `IGetFunctionPointer`.</span></span> <span data-ttu-id="e1b67-156">.NET Core 上的实现如下：</span><span class="sxs-lookup"><span data-stu-id="e1b67-156">The implementation on .NET Core is as follows:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

<span data-ttu-id="e1b67-157">接下来，配置 `SQLitePCLRaw` 提供程序。</span><span class="sxs-lookup"><span data-stu-id="e1b67-157">Next, configure the `SQLitePCLRaw` provider.</span></span> <span data-ttu-id="e1b67-158">确保在应用中使用 `Microsoft.Data.Sqlite` 之前完成此操作。</span><span class="sxs-lookup"><span data-stu-id="e1b67-158">Ensure this is done before `Microsoft.Data.Sqlite` is used in your app.</span></span> <span data-ttu-id="e1b67-159">另外，请避免使用可能替代提供程序的 `SQLitePCLRaw` 捆绑包。</span><span class="sxs-lookup"><span data-stu-id="e1b67-159">Also, avoid using a `SQLitePCLRaw` bundle package which might override your provider.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
