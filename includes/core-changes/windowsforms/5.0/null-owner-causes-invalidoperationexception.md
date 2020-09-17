---
ms.openlocfilehash: b6cb7c4b479551ff4563998f310ff518d935f48a
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656326"
---
### <a name="datagridview-related-apis-now-throw-invalidoperationexception"></a><span data-ttu-id="29c35-101">与 DataGridView 相关的 API 现在引发 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="29c35-101">DataGridView-related APIs now throw InvalidOperationException</span></span>

<span data-ttu-id="29c35-102">如果对象的 <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> 值为 `null`，则与 <xref:System.Windows.Forms.DataGridView> 相关的某些 API 现在会引发 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="29c35-102">Some APIs related to <xref:System.Windows.Forms.DataGridView> now throw an <xref:System.InvalidOperationException> if the object's <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> value is `null`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="29c35-103">更改说明</span><span class="sxs-lookup"><span data-stu-id="29c35-103">Change description</span></span>

<span data-ttu-id="29c35-104">在以前的 .NET 版本中，受影响的 API 在被调用时会引发 <xref:System.NullReferenceException>，并且 <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> 的值为 `null`。</span><span class="sxs-lookup"><span data-stu-id="29c35-104">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> when they are invoked and the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> value is `null`.</span></span> <span data-ttu-id="29c35-105">从 .NET 5.0 开始，如果在调用 API 时，<xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> 值为 `null`，这些 API 将引发 <xref:System.InvalidOperationException>，而不会引发 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="29c35-105">Starting in .NET 5.0, these APIs throw an <xref:System.InvalidOperationException> instead of a <xref:System.NullReferenceException> if the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> value is `null` when they are invoked.</span></span>

<span data-ttu-id="29c35-106">引发 <xref:System.InvalidOperationException> 符合 .NET 运行时的行为。</span><span class="sxs-lookup"><span data-stu-id="29c35-106">Throwing an <xref:System.InvalidOperationException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="29c35-107">它还通过清楚地传达无效属性来改进调试体验。</span><span class="sxs-lookup"><span data-stu-id="29c35-107">It also improves the debugging experience by clearly communicating the invalid property.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="29c35-108">引入的版本</span><span class="sxs-lookup"><span data-stu-id="29c35-108">Version introduced</span></span>

<span data-ttu-id="29c35-109">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="29c35-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="29c35-110">建议操作</span><span class="sxs-lookup"><span data-stu-id="29c35-110">Recommended action</span></span>

<span data-ttu-id="29c35-111">查看你的代码，并在必要时对其进行更新，以防止使用属性为 `null` 的 <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> 构造受影响的类型。</span><span class="sxs-lookup"><span data-stu-id="29c35-111">Review your code and, if necessary, update it to prevent constructing the affected types with the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property as `null`.</span></span>

#### <a name="category"></a><span data-ttu-id="29c35-112">类别</span><span class="sxs-lookup"><span data-stu-id="29c35-112">Category</span></span>

<span data-ttu-id="29c35-113">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="29c35-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="29c35-114">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="29c35-114">Affected APIs</span></span>

<span data-ttu-id="29c35-115">下表列出了受影响的方法和参数：</span><span class="sxs-lookup"><span data-stu-id="29c35-115">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="29c35-116">受影响的方法或属性</span><span class="sxs-lookup"><span data-stu-id="29c35-116">Affected method or property</span></span> | <span data-ttu-id="29c35-117">已验证的属性</span><span class="sxs-lookup"><span data-stu-id="29c35-117">Validated property</span></span> | <span data-ttu-id="29c35-118">新增的版本</span><span class="sxs-lookup"><span data-stu-id="29c35-118">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="29c35-119">5.0</span><span class="sxs-lookup"><span data-stu-id="29c35-119">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="29c35-120">5.0</span><span class="sxs-lookup"><span data-stu-id="29c35-120">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="29c35-121">5.0</span><span class="sxs-lookup"><span data-stu-id="29c35-121">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="29c35-122">5.0</span><span class="sxs-lookup"><span data-stu-id="29c35-122">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="29c35-123">5.0</span><span class="sxs-lookup"><span data-stu-id="29c35-123">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="29c35-124">5.0</span><span class="sxs-lookup"><span data-stu-id="29c35-124">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="29c35-125">5.0</span><span class="sxs-lookup"><span data-stu-id="29c35-125">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="29c35-126">5.0</span><span class="sxs-lookup"><span data-stu-id="29c35-126">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="29c35-127">5.0</span><span class="sxs-lookup"><span data-stu-id="29c35-127">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="29c35-128">5.0</span><span class="sxs-lookup"><span data-stu-id="29c35-128">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="29c35-129">5.0</span><span class="sxs-lookup"><span data-stu-id="29c35-129">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="29c35-130">5.0</span><span class="sxs-lookup"><span data-stu-id="29c35-130">5.0</span></span> |

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction`
- `P:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State`
- `M:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent`
- `M:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction`
- `M:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)`
- `M:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction`
- `M:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction`

-->
