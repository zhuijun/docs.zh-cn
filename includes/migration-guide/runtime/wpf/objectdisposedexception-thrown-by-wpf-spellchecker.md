---
ms.openlocfilehash: b836b26f3f52e9d0cc78feb764629bd2fa306657
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621773"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="b7775-101">WPF 拼写检查器引发的 ObjectDisposedException</span><span class="sxs-lookup"><span data-stu-id="b7775-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

#### <a name="details"></a><span data-ttu-id="b7775-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="b7775-102">Details</span></span>

<span data-ttu-id="b7775-103">应用程序关闭，拼写检查器引发 <xref:System.ObjectDisposedException?displayProperty=fullName>，在这期间，WPF 应用程序有时会出现故障。</span><span class="sxs-lookup"><span data-stu-id="b7775-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=fullName> thrown by the spellchecker.</span></span> <span data-ttu-id="b7775-104">.NET Framework 4.7 WPF 中已通过妥善处理异常解决了此问题，因此确保了应用程序不再受到不良影响。</span><span class="sxs-lookup"><span data-stu-id="b7775-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="b7775-105">应注意，在调试器控制下运行的应用程序中会继续观察到偶尔引发的最可能异常。</span><span class="sxs-lookup"><span data-stu-id="b7775-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b7775-106">建议</span><span class="sxs-lookup"><span data-stu-id="b7775-106">Suggestion</span></span>

<span data-ttu-id="b7775-107">升级到 .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="b7775-107">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="b7775-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="b7775-108">Name</span></span>    | <span data-ttu-id="b7775-109">“值”</span><span class="sxs-lookup"><span data-stu-id="b7775-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b7775-110">范围</span><span class="sxs-lookup"><span data-stu-id="b7775-110">Scope</span></span>   |<span data-ttu-id="b7775-111">边缘</span><span class="sxs-lookup"><span data-stu-id="b7775-111">Edge</span></span>|
|<span data-ttu-id="b7775-112">Version</span><span class="sxs-lookup"><span data-stu-id="b7775-112">Version</span></span>|<span data-ttu-id="b7775-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="b7775-113">4.6.1</span></span>|
|<span data-ttu-id="b7775-114">类型</span><span class="sxs-lookup"><span data-stu-id="b7775-114">Type</span></span>|<span data-ttu-id="b7775-115">运行时</span><span class="sxs-lookup"><span data-stu-id="b7775-115">Runtime</span></span>|
