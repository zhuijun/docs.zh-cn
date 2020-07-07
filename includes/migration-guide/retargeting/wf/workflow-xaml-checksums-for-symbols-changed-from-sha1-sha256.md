---
ms.openlocfilehash: 946e71f2f466664c8f9fcf4811288ce693a872eb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617786"
---
### <a name="workflow-xaml-checksums-for-symbols-changed-from-sha1-to-sha256"></a><span data-ttu-id="7a39f-101">符号的工作流 XAML 校验和从 SHA1 更改为 SHA256</span><span class="sxs-lookup"><span data-stu-id="7a39f-101">Workflow XAML checksums for symbols changed from SHA1 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="7a39f-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="7a39f-102">Details</span></span>

<span data-ttu-id="7a39f-103">为支持使用 Visual Studio 进行调试，工作流运行时使用哈希算法生成工作流 XAML 文件的校验和。</span><span class="sxs-lookup"><span data-stu-id="7a39f-103">To support debugging with Visual Studio, the Workflow runtime generates a checksum for a workflow XAML file using a hashing algorithm.</span></span> <span data-ttu-id="7a39f-104">在 .NET Framework 4.6.2 和早期版本中，工作流校验和哈希使用 MD5 算法，这会在启用 FIPS 的系统上导致问题。</span><span class="sxs-lookup"><span data-stu-id="7a39f-104">In the .NET Framework 4.6.2 and earlier versions, workflow checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="7a39f-105">从 .NET Framework 4.7 开始，默认算法已更改为 SHA1。</span><span class="sxs-lookup"><span data-stu-id="7a39f-105">Starting with the .NET Framework 4.7, the default algorithm was changed to SHA1.</span></span> <span data-ttu-id="7a39f-106">从 .NET Framework 4.8 开始，默认算法已更改为 SHA256。</span><span class="sxs-lookup"><span data-stu-id="7a39f-106">Starting with the .NET Framework 4.8, the default algorithm was changed to SHA256.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7a39f-107">建议</span><span class="sxs-lookup"><span data-stu-id="7a39f-107">Suggestion</span></span>

<span data-ttu-id="7a39f-108">如果由于校验和失败，代码无法加载工作流实例或找不到相应符号，请尝试将 `AppContext` 开关“Switch.System.Activities.UseSHA1HashForDebuggerSymbols”设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="7a39f-108">If your code is unable to load workflow instances or to find appropriate symbols due to a checksum failure, try setting the `AppContext` switch "Switch.System.Activities.UseSHA1HashForDebuggerSymbols" to `true`.</span></span> <span data-ttu-id="7a39f-109">在代码中：</span><span class="sxs-lookup"><span data-stu-id="7a39f-109">In code:</span></span>

```csharp
System.AppContext.SetSwitch("Switch.System.Activities.UseSHA1HashForDebuggerSymbols", true);
```

<span data-ttu-id="7a39f-110">或在配置中：</span><span class="sxs-lookup"><span data-stu-id="7a39f-110">Or in configuration:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Activities.UseSHA1HashForDebuggerSymbols=true" />
  </runtime>
</configuration>
```

| <span data-ttu-id="7a39f-111">“属性”</span><span class="sxs-lookup"><span data-stu-id="7a39f-111">Name</span></span>    | <span data-ttu-id="7a39f-112">“值”</span><span class="sxs-lookup"><span data-stu-id="7a39f-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7a39f-113">范围</span><span class="sxs-lookup"><span data-stu-id="7a39f-113">Scope</span></span>   | <span data-ttu-id="7a39f-114">次要</span><span class="sxs-lookup"><span data-stu-id="7a39f-114">Minor</span></span>       |
| <span data-ttu-id="7a39f-115">Version</span><span class="sxs-lookup"><span data-stu-id="7a39f-115">Version</span></span> | <span data-ttu-id="7a39f-116">4.8</span><span class="sxs-lookup"><span data-stu-id="7a39f-116">4.8</span></span>         |
| <span data-ttu-id="7a39f-117">类型</span><span class="sxs-lookup"><span data-stu-id="7a39f-117">Type</span></span>    | <span data-ttu-id="7a39f-118">重定目标</span><span class="sxs-lookup"><span data-stu-id="7a39f-118">Retargeting</span></span> |
