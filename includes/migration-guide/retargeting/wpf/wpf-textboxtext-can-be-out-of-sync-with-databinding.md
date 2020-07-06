---
ms.openlocfilehash: d0de1a262d57c67dd4dfb258d5ac013af5d8783d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617128"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a><span data-ttu-id="0d579-101">WPF TextBox.Text 可能与数据绑定不同步</span><span class="sxs-lookup"><span data-stu-id="0d579-101">WPF TextBox.Text can be out-of-sync with databinding</span></span>

#### <a name="details"></a><span data-ttu-id="0d579-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="0d579-102">Details</span></span>

<span data-ttu-id="0d579-103">在某些情况下，如果在数据绑定的写入操作期间修改属性，则 <xref:System.Windows.Controls.TextBox.Text> 属性会反映数据绑定属性值的以前的值。</span><span class="sxs-lookup"><span data-stu-id="0d579-103">In some cases, the <xref:System.Windows.Controls.TextBox.Text> property reflects a previous value of the databound property value if the property is modified during a databinding write operation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0d579-104">建议</span><span class="sxs-lookup"><span data-stu-id="0d579-104">Suggestion</span></span>

<span data-ttu-id="0d579-105">这不应有负面影响。</span><span class="sxs-lookup"><span data-stu-id="0d579-105">This should have no negative impact.</span></span> <span data-ttu-id="0d579-106">不过，你可以通过将 <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> 属性设置为 `false` 来还原以前的行为。</span><span class="sxs-lookup"><span data-stu-id="0d579-106">However, you can restore the previous behavior by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> property to `false`.</span></span>

| <span data-ttu-id="0d579-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="0d579-107">Name</span></span>    | <span data-ttu-id="0d579-108">“值”</span><span class="sxs-lookup"><span data-stu-id="0d579-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0d579-109">范围</span><span class="sxs-lookup"><span data-stu-id="0d579-109">Scope</span></span>   | <span data-ttu-id="0d579-110">边缘</span><span class="sxs-lookup"><span data-stu-id="0d579-110">Edge</span></span>        |
| <span data-ttu-id="0d579-111">Version</span><span class="sxs-lookup"><span data-stu-id="0d579-111">Version</span></span> | <span data-ttu-id="0d579-112">4.5</span><span class="sxs-lookup"><span data-stu-id="0d579-112">4.5</span></span>         |
|<span data-ttu-id="0d579-113">类型</span><span class="sxs-lookup"><span data-stu-id="0d579-113">Type</span></span>|<span data-ttu-id="0d579-114">重定目标</span><span class="sxs-lookup"><span data-stu-id="0d579-114">Retargeting</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0d579-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="0d579-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType>
