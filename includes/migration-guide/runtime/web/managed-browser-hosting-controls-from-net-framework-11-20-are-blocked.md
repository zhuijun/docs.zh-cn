---
ms.openlocfilehash: 83d3f24680531d1e447f047151a28c98ce0da04b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619870"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a><span data-ttu-id="0d711-101">锁定承载来自 .NET Framework 1.1 和 2.0 的控件的托管浏览器</span><span class="sxs-lookup"><span data-stu-id="0d711-101">Managed browser hosting controls from the .NET Framework 1.1 and 2.0 are blocked</span></span>

#### <a name="details"></a><span data-ttu-id="0d711-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="0d711-102">Details</span></span>

<span data-ttu-id="0d711-103">Internet Explorer 中阻止对这些控件的承载。</span><span class="sxs-lookup"><span data-stu-id="0d711-103">Hosting these controls is blocked in Internet Explorer.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0d711-104">建议</span><span class="sxs-lookup"><span data-stu-id="0d711-104">Suggestion</span></span>

<span data-ttu-id="0d711-105">Internet Explorer 将无法启动使用用于承载控件的托管浏览器的应用程序。</span><span class="sxs-lookup"><span data-stu-id="0d711-105">Internet Explorer will fail to launch an application that uses managed browser hosting controls.</span></span> <span data-ttu-id="0d711-106">通过将注册表子项 <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> 的 EnableIEHosting 值设置为 <code>1</code>（对于 x86 系统和 x64 系统上的 32 位处理器），并将注册表子项 <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> 的 <code>EnableIEHosting</code> 值设置为 <code>1</code>（对于 x64 系统上的 64 位处理器），可以还原之前的行为。</span><span class="sxs-lookup"><span data-stu-id="0d711-106">The previous behavior can be restored by setting the EnableIEHosting value of the registry subkey <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> to <code>1</code> for x86 systems and for 32-bit processes on x64 systems, and by setting the <code>EnableIEHosting</code> value of the registry subkey <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code> to <code>1</code> for 64-bit processes on x64 systems.</span></span>

| <span data-ttu-id="0d711-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="0d711-107">Name</span></span>    | <span data-ttu-id="0d711-108">“值”</span><span class="sxs-lookup"><span data-stu-id="0d711-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0d711-109">范围</span><span class="sxs-lookup"><span data-stu-id="0d711-109">Scope</span></span>   |<span data-ttu-id="0d711-110">次要</span><span class="sxs-lookup"><span data-stu-id="0d711-110">Minor</span></span>|
|<span data-ttu-id="0d711-111">Version</span><span class="sxs-lookup"><span data-stu-id="0d711-111">Version</span></span>|<span data-ttu-id="0d711-112">4.5</span><span class="sxs-lookup"><span data-stu-id="0d711-112">4.5</span></span>|
|<span data-ttu-id="0d711-113">类型</span><span class="sxs-lookup"><span data-stu-id="0d711-113">Type</span></span>|<span data-ttu-id="0d711-114">运行时</span><span class="sxs-lookup"><span data-stu-id="0d711-114">Runtime</span></span>|
