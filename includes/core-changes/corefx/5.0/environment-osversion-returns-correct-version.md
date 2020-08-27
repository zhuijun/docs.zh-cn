---
ms.openlocfilehash: ccd056f23d26e6cce4cc691542784792bffe9fc6
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558164"
---
### <a name="environmentosversion-returns-the-correct-operating-system-version"></a><span data-ttu-id="407f2-101">Environment.OSVersion 返回正确的操作系统版本</span><span class="sxs-lookup"><span data-stu-id="407f2-101">Environment.OSVersion returns the correct operating system version</span></span>

<span data-ttu-id="407f2-102"><xref:System.Environment.OSVersion?displayProperty=nameWithType> 返回操作系统 (OS) 的实际版本，而不是为应用程序兼容性而选择的 OS。</span><span class="sxs-lookup"><span data-stu-id="407f2-102"><xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system (OS) instead of, for example, the OS that's selected for application compatibility.</span></span>

#### <a name="change-description"></a><span data-ttu-id="407f2-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="407f2-103">Change description</span></span>

<span data-ttu-id="407f2-104">在以前的 .NET 版本中，当应用程序在 Windows 兼容模式下运行时，<xref:System.Environment.OSVersion?displayProperty=nameWithType> 返回的 OS 版本可能不正确。</span><span class="sxs-lookup"><span data-stu-id="407f2-104">In previous .NET versions, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns an OS version that may be incorrect when an application runs under Windows compatibility mode.</span></span> <span data-ttu-id="407f2-105">有关详细信息，请参阅 [GetVersionExA 函数备注](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks)。</span><span class="sxs-lookup"><span data-stu-id="407f2-105">For more information, see [GetVersionExA function remarks](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span></span>

<span data-ttu-id="407f2-106">从 .NET 5.0 开始，<xref:System.Environment.OSVersion?displayProperty=nameWithType> 返回操作系统的实际版本。</span><span class="sxs-lookup"><span data-stu-id="407f2-106">Starting in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="407f2-107">更改原因</span><span class="sxs-lookup"><span data-stu-id="407f2-107">Reason for change</span></span>

<span data-ttu-id="407f2-108">此属性的用户希望它返回操作系统的实际版本。</span><span class="sxs-lookup"><span data-stu-id="407f2-108">Users of this property expect it to return the actual version of the operating system.</span></span> <span data-ttu-id="407f2-109">大多数 .NET 应用并未在其应用程序清单中指定其支持的版本，因此会从 dotnet 主机获取默认的支持版本。</span><span class="sxs-lookup"><span data-stu-id="407f2-109">Most .NET apps don't specify their supported version in their application manifest, and thus get the default supported version from the dotnet host.</span></span> <span data-ttu-id="407f2-110">因此，兼容性填充码对于正在运行的应用没有什么意义。</span><span class="sxs-lookup"><span data-stu-id="407f2-110">As a result, the compatibility shim is rarely meaningful for the app that's running.</span></span> <span data-ttu-id="407f2-111">当 Windows 发布新版本时，如果较旧的 dotnet 主机仍在使用，这些应用可能会收到错误的 OS 版本。</span><span class="sxs-lookup"><span data-stu-id="407f2-111">When Windows releases a new version and an older dotnet host is still in use, these apps may get an incorrect OS version.</span></span> <span data-ttu-id="407f2-112">返回实际版本更符合开发人员对此 API 的期望。</span><span class="sxs-lookup"><span data-stu-id="407f2-112">Returning the actual version is more inline with developers' expectations of this API.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="407f2-113">引入的版本</span><span class="sxs-lookup"><span data-stu-id="407f2-113">Version introduced</span></span>

<span data-ttu-id="407f2-114">5.0</span><span class="sxs-lookup"><span data-stu-id="407f2-114">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="407f2-115">建议操作</span><span class="sxs-lookup"><span data-stu-id="407f2-115">Recommended action</span></span>

<span data-ttu-id="407f2-116">查看和测试使用 <xref:System.Environment.OSVersion?displayProperty=nameWithType> 的任何代码，以确保其行为符合预期。</span><span class="sxs-lookup"><span data-stu-id="407f2-116">Review and test any code that uses <xref:System.Environment.OSVersion?displayProperty=nameWithType> to ensure it behaves as desired.</span></span>

#### <a name="category"></a><span data-ttu-id="407f2-117">类别</span><span class="sxs-lookup"><span data-stu-id="407f2-117">Category</span></span>

<span data-ttu-id="407f2-118">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="407f2-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="407f2-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="407f2-119">Affected APIs</span></span>

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Environment.OSVersion`

-->
