---
ms.openlocfilehash: 8b0edd9a49ca431355ab4f57fa041c5d1756d7eb
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855656"
---
> [!CAUTION]
> 代码访问安全性 (CA) 和部分受信任代码
>
> .NET Framework 提供一种机制，对在相同应用程序中运行的不同代码强制实施不同的信任级别，该机制称为代码访问安全性 (CAS)。
>
> **.NET Core、.NET 5 或更高版本中不支持 CAS。低于7.0 的 c # 版本不支持 CAS。**
>
> .NET Framework 中的 CAS 不应作为一种机制，用于根据代码来源或其他标识方面强制实施安全边界。 不支持将 CA 和安全透明代码用作部分受信任的代码（尤其是未知来源的代码）的安全边界。 建议在未实施其他安全措施的情况下，不要加载和执行未知来源的代码。
>
> 此策略适用于 .NET Framework 的所有版本，但不适用于 Silverlight 中所含的 .NET Framework。
