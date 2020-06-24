---
ms.openlocfilehash: f42da00487735acdcc60f876c75e1dfd17103008
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702427"
---
### <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a><span data-ttu-id="f5715-101">WinForms 属性现在引发 ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="f5715-101">WinForms properties now throw ArgumentOutOfRangeException</span></span>

<span data-ttu-id="f5715-102">某些 Windows 窗体属性现在将针对无效参数引发 <xref:System.ArgumentOutOfRangeException>，之前不会这样。</span><span class="sxs-lookup"><span data-stu-id="f5715-102">Some Windows Forms properties now throw an <xref:System.ArgumentOutOfRangeException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f5715-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="f5715-103">Change description</span></span>

<span data-ttu-id="f5715-104">以前，当传递超出范围的参数时，这些属性将引发各种异常，如 <xref:System.NullReferenceException>、<xref:System.IndexOutOfRangeException> 或 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="f5715-104">Previously, these properties threw various exceptions, such as <xref:System.NullReferenceException>, <xref:System.IndexOutOfRangeException>, or <xref:System.ArgumentException>, when passed out-of-range arguments.</span></span> <span data-ttu-id="f5715-105">从 .NET 5.0 开始，如果传递的参数超出范围，则这些属性现在将引发 <xref:System.ArgumentOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="f5715-105">Starting in .NET 5.0, these properties now throw an <xref:System.ArgumentOutOfRangeException> when passed arguments that are out of range.</span></span>

<span data-ttu-id="f5715-106">引发 <xref:System.ArgumentOutOfRangeException> 符合 .NET 运行时的行为。</span><span class="sxs-lookup"><span data-stu-id="f5715-106">Throwing an <xref:System.ArgumentOutOfRangeException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="f5715-107">它还通过清楚地指示具体的无效参数来改进调试体验。</span><span class="sxs-lookup"><span data-stu-id="f5715-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f5715-108">引入的版本</span><span class="sxs-lookup"><span data-stu-id="f5715-108">Version introduced</span></span>

<span data-ttu-id="f5715-109">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="f5715-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f5715-110">建议操作</span><span class="sxs-lookup"><span data-stu-id="f5715-110">Recommended action</span></span>

- <span data-ttu-id="f5715-111">更新代码以防止传递无效参数。</span><span class="sxs-lookup"><span data-stu-id="f5715-111">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="f5715-112">如有必要，请在设置属性时处理 <xref:System.ArgumentOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="f5715-112">If necessary, handle an <xref:System.ArgumentOutOfRangeException> when setting the property.</span></span>

#### <a name="category"></a><span data-ttu-id="f5715-113">类别</span><span class="sxs-lookup"><span data-stu-id="f5715-113">Category</span></span>

<span data-ttu-id="f5715-114">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="f5715-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f5715-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="f5715-115">Affected APIs</span></span>

<span data-ttu-id="f5715-116">下表列出了受影响的方法和参数：</span><span class="sxs-lookup"><span data-stu-id="f5715-116">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="f5715-117">Property</span><span class="sxs-lookup"><span data-stu-id="f5715-117">Property</span></span> | <span data-ttu-id="f5715-118">参数名称</span><span class="sxs-lookup"><span data-stu-id="f5715-118">Parameter name</span></span> | <span data-ttu-id="f5715-119">新增的版本</span><span class="sxs-lookup"><span data-stu-id="f5715-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | <span data-ttu-id="f5715-120">5.0 预览版 5</span><span class="sxs-lookup"><span data-stu-id="f5715-120">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="f5715-121">5.0 预览版 6</span><span class="sxs-lookup"><span data-stu-id="f5715-121">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="f5715-122">5.0 预览版 6</span><span class="sxs-lookup"><span data-stu-id="f5715-122">5.0 Preview 6</span></span> |

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

-->
