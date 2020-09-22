---
ms.openlocfilehash: 59e7b55516d79aa5c574a8869698e1a18576ef41
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770877"
---
### <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="2b53f-101">WinForms 方法现在会引发 ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="2b53f-101">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="2b53f-102">某些 Windows 窗体方法现在将针对 null 参数引发 <xref:System.ArgumentNullException>，而之前它们会引发 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="2b53f-102">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="2b53f-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="2b53f-103">Change description</span></span>

<span data-ttu-id="2b53f-104">以前，如果传递 null 参数，某些 Windows 窗体方法将引发 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="2b53f-104">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="2b53f-105">从 .NET 5.0 开始，这些方法现在将针对 null 参数引发 <xref:System.ArgumentNullException>。</span><span class="sxs-lookup"><span data-stu-id="2b53f-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments, instead.</span></span>

<span data-ttu-id="2b53f-106">引发 <xref:System.ArgumentNullException> 符合 .NET 运行时的行为。</span><span class="sxs-lookup"><span data-stu-id="2b53f-106">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="2b53f-107">它还通过清楚地指示参数为 null 和具体参数来改进调试体验。</span><span class="sxs-lookup"><span data-stu-id="2b53f-107">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2b53f-108">引入的版本</span><span class="sxs-lookup"><span data-stu-id="2b53f-108">Version introduced</span></span>

<span data-ttu-id="2b53f-109">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="2b53f-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2b53f-110">建议操作</span><span class="sxs-lookup"><span data-stu-id="2b53f-110">Recommended action</span></span>

<span data-ttu-id="2b53f-111">如果调用这些方法中的任何一种，你的代码当前都会针对 null 参数捕获 <xref:System.NullReferenceException>，请改为捕获 <xref:System.ArgumentNullException>。</span><span class="sxs-lookup"><span data-stu-id="2b53f-111">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="2b53f-112">此外，请考虑更新代码，以避免将 null 参数传递到列出的方法。</span><span class="sxs-lookup"><span data-stu-id="2b53f-112">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

#### <a name="category"></a><span data-ttu-id="2b53f-113">类别</span><span class="sxs-lookup"><span data-stu-id="2b53f-113">Category</span></span>

<span data-ttu-id="2b53f-114">Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="2b53f-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2b53f-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="2b53f-115">Affected APIs</span></span>

