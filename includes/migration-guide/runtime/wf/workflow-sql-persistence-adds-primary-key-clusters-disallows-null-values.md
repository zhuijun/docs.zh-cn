---
ms.openlocfilehash: 809ca85b347fabc44573e2e0c5a43261d68590d3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621057"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="412e6-101">工作流 SQL 持久性添加主键群集并在某些列中禁止 null 值</span><span class="sxs-lookup"><span data-stu-id="412e6-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

#### <a name="details"></a><span data-ttu-id="412e6-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="412e6-102">Details</span></span>

<span data-ttu-id="412e6-103">从 .NET Framework 4.7 起，SqlWorkflowInstanceStoreSchema.sql 脚本为 SQL 工作流实例存储 (SWIS) 创建的表格使用群集主键。</span><span class="sxs-lookup"><span data-stu-id="412e6-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="412e6-104">因此，标识不支持 <code>null</code> 值。</span><span class="sxs-lookup"><span data-stu-id="412e6-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="412e6-105">此更改不影响 SWIS 操作。</span><span class="sxs-lookup"><span data-stu-id="412e6-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="412e6-106">进行了更新以支持 SQL Server 事务复制。</span><span class="sxs-lookup"><span data-stu-id="412e6-106">The updates were made to support SQL Server Transactional Replication.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="412e6-107">建议</span><span class="sxs-lookup"><span data-stu-id="412e6-107">Suggestion</span></span>

<span data-ttu-id="412e6-108">若要体验此更改，SQL 文件 SqlWorkflowInstanceStoreSchemaUpgrade.sql 必须应用到现有安装。</span><span class="sxs-lookup"><span data-stu-id="412e6-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="412e6-109">新数据库安装自动具有此更改。</span><span class="sxs-lookup"><span data-stu-id="412e6-109">New database installations will automatically have the change.</span></span>

| <span data-ttu-id="412e6-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="412e6-110">Name</span></span>    | <span data-ttu-id="412e6-111">值</span><span class="sxs-lookup"><span data-stu-id="412e6-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="412e6-112">范围</span><span class="sxs-lookup"><span data-stu-id="412e6-112">Scope</span></span>   |<span data-ttu-id="412e6-113">边缘</span><span class="sxs-lookup"><span data-stu-id="412e6-113">Edge</span></span>|
|<span data-ttu-id="412e6-114">Version</span><span class="sxs-lookup"><span data-stu-id="412e6-114">Version</span></span>|<span data-ttu-id="412e6-115">4.7</span><span class="sxs-lookup"><span data-stu-id="412e6-115">4.7</span></span>|
|<span data-ttu-id="412e6-116">类型</span><span class="sxs-lookup"><span data-stu-id="412e6-116">Type</span></span>|<span data-ttu-id="412e6-117">运行时</span><span class="sxs-lookup"><span data-stu-id="412e6-117">Runtime</span></span>|
