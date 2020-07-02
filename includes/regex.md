---
ms.openlocfilehash: b893966ceb65246ed6a7d214011b17ca14c50d5a
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85802841"
---

> [!WARNING]
> <span data-ttu-id="cb419-101">如果使用 <xref:System.Text.RegularExpressions> 处理不受信任的输入，则传递一个超时。</span><span class="sxs-lookup"><span data-stu-id="cb419-101">When using <xref:System.Text.RegularExpressions> to process untrusted input, pass a timeout.</span></span> <span data-ttu-id="cb419-102">恶意用户可能会向 `RegularExpressions` 提供输入，从而导致[拒绝服务攻击](https://www.us-cert.gov/ncas/tips/ST04-015)。</span><span class="sxs-lookup"><span data-stu-id="cb419-102">A malicious user can provide input to `RegularExpressions` causing a [Denial-of-Service attack](https://www.us-cert.gov/ncas/tips/ST04-015).</span></span> <span data-ttu-id="cb419-103">使用 `RegularExpressions` 的 ASP.NET Core 框架 API 会传递一个超时。</span><span class="sxs-lookup"><span data-stu-id="cb419-103">ASP.NET Core framework APIs that use `RegularExpressions` pass a timeout.</span></span>
