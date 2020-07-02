---
ms.openlocfilehash: c5099f610569f7788bb829a2153006d20d8a4ea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615609"
---
### <a name="building-an-entity-framework-edmx-with-visual-studio-2013-can-fail-with-error-msb4062-if-using-the-entitydeploysplit-or-entityclean-tasks"></a><span data-ttu-id="179e7-101">如果使用 EntityDeploySplit 或 EntityClean 任务，使用 Visual Studio 2013 生成 Entity Framework edmx 会失败，错误编码为 MSB4062</span><span class="sxs-lookup"><span data-stu-id="179e7-101">Building an Entity Framework edmx with Visual Studio 2013 can fail with error MSB4062 if using the EntityDeploySplit or EntityClean tasks</span></span>

#### <a name="details"></a><span data-ttu-id="179e7-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="179e7-102">Details</span></span>

<span data-ttu-id="179e7-103">MSBuild 12.0 工具（包括在 Visual Studio 2013 中）更改了 MSBuild 文件位置，使得旧 Entity Framework 目标文件变为无效文件。</span><span class="sxs-lookup"><span data-stu-id="179e7-103">MSBuild 12.0 tools (included in Visual Studio 2013) changed MSBuild file locations, causing older Entity Framework targets files to be invalid.</span></span> <span data-ttu-id="179e7-104">结果是 `EntityDeploySplit` 和 `EntityClean` 任务失败，因为它们无法找到 `Microsoft.Data.Entity.Build.Tasks.dll`。</span><span class="sxs-lookup"><span data-stu-id="179e7-104">The result is that `EntityDeploySplit` and `EntityClean` tasks fail because they are unable to find `Microsoft.Data.Entity.Build.Tasks.dll`.</span></span> <span data-ttu-id="179e7-105">请注意，此中断是由于工具集 (MSBuild/VS) 更改而引起的，并不是因为 .NET Framework 更改。</span><span class="sxs-lookup"><span data-stu-id="179e7-105">Note that this break is because of a toolset (MSBuild/VS) change, not because of a .NET Framework change.</span></span> <span data-ttu-id="179e7-106">它仅在升级开发人员工具时才会发生，仅升级 .NET Framework 不会发生。</span><span class="sxs-lookup"><span data-stu-id="179e7-106">It will only occur when upgrading developer tools, not when merely upgrading the .NET Framework.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="179e7-107">建议</span><span class="sxs-lookup"><span data-stu-id="179e7-107">Suggestion</span></span>

<span data-ttu-id="179e7-108">从 .NET Framework 4.6 开始，Entity Framework 目标文件已修复，可与新 MSBuild 布局一起使用。</span><span class="sxs-lookup"><span data-stu-id="179e7-108">Entity Framework targets files are fixed to work with the new MSBuild layout beginning in the .NET Framework 4.6.</span></span> <span data-ttu-id="179e7-109">升级到该版本的 Framework 将解决此问题。</span><span class="sxs-lookup"><span data-stu-id="179e7-109">Upgrading to that version of the Framework will fix this issue.</span></span> <span data-ttu-id="179e7-110">或者，可使用[此解决方法](https://stackoverflow.com/a/24249247/131944)直接修补目标文件。</span><span class="sxs-lookup"><span data-stu-id="179e7-110">Alternatively, [this workaround](https://stackoverflow.com/a/24249247/131944) can be used to patch the targets files directly.</span></span>

| <span data-ttu-id="179e7-111">“属性”</span><span class="sxs-lookup"><span data-stu-id="179e7-111">Name</span></span>    | <span data-ttu-id="179e7-112">“值”</span><span class="sxs-lookup"><span data-stu-id="179e7-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="179e7-113">范围</span><span class="sxs-lookup"><span data-stu-id="179e7-113">Scope</span></span>   | <span data-ttu-id="179e7-114">主要</span><span class="sxs-lookup"><span data-stu-id="179e7-114">Major</span></span>       |
| <span data-ttu-id="179e7-115">Version</span><span class="sxs-lookup"><span data-stu-id="179e7-115">Version</span></span> | <span data-ttu-id="179e7-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="179e7-116">4.5.1</span></span>       |
| <span data-ttu-id="179e7-117">类型</span><span class="sxs-lookup"><span data-stu-id="179e7-117">Type</span></span>    | <span data-ttu-id="179e7-118">重定目标</span><span class="sxs-lookup"><span data-stu-id="179e7-118">Retargeting</span></span> |
