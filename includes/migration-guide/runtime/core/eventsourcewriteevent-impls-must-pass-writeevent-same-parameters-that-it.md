---
ms.openlocfilehash: 662c140f019add66ff6605d47ad1f32c3f50d711
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619836"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a><span data-ttu-id="0d42a-101">EventSource.WriteEvent impls 必须传递它接收的相同参数 WriteEvent（以及 ID）</span><span class="sxs-lookup"><span data-stu-id="0d42a-101">EventSource.WriteEvent impls must pass WriteEvent the same parameters that it received (plus ID)</span></span>

#### <a name="details"></a><span data-ttu-id="0d42a-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="0d42a-102">Details</span></span>

<span data-ttu-id="0d42a-103">运行时现在强制执行指定以下内容的合同：如果类派生自 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 且用于定义 ETW 事件方法，它必须使用事件 ID（后跟已传递给 ETW 事件方法的相同参数）调用基类 <code>EventSource.WriteEvent</code> 方法。</span><span class="sxs-lookup"><span data-stu-id="0d42a-103">The runtime now enforces the contract that specifies the following: A class derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> that defines an ETW event method must call the base class <code>EventSource.WriteEvent</code> method with the event ID followed by the same arguments that the ETW event method was passed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0d42a-104">建议</span><span class="sxs-lookup"><span data-stu-id="0d42a-104">Suggestion</span></span>

<span data-ttu-id="0d42a-105">如果 <xref:System.IndexOutOfRangeException?displayProperty=fullName> 读取违反此协定的事件源进程中的 <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> 数据，则将引发 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 异常。</span><span class="sxs-lookup"><span data-stu-id="0d42a-105">An <xref:System.IndexOutOfRangeException?displayProperty=fullName> exception is thrown if an <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> reads <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> data in process for an event source that violates this contract.</span></span>

| <span data-ttu-id="0d42a-106">“属性”</span><span class="sxs-lookup"><span data-stu-id="0d42a-106">Name</span></span>    | <span data-ttu-id="0d42a-107">“值”</span><span class="sxs-lookup"><span data-stu-id="0d42a-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0d42a-108">范围</span><span class="sxs-lookup"><span data-stu-id="0d42a-108">Scope</span></span>   |<span data-ttu-id="0d42a-109">次要</span><span class="sxs-lookup"><span data-stu-id="0d42a-109">Minor</span></span>|
|<span data-ttu-id="0d42a-110">Version</span><span class="sxs-lookup"><span data-stu-id="0d42a-110">Version</span></span>|<span data-ttu-id="0d42a-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="0d42a-111">4.5.1</span></span>|
|<span data-ttu-id="0d42a-112">类型</span><span class="sxs-lookup"><span data-stu-id="0d42a-112">Type</span></span>|<span data-ttu-id="0d42a-113">运行时</span><span class="sxs-lookup"><span data-stu-id="0d42a-113">Runtime</span></span>|
