---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 55f70157b6759c5e1cb45da20eed928fa1d4a183
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176053"
---
# \<commonBehaviors>

<span data-ttu-id="6f2b9-101">`commonBehaviors` 节只能在 machine.config 文件中定义。</span><span class="sxs-lookup"><span data-stu-id="6f2b9-101">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="6f2b9-102">它定义了名为 `endpointBehaviors` 和 `serviceBehaviors` 的两个子集合。</span><span class="sxs-lookup"><span data-stu-id="6f2b9-102">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="6f2b9-103">每个集合分别定义计算机上所有 WCF 终结点和服务所使用的行为元素。</span><span class="sxs-lookup"><span data-stu-id="6f2b9-103">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="6f2b9-104">在 `endpointBehaviors` 中定义的行为只适用于客户端，在 `serviceBehaviors` 中定义的行为只适用于服务。</span><span class="sxs-lookup"><span data-stu-id="6f2b9-104">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="6f2b9-105">如果在 `commonBehaviors` 和 `behaviors` 节中都定义某行为，则 `behaviors` 节中的行为优先。</span><span class="sxs-lookup"><span data-stu-id="6f2b9-105">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
