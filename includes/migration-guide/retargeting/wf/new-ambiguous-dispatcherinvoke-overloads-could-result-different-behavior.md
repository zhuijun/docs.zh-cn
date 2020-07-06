---
ms.openlocfilehash: 80e61d4dd5b8d4754a39e95e37475fefff57fcbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617119"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a><span data-ttu-id="8830b-101">新的（不明确的）Dispatcher.Invoke 重载可能导致不同的行为</span><span class="sxs-lookup"><span data-stu-id="8830b-101">New (ambiguous) Dispatcher.Invoke overloads could result in different behavior</span></span>

#### <a name="details"></a><span data-ttu-id="8830b-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="8830b-102">Details</span></span>

<span data-ttu-id="8830b-103">.NET Framework 4.5 将新重载添加到包括 <xref:System.Action> 类型参数的 <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8830b-103">The .NET Framework 4.5 adds new overloads to <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> that include a parameter of type <xref:System.Action>.</span></span> <span data-ttu-id="8830b-104">在重新编译现有代码时，编译器可能将对具有 <xref:System.Delegate> 参数的 Dispatcher.Invoke 方法的调用解析为对具有 <xref:System.Action> 参数的 Dispatcher.Invoke 方法的调用。</span><span class="sxs-lookup"><span data-stu-id="8830b-104">When existing code is recompiled, compilers may resolve calls to Dispatcher.Invoke methods that have a <xref:System.Delegate> parameter as calls to Dispatcher.Invoke methods with an <xref:System.Action> parameter.</span></span> <span data-ttu-id="8830b-105">如果将对具有 <xref:System.Delegate> 参数的 Dispatcher.Invoke 重载的调用解析为对具有 <xref:System.Action> 参数的 Dispatcher.Invoke 重载的调用，可能出现以下行为差异：</span><span class="sxs-lookup"><span data-stu-id="8830b-105">If a call to a Dispatcher.Invoke overload with a  <xref:System.Delegate> parameter is resolved as a call to a Dispatcher.Invoke overload with an <xref:System.Action> parameter, the following differences in behavior may occur:</span></span>

- <span data-ttu-id="8830b-106">如果出现异常，则不引发 <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> 和 <xref:System.Windows.Threading.Dispatcher.UnhandledException> 事件。</span><span class="sxs-lookup"><span data-stu-id="8830b-106">If an exception occurs, the <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> and <xref:System.Windows.Threading.Dispatcher.UnhandledException> events are not raised.</span></span> <span data-ttu-id="8830b-107">相反，通过 <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> 事件处理异常。</span><span class="sxs-lookup"><span data-stu-id="8830b-107">Instead, exceptions are handled by the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> event.</span></span>
- <span data-ttu-id="8830b-108">对某些成员（如 <xref:System.Windows.Threading.DispatcherOperation.Result>）的调用会受阻，直到操作完成。</span><span class="sxs-lookup"><span data-stu-id="8830b-108">Calls to some members, such as <xref:System.Windows.Threading.DispatcherOperation.Result>, block until the operation has completed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8830b-109">建议</span><span class="sxs-lookup"><span data-stu-id="8830b-109">Suggestion</span></span>

<span data-ttu-id="8830b-110">若要避免出现多义性（以及异常处理或阻止行为中可能出现的差异），调用 Dispatcher.Invoke 的代码可传递空 object[] 作为 Invoke 调用的第二个参数，确保解析为 .NET Framework 4.0 方法重载。</span><span class="sxs-lookup"><span data-stu-id="8830b-110">To avoid ambiguity (and potential differences in exception handling or blocking behaviors), code calling Dispatcher.Invoke can pass an empty object[] as a second parameter to the Invoke call to be sure of resolving to the .NET Framework 4.0 method overload.</span></span>

| <span data-ttu-id="8830b-111">“属性”</span><span class="sxs-lookup"><span data-stu-id="8830b-111">Name</span></span>    | <span data-ttu-id="8830b-112">“值”</span><span class="sxs-lookup"><span data-stu-id="8830b-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8830b-113">范围</span><span class="sxs-lookup"><span data-stu-id="8830b-113">Scope</span></span>   | <span data-ttu-id="8830b-114">次要</span><span class="sxs-lookup"><span data-stu-id="8830b-114">Minor</span></span>       |
| <span data-ttu-id="8830b-115">Version</span><span class="sxs-lookup"><span data-stu-id="8830b-115">Version</span></span> | <span data-ttu-id="8830b-116">4.5</span><span class="sxs-lookup"><span data-stu-id="8830b-116">4.5</span></span>         |
| <span data-ttu-id="8830b-117">类型</span><span class="sxs-lookup"><span data-stu-id="8830b-117">Type</span></span>    | <span data-ttu-id="8830b-118">重定目标</span><span class="sxs-lookup"><span data-stu-id="8830b-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="8830b-119">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="8830b-119">Affected APIs</span></span>

- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
