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
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>如何：使用反射获取类型和成员信息
<xref:System.Reflection> 命名空间包含许多获取关于类型及其成员的信息的方法。 本文介绍其中一种方法：<xref:System.Type.GetMembers%2A?displayProperty=nameWithType>。 有关其他信息，请参阅[反射概述](reflection.md)。
  
## <a name="example"></a>示例

下例演示通过使用反射获取类型和成员信息：

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>请参阅

- [使用应用程序域进行编程](../app-domains/application-domains.md#programming-with-application-domains)
- [反射](reflection.md)
- [使用应用程序域](../app-domains/use.md)
