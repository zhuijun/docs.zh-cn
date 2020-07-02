---
ms.openlocfilehash: a44458484ea09c566defeabc9b604bd55d994e93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617521"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="5c076-101">在启用触摸的系统上调用 System.Windows.Input.PenContext.Disable 可能会引发 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="5c076-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

#### <a name="details"></a><span data-ttu-id="5c076-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="5c076-102">Details</span></span>

<span data-ttu-id="5c076-103">在某些情况下，在启用触摸的系统上调用内部 **System.Windows.Intput.PenContext.Disable** 方法可能会因为重新进入而引发未处理的 `T:System.ArgumentException`。</span><span class="sxs-lookup"><span data-stu-id="5c076-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled `T:System.ArgumentException` because of reentrancy.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5c076-104">建议</span><span class="sxs-lookup"><span data-stu-id="5c076-104">Suggestion</span></span>

<span data-ttu-id="5c076-105">此问题已在 .NET Framework 4.7 中得到解决。</span><span class="sxs-lookup"><span data-stu-id="5c076-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="5c076-106">若要避免此异常，升级到 .NET Framework 4.7 及以上版本。</span><span class="sxs-lookup"><span data-stu-id="5c076-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>

| <span data-ttu-id="5c076-107">“属性”</span><span class="sxs-lookup"><span data-stu-id="5c076-107">Name</span></span>    | <span data-ttu-id="5c076-108">“值”</span><span class="sxs-lookup"><span data-stu-id="5c076-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5c076-109">范围</span><span class="sxs-lookup"><span data-stu-id="5c076-109">Scope</span></span>   | <span data-ttu-id="5c076-110">边缘</span><span class="sxs-lookup"><span data-stu-id="5c076-110">Edge</span></span>        |
| <span data-ttu-id="5c076-111">Version</span><span class="sxs-lookup"><span data-stu-id="5c076-111">Version</span></span> | <span data-ttu-id="5c076-112">4.6.1</span><span class="sxs-lookup"><span data-stu-id="5c076-112">4.6.1</span></span>       |
| <span data-ttu-id="5c076-113">类型</span><span class="sxs-lookup"><span data-stu-id="5c076-113">Type</span></span>    | <span data-ttu-id="5c076-114">重定目标</span><span class="sxs-lookup"><span data-stu-id="5c076-114">Retargeting</span></span> |
