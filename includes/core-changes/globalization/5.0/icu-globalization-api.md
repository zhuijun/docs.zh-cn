---
ms.openlocfilehash: 18718ebc934e0175c20411055b8c0a90ef6b175f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539440"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a><span data-ttu-id="5c014-101">全球化 API 在 Windows 上使用 ICU 库</span><span class="sxs-lookup"><span data-stu-id="5c014-101">Globalization APIs use ICU libraries on Windows</span></span>

<span data-ttu-id="5c014-102">当在 Windows 10 2019 年 5 月更新或更高版本上运行时，.NET 5.0 及更高版本使用 [Unicode 国际组件 (ICU)](http://site.icu-project.org/home) 库来实现全球化功能。</span><span class="sxs-lookup"><span data-stu-id="5c014-102">.NET 5.0 and later versions use [International Components for Unicode (ICU)](http://site.icu-project.org/home) libraries for globalization functionality when running on Windows 10 May 2019 Update or later.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5c014-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="5c014-103">Change description</span></span>

<span data-ttu-id="5c014-104">以前，.NET 库使用[区域语言支持 (NLS)](/windows/win32/intl/national-language-support) API 来实现全球化功能。</span><span class="sxs-lookup"><span data-stu-id="5c014-104">Previously, .NET libraries used [National Language Support (NLS)](/windows/win32/intl/national-language-support) APIs for globalization functionality.</span></span> <span data-ttu-id="5c014-105">例如，NLS 函数用于获取区域性数据（例如日期和时间格式模式），比较字符串，并在适当的区域中执行字符串大小写。</span><span class="sxs-lookup"><span data-stu-id="5c014-105">For example, NLS functions were used to get culture data, such as date and time format patterns, compare strings, and perform string casing in the appropriate culture.</span></span>

<span data-ttu-id="5c014-106">从 .NET 5.0 开始，如果应用在 Windows 10 2019 年 5 月更新或更高版本上运行，.NET 库将使用 [ICU](http://site.icu-project.org/home) 全球化 API。</span><span class="sxs-lookup"><span data-stu-id="5c014-106">Starting in .NET 5.0, if an app is running on Windows 10 May 2019 Update or later, .NET libraries use [ICU](http://site.icu-project.org/home) globalization APIs.</span></span> <span data-ttu-id="5c014-107">Windows 10 2019 年 5 月更新及更高版本随 ICU 本机库一起提供。</span><span class="sxs-lookup"><span data-stu-id="5c014-107">Windows 10 May 2019 Update and later versions ship with the ICU native library.</span></span> <span data-ttu-id="5c014-108">如果 .NET 运行时无法加载 ICU，它将改用 NLS。</span><span class="sxs-lookup"><span data-stu-id="5c014-108">If the .NET runtime can't load ICU, it uses NLS instead.</span></span>

<span data-ttu-id="5c014-109">引入此更改的原因有两个：</span><span class="sxs-lookup"><span data-stu-id="5c014-109">This change was introduced for two reasons:</span></span>

- <span data-ttu-id="5c014-110">应用跨平台（包括 Linux、macOS 和 Windows）具有相同的全球化行为。</span><span class="sxs-lookup"><span data-stu-id="5c014-110">Apps have the same globalization behavior across platforms, including Linux, macOS, and Windows.</span></span>
- <span data-ttu-id="5c014-111">应用可以通过使用自定义 ICU 库来控制全球化行为。</span><span class="sxs-lookup"><span data-stu-id="5c014-111">Apps can control globalization behavior by using custom ICU libraries.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5c014-112">引入的版本</span><span class="sxs-lookup"><span data-stu-id="5c014-112">Version introduced</span></span>

<span data-ttu-id="5c014-113">.NET 5.0 预览版 4</span><span class="sxs-lookup"><span data-stu-id="5c014-113">.NET 5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5c014-114">建议操作</span><span class="sxs-lookup"><span data-stu-id="5c014-114">Recommended action</span></span>

<span data-ttu-id="5c014-115">开发人员一方不需要执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="5c014-115">No action is required on the part of the developer.</span></span> <span data-ttu-id="5c014-116">但是，如果你想要继续使用 NLS 全球化 API，则可以将[运行时开关](../../../../docs/core/run-time-config/globalization.md#nls)设置为还原到该行为。</span><span class="sxs-lookup"><span data-stu-id="5c014-116">However, if you wish to continue using NLS globalization APIs, you can set a [run-time switch](../../../../docs/core/run-time-config/globalization.md#nls) to revert to that behavior.</span></span> <span data-ttu-id="5c014-117">有关可用开关的详细信息，请参阅 [.NET 全球化和 ICU](../../../../docs/standard/globalization-localization/globalization-icu.md) 一文。</span><span class="sxs-lookup"><span data-stu-id="5c014-117">For more information about the available switches, see the [.NET globalization and ICU](../../../../docs/standard/globalization-localization/globalization-icu.md) article.</span></span>

#### <a name="category"></a><span data-ttu-id="5c014-118">类别</span><span class="sxs-lookup"><span data-stu-id="5c014-118">Category</span></span>

<span data-ttu-id="5c014-119">全球化</span><span class="sxs-lookup"><span data-stu-id="5c014-119">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5c014-120">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="5c014-120">Affected APIs</span></span>

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <span data-ttu-id="5c014-121"><xref:System.Globalization?displayProperty=fullName> 命名空间中的大多数类型</span><span class="sxs-lookup"><span data-stu-id="5c014-121">Most types in the <xref:System.Globalization?displayProperty=fullName> namespace</span></span>

<!--

#### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`

-->
