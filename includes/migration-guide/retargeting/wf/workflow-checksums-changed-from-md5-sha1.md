---
ms.openlocfilehash: 72d48d1daa85b6891c122f2fcc5279642253b926
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614387"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a><span data-ttu-id="9c0db-101">工作流校验和已从 MD5 更改为 SHA1</span><span class="sxs-lookup"><span data-stu-id="9c0db-101">Workflow checksums changed from MD5 to SHA1</span></span>

#### <a name="details"></a><span data-ttu-id="9c0db-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="9c0db-102">Details</span></span>

<span data-ttu-id="9c0db-103">为支持使用 Visual Studio 进行调试，工作流运行时使用哈希算法为工作流实例生成校验和。</span><span class="sxs-lookup"><span data-stu-id="9c0db-103">To support debugging with Visual Studio, the Workflow runtime generates a checksum for a workflow instance using a hashing algorithm.</span></span> <span data-ttu-id="9c0db-104">在 .NET Framework 4.6.2 和早期版本中，工作流校验和哈希使用 MD5 算法，这会在启用 FIPS 的系统上导致问题。</span><span class="sxs-lookup"><span data-stu-id="9c0db-104">In the .NET Framework 4.6.2 and earlier versions, workflow checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="9c0db-105">从 .NET Framework 4.7 开始，算法为 SHA1。</span><span class="sxs-lookup"><span data-stu-id="9c0db-105">Starting with the .NET Framework 4.7, the algorithm is SHA1.</span></span> <span data-ttu-id="9c0db-106">如果代码保留了这些校验和，它们将是不兼容的。</span><span class="sxs-lookup"><span data-stu-id="9c0db-106">If your code has persisted these checksums, they will be incompatible.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9c0db-107">建议</span><span class="sxs-lookup"><span data-stu-id="9c0db-107">Suggestion</span></span>

<span data-ttu-id="9c0db-108">如果代码由于校验和失败而无法加载工作流实例，请尝试将 `AppContext` 开关 &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; 设置为 true。在代码中：</span><span class="sxs-lookup"><span data-stu-id="9c0db-108">If your code is unable to load workflow instances due to a checksum failure, try setting the `AppContext` switch &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; to true.In code:</span></span>

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseMD5ForWFDebugger", true);
```

<span data-ttu-id="9c0db-109">或在配置中：</span><span class="sxs-lookup"><span data-stu-id="9c0db-109">Or in configuration:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseMD5ForWFDebugger=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="9c0db-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="9c0db-110">Name</span></span>    | <span data-ttu-id="9c0db-111">“值”</span><span class="sxs-lookup"><span data-stu-id="9c0db-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9c0db-112">范围</span><span class="sxs-lookup"><span data-stu-id="9c0db-112">Scope</span></span>   | <span data-ttu-id="9c0db-113">次要</span><span class="sxs-lookup"><span data-stu-id="9c0db-113">Minor</span></span>       |
| <span data-ttu-id="9c0db-114">Version</span><span class="sxs-lookup"><span data-stu-id="9c0db-114">Version</span></span> | <span data-ttu-id="9c0db-115">4.7</span><span class="sxs-lookup"><span data-stu-id="9c0db-115">4.7</span></span>         |
| <span data-ttu-id="9c0db-116">类型</span><span class="sxs-lookup"><span data-stu-id="9c0db-116">Type</span></span>    | <span data-ttu-id="9c0db-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="9c0db-117">Retargeting</span></span> |
