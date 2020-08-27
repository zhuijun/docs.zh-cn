---
ms.openlocfilehash: 0246f325a6274082b7fb0d5590cec7c80687ae85
ms.sourcegitcommit: ef86c24c418439b8bb5e3e7d64bbdbe5e11c3e9c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/21/2020
ms.locfileid: "88720174"
---
### <a name="uri-recognition-of-unc-paths-on-unix"></a><span data-ttu-id="3ea7f-101">Unix 上 UNC 路径的 URI 识别</span><span class="sxs-lookup"><span data-stu-id="3ea7f-101">Uri recognition of UNC paths on Unix</span></span>

<span data-ttu-id="3ea7f-102">现在，<xref:System.Uri> 类将以两个正斜杠 (`//`) 开头的字符串识别为 Unix 操作系统上的通用命名约定 (UNC) 路径。</span><span class="sxs-lookup"><span data-stu-id="3ea7f-102">The <xref:System.Uri> class now recognizes strings that start with two forward slashes (`//`) as universal naming convention (UNC) paths on Unix operating systems.</span></span> <span data-ttu-id="3ea7f-103">此更改使此类字符串的行为在所有平台中保持一致。</span><span class="sxs-lookup"><span data-stu-id="3ea7f-103">This change makes the behavior for such strings consistent across all platforms.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3ea7f-104">更改描述</span><span class="sxs-lookup"><span data-stu-id="3ea7f-104">Change description</span></span>

<span data-ttu-id="3ea7f-105">在早期版本的 .NET 中，<xref:System.Uri> 类将以两个正斜杠开头的字符串（例如 `//contoso`）识别为 Unix 操作系统上的绝对文件路径。</span><span class="sxs-lookup"><span data-stu-id="3ea7f-105">In previous versions of .NET, the <xref:System.Uri> class recognizes strings that start with with two forward slashes, for example, `//contoso`, as absolute file paths on Unix operating systems.</span></span> <span data-ttu-id="3ea7f-106">但是，在 Windows 上，此类字符串被识别为 UNC 路径。</span><span class="sxs-lookup"><span data-stu-id="3ea7f-106">However, on Windows, such strings are recognized as UNC paths.</span></span>

<span data-ttu-id="3ea7f-107">从 .NET 5.0 开始，<xref:System.Uri> 类将以两个正斜杠开头的字符串识别为所有平台（包括 Unix）上的 UNC 路径。</span><span class="sxs-lookup"><span data-stu-id="3ea7f-107">Starting in .NET 5.0,  the <xref:System.Uri> class recognizes strings that start with with two forward slashes as UNC paths on all platforms, including Unix.</span></span> <span data-ttu-id="3ea7f-108">此外，属性的行为遵循 UNC 语义：</span><span class="sxs-lookup"><span data-stu-id="3ea7f-108">In addition, properties behave according to UNC semantics:</span></span>

- <span data-ttu-id="3ea7f-109"><xref:System.Uri.IsUnc?displayProperty=nameWithType> 返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="3ea7f-109"><xref:System.Uri.IsUnc?displayProperty=nameWithType> returns `true`.</span></span>
- <span data-ttu-id="3ea7f-110">路径中的反斜杠替换为正斜杠。</span><span class="sxs-lookup"><span data-stu-id="3ea7f-110">Backslashes in the path are replaced with forward slashes.</span></span> <span data-ttu-id="3ea7f-111">例如，`//first\second` 重命名为 `//first/second`。</span><span class="sxs-lookup"><span data-stu-id="3ea7f-111">For example, `//first\second` becomes `//first/second`.</span></span>
- <span data-ttu-id="3ea7f-112"><xref:System.Uri.LocalPath?displayProperty=nameWithType> 不对字符进行百分号编码。</span><span class="sxs-lookup"><span data-stu-id="3ea7f-112"><xref:System.Uri.LocalPath?displayProperty=nameWithType> doesn't percent-encode characters.</span></span> <span data-ttu-id="3ea7f-113">例如，`//first/\uFFF0` 不转换为 `//first/%EF%BF%B0`。</span><span class="sxs-lookup"><span data-stu-id="3ea7f-113">For example, `//first/\uFFF0` is *not* converted to `//first/%EF%BF%B0`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3ea7f-114">引入的版本</span><span class="sxs-lookup"><span data-stu-id="3ea7f-114">Version introduced</span></span>

<span data-ttu-id="3ea7f-115">5.0</span><span class="sxs-lookup"><span data-stu-id="3ea7f-115">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3ea7f-116">建议操作</span><span class="sxs-lookup"><span data-stu-id="3ea7f-116">Recommended action</span></span>

<span data-ttu-id="3ea7f-117">开发人员一方不需要执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="3ea7f-117">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="3ea7f-118">类别</span><span class="sxs-lookup"><span data-stu-id="3ea7f-118">Category</span></span>

<span data-ttu-id="3ea7f-119">Core .NET 库</span><span class="sxs-lookup"><span data-stu-id="3ea7f-119">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3ea7f-120">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="3ea7f-120">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Uri`

-->
