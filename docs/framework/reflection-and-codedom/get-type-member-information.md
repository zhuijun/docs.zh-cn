---
title: 如何：使用反射获取类型和成员信息
description: 了解如何通过 System.Reflection 命名空间使用反射获取类型和成员信息。
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: fa7af39c0addb328944a03236c26982301caf722
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865315"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="5c85e-103">如何：使用反射获取类型和成员信息</span><span class="sxs-lookup"><span data-stu-id="5c85e-103">How to: Get type and member information by using reflection</span></span>
<span data-ttu-id="5c85e-104"><xref:System.Reflection> 命名空间包含许多获取关于类型及其成员的信息的方法。</span><span class="sxs-lookup"><span data-stu-id="5c85e-104">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="5c85e-105">本文介绍其中一种方法：<xref:System.Type.GetMembers%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="5c85e-105">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5c85e-106">有关其他信息，请参阅[反射概述](reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="5c85e-106">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="5c85e-107">示例</span><span class="sxs-lookup"><span data-stu-id="5c85e-107">Example</span></span>

<span data-ttu-id="5c85e-108">下例演示通过使用反射获取类型和成员信息：</span><span class="sxs-lookup"><span data-stu-id="5c85e-108">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="5c85e-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="5c85e-109">See also</span></span>

- [<span data-ttu-id="5c85e-110">使用应用程序域进行编程</span><span class="sxs-lookup"><span data-stu-id="5c85e-110">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="5c85e-111">反射</span><span class="sxs-lookup"><span data-stu-id="5c85e-111">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="5c85e-112">使用应用程序域</span><span class="sxs-lookup"><span data-stu-id="5c85e-112">Use application domains</span></span>](../app-domains/use.md)
