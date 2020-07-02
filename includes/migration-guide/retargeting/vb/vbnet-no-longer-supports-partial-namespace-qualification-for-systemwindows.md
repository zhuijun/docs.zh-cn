---
ms.openlocfilehash: cef8096c971da8ae245ff974697022f350cb9195
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616023"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="bf3a8-101">VB.NET 不再支持 System.Windows API 的部分命名空间限定</span><span class="sxs-lookup"><span data-stu-id="bf3a8-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

#### <a name="details"></a><span data-ttu-id="bf3a8-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="bf3a8-102">Details</span></span>

<span data-ttu-id="bf3a8-103">从 .NET Framework 4.5.2 开始，VB.NET 项目无法通过部分限定命名空间指定 System.Windows API。</span><span class="sxs-lookup"><span data-stu-id="bf3a8-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="bf3a8-104">例如，对 `Windows.Forms.DialogResult` 的引用将失败。</span><span class="sxs-lookup"><span data-stu-id="bf3a8-104">For example, referring to `Windows.Forms.DialogResult` will fail.</span></span> <span data-ttu-id="bf3a8-105">而代码必须引用完全限定名称 (<xref:System.Windows.Forms.DialogResult>)，或导入特定命名空间并仅引用 <xref:System.Windows.Forms.DialogResult?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="bf3a8-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bf3a8-106">建议</span><span class="sxs-lookup"><span data-stu-id="bf3a8-106">Suggestion</span></span>

<span data-ttu-id="bf3a8-107">应更新代码，以使用简单名称（并导入相关命名空间）或使用完全限定名称来引用 `System.Windows` API。</span><span class="sxs-lookup"><span data-stu-id="bf3a8-107">Code should be updated to refer to `System.Windows` APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>

| <span data-ttu-id="bf3a8-108">“属性”</span><span class="sxs-lookup"><span data-stu-id="bf3a8-108">Name</span></span>    | <span data-ttu-id="bf3a8-109">“值”</span><span class="sxs-lookup"><span data-stu-id="bf3a8-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bf3a8-110">范围</span><span class="sxs-lookup"><span data-stu-id="bf3a8-110">Scope</span></span>   | <span data-ttu-id="bf3a8-111">次要</span><span class="sxs-lookup"><span data-stu-id="bf3a8-111">Minor</span></span>       |
| <span data-ttu-id="bf3a8-112">Version</span><span class="sxs-lookup"><span data-stu-id="bf3a8-112">Version</span></span> | <span data-ttu-id="bf3a8-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="bf3a8-113">4.5.2</span></span>       |
| <span data-ttu-id="bf3a8-114">类型</span><span class="sxs-lookup"><span data-stu-id="bf3a8-114">Type</span></span>    | <span data-ttu-id="bf3a8-115">重定目标</span><span class="sxs-lookup"><span data-stu-id="bf3a8-115">Retargeting</span></span> |
