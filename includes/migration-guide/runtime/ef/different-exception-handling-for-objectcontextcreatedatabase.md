---
ms.openlocfilehash: 687118157020ede200f97a0125c4740a06bf4b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619849"
---
### <a name="different-exception-handling-for-objectcontextcreatedatabase-and-dbproviderservicescreatedatabase-methods"></a><span data-ttu-id="1ab88-101">ObjectContext.CreateDatabase 和 DbProviderServices.CreateDatabase 方法处理异常的方式不同</span><span class="sxs-lookup"><span data-stu-id="1ab88-101">Different exception handling for ObjectContext.CreateDatabase and DbProviderServices.CreateDatabase methods</span></span>

#### <a name="details"></a><span data-ttu-id="1ab88-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="1ab88-102">Details</span></span>

<span data-ttu-id="1ab88-103">从 .NET Framework 4.5 开始，如果数据库创建失败，<code>CreateDatabase</code> 方法将尝试删除空数据库。</span><span class="sxs-lookup"><span data-stu-id="1ab88-103">Beginning in .NET Framework 4.5, if database creation fails, <code>CreateDatabase</code> methods will attempt to drop the empty database.</span></span> <span data-ttu-id="1ab88-104">如果该操作成功，将传播原始 <xref:System.Data.SqlClient.SqlException?displayProperty=fullName>（而非始终在 .NET Framework 4.0 中引发的 <xref:System.InvalidOperationException?displayProperty=fullName>）</span><span class="sxs-lookup"><span data-stu-id="1ab88-104">If that operation succeeds, the original <xref:System.Data.SqlClient.SqlException?displayProperty=fullName> will be propagated (instead of the <xref:System.InvalidOperationException?displayProperty=fullName> that was always thrown in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1ab88-105">建议</span><span class="sxs-lookup"><span data-stu-id="1ab88-105">Suggestion</span></span>

<span data-ttu-id="1ab88-106">在执行 <xref:System.Data.Objects.ObjectContext.CreateDatabase> 或 <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)> 时如果捕获到 <xref:System.InvalidOperationException?displayProperty=fullName>，现在也应会捕获到 SQLExceptions。</span><span class="sxs-lookup"><span data-stu-id="1ab88-106">When catching an <xref:System.InvalidOperationException?displayProperty=fullName> while executing <xref:System.Data.Objects.ObjectContext.CreateDatabase> or <xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)>, SQLExceptions should now also be caught.</span></span>

| <span data-ttu-id="1ab88-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="1ab88-107">Name</span></span>    | <span data-ttu-id="1ab88-108">“值”</span><span class="sxs-lookup"><span data-stu-id="1ab88-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1ab88-109">范围</span><span class="sxs-lookup"><span data-stu-id="1ab88-109">Scope</span></span>   |<span data-ttu-id="1ab88-110">次要</span><span class="sxs-lookup"><span data-stu-id="1ab88-110">Minor</span></span>|
|<span data-ttu-id="1ab88-111">Version</span><span class="sxs-lookup"><span data-stu-id="1ab88-111">Version</span></span>|<span data-ttu-id="1ab88-112">4.5</span><span class="sxs-lookup"><span data-stu-id="1ab88-112">4.5</span></span>|
|<span data-ttu-id="1ab88-113">类型</span><span class="sxs-lookup"><span data-stu-id="1ab88-113">Type</span></span>|<span data-ttu-id="1ab88-114">运行时</span><span class="sxs-lookup"><span data-stu-id="1ab88-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1ab88-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="1ab88-115">Affected APIs</span></span>

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbProviderServices.CreateDatabase(System.Data.Common.DbConnection,System.Nullable{System.Int32},System.Data.Metadata.Edm.StoreItemCollection)?displayProperty=nameWithType></li></ul>|
