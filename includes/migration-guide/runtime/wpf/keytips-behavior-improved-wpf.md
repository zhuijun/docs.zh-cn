---
ms.openlocfilehash: 1487b5f47966cfcae0e47848dae99b39b42db18d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496934"
---
### <a name="keytips-behavior-improved-in-wpf"></a><span data-ttu-id="f5e0e-101">WPF 中改进的 Keytip 行为</span><span class="sxs-lookup"><span data-stu-id="f5e0e-101">Keytips behavior improved in WPF</span></span>

#### <a name="details"></a><span data-ttu-id="f5e0e-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="f5e0e-102">Details</span></span>

<span data-ttu-id="f5e0e-103">已修改 Keytip 行为，以便对 Microsoft Word 和 Windows 资源管理器行为进行奇偶校验。</span><span class="sxs-lookup"><span data-stu-id="f5e0e-103">Keytips behavior has been modified to bring parity with behavior on Microsoft Word and Windows Explorer.</span></span> <span data-ttu-id="f5e0e-104">通过在按下 <xref:System.Windows.Input.KeyEventArgs.SystemKey>（特别是 <xref:System.Windows.Input.Key> 或 <xref:System.Windows.Input.Key.F11>）的情况下检查是否启用 keytip 状态，WPF 可正确地处理 keytip 键。</span><span class="sxs-lookup"><span data-stu-id="f5e0e-104">By checking whether keytip state is enabled or not in the case of a <xref:System.Windows.Input.KeyEventArgs.SystemKey> (in particular, <xref:System.Windows.Input.Key> or <xref:System.Windows.Input.Key.F11>) being pressed, WPF handles keytip keys appropriately.</span></span> <span data-ttu-id="f5e0e-105">现在，即使是通过鼠标打开的菜单，keytip 也可将其关闭。</span><span class="sxs-lookup"><span data-stu-id="f5e0e-105">Keytips now dismiss a menu even when it is opened by mouse.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f5e0e-106">建议</span><span class="sxs-lookup"><span data-stu-id="f5e0e-106">Suggestion</span></span>

<span data-ttu-id="f5e0e-107">不可用</span><span class="sxs-lookup"><span data-stu-id="f5e0e-107">N/A</span></span>

| <span data-ttu-id="f5e0e-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="f5e0e-108">Name</span></span>    | <span data-ttu-id="f5e0e-109">“值”</span><span class="sxs-lookup"><span data-stu-id="f5e0e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f5e0e-110">范围</span><span class="sxs-lookup"><span data-stu-id="f5e0e-110">Scope</span></span>   |<span data-ttu-id="f5e0e-111">边缘</span><span class="sxs-lookup"><span data-stu-id="f5e0e-111">Edge</span></span>|
|<span data-ttu-id="f5e0e-112">Version</span><span class="sxs-lookup"><span data-stu-id="f5e0e-112">Version</span></span>|<span data-ttu-id="f5e0e-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="f5e0e-113">4.7.2</span></span>|
|<span data-ttu-id="f5e0e-114">类型</span><span class="sxs-lookup"><span data-stu-id="f5e0e-114">Type</span></span>|<span data-ttu-id="f5e0e-115">运行时</span><span class="sxs-lookup"><span data-stu-id="f5e0e-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="f5e0e-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="f5e0e-116">Affected APIs</span></span>

<span data-ttu-id="f5e0e-117">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="f5e0e-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