<span data-ttu-id="2b53f-116">下表列出了受影响的方法和参数：</span><span class="sxs-lookup"><span data-stu-id="2b53f-116">The following table lists the affected methods and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="2b53f-117">方法</span><span class="sxs-lookup"><span data-stu-id="2b53f-117">Method</span></span> | <span data-ttu-id="2b53f-118">参数名称</span><span class="sxs-lookup"><span data-stu-id="2b53f-118">Parameter name</span></span> | <span data-ttu-id="2b53f-119">新增的版本</span><span class="sxs-lookup"><span data-stu-id="2b53f-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)> | `owner` | <span data-ttu-id="2b53f-120">预览版 1</span><span class="sxs-lookup"><span data-stu-id="2b53f-120">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType> | `item` | <span data-ttu-id="2b53f-121">预览版 1</span><span class="sxs-lookup"><span data-stu-id="2b53f-121">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)> | `container` | <span data-ttu-id="2b53f-122">预览版 1</span><span class="sxs-lookup"><span data-stu-id="2b53f-122">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="2b53f-123">预览版 1</span><span class="sxs-lookup"><span data-stu-id="2b53f-123">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="2b53f-124">预览版 1</span><span class="sxs-lookup"><span data-stu-id="2b53f-124">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="2b53f-125">预览版 1</span><span class="sxs-lookup"><span data-stu-id="2b53f-125">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="2b53f-126">预览版 1</span><span class="sxs-lookup"><span data-stu-id="2b53f-126">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType> > | `e` | <span data-ttu-id="2b53f-127">预览版 1</span><span class="sxs-lookup"><span data-stu-id="2b53f-127">Preview 1</span></span> |
> | <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType> | `dataGridViewCellStyle` | <span data-ttu-id="2b53f-128">预览版 2</span><span class="sxs-lookup"><span data-stu-id="2b53f-128">Preview 2</span></span> |
> | <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> | `data` | <span data-ttu-id="2b53f-129">预览版 2</span><span class="sxs-lookup"><span data-stu-id="2b53f-129">Preview 2</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="2b53f-130">预览版 5</span><span class="sxs-lookup"><span data-stu-id="2b53f-130">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="2b53f-131">预览版 5</span><span class="sxs-lookup"><span data-stu-id="2b53f-131">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | <span data-ttu-id="2b53f-132">预览版 5</span><span class="sxs-lookup"><span data-stu-id="2b53f-132">Preview 5</span></span> |
> | <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)> | `className` | <span data-ttu-id="2b53f-133">预览版 5</span><span class="sxs-lookup"><span data-stu-id="2b53f-133">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="2b53f-134">预览版 6</span><span class="sxs-lookup"><span data-stu-id="2b53f-134">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Object[])> | <span data-ttu-id="2b53f-135">`owner`，`value`</span><span class="sxs-lookup"><span data-stu-id="2b53f-135">`owner`, `value`</span></span> | <span data-ttu-id="2b53f-136">预览版 6</span><span class="sxs-lookup"><span data-stu-id="2b53f-136">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)> | <span data-ttu-id="2b53f-137">`owner`，`value`</span><span class="sxs-lookup"><span data-stu-id="2b53f-137">`owner`, `value`</span></span> | <span data-ttu-id="2b53f-138">预览版 6</span><span class="sxs-lookup"><span data-stu-id="2b53f-138">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])?displayProperty=nameWithType> | `items` | <span data-ttu-id="2b53f-139">预览版 6</span><span class="sxs-lookup"><span data-stu-id="2b53f-139">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)?displayProperty=nameWithType> | `value` | <span data-ttu-id="2b53f-140">预览版 6</span><span class="sxs-lookup"><span data-stu-id="2b53f-140">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="2b53f-141">预览版 6</span><span class="sxs-lookup"><span data-stu-id="2b53f-141">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.System%23Collections%23ICollection%23CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="2b53f-142">预览版 6</span><span class="sxs-lookup"><span data-stu-id="2b53f-142">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListView.SelectedIndexCollection.%23ctor(System.Windows.Forms.ListView)> | `owner` | <span data-ttu-id="2b53f-143">预览版 7</span><span class="sxs-lookup"><span data-stu-id="2b53f-143">Preview 7</span></span> |
> | <xref:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="2b53f-144">`key` 为 `null` 或空</span><span class="sxs-lookup"><span data-stu-id="2b53f-144">`key` is `null` or empty</span></span> | <span data-ttu-id="2b53f-145">预览版 8</span><span class="sxs-lookup"><span data-stu-id="2b53f-145">Preview 8</span></span> |
> | <xref:System.Windows.Forms.ListView.ListViewItemCollection.Find(System.String,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="2b53f-146">`key` 为 `null` 或空</span><span class="sxs-lookup"><span data-stu-id="2b53f-146">`key` is `null` or empty</span></span> | <span data-ttu-id="2b53f-147">RC1</span><span class="sxs-lookup"><span data-stu-id="2b53f-147">RC1</span></span> |
> | <xref:System.Windows.Forms.ScrollableControl.OnPaintBackground(System.Windows.Forms.PaintEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="2b53f-148">RC1</span><span class="sxs-lookup"><span data-stu-id="2b53f-148">RC1</span></span> |

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.Control.ControlCollection.#ctor(System.Windows.Forms.Control)`
- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.TableLayoutControlCollection.#ctor(System.Windows.Forms.TableLayoutPanel)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)`
- `M:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)`
- `M:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)`
- `M:System.Windows.Forms.ListViewGroup.System#Runtime#Serialization#ISerializable#GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`
- `M:System.Windows.Forms.VisualStyles.VisualStyleRenderer.#ctor(System.String,System.Int32,System.Int32)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.#ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox,System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.System#Collections#ICollection#CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListView.SelectedIndexCollection.#ctor(System.Windows.Forms.ListView)`
- `M:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)`
- `M:System.Windows.Forms.ListView.ListViewItemCollection.Find(System.String,System.Boolean)`
- `M:System.Windows.Forms.ScrollableControl.OnPaintBackground(System.Windows.Forms.PaintEventArgs)`

-->
