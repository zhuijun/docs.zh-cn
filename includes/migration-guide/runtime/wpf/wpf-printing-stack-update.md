---
ms.openlocfilehash: 5e2e8d1ec5d698d1c1649c2a0a1b4b77dbdf4022
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621117"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="0ae72-101">WPF 打印堆栈更新</span><span class="sxs-lookup"><span data-stu-id="0ae72-101">WPF Printing Stack Update</span></span>

#### <a name="details"></a><span data-ttu-id="0ae72-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="0ae72-102">Details</span></span>

<span data-ttu-id="0ae72-103">WPF 打印 API 现在使用 <xref:System.Printing.PrintQueue?displayProperty=fullName> 调用窗口的打印文档包 API，以支持现已弃用的 XPS 打印 API。</span><span class="sxs-lookup"><span data-stu-id="0ae72-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=fullName> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="0ae72-104">这一更改是基于可维护性考虑的，因此用户和开发者应该都不会看到任何行为或 API 使用变化。</span><span class="sxs-lookup"><span data-stu-id="0ae72-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="0ae72-105">当在 Windows 10 创意者更新中运行时，此新打印堆栈默认情况下处于启用状态。</span><span class="sxs-lookup"><span data-stu-id="0ae72-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="0ae72-106">在旧版 Windows 中，旧打印堆栈将继续像过去一样运行。</span><span class="sxs-lookup"><span data-stu-id="0ae72-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0ae72-107">建议</span><span class="sxs-lookup"><span data-stu-id="0ae72-107">Suggestion</span></span>

<span data-ttu-id="0ae72-108">若要在 Windows 10 创意者更新中使用旧堆栈，请将 <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> 注册表项的 <code>UseXpsOMPrinting</code> REG_DWORD 值设置为 <code>1</code>。</span><span class="sxs-lookup"><span data-stu-id="0ae72-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>

| <span data-ttu-id="0ae72-109">“属性”</span><span class="sxs-lookup"><span data-stu-id="0ae72-109">Name</span></span>    | <span data-ttu-id="0ae72-110">值</span><span class="sxs-lookup"><span data-stu-id="0ae72-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0ae72-111">范围</span><span class="sxs-lookup"><span data-stu-id="0ae72-111">Scope</span></span>   |<span data-ttu-id="0ae72-112">边缘</span><span class="sxs-lookup"><span data-stu-id="0ae72-112">Edge</span></span>|
|<span data-ttu-id="0ae72-113">Version</span><span class="sxs-lookup"><span data-stu-id="0ae72-113">Version</span></span>|<span data-ttu-id="0ae72-114">4.7</span><span class="sxs-lookup"><span data-stu-id="0ae72-114">4.7</span></span>|
|<span data-ttu-id="0ae72-115">类型</span><span class="sxs-lookup"><span data-stu-id="0ae72-115">Type</span></span>|<span data-ttu-id="0ae72-116">运行时</span><span class="sxs-lookup"><span data-stu-id="0ae72-116">Runtime</span></span>|
