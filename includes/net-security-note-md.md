---
ms.openlocfilehash: 8b0edd9a49ca431355ab4f57fa041c5d1756d7eb
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855656"
---
> [!CAUTION]
> <span data-ttu-id="0cf5d-101">代码访问安全性 (CA) 和部分受信任代码</span><span class="sxs-lookup"><span data-stu-id="0cf5d-101">Code Access Security (CAS) and Partially Trusted Code</span></span>
>
> <span data-ttu-id="0cf5d-102">.NET Framework 提供一种机制，对在相同应用程序中运行的不同代码强制实施不同的信任级别，该机制称为代码访问安全性 (CAS)。</span><span class="sxs-lookup"><span data-stu-id="0cf5d-102">The .NET Framework provides a mechanism for the enforcement of varying levels of trust on different code running in the same application called Code Access Security (CAS).</span></span>
>
> <span data-ttu-id="0cf5d-103">**.NET Core、.NET 5 或更高版本中不支持 CAS。低于7.0 的 c # 版本不支持 CAS。**</span><span class="sxs-lookup"><span data-stu-id="0cf5d-103">**CAS is not supported in .NET Core, .NET 5, or later versions. CAS is not supported by versions of C# later than 7.0.**</span></span>
>
> <span data-ttu-id="0cf5d-104">.NET Framework 中的 CAS 不应作为一种机制，用于根据代码来源或其他标识方面强制实施安全边界。</span><span class="sxs-lookup"><span data-stu-id="0cf5d-104">CAS in .NET Framework should not be used as a mechanism for enforcing security boundaries based on code origination or other identity aspects.</span></span> <span data-ttu-id="0cf5d-105">不支持将 CA 和安全透明代码用作部分受信任的代码（尤其是未知来源的代码）的安全边界。</span><span class="sxs-lookup"><span data-stu-id="0cf5d-105">CAS and Security-Transparent Code are not supported as a security boundary with partially trusted code, especially code of unknown origin.</span></span> <span data-ttu-id="0cf5d-106">建议在未实施其他安全措施的情况下，不要加载和执行未知来源的代码。</span><span class="sxs-lookup"><span data-stu-id="0cf5d-106">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span>
>
> <span data-ttu-id="0cf5d-107">此策略适用于 .NET Framework 的所有版本，但不适用于 Silverlight 中所含的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="0cf5d-107">This policy applies to all versions of .NET Framework, but does not apply to the .NET Framework included in Silverlight.</span></span>
