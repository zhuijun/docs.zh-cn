---
ms.openlocfilehash: 0e25d5d9b545e5cb400cbf701fb13da572fadf10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614335"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a><span data-ttu-id="577f4-101">ETW 事件名称无法仅通过“Start”或“Stop”后缀区别开来</span><span class="sxs-lookup"><span data-stu-id="577f4-101">ETW event names cannot differ only by a "Start" or "Stop" suffix</span></span>

#### <a name="details"></a><span data-ttu-id="577f4-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="577f4-102">Details</span></span>

<span data-ttu-id="577f4-103">在 .NET Framework 4.6 和 4.6.1 中，当两个 Windows 事件跟踪 (ETW) 事件名称只有“Start”或“Stop”后缀不同时（例如，当一个事件命名为 `LogUser`，另一个事件命名为 `LogUserStart`），运行时会引发 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="577f4-103">In the .NET Framework 4.6 and 4.6.1, the runtime throws an <xref:System.ArgumentException> when two Event Tracing for Windows (ETW) event names differ only by a "Start" or "Stop" suffix (as when one event is named `LogUser` and another is named `LogUserStart`).</span></span> <span data-ttu-id="577f4-104">在这种情况下，运行时不会构建不能发出任何日志记录的事件源。</span><span class="sxs-lookup"><span data-stu-id="577f4-104">In this case, the runtime cannot construct the event source, which cannot emit any logging.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="577f4-105">建议</span><span class="sxs-lookup"><span data-stu-id="577f4-105">Suggestion</span></span>

<span data-ttu-id="577f4-106">若要避免此异常，请确保两个事件名称不是只有“Start”或“Stop”后缀不同。从 .NET Framework 4.6.2 开始，将删除此要求，运行时可区分只有“Start”和“Stop”后缀不同的事件名称。</span><span class="sxs-lookup"><span data-stu-id="577f4-106">To prevent the exception, ensure that no two event names differ only by a "Start" or "Stop" suffix.This requirement is removed starting with the .NET Framework 4.6.2; the runtime can disambiguate event names that differ only by the "Start" and "Stop" suffix.</span></span>

| <span data-ttu-id="577f4-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="577f4-107">Name</span></span>    | <span data-ttu-id="577f4-108">“值”</span><span class="sxs-lookup"><span data-stu-id="577f4-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="577f4-109">范围</span><span class="sxs-lookup"><span data-stu-id="577f4-109">Scope</span></span>   | <span data-ttu-id="577f4-110">边缘</span><span class="sxs-lookup"><span data-stu-id="577f4-110">Edge</span></span>        |
| <span data-ttu-id="577f4-111">Version</span><span class="sxs-lookup"><span data-stu-id="577f4-111">Version</span></span> | <span data-ttu-id="577f4-112">4.6</span><span class="sxs-lookup"><span data-stu-id="577f4-112">4.6</span></span>         |
| <span data-ttu-id="577f4-113">类型</span><span class="sxs-lookup"><span data-stu-id="577f4-113">Type</span></span>    | <span data-ttu-id="577f4-114">重定目标</span><span class="sxs-lookup"><span data-stu-id="577f4-114">Retargeting</span></span> |
