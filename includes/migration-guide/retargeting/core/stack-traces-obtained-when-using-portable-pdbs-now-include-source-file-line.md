---
ms.openlocfilehash: c7500550cd9714a9788a7dea68af04823f000f7f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614375"
---
### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a><span data-ttu-id="8151d-101">使用便携式 PDB 时获取的堆栈跟踪现在包括源文件和行信息（如果请求）</span><span class="sxs-lookup"><span data-stu-id="8151d-101">Stack traces obtained when using portable PDBs now include source file and line information if requested</span></span>

#### <a name="details"></a><span data-ttu-id="8151d-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="8151d-102">Details</span></span>

<span data-ttu-id="8151d-103">从 .NET Framework 4.7.2 开始，使用便携式 PDB 时获取的堆栈跟踪包括源文件和行信息（如果请求）。</span><span class="sxs-lookup"><span data-stu-id="8151d-103">Starting with .NET Framework 4.7.2, stack traces obtained when using portable PDBs include source file and line information when requested.</span></span> <span data-ttu-id="8151d-104">在 .NET Framework 4.7.2 之前的版本中，即使已显式请求，使用便携式 PDB 时也不会提供源文件和行信息。</span><span class="sxs-lookup"><span data-stu-id="8151d-104">In versions prior to .NET Framework 4.7.2, source file and line information would be unavailable when using portable PDBs even if explicitly requested.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8151d-105">建议</span><span class="sxs-lookup"><span data-stu-id="8151d-105">Suggestion</span></span>

<span data-ttu-id="8151d-106">对于面向 .NET Framework 4.7.2 的应用程序，如果不需要在使用便携式 PDB 时获取的源文件和行信息，可通过将以下内容添加到 `app.config` 文件的 `<runtime>` 部分，从而选择弃用：</span><span class="sxs-lookup"><span data-stu-id="8151d-106">For applications that target the .NET Framework 4.7.2, you can opt out of the source file and line information when using portable PDBs if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true" />
</runtime>
```

<span data-ttu-id="8151d-107">对于面向旧版 .NET Framework，但在 .NET Framework 4.7.2 或更高版本上运行的应用程序，可通过将以下内容添加到 `app.config` 文件的 `<runtime>` 部分，从而选择启用在使用便携式 PDB 时获取源文件和行信息：</span><span class="sxs-lookup"><span data-stu-id="8151d-107">For applications that target earlier versions of the .NET Framework but run on the .NET Framework 4.7.2 or later, you can opt in to the source file and line information when using portable PDBs by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false" />
</runtime>
```

| <span data-ttu-id="8151d-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="8151d-108">Name</span></span>    | <span data-ttu-id="8151d-109">“值”</span><span class="sxs-lookup"><span data-stu-id="8151d-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8151d-110">范围</span><span class="sxs-lookup"><span data-stu-id="8151d-110">Scope</span></span>   | <span data-ttu-id="8151d-111">边缘</span><span class="sxs-lookup"><span data-stu-id="8151d-111">Edge</span></span>        |
| <span data-ttu-id="8151d-112">Version</span><span class="sxs-lookup"><span data-stu-id="8151d-112">Version</span></span> | <span data-ttu-id="8151d-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="8151d-113">4.7.2</span></span>       |
| <span data-ttu-id="8151d-114">类型</span><span class="sxs-lookup"><span data-stu-id="8151d-114">Type</span></span>    | <span data-ttu-id="8151d-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="8151d-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8151d-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="8151d-116">Affected APIs</span></span>

- <xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)>
