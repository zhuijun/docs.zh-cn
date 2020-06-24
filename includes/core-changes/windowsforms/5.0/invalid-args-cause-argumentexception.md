---
ms.openlocfilehash: aab7d8538c875e35c832acc2a6c64beb84d4fb47
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702426"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="5c4a8-101">WinForms 方法现在会引发 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="5c4a8-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="5c4a8-102">某些 Windows 窗体方法现在将针对无效参数引发 <xref:System.ArgumentException>，之前不会这样。</span><span class="sxs-lookup"><span data-stu-id="5c4a8-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5c4a8-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="5c4a8-103">Change description</span></span>

<span data-ttu-id="5c4a8-104">以前，如果将异常类型或错误类型的参数传递给某些 Windows 窗体方法，会导致不确定的状态。</span><span class="sxs-lookup"><span data-stu-id="5c4a8-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="5c4a8-105">从 .NET 5.0 开始，在传递无效参数后，这些方法现在会引发 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="5c4a8-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="5c4a8-106">引发 <xref:System.ArgumentException> 符合 .NET 运行时的行为。</span><span class="sxs-lookup"><span data-stu-id="5c4a8-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="5c4a8-107">它还通过清楚地指示具体的无效参数来改进调试体验。</span><span class="sxs-lookup"><span data-stu-id="5c4a8-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

<span data-ttu-id="5c4a8-108">下表列出了受影响的方法和参数：</span><span class="sxs-lookup"><span data-stu-id="5c4a8-108">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="5c4a8-109">方法</span><span class="sxs-lookup"><span data-stu-id="5c4a8-109">Method</span></span> | <span data-ttu-id="5c4a8-110">参数名称</span><span class="sxs-lookup"><span data-stu-id="5c4a8-110">Parameter name</span></span> | <span data-ttu-id="5c4a8-111">条件</span><span class="sxs-lookup"><span data-stu-id="5c4a8-111">Condition</span></span> | <span data-ttu-id="5c4a8-112">新增的版本</span><span class="sxs-lookup"><span data-stu-id="5c4a8-112">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="5c4a8-113">参数不属于 <xref:System.Windows.Forms.TabPage> 类型。</span><span class="sxs-lookup"><span data-stu-id="5c4a8-113">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="5c4a8-114">5.0 预览版 1</span><span class="sxs-lookup"><span data-stu-id="5c4a8-114">5.0 Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="5c4a8-115">参数为 `null`、<xref:System.String.Empty?displayProperty=nameWithType> 或空格。</span><span class="sxs-lookup"><span data-stu-id="5c4a8-115">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="5c4a8-116">5.0 预览版 5</span><span class="sxs-lookup"><span data-stu-id="5c4a8-116">5.0 Preview 5</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="5c4a8-117">引入的版本</span><span class="sxs-lookup"><span data-stu-id="5c4a8-117">Version introduced</span></span>

<span data-ttu-id="5c4a8-118">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="5c4a8-118">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5c4a8-119">建议操作</span><span class="sxs-lookup"><span data-stu-id="5c4a8-119">Recommended action</span></span>

- <span data-ttu-id="5c4a8-120">更新代码以防止传递无效参数。</span><span class="sxs-lookup"><span data-stu-id="5c4a8-120">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="5c4a8-121">如有必要，请在调用方法时处理 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="5c4a8-121">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="5c4a8-122">类别</span><span class="sxs-lookup"><span data-stu-id="5c4a8-122">Category</span></span>

<span data-ttu-id="5c4a8-123">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="5c4a8-123">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5c4a8-124">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="5c4a8-124">Affected APIs</span></span>

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>
- <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`

-->
