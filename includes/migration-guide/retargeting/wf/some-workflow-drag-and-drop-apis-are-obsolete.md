---
ms.openlocfilehash: b6cb7edcd6bed50efdf59f3321320ac8cd1b1ab8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617127"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a><span data-ttu-id="0a7ca-101">某些工作流拖放 API 已过时</span><span class="sxs-lookup"><span data-stu-id="0a7ca-101">Some WorkFlow drag-and-drop APIs are obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="0a7ca-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="0a7ca-102">Details</span></span>

<span data-ttu-id="0a7ca-103">此工作流拖放 API 已过时，如果针对 4.5 重新生成应用，将引发编译器警告。</span><span class="sxs-lookup"><span data-stu-id="0a7ca-103">This WorkFlow drag-and-drop API is obsolete and will cause compiler warnings if the app is rebuilt against 4.5.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0a7ca-104">建议</span><span class="sxs-lookup"><span data-stu-id="0a7ca-104">Suggestion</span></span>

<span data-ttu-id="0a7ca-105">应改用支持包含多个对象的操作的新 <xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName> API。</span><span class="sxs-lookup"><span data-stu-id="0a7ca-105">New <xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName> APIs that support operations with multiple objects should be used instead.</span></span> <span data-ttu-id="0a7ca-106">或者，可以禁止显示生成警告，也可以使用较早的编译器避免出现此类警告。</span><span class="sxs-lookup"><span data-stu-id="0a7ca-106">Alternatively, the build warnings can be suppressed or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="0a7ca-107">API 仍受支持。</span><span class="sxs-lookup"><span data-stu-id="0a7ca-107">The APIs are still supported.</span></span>

| <span data-ttu-id="0a7ca-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="0a7ca-108">Name</span></span>    | <span data-ttu-id="0a7ca-109">“值”</span><span class="sxs-lookup"><span data-stu-id="0a7ca-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0a7ca-110">范围</span><span class="sxs-lookup"><span data-stu-id="0a7ca-110">Scope</span></span>   | <span data-ttu-id="0a7ca-111">次要</span><span class="sxs-lookup"><span data-stu-id="0a7ca-111">Minor</span></span>       |
| <span data-ttu-id="0a7ca-112">Version</span><span class="sxs-lookup"><span data-stu-id="0a7ca-112">Version</span></span> | <span data-ttu-id="0a7ca-113">4.5</span><span class="sxs-lookup"><span data-stu-id="0a7ca-113">4.5</span></span>         |
| <span data-ttu-id="0a7ca-114">类型</span><span class="sxs-lookup"><span data-stu-id="0a7ca-114">Type</span></span>    | <span data-ttu-id="0a7ca-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="0a7ca-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="0a7ca-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="0a7ca-116">Affected APIs</span></span>

- <xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType>
