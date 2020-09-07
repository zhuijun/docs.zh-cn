---
ms.openlocfilehash: 086dac69d085d070511fcfd5820bd2644ee4598e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497473"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a><span data-ttu-id="1215a-101">Marshal.SizeOf 和 Marshal.PtrToStructure 重载中断动态代码</span><span class="sxs-lookup"><span data-stu-id="1215a-101">Marshal.SizeOf and Marshal.PtrToStructure overloads break dynamic code</span></span>

#### <a name="details"></a><span data-ttu-id="1215a-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="1215a-102">Details</span></span>

<span data-ttu-id="1215a-103">从 .NET Framework 4.5.1 开始，动态绑定到方法 <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>、<xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>、<xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>、<xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>、<xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> 或 <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>（例如通过 Windows PowerShell、IronPython 或 C# dynamic 关键字）将引发 <code>MethodInvocationExceptions</code>，因为这些方法的新重载已添加，使得对于脚本引擎而言可能不明确。</span><span class="sxs-lookup"><span data-stu-id="1215a-103">Beginning in the .NET Framework 4.5.1, dynamically binding to the methods <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, or <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (via Windows PowerShell, IronPython, or the C# dynamic keyword, for example) can result in <code>MethodInvocationExceptions</code> because new overloads of these methods have been added that may be ambiguous to the scripting engines.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1215a-104">建议</span><span class="sxs-lookup"><span data-stu-id="1215a-104">Suggestion</span></span>

<span data-ttu-id="1215a-105">更新脚本以清楚指示应使用哪个重载。</span><span class="sxs-lookup"><span data-stu-id="1215a-105">Update scripts to clearly indicate which overload should be used.</span></span> <span data-ttu-id="1215a-106">通常，这可通过将方法的类型参数显式转换为 <xref:System.Type> 来实现。</span><span class="sxs-lookup"><span data-stu-id="1215a-106">This can typically done by explicitly casting the methods' type parameters as <xref:System.Type>.</span></span> <span data-ttu-id="1215a-107">有关如何解决此问题的详细信息和示例，请参阅[此链接](https://support.microsoft.com/kb/2909958/)。</span><span class="sxs-lookup"><span data-stu-id="1215a-107">See [this link](https://support.microsoft.com/kb/2909958/) for more detail and examples of how to workaround the issue.</span></span>

| <span data-ttu-id="1215a-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="1215a-108">Name</span></span>    | <span data-ttu-id="1215a-109">“值”</span><span class="sxs-lookup"><span data-stu-id="1215a-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1215a-110">范围</span><span class="sxs-lookup"><span data-stu-id="1215a-110">Scope</span></span>   |<span data-ttu-id="1215a-111">次要</span><span class="sxs-lookup"><span data-stu-id="1215a-111">Minor</span></span>|
|<span data-ttu-id="1215a-112">Version</span><span class="sxs-lookup"><span data-stu-id="1215a-112">Version</span></span>|<span data-ttu-id="1215a-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="1215a-113">4.5.1</span></span>|
|<span data-ttu-id="1215a-114">类型</span><span class="sxs-lookup"><span data-stu-id="1215a-114">Type</span></span>|<span data-ttu-id="1215a-115">运行时</span><span class="sxs-lookup"><span data-stu-id="1215a-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="1215a-116">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="1215a-116">Affected APIs</span></span>

<span data-ttu-id="1215a-117">无法通过 API 分析检测到。</span><span class="sxs-lookup"><span data-stu-id="1215a-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
