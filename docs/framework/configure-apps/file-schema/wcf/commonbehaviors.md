---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2020
ms.locfileid: "61704357"
---
# \<commonBehaviors>
`commonBehaviors` 节只能在 machine.config 文件中定义。 它定义了名为 `endpointBehaviors` 和 `serviceBehaviors` 的两个子集合。  每个集合分别定义计算机上所有 WCF 终结点和服务所使用的行为元素。 在 `endpointBehaviors` 中定义的行为只适用于客户端，在 `serviceBehaviors` 中定义的行为只适用于服务。 如果在 `commonBehaviors` 和 `behaviors` 节中都定义某行为，则 `behaviors` 节中的行为优先。
